# 統一且一致的狀態和狀態表示法

已在此版本中為自動化組建 LCM 狀態與 DSC 狀態增加了一系列的增強功能。 這些包括整合且一致的狀態和狀態表示法、由 Get-DscConfigurationStatus Cmdlet傳回之狀態物件的可管理 datetime 屬性，及由 Get-DscLocalConfigurationManager Cmdlet 傳回之增強的 LCM 狀態詳細資料屬性。

LCM 狀態和 DSC 作業狀態的表示法根據下列規則進行重新瀏覽和整合︰
1.  Notprocessed 資源不會影響 LCM 狀態與 DSC 狀態。
2.  一旦遇到要求重新開機的資源，LCM 就會停止處理更多資源。
3.  要求重新開機的資源不處於所需的狀態，直到重新開機真正發生。
4.  在發生失敗的資源之後，只要其他資源不是依存於失敗的資源，LCM 就會持續處理更多資源。
5.  Get-DscConfigurationStatus Cmdlet 所傳回的整體狀態是所有資源狀態的超集。
6.  PendingReboot 狀態為 PendingConfiguration 狀態的超集。

下表說明一些典型狀況下的結果狀態和與狀態相關的屬性。

| **案例**                    | **LCMState\***       | **狀態** | **要求重新開機**  | **ResourcesInDesiredState**  | **ResourcesNotInDesiredState** |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | 閒置                 | Success    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | 失敗    | $false        | $null                        | F                              |
| S,F                             | PendingConfiguration | 失敗    | $false        | S                            | F                              |
| F,S                             | PendingConfiguration | 失敗    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | 失敗    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | 失敗    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Success    | $true         | S                            | r                              |
| F, r                            | PendingReboot        | 失敗    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Success    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Success    | $true         | $null                        | r                              |

^
S<sub>i</sub>︰一系列成功套用的資源
F<sub>i</sub>︰一系列套用失敗的資源
r︰需要重新開機的資源
\*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## Get-DscConfigurationStatus Cmdlet 中的增強功能

已在此版本中對 Get-DscConfigurationStatus Cmdlet 進行了一些增強功能。 先前由 Cmdlet 傳回的物件 StartDate 屬性為字串類型。 現在，它是 Datetime 類型，可根據 Datetime 物件內建內容讓複雜的選取和篩選更為容易。
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

以下為傳回所有 DSC 作業記錄的範例，此作業記錄發生在每週和今天相同的日子。
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

不變更節點設定的作業記錄 (也就是唯讀作業)。 因此，Test-DscConfiguration、Get-DscConfiguration 作業不會再次混入從 Get-DscConfigurationStatus Cmdlet 傳回的物件。
中繼設定的設定作業記錄會加入至 Get-DscConfigurationStatus Cmdlet 傳回的物件。

以下是從 Get-DscConfigurationStatus –All Cmdlet 傳回結果的範例。
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## Get-DscLocalConfigurationManager Cmdlet 中的增強功能
LCMStateDetail 的新欄位加入至從 Get-DscLocalConfigurationManager Cmdlet 傳回的物件。 LCMState「忙碌」時，就會將此欄位填滿。 它可以由下列 Cmdlet 擷取：
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

以下是連續監控設定的範例輸出，它需要遠端節點上的兩次重新開機。
```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
<!--HONumber=Mar16_HO2-->
