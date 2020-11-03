---
description: 提供有關本機和遠端電腦上背景工作的詳細資料。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 0d85cd242c8e79281fa8be153b0e140660f16c1a
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208604"
---
# <a name="about-job-details"></a>關於工作詳細資料

## <a name="short-description"></a>簡短描述
提供有關本機和遠端電腦上背景工作的詳細資料。

## <a name="detailed-description"></a>詳細描述

本主題說明背景工作的概念，並提供有關如何在 PowerShell 中執行背景工作的技術資訊。

本主題是 [about_Jobs](about_Jobs.md)、 [about_Thread_Jobs](about_Thread_Jobs.md)和 [about_Remote_Jobs](about_Remote_Jobs.md) 主題的補充。

### <a name="about-background-jobs"></a>關於背景工作

背景工作會以非同步方式執行命令或運算式。 它可能會執行 Cmdlet、函式、腳本或任何其他以命令為基礎的工作。 它是設計來執行長時間執行的命令，但是您可以使用它在背景中執行任何命令。

當同步命令執行時，會隱藏 PowerShell 命令提示字元，直到命令完成為止。 但背景工作不會抑制 PowerShell 提示字元。 啟動背景工作的命令會傳回工作物件。
提示會立即傳回，讓您可以在背景工作執行時處理其他工作。

不過，當您啟動背景工作時，即使作業的執行速度非常快，也不會立即取得結果。 傳回的工作物件包含工作的相關實用資訊，但是不包含工作結果。 您必須執行個別的命令以取得工作結果。 您也可以執行命令來停止工作、等候工作完成，以及刪除工作。

為了讓背景工作的時間與其他命令無關，每個背景工作會在自己的 PowerShell 會話中執行。 不過，這可以是只為了執行工作而建立的暫時連線，然後終結，也可以是持續的 **PSSession** ，讓您用來執行數個相關的作業或命令。

### <a name="using-the-job-cmdlets"></a>使用 job Cmdlet

使用 `Start-Job` 命令在本機電腦上啟動背景工作。
`Start-Job` 傳回工作物件。 您也可以使用 Cmdlet 取得代表在本機電腦上啟動之作業的物件 `Get-Job` 。

若要取得工作結果，請使用 `Receive-Job` 命令。 如果作業未完成，則會傳回 `Receive-Job` 部分結果。 您也可以使用 `Wait-Job` Cmdlet 來抑制命令提示字元，直到會話中啟動的一或所有工作完成為止。

若要停止背景工作，請使用 `Stop-Job` Cmdlet。 若要刪除作業，請使用 `Remove-Job` Cmdlet。

如需 Cmdlet 運作方式的詳細資訊，請參閱每個 Cmdlet 的說明主題，並查看 [about_Jobs](about_Jobs.md)。

### <a name="starting-background-jobs-on-remote-computers"></a>在遠端電腦上啟動背景工作

您可以在本機或遠端電腦上建立和管理背景工作。 若要從遠端執行背景工作，請使用 Cmdlet 的 **AsJob** 參數（例如 `Invoke-Command` ），或使用 `Invoke-Command` Cmdlet `Start-Job` 從遠端執行命令。 您也可以在互動式會話中啟動背景工作。

如需有關遠端背景工作的詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。

### <a name="child-jobs"></a>子工作

每個背景工作都是由父工作和一或多個子作業所組成。 在使用 `Start-Job` 或的 **AsJob** 參數啟動的工作中 `Invoke-Command` ，父作業為執行。 它不會執行任何命令或傳回任何結果。 這些命令實際上是由子工作所執行。 使用其他 Cmdlet 啟動的工作可能會有不同的運作方式。

子工作會儲存在父工作物件的 **ChildJobs** 屬性中。 **ChildJobs** 屬性可包含一或多個子工作物件。
子工作物件的 **名稱** 、 **識別碼** 和 **InstanceId** 與父作業不同，因此您可以個別或單位來管理父工作和子工作。

若要取得作業的父系和子作業，請使用 Cmdlet 的 **IncludeChildJobs** 參數 `Get-Job` 。 **IncludeChildJob** 參數是在 Windows PowerShell 3.0 中引進。

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

若要取得父工作，且僅取得具有特定 **狀態值** 的子工作，請使用 Cmdlet 的 **ChildJobState** 參數 `Get-Job` 。 **ChildJobState** 參數是在 Windows PowerShell 3.0 中引進。

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

若要在所有版本的 PowerShell 上取得作業的子工作，請使用父工作的 **>childjob** 屬性。

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

您也可以 `Get-Job` 在子工作上使用命令，如下列命令所示：

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

子工作的設定取決於您用來啟動作業的命令。

- 當您使用在 `Start-Job` 本機電腦上啟動作業時，此作業包含執行命令的執行程式父工作和子工作。

- 當您使用的 **AsJob** 參數 `Invoke-Command` 在一或多部電腦上啟動作業時，此作業會由執行父工作和每一部電腦上執行的每個作業組成子工作。

- 當您使用在 `Invoke-Command` `Start-Job` 一或多部遠端電腦上執行命令時，其結果與在每部遠端電腦上執行的本機命令相同。 此命令會傳回每一部電腦的工作物件。 工作物件包含執行命令的執行父項作業和一個子工作。

父作業代表所有子工作。 當您管理父工作時，也會管理相關聯的子工作。 例如，如果您停止父工作，則會停止所有子工作。 如果您取得父作業的結果，則會取得所有子工作的結果。

不過，您也可以個別管理子工作。 當您想要調查作業的問題，或是只使用的 **AsJob** 參數來取得一些子工作的結果時，這項功能最有用 `Invoke-Command` 。

下列命令使用的 **AsJob** 參數， `Invoke-Command` 在本機電腦和兩部遠端電腦上啟動背景工作。 此命令會將工作儲存在 `$j` 變數中。

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

當您在中顯示作業的 Name 和 **>childjob** 屬性時 `$j` ，會顯示命令傳回具有三個子工作的工作物件，每一部電腦各一項。

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

當您顯示父工作時，會顯示作業失敗。

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

但是，當您執行可 `Get-Job` 取得子工作的命令時，輸出會顯示只有一個子工作失敗。

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

若要取得所有子作業的結果，請使用 `Receive-Job` Cmdlet 來取得父工作的結果。 但是，您也可以取得特定子作業的結果，如下列命令所示。

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

PowerShell 背景工作的子工作功能可讓您更充分掌控您所執行的作業。

### <a name="job-types"></a>工作類型

PowerShell 針對不同的工作支援不同類型的作業。 從 Windows PowerShell 3.0 開始，開發人員可以撰寫「作業來源介面卡」，以將新的作業類型新增至 PowerShell，並在模組中包含作業來源介面卡。
當您匯入模組時，您可以在會話中使用新的作業類型。

例如，PSScheduledJob 模組會新增排程的工作，而 PSWorkflow 模組會新增工作流程工作。

自訂工作類型與標準 PowerShell 背景工作的差異可能會大不相同。 例如，排程的工作會儲存在磁片上;它們只存在於特定會話中。 您可以暫停和繼續工作流程工作。

您用來管理自訂作業的 Cmdlet 取決於作業類型。 在某些情況下，您會使用標準的工作 Cmdlet，例如 `Get-Job` 和 `Start-Job` 。 有些則是專門用來管理特定工作類型的專用 Cmdlet。 如需自訂工作類型的詳細資訊，請參閱有關工作類型的說明主題。

若要尋找工作的工作類型，請使用 `Get-Job` Cmdlet。 `Get-Job` 針對不同類型的作業傳回不同的工作物件。 傳回的工作物件之 **PSJobTypeName** 屬性的值 `Get-Job` 表示作業類型。

下表列出 PowerShell 隨附的作業類型。

|    作業類型    |                       Description                        |
| -------------- | -------------------------------------------------------- |
| BackgroundJob  | 已開始使用 `Start-Job` Cmdlet。                    |
| RemoteJob      | 開始使用的 **AsJob** 參數             |
|                | `Invoke-Command` Cmdlet。                                 |
| PSWorkflowJob  | 開始使用工作流程的 **AsJob** 參數。     |
| PSScheduledJob | 工作觸發程式啟動的排程工作實例。 |
| CIMJob         | 開始使用來自的 Cmdlet 的 **AsJob** 參數 |
|                | CDXML 模組。                                            |
| WMIJob         | 開始使用來自的 Cmdlet 的 **AsJob** 參數 |
|                | WMI 模組。                                              |
| PSEventJob     | 使用建立 `Register-ObjectEvent` ，並指定    |
|                | **action 參數的** 動作。                    |

注意：使用指令程式 `Get-Job` 取得特定類型的作業之前，請先確認新增工作類型的模組已匯入至目前的會話。
否則，就 `Get-Job` 不會取得該類型的作業。

## <a name="examples"></a>範例

下列命令會建立本機背景工作、遠端背景工作、工作流程工作和排程工作。 然後，它會使用 `Get-Job` Cmdlet 來取得工作。 `Get-Job` 不會取得排程工作，但會取得排程工作的任何已啟動實例。

在本機電腦上啟動背景工作。

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

啟動在遠端電腦上執行的背景工作。

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

建立排程工作

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

建立工作流程。

```powershell
PS> workflow Test-Workflow {Get-Process}
```

以工作的形式執行工作流程。

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

取得作業。 此 `Get-Job` 命令不會取得排程的工作，但會取得已啟動之排程工作的實例。

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

若要取得排程工作，請使用 `Get-ScheduledJob` Cmdlet。

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a>另請參閱

- [about_Jobs](about_Jobs.md)
- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Remote](about_Remote.md)
- [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
