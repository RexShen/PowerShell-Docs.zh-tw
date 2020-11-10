---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388459"
---
# Suspend-Job

## 概要
暫時停止工作流程工作。

## SYNTAX

### SessionIdParameterSet (預設值)

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Suspend-Job` Cmdlet 會暫停工作流程工作。 暫止表示暫時中斷或暫停工作流程工作。 此 Cmdlet 可讓正在執行工作流程的使用者暫停工作流程。 它會補充暫止工作流程 https://go.microsoft.com/fwlink/?LinkId=267141 活動，此活動是工作流程中暫停工作流程的命令。

此 `Suspend-Job` Cmdlet 只適用于工作流程工作。 它無法在標準背景工作（例如使用 Cmdlet 啟動的背景工作）上運作 `Start-Job` 。

若要識別工作流程工作，請尋找工作之 PSJobTypeName 屬性中 **PSWorkflowJob** 的值。 若要判斷特定的自訂工作類型是否支援 `Suspend-Job` Cmdlet，請參閱自訂工作類型的說明主題。

當您暫停工作流程工作時，工作流程工作會執行至下一個檢查點，接著暫停，然後立即傳回工作流程工作物件。 若要在取得作業之前等候暫停完成，請使用或 Cmdlet 的 **wait** 參數 `Suspend-Job` `Wait-Job` 。 當工作流程工作暫停時，工作的 **State** 屬性值會被擱置。

是否能夠正確暫停需依賴檢查點。 目前的工作狀態、中繼資料及輸出會儲存在檢查點中，因此工作流程工作可以在不遺失狀態或資料的情況下繼續。 如果工作流程工作沒有檢查點，就無法正確地暫停。 若要新增檢查點至您正在執行的工作流程，請使用 **PSPersist** 工作流程一般參數。 您可以使用 **Force** 參數立即暫停任何工作流程工作，並暫停沒有檢查點的工作流程工作，但動作可能會導致狀態和資料遺失。

在自訂工作類型（例如工作流程工作）上使用 Job Cmdlet 之前 ( **PSWorkflowJob** ) 匯入支援自訂工作類型的模組，方法是使用 `Import-Module` Cmdlet 或使用或使用模組中的 Cmdlet。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：依名稱暫止工作流程工作

此範例顯示如何暫停工作流程工作。

第一個命令會建立 `Get-SystemLog` 工作流程。 工作流程會使用 `CheckPoint-Workflow` 活動來定義工作流程中的檢查點。

第二個命令會使用所有工作流程通用的 **AsJob** 參數，以背景工作的 `Get-SystemLog` 形式執行工作流程。 命令會使用 **JobName** 工作流程一般參數，指定工作流程工作的好記名稱。

第三個命令會使用 `Get-Job` Cmdlet 來取得 `Get-SystemLogJob` 工作流程工作。 輸出顯示 **PSJobTypeName** 屬性的值為 PSWorkflowJob。

第四個命令會使用 `Suspend-Job` Cmdlet 來暫停 `Get-SystemLogJob` 作業。 工作會執行至檢查點，然後暫停。

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### 範例2：暫停和繼續工作流程工作

此範例顯示如何暫停及繼續工作流程工作。

第一個命令會暫停 LogWorkflowJob 工作。此命令會立即傳回。 輸出顯示工作流程工作仍在執行中，即使它已暫止也一樣。

第二個命令會使用 `Get-Job` Cmdlet 來取得 LogWorkflowJob 工作。 輸出會顯示已順利暫停工作流程工作。

第三個命令 `Get-Job` 會使用 Cmdlet 來取得 LogWorkflowJob 作業，並使用 `Resume-Job` Cmdlet 來繼續執行。 輸出會顯示已順利繼續工作流程工作並且現在正在執行。

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### 範例3：暫停遠端電腦上的工作流程工作

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

此命令會使用 `Invoke-Command` Cmdlet 來暫停 Srv01 遠端電腦上的工作流程工作。 **篩選** 參數的值是指定 CustomID 值的雜湊表。
此 **CustomID** 為工作中繼資料 ( **PSPrivateMetadata** )。

### 範例4：等候工作流程工作暫停

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

此命令會暫停 VersionCheck 工作流程工作。 命令會使用 **Wait** 參數以等待工作流程工作暫停。 當工作流程工作執行至下一個檢查點並暫停時，命令就會完成並傳回工作物件。

### 範例5：強制工作流程工作暫停

```
PS C:\> Suspend-Job Maintenance -Force
```

此命令會強制暫停 Maintenance 工作流程工作。 維護作業沒有檢查點。 無法正確地暫停，而且可能無法正確地繼續。

## PARAMETERS

### -Filter

指定條件的雜湊表。 此 Cmdlet 會暫停滿足所有條件的工作。
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

### -Force

立即暫停工作流程工作。 這個動作可能會導致狀態與資料遺失。

依預設， `Suspend-Job` 會讓工作流程工作執行至下一個檢查點，然後暫停它。
您也可以使用此參數來暫停沒有檢查點的工作流程工作。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定此 Cmdlet 所暫停之作業的識別碼。

識別碼是一個整數，可唯一識別目前工作階段中的工作。 它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。 您可以輸入一個或多個識別碼，以逗號分隔。 若要尋找工作的識別碼，請使用 `Get-Job` Cmdlet。

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

指定此 Cmdlet 所暫停之作業的實例識別碼。 預設為所有工作。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。 若要尋找工作的實例識別碼，請使用 `Get-Job` 。

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

指定此 Cmdlet 停止的工作流程工作。 輸入包含工作流程工作的變數，或輸入可取得工作流程工作的命令。 您也可以透過管線將工作流程作業傳送至 `Suspend-Job` Cmdlet。

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

指定此 Cmdlet 所暫止之作業的易記名稱。 輸入一或多個工作流程工作名稱。
支援使用萬用字元。

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

指定工作狀態。 此 Cmdlet 只停止處於指定狀態的工作。 此參數可接受的值為：

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

`Suspend-Job` 只暫停處於執行 **中狀態的** 工作流程工作。

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

指出此 Cmdlet 會抑制命令提示字元，直到工作流程工作處於暫停狀態。 根據預設， `Suspend-Job` 會立即傳回，即使工作流程工作尚未處於暫停狀態也一樣。

**Wait** 參數相當於將 `Suspend-Job` 命令輸送至 `Wait-Job` Cmdlet。

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

您可以透過管道將所有類型的作業傳送至此 Cmdlet。 但是，如果 `Suspend-Job` 取得不支援之類型的作業，則會傳回終止錯誤。

## 輸出

### System.Management.Automation.Job
此 Cmdlet 會傳回它所暫停的工作。

## 注意

- 用於儲存暫停工作的機制與位置可能會視工作類型不同而改變。 例如，暫停的工作流程工作是預設儲存在一般檔案存放區，但是也可以儲存在資料庫中。
- 如果您提交不是處於執行中狀態的工作流程工作，則會 `Suspend-Job` 顯示警告訊息。 若要隱藏警告，請使用 **WarningAction** 一般參數搭配 SilentlyContinue 的值。

  如果作業不是支援暫止的型別，則會傳回 `Suspend-Job` 終止錯誤。

- 若要尋找已暫止的工作流程工作（包括此 Cmdlet 所暫停的工作），請使用 Cmdlet 的 **State** 參數 `Get-Job` 來取得處於暫停狀態的工作流程工作。
- 部分工作類型具有可防止 Windows PowerShell 暫停工作的選項或屬性。
  如果嘗試暫停工作失敗，請確認工作選項與屬性是否允許暫停。

## 相關連結

[Get-Job](Get-Job.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
