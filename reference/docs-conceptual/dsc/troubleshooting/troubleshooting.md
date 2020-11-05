---
ms.date: 10/30/2018
keywords: dsc,powershell,設定,安裝
title: 疑難排解 DSC
description: 此文章提供常見錯誤的疑難排解指示。
ms.openlocfilehash: 2ac86689fa2695add247995bfb91c0ea85e22d60
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656254"
---
# <a name="troubleshooting-dsc"></a>疑難排解 DSC

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

此文章提供常見錯誤的疑難排解指示。

## <a name="winrm-dependency"></a>WinRM 相依性

Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。 若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。

## <a name="using-get-dscconfigurationstatus"></a>使用 Get-DscConfigurationStatus

[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet 會從目標節點取得設定狀態的相關資訊。 高級物件已傳回，此物件包含關於設定是否順利執行的高等級資訊。 您可以深入了解此物件，以探索有關設定執行的詳細資料，例如︰

- 所有失敗的資源
- 要求重新開機的任何資源
- 在設定執行時中繼設定的設定
- 等。

下列的參數集傳回上次設定執行時的狀態資訊︰

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

下列的參數集傳回所有先前設定執行時的狀態資訊︰

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a>範例

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a>我的指令碼不執行：使用 DSC 記錄診斷指令碼錯誤

像所有的 Windows 軟體一樣，DSC 會在[記錄](/windows/desktop/EventLog/about-event-logging)中記錄錯誤和事件，並可從[事件檢視器](https://support.microsoft.com/hub/4338813/windows-help)加以檢視。 檢查這些記錄檔可以幫助您了解特定作業失敗的原因，以及如何避免失敗再度發生。
撰寫設定指令碼可能很困難，因此為方便您在撰寫時追蹤錯誤，請使用 DSC 記錄資源在 DSC 分析事件記錄檔中追蹤設定進度。

## <a name="where-are-dsc-event-logs"></a>DSC 事件記錄檔在哪裡？

在事件檢視器中，DSC 事件位於： **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**

您也可以執行對應的 PowerShell Cmdlet [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)，來檢視事件記錄檔：

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

如上所示，DSC 的主要記錄檔名稱是 **Microsoft->Windows->DSC** (為畫面簡潔起見，這裡不顯示 Windows 下的其他記錄檔名稱)。 主要名稱會附加在通道名稱後面，以建立完整的記錄檔名稱。 DSC 引擎主要會寫入三種記錄：[作業、分析和偵錯記錄](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11))。
因為分析和偵錯記錄檔預設是關閉的，您應該在 [事件檢視器] 中啟用它們。
啟用方法是在 Windows PowerShell 中輸入 Show-EventLog；或依序按一下 [開始] 按鈕、[控制台]、[系統管理工具] 和 [事件檢視器]。 在事件檢視器的 [檢視] 功能表中，按一下 [顯示分析與偵錯記錄]。 分析通道的記錄名稱是 **Microsoft-Windows-Dsc/Analytic** ，偵錯通道則是 **Microsoft-Windows-Dsc/Debug** 。 您也可以使用 [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) 公用程式來啟用記錄，如下例所示。

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a>DSC 記錄檔包含哪些內容？

DSC 記錄檔會根據訊息的重要性分成三個記錄檔通道。 DSC 的作業記錄檔包含所有錯誤訊息，可用來識別問題。 分析記錄檔掌握巨量的事件，可以識別錯誤發生的位置。 這個通道也包含詳細資訊訊息 (如果有的話)。 偵錯記錄檔包含的記錄可以幫助您了解錯誤是如何發生的。 DSC 事件訊息的結構為，每個事件訊息的開頭都是唯一代表 DSC 作業的工作識別碼。 下例嘗試取得記入作業 DSC 記錄檔的第一筆事件的訊息。

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

DSC 事件的特定記錄結構，能讓使用者彙總一個 DSC 工作的事件。 其結構如下所示：

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a>收集單一 DSC 作業的事件

DSC 事件記錄檔包含各種 DSC 作業產生的事件。 不過，您通常只關心某個特定作業的詳細資料。 DSC 的所有記錄都是依照每個 DSC 作業的唯一工作識別碼屬性分組 。 所有 DSC 事件的第一個屬性值都是顯示工作識別碼。 下列步驟說明如何將所有事件累計到分組的陣列結構中。

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

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

您可以使用 [Where-Object](/powershell/module/microsoft.powershell.core/where-object) 擷取變數 `$SeparateDscOperations` 中的資料。 下面有五個案例，您要擷取其資料以疑難排解 DSC：

### <a name="1-operations-failures"></a>1：作業失敗

所有的事件都有[嚴重性等級](/windows/desktop/WES/defining-severity-levels)。 這項資訊可以用來識別錯誤事件：

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a>2：過去半小時內執行的作業詳細資料

`TimeCreated` 是每個 Windows 事件都有的屬性，指出事件的建立時間。 比較這個屬性和特定的日期/時間物件，可用以篩選所有事件：

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a>3：最新作業的訊息

最新的作業會儲存在陣列群組 `$SeparateDscOperations` 的第一個索引中。
查詢索引 0 的群組訊息會傳回最新作業的所有訊息：

```powershell
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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a>4：近期的作業失敗錯誤訊息記錄

`$SeparateDscOperations[0].Group` 包含最新作業的事件集。 執行 `Where-Object` Cmdlet 會根據層級顯示名稱篩選事件。 結果儲存在 `$myFailedEvent` 變數中，可進一步解析以取得事件訊息：

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with
 -Path parameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a>5：針對特定工作識別碼產生的所有事件。

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a>使用 xDscDiagnostics 分析 DSC 記錄

**xDscDiagnostics** 是 PowerShell 模組，由數個可協助分析電腦上 DSC 失敗的函數組成。 這些函式可協助您識別過去 DSC 作業的所有本機事件，或 (具有效認證的) 遠端電腦的 DSC 事件。 本文中，DSC 作業一詞是用來定義從開始到結束的單一唯一 DSC 執行。 例如，`Test-DscConfiguration` 就會是另外一個 DSC 作業。 同樣地，DSC 中每個其他的 Cmdlet (例如 `Get-DscConfiguration`、`Start-DscConfiguration` 等等) 各自都可能被視為個別的 DSC 作業。 [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics) 會說明函數。 執行 `Get-Help <cmdlet name>` 即可取得說明。

### <a name="getting-details-of-dsc-operations"></a>取得 DSC 作業的詳細資訊

`Get-xDscOperation` 函數可讓您尋找在一或多部電腦上執行的 DSC 作業結果，並傳回物件，其中包含每個 DSC 作業產生的事件集合。 例如，在下列輸出中，執行了三個命令。 第一個成功，而其他兩個失敗了。 這些結果會摘述在 `Get-xDscOperation` 輸出中。

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

您也可以使用 `Newest` 參數指定只要最近作業的結果︰

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a>取得 DSC 事件的詳細資訊

`Trace-xDscOperation` Cmdlet 傳回的物件包含了事件集合、其事件類型，以及從特定 DSC 作業產生的訊息輸出。 一般而言，當您使用 `Get-xDscOperation` 在任何作業中發現失敗時，您都可以追蹤該作業，找出導致失敗的事件。

使用 `SequenceID` 參數以取得特定電腦的特定作業事件。
例如，`SequenceID` 如果指定為 9，則 `Trace-xDscOperaion` 就會取得上一個作業的第 9 筆 DSC 作業追蹤記錄︰

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

傳遞指派給特定 DSC 作業的 **GUID** (如 `Get-xDscOperation` Cmdlet 所傳回) 來取得該 DSC 作業的事件詳細資料：

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

請注意，由於 `Trace-xDscOperation` 會彙總分析、偵錯和作業記錄的事件，所以會提示您啟用這些記錄，如上文所述。

此外，您也可以將 `Trace-xDscOperation` 的輸出存入變數中來收集事件相關資訊。 您可以使用下列命令來顯示特定 DSC 作業的所有事件。

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

這和 `Get-WinEvent` Cmdlet 會顯示相同的結果，如以下輸出所示：

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

理想的情況是先使用 `Get-xDscOperation` 列出電腦上執行的最新幾個 DSC 設定。 接著使用 `Trace-xDscOperation` 檢查任何單一作業 (使用其 SequenceID 或 JobID)，探索它在幕後的工作內容。

### <a name="getting-events-for-a-remote-computer"></a>取得遠端電腦的事件

使用 `Trace-xDscOperation` Cmdlet 的 `ComputerName` 參數來取得遠端電腦上的事件詳細資訊。 執行這項作業之前，您必須先建立防火牆規則，允許在遠端電腦上進行遠端系統管理︰

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

現在，您可以在 `Trace-xDscOperation` 呼叫中指定該部電腦：

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a>我的資源不更新：如何重設快取

基於效率考量，DSC 引擎會快取實作為 PowerShell 模組的資源。
不過，這可能會在撰寫並同時測試資源時造成問題，因為在程序重新啟動前，DSC 會載入快取的版本。 讓 DSC 載入較新版本的唯一方法，是明確結束主控 DSC 引擎的程序。

同樣地，當您執行 `Start-DscConfiguration`，在新增及修改自訂的資源後，可能要重新啟動電腦才會執行修改的內容。 這是因為 DSC 是在 WMI 提供者主機處理程序 (WmiPrvSE) 中執行，通常一次會執行多個 WmiPrvSE 執行個體。 當您重新開機時，主機處理程序就會重新啟動，而快取也會清除。

若要順利回收設定和清除快取卻不重新開機，您必須停止然後再重新啟動主機處理程序。 您可以對每個執行個體都執行識別、停止和重新啟動程序。 或者如下文所示，使用 `DebugMode` 重新載入 PowerShell DSC 資源。

若要識別出並停止每個執行個體上主控 DSC 引擎的處理程序，您可以列出主控 DSC 引擎的 WmiPrvSE 處理程序識別碼。 然後，更新提供者、使用下列命令停止 WmiPrvSE 處理程序，再執行一次 **Start-DscConfiguration** 。

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

## <a name="using-debugmode"></a>使用 DebugMode

您可以設定 DSC 本機設定管理員 (LCM) 使用 `DebugMode` 在重新啟動主機處理程序時，一律清除快取。 設為 **TRUE** 時，會讓引擎一律重新載入 PowerShell DSC 資源。 資源完成撰寫後，您就可以將其設回 **FALSE** ，引擎會還原成快取模組行為。

下面的示範會說明 `DebugMode` 如何自動重新整理快取。 首先，我們來看一下預設設定：

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

您可以看到 `DebugMode` 設為 **"None"** 。

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

您將會看到檔案的內容：`$env:SystemDrive\OutputFromTestProviderDebugMode.txt` 是 **1** 。

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

這個指令碼會產生一個隨機數字，以此更新提供者程式碼。 在將 `DebugMode` 設定為 False 的情況下，`$env:SystemDrive\OutputFromTestProviderDebugMode.txt` 檔案的內容一律不會變更。

現在，在設定指令碼中將 `DebugMode` 設為 **"ForceModuleImport"** ：

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
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

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a>DSC 向 Windows 提取伺服器註冊時，傳回了「未預期的回應碼 InternalServerError」

將中繼設定套用至伺服器，以向 Windows 提取伺服器的執行個體註冊時，您可能會發生下列錯誤。

```
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

當伺服器上用來加密流量的憑證通用名稱 (CN) 與節點用來解析 URL 的 DNS 名稱不同時，就可能發生此問題。 更新 Windows 提取伺服器執行個體，以使用名稱經更正的憑證。

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a>在套用 DSC 組態後，執行 Sysprep 時發生錯誤

在套用 DSC 組態後，嘗試執行 Sysprep 將 Windows Server 一般化時，您可能會遇到下列錯誤。

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

不支援在使用 Windows PowerShell Desired State Configuration 設定伺服器後將伺服器一般化。 請改為在 Windows 安裝程式的特殊化階段完成之後，將組態套用至 Windows。

## <a name="see-also"></a>另請參閱

### <a name="concepts"></a>概念

- [建置自訂的 Windows PowerShell 預期狀態設定資源](../resources/authoringResource.md)

### <a name="other-resources"></a>其他資源

- [Windows PowerShell 預期狀態設定 Cmdlet](/powershell/module/psdesiredstateconfiguration/)
