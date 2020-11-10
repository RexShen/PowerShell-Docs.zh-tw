---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388530"
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

此 `Resume-Job` Cmdlet 會繼續已暫停的工作流程工作，例如使用 `Suspend-Job` Cmdlet 或 [about_Suspend 工作流程](../PSWorkflow/about/about_Suspend-Workflow.md) 活動。 當工作流程工作繼續時，工作引擎會從儲存的資源（例如檢查點）重建狀態、中繼資料和輸出。 作業會在沒有任何狀態或資料遺失的情況下重新開機。
工作狀態會從 **Suspended** 變更為 **Running** 。

使用的參數， `Resume-Job` 依名稱、識別碼、實例識別碼選取工作，或使用管線將工作物件（例如 Cmdlet 所傳回的物件）傳送 `Get-Job` 至 `Resume-Job` 。 您也可以使用屬性篩選來選取要繼續的工作。

根據預設， `Resume-Job` 會立即傳回，即使所有工作可能尚未繼續也一樣。 若要防止在指定工作繼續之前顯示命令提示字元，請使用 **Wait** 參數。

此 `Resume-Job` Cmdlet 只適用于自訂工作類型，例如工作流程工作。 它無法在標準背景工作（例如使用 Cmdlet 啟動的背景工作）上運作 `Start-Job` 。 如果您送出不受支援類型的作業，則會 `Resume-Job` 產生終止錯誤並停止執行。

若要識別工作流程工作，請尋找工作之 **PSJobTypeName** 屬性中 **PSWorkflowJob** 的值。 若要判斷特定的自訂工作類型是否支援 `Resume-Job` Cmdlet，請參閱自訂工作類型的說明主題。

在自訂工作類型上使用 Job Cmdlet 之前，請先使用 `Import-Module` Cmdlet 或取得或使用模組中的 Cmdlet，以匯入支援自訂工作類型的模組。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：依識別碼繼續工作

此範例中的命令會確認工作是否為暫停的工作流程工作，然後繼續該工作。 第一個命令會使用 `Get-Job` Cmdlet 來取得工作。 輸出說明工作是已暫停的工作流程工作。 第二個命令會使用 Cmdlet 的 **id** 參數 `Resume-Job` ，繼續 **識別碼** 值為4的工作。

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### 範例2：依名稱繼續工作

此命令使用 **Name** 參數繼續本機電腦上的數個工作流程工作。

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### 範例3：使用自訂屬性值

此命令使用自訂屬性的值來識別工作流程工作以繼續工作。 它會使用 **Filter** 參數依工作流程工作的 **CustomID** 屬性識別工作。 它也會使用 **State** 參數先確認工作流程工作已經暫停，然後再嘗試繼續工作。

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### 範例4：繼續遠端電腦上所有已暫停的工作

此命令會繼續 Srv01 遠端電腦上所有已暫停的工作。

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

此命令會使用 `Invoke-Command` Cmdlet 在 Srv01 電腦上執行命令。 遠端命令會使用 Cmdlet 的 **State** 參數 `Get-Job` 來取得電腦上所有已暫停的工作。 管線運算子 (`|`) 會將擱置的工作傳送至 `Resume-Job` Cmdlet，以繼續執行。

### 範例5：等候工作繼續

此命令會使用 **Wait** 參數， `Resume-Job` 只有在所有指定的工作都繼續執行之後，才會傳回。 在假設指令碼繼續之前會先繼續工作的指令碼中， **Wait** 參數特別有用。

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### 範例6：繼續暫停本身的工作流程

這個程式碼範例會顯示 `Suspend-Workflow` 工作流程中的活動。

`Test-Suspend`Server01 電腦上的工作流程。 當您執行工作流程時，工作流程會執行 `Get-Date` 活動，並將結果儲存在 `$a` 變數中。 然後，它會執行 `Suspend-Workflow` 活動。 回應時，它會取得檢查點，暫停工作流程，然後傳回工作流程工作物件。 `Suspend-Workflow` 傳回工作流程工作物件，即使工作流程未明確地以工作方式執行。

`Resume-Job` 繼續 `Test-Suspend` Job8 中的工作流程。 它會使用 **Wait** 參數來防止在工作繼續之前顯示命令提示字元。

`Receive-Job`Cmdlet 會取得工作流程的結果 `Test-Suspend` 。 工作流程中的最後一個命令會傳回 **TimeSpan** 物件，此物件代表目前日期和時間之間的經過時間，以及在 `$a` 工作流程暫停之前儲存在變數中的日期和時間。

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

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

此 `Resume-Job` Cmdlet 可讓您繼續使用活動暫停的工作流程工作 `Suspend-Workflow` 。 此活動會從工作流程內暫停工作流程。 它只在工作流程中有效。

如需的詳細資訊 `Suspend-Workflow` ，請參閱 about_Suspend-Workflow] (。/PSWorkflow/about/about_Suspend-Workflow. md) 。

## PARAMETERS

### -Filter

指定條件的雜湊表。 此 Cmdlet 會繼續符合雜湊表中所有條件的工作。 輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。

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

識別碼是一個整數，可唯一識別目前工作階段中的工作。 它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。 您可以輸入一個或多個識別碼，以逗號分隔。 若要尋找作業的識別碼，請執行 `Get-Job` 。

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

指定此 Cmdlet 繼續之作業的實例識別碼陣列。 預設為所有工作。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。 若要尋找工作的實例識別碼，請執行 `Get-Job` 。

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

指定要繼續的工作。 輸入包含工作的變數，或輸入可取得工作的命令。 您也可以透過管線將作業傳送至 `Resume-Job` Cmdlet。

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

指定此 Cmdlet 所繼續之作業的易記名稱陣列。 輸入一或多個工作名稱。
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

指定要繼續之作業的狀態。 此參數可接受的值為：

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

如需有關工作狀態的詳細資訊，請參閱 [JobState 列舉](/dotnet/api/system.management.automation.jobstate)。

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

指出此 Cmdlet 會抑制命令提示字元，直到重新開機所有工作結果為止。 根據預設，此 Cmdlet 會立即傳回可用的結果。

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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

您可以透過管道將所有類型的作業傳送至此 Cmdlet。 如果 `Resume-Job` 取得不支援之類型的作業，則會傳回終止錯誤。

## 輸出

### 無，系統管理。作業

如果您使用 **PassThru** 參數，此 Cmdlet 會傳回它嘗試繼續的工作。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

- `Resume-Job` 只能繼續已暫停的工作。 如果您以不同的狀態提交作業， `Resume-Job` 會在作業上執行繼續作業，但會產生警告，通知您無法繼續作業。 若要隱藏警告，請使用 **WarningAction** 一般參數搭配 SilentlyContinue 的值。
- 如果作業不是支援繼續的型別，例如 ( **PSWorkflowJob** ) 的工作流程工作，就會傳回 `Resume-Job` 終止錯誤。
- 用於儲存暫停工作的機制與位置可能會視工作類型不同而改變。 例如，暫停的工作流程工作是預設儲存在一般檔案存放區，但是也可以儲存在 SQL 資料庫中。
- 當您繼續工作時，工作狀態會從 **Suspended** 變更為 **Running** 。 若要尋找正在執行的作業（包括此 Cmdlet 所繼續的工作），請使用 Cmdlet 的 **State** 參數 `Get-Job` 來取得處於執行中狀態 **的** 工作。
- 部分工作類型具有可防止 Windows PowerShell 暫停工作的選項或屬性。
  如果嘗試暫停工作失敗，請確認工作選項與屬性是否允許暫停。

## 相關連結

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
