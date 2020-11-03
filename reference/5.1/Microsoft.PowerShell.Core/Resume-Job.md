---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202675"
---
# Resume-Job

## 概要
重新啟動暫停的工作。

## SYNTAX

### SessionIdParameterSet (預設值)

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Resume** 工作 Cmdlet 會繼續已暫停的工作流程工作，例如使用 Suspend-Job Cmdlet 或 About_Suspend 工作流程活動。
當工作流程工作繼續時，工作引擎會從儲存的資源（例如檢查點）重建狀態、中繼資料和輸出。
作業會在沒有任何狀態或資料遺失的情況下重新開機。
工作狀態會從 **Suspended** 變更為 **Running** 。

使用 **Resume 工作** 的參數，依名稱、識別碼、實例識別碼選取工作，或使用管線將工作物件（例如 Get-Job Cmdlet 所傳回的工作物件）選取為 **繼續作業** 。
您也可以使用屬性篩選來選取要繼續的工作。

依照預設， **Resume-Job** 會立即傳回，即使所有工作可能尚未繼續。
若要防止在指定工作繼續之前顯示命令提示字元，請使用 *Wait* 參數。

**Resume-Job** Cmdlet 只能使用於自訂工作類型，例如工作流程工作。
它無法在標準背景工作（例如使用 Start-Job Cmdlet 啟動的背景工作）上運作。
如果您送出不受支援類型的工作， **Resume-Job** 會產生終止錯誤並停止執行。

若要識別工作流程工作，請尋找工作之 **PSJobTypeName** 屬性中 **PSWorkflowJob** 的值。
若要判斷特定的自訂工作類型是否支援 **Resume 工作** Cmdlet，請參閱自訂工作類型的說明主題。

在自訂工作類型上使用 Job Cmdlet 之前，請使用 Import-Module Cmdlet 或取得或使用模組中的 Cmdlet，匯入支援自訂工作類型的模組。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：依識別碼繼續工作

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

此範例中的命令會確認工作是否為暫停的工作流程工作，然後繼續該工作。

### 範例2：依名稱繼續工作

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

此命令使用 *Name* 參數繼續本機電腦上的數個工作流程工作。

### 範例3：使用自訂屬性值

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

此命令使用自訂屬性的值來識別工作流程工作以繼續工作。
它會使用 *Filter* 參數依工作流程工作的 **CustomID** 屬性識別工作。
它也會使用 *State* 參數先確認工作流程工作已經暫停，然後再嘗試繼續工作。

### 範例4：繼續遠端電腦上所有已暫停的工作

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

此命令會繼續 Srv01 遠端電腦上所有已暫停的工作。

命令使用 Invoke-Command Cmdlet 在 Srv01 電腦上執行命令。
遠端命令會使用「 **取得工作** 」 Cmdlet 的 *State* 參數來取得電腦上所有已暫停的工作。
管線運算子 (|) 會將已暫停工作傳送至 **Resume-Job** Cmdlet，以繼續工作。

### 範例5：等候工作繼續

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

此命令會使用 *Wait* 參數 **，直接在所有指定的工作** 都繼續之後才傳回。
在假設指令碼繼續之前會先繼續工作的指令碼中， *Wait* 參數特別有用。

### 範例6：繼續暫停本身的工作流程

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

Resume 工作指令 **程式** 可讓您繼續使用 **暫停工作流程** 活動暫停的工作流程工作。
此活動會從工作流程內暫停工作流程。
它只在工作流程中有效。

如需 Suspend-Workflow 的相關資訊，請參閱 about_Suspend-Workflow。

## PARAMETERS

### -Filter
指定條件的雜湊表。
此 Cmdlet 會繼續符合雜湊表中所有條件的工作。
輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Id
針對此 Cmdlet 繼續的作業指定識別碼陣列。

識別碼是一個整數，可唯一識別目前工作階段中的工作。
它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。
您可以輸入一個或多個識別碼，以逗號分隔。
若要尋找作業的識別碼，請執行 **Get 作業** 。

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId
指定此 Cmdlet 繼續之作業的實例識別碼陣列。
預設為所有工作。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。
若要尋找工作的實例識別碼，請執行 **Get 作業** 。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job
指定要繼續的工作。
輸入包含工作的變數，或輸入可取得工作的命令。
您也可以使用管線將工作傳送至 **Resume-Job** Cmdlet。

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
指定此 Cmdlet 所繼續之作業的易記名稱陣列。
輸入一或多個工作名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -State
指定要繼續之作業的狀態。
此參數可接受的值為：

- NotStarted
- 執行中
- Completed
- 失敗
- 已停止
- 封鎖
- 暫止
- 已中斷連接
- Suspending
- 停止中

此 Cmdlet 只會恢復處於 **暫停** 狀態的工作。

如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wait
指出此 Cmdlet 會抑制命令提示字元，直到重新開機所有工作結果為止。
根據預設，此 Cmdlet 會立即傳回可用的結果。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.Job
您可以透過管道將所有類型的作業傳送至此 Cmdlet。
如果 **繼續作業** 取得不支援之類型的作業，則會傳回終止錯誤。

## 輸出

### 無，系統管理。作業
如果您使用 *PassThru* 參數，此 Cmdlet 會傳回它嘗試繼續的工作。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* **Resume-工作** 只能繼續已暫停的工作。 如果您送出狀態不同的工作， **Resume-Job** 會在工作上執行繼續操作，但是會產生警告以通知您無法繼續該工作。 若要隱藏警告，請使用 *WarningAction* 一般參數搭配 SilentlyContinue 的值。
* 如果作業不是支援繼續的型別，例如工作流程工作 ( **PSWorkflowJob** ) ，則 **Resume 作業** 會傳回終止錯誤。
* 用於儲存暫停工作的機制與位置可能會視工作類型不同而改變。 例如，暫停的工作流程工作是預設儲存在一般檔案存放區，但是也可以儲存在 SQL 資料庫中。
* 當您繼續工作時，工作狀態會從 **Suspended** 變更為 **Running** 。 若要尋找正在執行的作業（包括此 Cmdlet 所繼續的工作），請使用「 **取得工作** 」 Cmdlet 的 *State* 參數來取得處於執行中 **狀態的** 工作。
* 部分工作類型具有可防止 Windows PowerShell 暫停工作的選項或屬性。 如果嘗試暫停工作失敗，請確認工作選項與屬性是否允許暫停。

## 相關連結

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
