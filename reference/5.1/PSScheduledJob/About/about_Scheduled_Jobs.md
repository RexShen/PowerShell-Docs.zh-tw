---
description: 描述排程工作並說明如何在 PowerShell 和工作排程器中使用和管理排程工作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207256"
---
# <a name="about-scheduled-jobs"></a>關於排程工作

## <a name="short-description"></a>簡短描述

描述排程工作並說明如何在 PowerShell 和工作排程器中使用和管理排程工作。

## <a name="long-description"></a>完整描述

PowerShell 排程工作是 PowerShell 背景工作和工作排程器工作的實用混合。

就像 PowerShell 背景工作一樣，排程工作會在背景中以非同步方式執行。 您可以使用 job Cmdlet 來管理已執行之排程工作的實例，例如、、 `Start-Job` `Get-Job` `Stop-Job` 和 `Receive-Job` 。

就像工作排程器工作一樣，排程工作會儲存至磁片。 您可以在工作排程器中查看和管理工作、視需要啟用及停用工作、執行工作或使用它們作為範本、建立單次或週期性排程來啟動作業，或設定工作開始的條件。

此外，排程工作實例的結果會以容易存取的格式儲存到磁片，提供工作輸出的執行記錄。 排程的工作隨附一組自訂的 Cmdlet 來管理它們。 這些 Cmdlet 可讓您建立、編輯、管理、停用及重新啟用排程工作、工作觸發程式和工作選項。

這套全方位且彈性的工具組，讓排程工作成為許多專業版 PowerShell IT 解決方案的重要元件。

排程工作 Cmdlet 包含在隨 PowerShell 安裝的 **PSScheduledJob** 模組中。 此課程模組是在 PowerShell 3.0 中引進，適用于 powershell 3.0 和更新版本的 PowerShell。 如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。

如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)。

如需工作排程器的詳細資訊，請參閱 [工作排程器](/windows/desktop/TaskSchd/task-scheduler-reference)。

> [!NOTE]
> 您可以在工作排程器中查看和管理 PowerShell 排程工作。 PowerShell 工作和排程工作 Cmdlet 只適用于在 PowerShell 中建立的排程工作。

## <a name="quick-start"></a>快速入門

此範例會建立在每天上午3:00 開始的排程工作，並執行 `Get-Process` Cmdlet。 即使電腦是以電池執行，也會啟動作業。

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

`Get-ScheduledJob`Cmdlet 會取得本機電腦上的排程工作。

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

`Get-JobTrigger` 取得 **ProcessJob** 的工作觸發程式。 輸入參數會指定排程工作，而不是觸發程式，因為觸發程式是儲存在排程工作中。

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

此範例會使用 Cmdlet 的 **ContinueIfGoingOnBattery** 參數 `Set-ScheduledJob` ，將 **ProcessJob** 的 **StopIfGoingOnBatteries** 屬性變更為 **False** 。

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
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

`Get-ScheduledJob`Cmdlet 會取得 **ProcessJob** 排程工作。

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

此 `Get-Job` Cmdlet 會取得到目前為止執行的 **ProcessJob** 排程工作的所有實例。 `Get-Job`只有將 **PSScheduledJob** 模組匯入目前的會話時，此 Cmdlet 才會取得排程工作。

> [!TIP]
> 請注意，您可以使用「排程工作」 Cmdlet 來管理排程的工作，但您可以使用 job Cmdlet 來管理排程工作的實例。

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

此 `Receive-Job` Cmdlet 會取得 **ProcessJob** 排程工作的最新實例的結果 (識別碼 = 51) 。

```powershell
Receive-Job -ID 51
```

即使命令未 `Receive-Job` 包含 **Keep** 參數，作業的結果仍會儲存在磁片上，直到您將其刪除或超過結果數目上限為止。

此會話已無法再使用工作結果，但如果您啟動新的會話或開啟新的 PowerShell 視窗，則會再次提供作業的結果。

下列命令會使用 Cmdlet 的 **DefinitionName** 參數 `Start-Job` 來啟動 **ProcessJob** 排程工作。

使用 Cmdlet 啟動的作業 `Start-Job` 是標準的 PowerShell 背景工作，而不是排程工作的實例。 就像所有背景工作一樣，這些作業會立即啟動、不受工作選項影響，也不會受到工作觸發程式的影響，且其輸出不會儲存在排程工作目錄的輸出目錄中。

```powershell
Start-Job -DefinitionName ProcessJob
```

此 `Unregister-ScheduledJob` Cmdlet 會刪除 **ProcessJob** 排程工作，以及其工作實例的所有儲存結果。

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a>排程工作概念

排程工作會執行命令或腳本。 排程工作可以包含工作觸發程式，以啟動作業和工作選項來設定執行作業的條件。

工作觸發程式會自動啟動排程工作。 工作觸發程式可以包含一次性或週期性排程，或指定事件，例如當使用者登入或 Windows 啟動時。 排程工作可以有一或多個工作觸發程式，您可以建立、新增、啟用、停用和取得工作觸發程式。

工作觸發程序是選擇性的。 您可以使用來立即啟動排程工作 `Start-Job cmdlet` ，或將 **RunNow** 參數新增至 `Register-ScheduledJob` 命令。

作業選項會設定執行排程工作的條件。 每個排程工作都有一個工作選項物件。 您可以建立和編輯作業選項物件，並將它們新增至一或多個排程工作。

每次排程工作啟動時，就會建立一個工作實例。 使用 PowerShell 工作 Cmdlet 來查看和管理作業實例。

排程的工作會儲存至磁片，並使用 Cmdlet 動詞命令， `Register` 而不是 `New` 。 XML 檔案位於目錄中的本機電腦上 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 。

PowerShell 會建立每個排程工作的目錄，並將工作命令、工作觸發程式、工作選項和工作結果儲存在排程的工作目錄中。 工作觸發程式和工作選項不會獨立儲存至磁片。
它們會儲存在與其相關聯之每個排程工作的排程工作 XML 中。

排程工作、工作觸發程式和工作選項會以物件的形式出現在 PowerShell 中。
這些物件是 interlinked 的，可讓您輕鬆地探索和使用命令和腳本。

排程的工作會顯示為 **>scheduledjobdefinition** 物件。 **>scheduledjobdefinition** 物件具有 **JobTriggers** 屬性，其中包含排程工作的工作觸發程式，以及包含作業選項的 **Options** 屬性。 分別代表工作觸發程式和工作選項的 **ScheduledJobTriggers** 和 **ScheduledJobOptions** 物件具有 **JobDefinition** 屬性，其中包含與其相關聯的排程工作。 這種遞迴互連可讓您輕鬆地尋找排程工作的觸發程式和選項，以及尋找、腳本和顯示與任何工作觸發程式或工作選項相關聯的排程工作。

## <a name="see-also"></a>另請參閱

[about_Scheduled_Jobs_Basics](about_Scheduled_Jobs_Basics.md)

[about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md)

[about_Scheduled_Jobs_Troubleshooting](about_Scheduled_Jobs_Troubleshooting.md)

[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet

[工作排程器](/windows/desktop/TaskSchd/task-scheduler-reference)
