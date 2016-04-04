# 疑難排解 DSC

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

本主題說明讓預期狀態設定 (DSC) 指令碼執行不發生錯誤的方法。 只要善加利用記錄檔追蹤錯誤，以及了解如何回收快取以查看資源變更的立即結果，您就可以更有效地疑難排解 DSC。 下面兩節會討論這些技術問題：

* 我的指令碼不執行：**使用 DSC 記錄診斷指令碼錯誤**
* 我的資源不更新：**如何重設快取**

## 我的指令碼不執行：使用 DSC 記錄診斷指令碼錯誤

像所有的 Windows 軟體一樣，DSC 會在[記錄檔](https://msdn.microsoft.com/library/windows/desktop/aa363632.aspx)中記錄錯誤和事件，[[事件檢視器]](http://windows.microsoft.com/windows/what-information-event-logs-event-viewer) 可檢視這些記錄。 檢查這些記錄檔可以幫助您了解特定作業失敗的原因，以及如何避免失敗再度發生。 撰寫設定指令碼可能很困難，因此為方便您在撰寫時追蹤錯誤，請使用 DSC 記錄資源在 DSC 分析事件記錄檔中追蹤設定進度。

## DSC 事件記錄檔在哪裡？

在 [事件檢視器] 中，DSC 事件位於：**Applications and Services Logs/Microsoft/Windows/Desired State Configuration**

您也可以執行對應的 PowerShell Cmdlet，[Get-WinEvent](https://technet.microsoft.com/library/hh849682.aspx)，來檢視事件記錄檔：

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                                                                                  
-----------                     -- ---------------- -------                                                                                                  
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
```

如上所示，DSC 的主要記錄檔名稱是 **Microsoft->Windows->DSC** (為畫面簡潔起見，這裡不顯示 Windows 的其他記錄檔名稱)。 主要名稱會附加在通道名稱後面，以建立完整的記錄檔名稱。 DSC 引擎主要會寫入三種記錄檔：[操作、分析和偵錯記錄檔](https://technet.microsoft.com/library/cc722404.aspx)。 因為分析和偵錯記錄檔預設是關閉的，您應該在 [事件檢視器] 中啟用它們。 啟用方法是在 Windows PowerShell 中輸入 Show-EventLog；或依序按一下 **[開始]** 按鈕、**[控制台]**、**[系統管理工具]** 和 **[事件檢視器]**。 在 [事件檢視器] 的 **[檢視]** 功能表中，按一下 **[顯示分析與偵錯記錄檔]**。 分析通道的記錄檔名稱是 **Microsoft-Windows-Dsc/Analytic**，偵錯通道則是 **Microsoft-Windows-Dsc/Debug**。 您也可以使用 [wevtutil](https://technet.microsoft.com/library/cc732848.aspx) 公用程式來啟用記錄檔，如下例所示。

```powershell
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
```

## DSC 記錄檔包含哪些內容？

DSC 記錄檔會根據訊息的重要性分成三個記錄檔通道。 DSC 的作業記錄檔包含所有錯誤訊息，可用來識別問題。 分析記錄檔掌握巨量的事件，可以識別錯誤發生的位置。 這個通道也包含詳細資訊訊息 (如果有的話)。 偵錯記錄檔包含的記錄可以幫助您了解錯誤是如何發生的。 DSC 事件訊息的結構為，每個事件訊息的開頭都是唯一代表 DSC 作業的工作識別碼。 下例嘗試取得記入作業 DSC 記錄檔的第一筆事件的訊息。

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} : 
Consistency engine was run successfully. 
```

DSC 事件的特定記錄結構，能讓使用者彙總一個 DSC 工作的事件。 結構如下：

**工作識別碼：<Guid>**
**<Event Message>**

## 收集單一 DSC 作業的事件

DSC 事件記錄檔包含各種 DSC 作業產生的事件。 不過，您通常只關心某個特定作業的詳細資料。 DSC 的所有記錄都是依照每個 DSC 作業的唯一工作識別碼屬性分組 。 所有 DSC 事件的第一個屬性值都是顯示工作識別碼。 下列步驟說明如何將所有事件累計到分組的陣列結構中。

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>
 
wevtutil.exe set-log “Microsoft-Windows-Dsc/Analytic” /q:true /e:true
wevtutil.exe set-log “Microsoft-Windows-Dsc/Debug” /q:True /e:true
 
<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>
 
Get-DscLocalConfigurationManager
 
<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>
 
$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)
 
 
<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}  
```

在此，變數 `$SeparateDscOperations` 包含依工作識別碼分組的記錄檔。 這個變數的每個陣列元素都代表一組依照不同 DSC 作業記錄的事件，讓您存取有關記錄檔的詳細資訊。

```
PS C:\> $SeparateDscOperations
 
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
PS C:\> $SeparateDscOperations[0].Group
   ProviderName: Microsoft-Windows-DSC
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...      
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...       
```

您可以使用 [Where-Object](https://technet.microsoft.com/library/ee177028.aspx) 擷取變數 `$SeparateDscOperations` 中的資料。 下面有五個案例，您要擷取其資料以疑難排解 DSC：

### 1：作業失敗

所有的事件都有[嚴重性層級](https://msdn.microsoft.com/library/dd996917(v=vs.85))。 這項資訊可以用來識別錯誤事件：

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### 2：過去半小時內執行的作業詳細資料

`TimeCreated` 是每個 Windows 事件都有的屬性，指出事件的建立時間。 比較這個屬性和特定的日期/時間物件，可用以篩選所有事件：

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}
Count Name                      Group                                                                     
----- ----                      -----                                                                     
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}   
```

### 3：最新作業的訊息

最新的作業會儲存在陣列群組 `$SeparateDscOperations` 的第一個索引中。 查詢索引 0 的群組訊息會傳回最新作業的所有訊息：

```powershelll
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : 
Displaying messages from built-in DSC resources:
 WMI channel 1 
 ResourceID:  
 Message : [INCH-VM]:                            [] Consistency check completed. 
```

### 4：近期的作業失敗錯誤訊息記錄

`$SeparateDscOperations[0].Group` 包含最新作業的事件集。 執行 `Where-Object` Cmdlet 會根據層級顯示名稱篩選事件。 結果儲存在 `$myFailedEvent` 變數中，可進一步解析以取得事件訊息：

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})
 
PS C:\> $myFailedEvent.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} : 
DSC Engine Error : 
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first. 
Error Code : 1 
```

### 5：針對特定工作識別碼產生的所有事件。

`$SeparateDscOperations` 是群組陣列，每一個都有和唯一工作識別碼相同的名稱。 執行 `Where-Object` Cmdlet 就可以擷取這些有特定工作識別碼的事件群組：

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC
 
TimeCreated                     Id LevelDisplayName Message                                               
-----------                     -- ---------------- -------                                               
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...      
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...  
```

## 使用 xDscDiagnostics 分析 DSC 記錄

**xDscDiagnostics** 是 PowerShell 模組，由兩個可協助分析電腦上 DSC 失敗的簡單函式組成：`Get-xDscOperation` 和 `Trace-xDscOperation`。 這些函式可協助您識別過去 DSC 作業的所有本機事件，或 (具有效認證的) 遠端電腦的 DSC 事件。 本文中，DSC 作業一詞是用來定義從開始到結束的單一唯一 DSC 執行。 例如，`Test-DscConfiguration` 就會是另外一個 DSC 作業。 同樣地，DSC 中每個其他的 Cmdlet (例如 `Get-DscConfiguration`、`Start-DscConfiguration` 等等) 各自都可能被視為個別的 DSC 作業。 [xDscDiagnostics](https://powershellgallery.com/packages/xDscDiagnostics) PowerShell 模組 (DSC Resource Kit) 中會說明這兩個函式，下文亦有詳細說明。 執行 `Get-Help <cmdlet name>` 即可取得說明。

## Get-xDscOperation

這個函式可讓您尋找在一部或多部電腦上執行的 DSC 作業結果，並傳回物件，其中包含每個 DSC 作業產生的事件集合。 例如，在下列輸出中，執行了三個命令。 第一個成功，而其他兩個失敗了。 這些結果會摘述在 `Get-xDscOperation` 輸出中。

TODO：取代顯示 Get-xDscOperation 輸出的這個映像

### 參數

* **Newest**：接受整數值，表示要顯示的作業數目。 預設會傳回 10 個最新的作業。 舉例來說：
  TODO：顯示 Get-xDscOperation -Newest 5
* **ComputerName**：接受字串陣列的參數，每一個都會包含您想要收集之 DSC 事件記錄檔資料的電腦名稱。 預設會收集本機電腦的資料。 若要啟用這項功能，您必須在遠端電腦執行下列命令，在提高權限的模式中收集事件
```powershell
  New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
* **Credential**：PSCredential 類型的參數，可協助存取 ComputerName 參數中所指定的電腦。

### 傳回的物件

Cmdlet 會傳回物件陣列，每個類型都是 **Microsoft.PowerShell.xDscDiagnostics.GroupedEvents**。 這個陣列中的每個物件都屬於不同的 DSC 作業。 這個物件預設顯示下列屬性
* **SequenceID**：根據時間指定指派給 DSC 作業的增量號碼。 例如，上次執行作業的 SequenceID 為 1，上次 DSC 作業的第二個作業的 SequenceID 為 2，以此類推。 這個數字是傳回的陣列中每個物件的另一個識別碼。
* **TimeCreated**：表示 DSC 作業開始時間的 DateTime 值。
* **ComputerName**：彙總結果的電腦名稱。
* **Result**：帶有值 **Failure** 或 **Success** 的字串，分別表示該 DSC 作業是否發生了錯誤。
* **AllEvents**：表示 DSC 作業產生事件集合的物件。

例如，下列輸出會顯示多部電腦的上次作業結果：
  TODO：取代顯示遠端電腦記錄的 Get-xDscOperation 圖片

## Trace-xDscOperation

這個 Cmdlet 傳回的物件包含了事件集合、其事件類型，以及從特定 DSC 作業產生的訊息輸出。 一般而言，當您使用 `Get-xDscOperation` 在任何作業中發現失敗時，您都可以追蹤該作業，找出導致失敗的事件。

### 參數

* **SequenceID**：這是指派給有關特定電腦任何作業的整數值。 藉由指定序列識別碼，假設 4，就會輸出上次是第 4 次的 DSC 作業

具有所指定順序識別碼的 Trace-xDscOperation
* **JobID**：這是 LCM xDscOperation 所指派，唯一識別作業的 GUID 值。 指定了 JobID 後，就會輸出對應的 DSC 作業追蹤。
  TODO：取代將 JobID 當做參數的 Trace-xDscOperation 圖片
* **ComputerName** 和 **Credential**：這些參數可讓您從遠端電腦收集追蹤：
```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -Action Allow
```
  TODO：取代在不同電腦上執行的 Trace-xDscOperation 圖片

請注意，由於 `Trace-xDscOperation` 會彙總分析、偵錯和作業記錄的事件，所以會提示您啟用這些記錄，如上文所述。

### 傳回的物件

此 Cmdlet 會傳回物件陣列，每個都是類型 `Microsoft.PowerShell.xDscDiagnostics.TraceOutput`。 這個陣列中的每個物件都包含下列欄位：
* **ComputerName**：要收集記錄檔的電腦名稱。
* **EventType**：這是包含事件類型資訊的列舉程式類型欄位。 它可以是下列任一項：
  - *Operational*：作業記錄檔中的事件。
  - *Analytic*：分析記錄檔中的事件。
  - *Debug*：偵錯記錄檔中的事件。
  - *Verbose*：在執行期間輸出為詳細資訊訊息的事件。 詳細資訊訊息讓識別已發行事件的順序變得更為容易。
  - *Error*：錯誤事件。 藉由尋找錯誤事件，通常可以快速找出失敗的原因。
* **TimeCreated**：表示 DSC 記錄事件的時間的 DateTime 值。
* **Message**：DSC 記錄到事件記錄檔中的訊息。

以下是這個物件中的欄位，可用於事件的詳細資訊，但預設不顯示：

* **JobID**：DSC 作業專用的工作識別碼 (GUID 格式)。
* **SequenceID**：DSC 作業在該部電腦的唯一 SequenceID。
* **Event**：這是 DSC 記錄的實際事件，類型為 `System.Diagnostics.Eventing.Reader.EventLogRecord`。 執行 Cmdlet `Get-WinEvent` 也可以取得它。 它包含工作、eventID 及事件層級等詳細資訊。

此外，您也可以將 `Trace-xDscOperation` 的輸出存入變數中來收集事件相關資訊。 您可以使用下列命令來顯示特定 DSC 作業的所有事件：

```powershell
(Trace-xDscOperation -SequenceID 3).Event
```

這和 `Get-WinEvent` Cmdlet 會顯示相同的結果，如以下輸出所示：
  TODO：什麼輸出？

理想的情況是先使用 `Get-xDscOperation` 列出電腦上執行的最新幾個 DSC 設定。 接著使用 `Trace-xDscOperation` 檢查任何單一作業 (使用其 SequenceID 或 JobID)，探索它在幕後的工作內容。

## 我的資源不更新：如何重設快取

基於效率考量，DSC 引擎會快取實作為 PowerShell 模組的資源。 不過，這可能會在撰寫並同時測試資源時造成問題，因為在程序重新啟動前，DSC 會載入快取的版本。 讓 DSC 載入較新版本的唯一方法，是明確結束主控 DSC 引擎的程序。

同樣地，當您執行 `Start-DscConfiguration`，在新增及修改自訂的資源後，可能要重新啟動電腦才會執行修改的內容。 這是因為 DSC 是在 WMI 提供者主機處理程序 (WmiPrvSE) 中執行，通常一次會執行多個 WmiPrvSE 執行個體。 當您重新開機時，主機處理程序就會重新啟動，而快取也會清除。

若要順利回收設定和清除快取卻不重新開機，您必須停止然後再重新啟動主機處理程序。 您可以對每個執行個體都執行識別、停止和重新啟動程序。 或者如下文所示，使用 `DebugMode` 重新載入 PowerShell DSC 資源。

若要識別出並停止每個執行個體上主控 DSC 引擎的處理程序，您可以列出主控 DSC 引擎的 WmiPrvSE 處理程序識別碼。 然後，更新提供者、使用下列命令停止 WmiPrvSE 處理程序，再執行一次 **Start-DscConfiguration**。

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers | 
Where-Object {$_.provider -like 'dsccore'} | 
Select-Object -ExpandProperty HostProcessIdentifier 

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## 使用 DebugMode

您可以設定 DSC 本機設定管理員 (LCM) 使用 `DebugMode` 在重新啟動主機處理程序時，一律清除快取。 設為 **TRUE** 時，會讓引擎一律重新載入 PowerShell DSC 資源。 資源完成撰寫後，您就可以將它設回 **FALSE**，引擎會還原成快取模組行為。

下面的示範會說明 `DebugMode` 如何自動重新整理快取。 首先，我們來看一下預設設定：

```
PS C:\> Get-DscLocalConfigurationManager
 
 
AllowModuleOverwrite           : False
CertificateID                  : 
ConfigurationID                : 
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     : 
DebugMode                      : False
DownloadManagerCustomData      : 
DownloadManagerName            : 
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :  
```

您可以看到 `DebugMode` 設為 **FALSE**。

若要安裝 `DebugMode` 示範，請使用下列 PowerShell 資源：

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
} 
```

現在，使用上述資源中的 `TestProviderDebugMode` 來撰寫設定：

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

您會看到檔案的內容：“**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” 是 **1**。

現在使用下列指令碼來更新提供者程式碼：

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

這個指令碼會產生一個隨機數字，以此更新提供者程式碼。 若 `DebugMode` 設為 false，檔案內容 “**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**” 絕不變更。

現在，在設定指令碼中將 `DebugMode` 設為 **TRUE**：

```powershell
LocalConfigurationManager
{
    DebugMode = $true
} 
```

當您再次執行上述指令碼時，會看到檔案的內容每次都不同。 (您可以執行 `Get-DscConfiguration` 檢查它)。 以下是另外兩次的執行結果 (執行指令碼時您的結果可能不同)：

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
20                                      localhost                              
 
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)
 
onlyProperty                            PSComputerName                         
------------                            --------------                         
14                                      localhost
```

## 另請參閱

### 參考資料
* [DSC 記錄檔資源](logResource.md)

### 概念
* [建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)

### 其他資源
* [Windows PowerShell 預期狀態設定 Cmdlet](https://technet.microsoft.com/en-us/library/dn521624(v=wps.630).aspx)


<!--HONumber=Mar16_HO1-->


