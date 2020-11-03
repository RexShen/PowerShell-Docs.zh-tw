---
description: 說明如何建立及管理排程工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207251"
---
# <a name="about-scheduled-jobs-basics"></a>關於排程工作的基本概念

## <a name="short-description"></a>簡短描述

說明如何建立及管理排程工作。

## <a name="long-description"></a>完整描述

本檔說明如何執行建立和管理排程工作的基本工作。 如需更多工具的詳細資訊，請參閱 [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)。

如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。

## <a name="how-to-create-a-scheduled-job"></a>如何建立排程工作

若要建立排程工作，請使用 `Register-ScheduledJob` Cmdlet。 此 Cmdlet 需要工作執行的名稱和命令或腳本。 您可以藉由新增 **RunNow** 參數來立即執行作業，或建立工作觸發程式，並在建立工作時設定工作選項，或編輯現有的作業。

若要建立執行腳本的作業，請使用 **FilePath** 參數指定腳本檔案的路徑。 若要建立執行命令的作業，請使用 **ScriptBlock** 參數。

此 `Register-ScheduledJob` Cmdlet 會建立 **ProcessJob** ，以執行 `Get-Process` 命令。 此排程工作具有預設工作選項，且沒有工作觸發程式。

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a>如何建立工作觸發程式

工作觸發程式會自動啟動排程工作。 工作觸發程式可以是一次性或週期性排程或事件，例如當使用者登入或 Windows 啟動時。 每個作業都可以有零個、一個或多個工作觸發程式。

若要建立工作觸發程式，請使用 `New-JobTrigger` Cmdlet。 下列命令會建立工作觸發程式，此觸發程式會在每星期一和星期四上午5:00 啟動工作。
此命令會將工作觸發程式儲存在 `$T` 變數中。

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

工作觸發程序是選擇性的。 您可以在命令中新增 **RunNow** 參數 `Register-ScheduledJob` ，或使用 Cmdlet，隨時啟動排程工作 `Start-Job` 。

## <a name="how-to-add-a-job-trigger"></a>如何新增工作觸發程式

當您將工作觸發程式新增至排程工作時，工作觸發程式會新增至排程工作的排程工作 XML 檔案，並成為排程工作的一部分。

您可以在建立排程工作時，將工作觸發程式新增至排程工作，或編輯現有的作業。 您可以隨時變更排程工作的工作觸發程式。

PowerShell 會使用工作排程器使用的一些相同工作觸發程式。 如需工作觸發程式的詳細資訊，請參閱 [enable-jobtrigger](xref:PSScheduledJob.New-JobTrigger) Cmdlet 的說明主題。

下列範例會使用展開來建立將 `$JobParms` 參數值傳遞給 Cmdlet 的參數值 `Register-ScheduledJob` 。 如需詳細資訊，請參閱 [about_Splatting md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)。
`Register-ScheduledJob`用 `@JobParms` 來建立排程工作。 它會使用 **Trigger** 參數來指定變數中的工作觸發程式 `$T` 。

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

您也可以在任何時間將工作觸發程式新增至現有的排程工作。 `Add-JobTrigger`Cmdlet 會將變數中的工作觸發程式新增 `$T` 至 **ProcessJob** 排程工作。

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

如此一來，工作觸發程式就會在每星期一和星期四的上午5:00 自動啟動 **ProcessJob** 。

## <a name="how-to-get-a-job-trigger"></a>如何取得工作觸發程式

若要取得排程工作的工作觸發程式，請使用 `Get-JobTrigger` Cmdlet。 您可以使用 **Name** 、 **ID** 和 **InputObject** 參數來指定排程工作，而不是工作觸發程式。

`Get-JobTrigger` 取得 **ProcessJob** 的工作觸發程式。

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a>如何建立工作選項

作業選項會建立開始和執行工作的條件。 每個作業都有預設的工作選項，除非您變更它們。 因為工作選項可以防止工作在排程的時間執行，所以請務必瞭解工作選項並謹慎使用。

PowerShell 會使用工作排程器使用的相同工作選項。 如需作業選項的詳細資訊，請參閱 [ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)的說明主題。

工作選項會儲存在排程的工作 XML 檔案中。 您可以在建立排程工作時設定工作選項，或隨時變更工作選項。

此 `New-ScheduledJobOption` Cmdlet 會建立排程工作選項，其中 **WakeToRun** 排程工作選項會設定為 True。 **WakeToRun** 選項會執行排程工作，即使電腦在排定的開始時間處於睡眠或休眠狀態。 此命令會將工作選項儲存在 `$O` 變數中。

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a>如何取得工作選項

若要取得排程工作的工作選項，請使用 `Get-ScheduledJobOption` Cmdlet。 您可以使用 **Name** 、 **ID** 和 **InputObject** 參數來指定排程工作，而不是工作選項。

`Get-ScheduledJobOption` 取得 **ProcessJob** 的工作選項。

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
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

## <a name="how-to-change-job-options"></a>如何變更工作選項

當您建立排程工作或編輯現有的作業時，您可以變更排程工作的工作選項。

Splatted `$JobParms` 會傳遞至 `Add-JobTrigger` Cmdlet 以建立處理作業。 它會使用 **ScheduledJobOption** 參數來指定變數中的工作選項 `$O` 。

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

您也可以在任何時間將工作選項變更為現有的排程工作。
下列命令會使用 `Set-ScheduledJobOption` Cmdlet，將 **ProcessJob** register-scheduledjob 的 **WakeToRun** 選項值變更為 **True** 。

`Set` **PSScheduledJob** 模組中的 Cmdlet （例如 `Set-ScheduledJobOption` Cmdlet）沒有 **名稱** 或 **識別碼** 參數。 您可以使用 **InputObject** 參數來指定排程工作選項，或使用管線將排程工作從 `Get-ScheduledJobOption` Cmdlet 傳送至 `Set-ScheduledJobOption` 。

此範例會使用 `Get-ScheduledJob` Cmdlet 來取得 ProcessJob。 它會使用 `Get-ScheduledJobOption` Cmdlet 來取得 **ProcessJob** 中的工作選項，以及使用 `Set-ScheduledJobOption` Cmdlet 將 ProcessJob 中的 **WakeToRun** 作業選項變更為 True。

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a>如何取得排程工作實例

當排程工作啟動時，PowerShell 會建立類似于標準 PowerShell 背景工作的工作實例。 您可以使用 job Cmdlet （例如 `Get-Job` ） `Stop-Job` 和 `Receive-Job` 來管理工作實例。

> [!NOTE]
> 若要在排程工作的實例上使用 job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。 若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。

若要取得 PowerShell 排程工作的所有實例，以及所有使用中的標準作業，請使用 `Get-Job` Cmdlet。 此 `Import-Module` Cmdlet 會匯入 **PSScheduledJob** 模組，並 `Get-Job` 取得本機電腦上的工作。

```powershell
Import-Module PSScheduledJob
Get-Job
```

`Get-Job` 取得本機電腦上的 **ProcessJob** 實例。

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

預設顯示不會顯示開始時間，這通常會區分相同排程工作的實例。

`Get-Job`Cmdlet 會將物件沿著管線向下傳送。 此 `Format-Table` Cmdlet 會顯示排程工作的 **名稱** 、 **識別碼** 和 **system.windows.media.animation.timeline.begintime** 屬性。

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
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

## <a name="get-scheduled-job-results"></a>取得排程的工作結果

若要取得排程工作實例的結果，請使用 `Receive-Job` Cmdlet。

> [!NOTE]
> 若要在排程工作的實例上使用 Job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。 若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。

此範例會取得 **ProcessJob** 排程工作的最新實例的結果 (識別碼 = 51) 。

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

排程工作的結果會儲存在磁片上，因此不需要 **Keep** 的參數 `Receive-Job` 。 不過，若沒有 **保留** 參數，您只可以在每個 PowerShell 會話中取得排程工作的結果一次。 若要啟動新的 PowerShell 會話，請輸入 `PowerShell` 或開啟新的 powershell 視窗。

## <a name="see-also"></a>另請參閱

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[about_Scheduled_Jobs](about_Scheduled_Jobs.md)

[about_Splatting md](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet

[工作排程器](/windows/desktop/TaskSchd/task-scheduler-reference)
