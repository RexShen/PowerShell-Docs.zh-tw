---
description: 說明如何解決排程工作的問題
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: 924205edb9d44724cfef201d84baa304ecde67ad
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207247"
---
# <a name="about-scheduled-jobs-troubleshooting"></a>關於排程工作的疑難排解

## <a name="short-description"></a>簡短描述

說明如何解決排程工作的問題

## <a name="long-description"></a>完整描述

本檔說明使用 PowerShell 的排程工作功能時，可能會遇到的一些問題，並建議解決這些問題的解決方案。

使用 PowerShell 排程工作之前，請參閱 [about_Scheduled_Jobs](about_Scheduled_Jobs.md) 以及相關的排程工作主題。

如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。

## <a name="cant-find-job-results"></a>找不到工作結果

### <a name="basic-method-for-getting-job-results-in-powershell"></a>在 PowerShell 中取得工作結果的基本方法

當排程工作執行時，它會建立排程工作的實例。 若要查看、管理和取得排程工作實例的結果，請使用 Job Cmdlet。

> [!NOTE]
> 若要在排程工作的實例上使用 Job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。 若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。

若要取得排程工作的所有實例清單，請使用 `Get-Job` Cmdlet。

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

`Get-Job`Cmdlet 會將 **ProcessJob** 物件沿著管線向下傳送。 此 `Format-Table` Cmdlet 會在資料表中顯示排程工作實例的 **名稱** 、 **識別碼** 和 **PSBeginTime** 屬性。

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

若要取得排程工作實例的結果，請使用 `Receive-Job` Cmdlet。 下列命令會取得 ProcessJob (ID = 50) 的最新實例的結果。

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a>在磁片上尋找工作結果的基本方法

若要管理排程工作，請使用 job Cmdlet，例如 `Get-Job` 和 `Receive-Job` 。

如果 `Get-Job` 未取得工作實例或未 `Receive-Job` 取得工作結果，您可以在磁片上搜尋作業的執行歷程記錄。
執行歷程記錄包含所有觸發之工作實例的記錄。

確認在下列路徑中，排程工作的目錄中有時間戳記命名的目錄：

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

例如：

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

例如，Cmdlet 會 `Get-ChildItem` 取得 **ProcessJob** 排程工作的磁片上執行歷程記錄。

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

每個以時間戳記命名的目錄都代表一個工作實例。 每個工作實例的結果會儲存在時間戳記命名目錄的 **Results.xml** 檔案中。

例如，下列命令會取得 **ProcessJob** 排程工作的每個已儲存實例的 **Results.xml** 檔案。 如果遺失 **Results.xml** 檔案，則 PowerShell 無法傳回或顯示工作結果。

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

Job Cmdlet 可能無法取得排程工作實例或其結果，因為 **PSScheduledJob** 模組未匯入會話中。

> [!NOTE]
> 在排程工作實例上使用 job Cmdlet 之前，請確認 **PSScheduledJob** 模組是否包含在會話中。 如果沒有 **PSScheduledJob** 模組，則工作 Cmdlet 無法取得排程工作實例或其結果。

若要匯入 **PSScheduledJob** 模組：

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a>Receive-Job Cmdlet 可能已經傳回結果

如果沒有傳回 `Receive-Job` 工作實例的結果，可能是因為未 `Receive-Job` 使用 **Keep** 參數在目前會話中執行該工作實例的命令。

當您使用 `Receive-Job` 而不使用 **Keep** 參數時，會傳回 `Receive-Job` 工作結果，並將工作實例的 **HasMoreData** 屬性設定為 **False** 。 **False** 值表示 `Receive-Job` 傳回作業的結果，而實例則不再傳回結果。 這項設定適用于標準背景工作，但不適用於已儲存至磁片的排程工作實例。

若要再次取得工作實例的結果，請輸入以啟動新的 PowerShell 會話 `PowerShell` 。 匯入 **PSScheduledJob** 模組，然後再次嘗試 `Receive-Job` 命令。

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a>在會話中使用 Keep 參數來取得超過一次的結果

若要在會話中多次取得工作實例的結果，請使用 Cmdlet 的 **Keep** 參數 `Receive-Job` 。

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a>排程工作可能已損毀

如果排程工作損毀，PowerShell 會刪除損毀的排程工作及其結果。 您無法復原損毀的排程工作結果。

若要判斷排程工作是否仍然存在，請使用 `Get-ScheduledJob` Cmdlet。

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a>結果數目可能已超過 ExecutionHistoryLength

排程工作的 **ExecutionHistoryLength** 屬性會決定要將多少個工作實例和其結果儲存至磁片。 預設值為 32。
當排程工作的實例數目超過此值時，PowerShell 會刪除最舊的工作實例，以騰出空間給每個新的工作實例。

若要取得排程工作的 **ExecutionHistoryLength** 屬性值，請使用下列命令格式：

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

例如，下列命令會取得 **ProcessJob** 排程工作的 **ExecutionHistoryLength** 屬性值。

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

若要設定或變更 **ExecutionHistoryLength** 屬性的值，請使用和 Cmdlet 的 **MaxResultCount** 參數 `Register-ScheduledJob` `Set-ScheduledJob` 。

下列命令會將 **ExecutionHistoryLength** 屬性的值增加為50。

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a>作業實例的結果可能已刪除

Cmdlet 的 **ClearExecutionHistory** 參數會 `Set-ScheduledJob` 刪除作業的執行歷程記錄。 您可以使用這項功能來釋出磁碟空間，或刪除不需要或已經使用、分析或儲存在不同位置的結果。

若要刪除排程工作的執行歷程記錄，請使用排程工作的 **ClearExecutionHistory** 參數。

下列命令會刪除 **ProcessJob** 排程工作的執行歷程記錄。

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

此外，此 `Remove-Job` Cmdlet 會刪除工作結果。 當您使用 `Remove-Job` 刪除排程工作時，它會刪除磁片上的所有作業實例，包括執行歷程記錄和所有工作結果。

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a>使用 Start-Job Cmdlet 啟動的作業不會儲存到磁片

當您使用 `Start-Job` 來啟動排程工作（而不是使用工作觸發程式）時，會 `Start-Job` 啟動標準的背景工作。 背景工作及其結果不會儲存在磁片上工作的執行歷程記錄中。

您可以使用指令程式 `Get-Job` 取得作業和 `Receive-Job` Cmdlet 來取得工作結果，但除非您使用指令程式的 Keep 參數，否則只有在收到這些結果時，才可使用這些結果 `Receive-Job` 。

此外，背景工作和其結果都是會話特定的;它們只存在於建立它們的會話中。 如果您刪除此作業 `Remove-Job` ，請關閉會話或關閉 PowerShell，作業實例及其結果會被刪除。

## <a name="scheduled-job-doesnt-run"></a>排程工作未執行

如果工作觸發程式或排程工作已停用，則排程工作不會自動執行。

使用 `Get-ScheduledJob` Cmdlet 來取得排程工作。 確認排程工作的 [ **已啟用** ] 屬性值為 [ **True** ]。

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

使用 `Get-JobTrigger` Cmdlet 來取得排程工作的工作觸發程式。
確認工作觸發程式的 **Enabled** 屬性值為 **True** 。

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a>如果工作觸發程式無效，則排程工作不會自動執行

例如，工作觸發程式可能會指定過去的日期或未發生的日期，例如當月的5星期一。

如果未滿足工作觸發程式或工作選項的條件，則排程工作不會自動執行。

例如，只有在特定使用者登入電腦時才會執行的排程工作，如果該使用者沒有登入或只連接遠端，就不會執行。

檢查排程工作的選項，並確定已滿足這些選項。
例如，需要電腦閒置或需要網路連接，或有長 **IdleDuration** 或簡短 **IdleTimeout** 的排程工作可能永遠不會執行。

使用 `Get-ScheduledJobOption` Cmdlet 來檢查工作選項和其值。

```powershell
Get-ScheduledJob -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

如需排程工作選項的描述，請參閱 [ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)。

### <a name="the-scheduled-job-instance-might-have-failed"></a>排程工作實例可能已失敗

如果排程工作命令失敗，PowerShell 會產生錯誤訊息來立即報告。 但是，如果工作排程器嘗試執行作業失敗，PowerShell 就無法使用此錯誤。

使用下列方法來偵測並更正作業失敗：

檢查工作排程器事件記錄檔中是否有錯誤。 若要檢查記錄檔，請使用事件檢視器或 PowerShell 命令，如下所示：

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

檢查工作排程器中的作業記錄。 PowerShell 排程工作會儲存在下列工作排程資料夾中：

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a>排程工作可能因為許可權不足而無法執行

排程工作是以建立工作之使用者的許可權，或是或命令中 **Credential** 參數所指定之使用者的許可權來執行 `Register-ScheduledJob` `Set-ScheduledJob` 。

如果該使用者沒有執行命令或腳本的許可權，作業就會失敗。

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a>無法取得排程工作或排程工作已損毀

在罕見的情況下，排程工作可能會損毀，或包含無法解決的內部您一致。 一般來說，當排程工作的 XML 檔案以手動方式編輯，導致 XML 無效時，就會發生這種情況。

當排程工作損毀時，PowerShell 會嘗試刪除排程工作、其執行歷程記錄，以及來自磁片的結果。

如果無法移除排程工作，每次執行 Cmdlet 時，您都會收到損毀的工作錯誤訊息 `Get-ScheduledJob` 。

若要移除損毀的排程工作，請使用下列其中一種方法：

刪除 `<ScheduledJobName>` 排程工作的目錄。 請勿刪除 **register-scheduledjob** 目錄。

目錄的位置：

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

例如：

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

使用工作排程器來刪除排程工作。 PowerShell 排程工作會出現在下列工作排程器路徑中：

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a>作業 Cmdlet 無法一致地找到排程工作

當 **PSScheduledJob** 模組不在目前的會話中時，作業 Cmdlet 無法取得排程的工作、啟動它們或取得其結果。

若要匯入 **PSScheduledJob** 模組，請 `Import-Module PSScheduledJob` 在模組中輸入或執行或取得任何 Cmdlet，例如 `Get-ScheduledJob` Cmdlet。
從 PowerShell 3.0 開始，當您取得或使用模組中的任何 Cmdlet 時，會自動匯入模組。

當 **PSScheduledJob** 模組不在目前的會話中時，可能會有下列命令順序。

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

發生此行為的原因是 `Get-ScheduledJob` 命令自動匯入 **PSScheduledJob** 模組，然後執行命令。

## <a name="see-also"></a>另請參閱

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet

[工作排程器](/windows/desktop/TaskSchd/task-scheduler-reference)
