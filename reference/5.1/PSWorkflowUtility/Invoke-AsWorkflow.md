---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202964"
---
# Invoke-AsWorkflow

## 概要
以 Windows PowerShell 工作流程形式執行命令或運算式。

## SYNTAX

### Command (預設值)

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### 運算式

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-AsWorkflow`工作流程會以工作流程中的內嵌腳本形式執行任何命令或運算式。
這些工作流程使用標準工作流程語意、具有所有工作流程一般參數，而且具有工作流程的所有優點 (包括可停止、繼續及復原的功能)。

工作流程是針對長時間執行的命令 (這些命令通常用來收集重要資料) 所設計，但也可用來執行任何命令。
如需詳細資訊，請參閱 [about_Workflows](../PSWorkflow/About/about_Workflows.md)。

您也可以新增工作流程一般參數到此命令。
如需工作流程一般參數的詳細資訊，請參閱 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)

此工作流程是在 Windows PowerShell 3.0 引進。

## 範例

### 範例 1：以工作流程形式執行 Cmdlet

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

此命令會 `Get-ExecutionPolicy` 在數百部電腦上以工作流程形式執行 Cmdlet。

此命令會使用 **CommandName** 參數來指定要在工作流程中執行的 Cmdlet。
它會使用 **PSComputerName** 工作流程一般參數來指定要在其上執行命令的電腦。
**PSComputerName** 參數的值是一個 `Get-Content` 命令，可從 Servers.txt 檔案中取得電腦名稱稱清單。
參數值會以括弧括住，以在 `Get-Command` 使用值之前直接 Windows PowerShell 執行命令。

類似所有遠端命令，若命令在本機電腦上執行 (若 PSComputerName 參數的值包含本機電腦)，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

### 範例 2：執行具有參數的 Cmdlet

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

第一個命令會使用 `Import-Csv` Cmdlet 從 Servers.csv 檔案中的內容建立物件。 此命令會使用 `Header` 參數來建立資料 `ServerName` 行的屬性，該資料行包含目的電腦的名稱，也稱為「遠端節點」。 命令會將結果儲存在 `$s` 變數中。

第二個命令會使用 `Invoke-AsWorkflow` 工作流程在 `Get-ExecutionPolicy` Servers.csv 檔案中的電腦上執行命令。 命令使用的 **CommandName** 參數 `Invoke-AsWorkflow`  來指定要在工作流程中執行的命令。 它會使用的 `Parameter` 參數 `Invoke-AsWorkflow` ，以 `Scope` 進程的值指定 `Get-ExecutionPolicy` Cmdlet 的參數。 **Process** 此命令也會使用 `PSConnectionRetryCount` 工作流程一般參數，將每個電腦的命令限制為五次，並使用 `PSComputerName` 工作流程一般參數來指定遠端節點的名稱， (目的電腦) 。 參數的值 `PSComputerName` 是可取得 `ServerName` 變數中每個物件之屬性的運算式 `$s` 。

這些命令會以 `Get-ExecutionPolicy` 工作流程的形式在數百部電腦上執行命令。
此命令會使用 `Scope` Cmdlet 的參數搭配 `Get-ExecutionPolicy` **Process** 值，以取得目前會話中的執行原則。

### 範例 3：以工作流程形式執行運算式

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

此命令會使用 `Invoke-AsWorkflow` 工作流程來執行 Ipconfig 命令，做為 DomainControllers.txt 檔中所列電腦上的工作流程工作。

此命令會使用 `Expression` 參數來指定要執行的運算式。
它會使用 `PSComputerName` 工作流程一般參數來指定遠端節點 (目的電腦) 的名稱。

此命令也會使用 `AsJob` 和 `JobName` 工作流程一般參數，以 "Ipconfig" 工作名稱在每部電腦上以背景工作的形式執行工作流程。

此命令會傳回 `ContainerParentJob` (`System.Management.Automation.ContainerParentJob`) 的物件，其中包含每一部電腦上的工作流程工作。

## PARAMETERS

### -CommandName

以工作流程形式執行指定的 Cmdlet 或進階函式。
輸入 Cmdlet 或函數名稱，例如 `Update-Help` 、 `Set-ExecutionPolicy` 或 `Set-NetFirewallRule` 。

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expression

指定此 Cmdlet 做為工作流程執行的運算式。
以字串形式輸入運算式，例如 `"ipconfig /all"` 。
若運算式包含空格或特殊字元，請將運算式括在引號中。

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parameter

指定參數中所指定之命令的參數和參數值 `CommandName` 。
輸入雜湊表，其中每個索引鍵都是參數名稱，而其值為參數值，例如 `@{ExecutionPolicy="AllSigned"}` 。

如需雜湊表的相關資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

用來允許管線輸入。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

### WorkflowCommonParameters

此 Cmdlet 也支援工作流程特定的一般參數。
如需詳細資訊，請參閱 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)。

## 輸入

### System.Object

您可以透過管線將任何物件傳送至 `InputObject` 參數。

## 輸出

### 無

此命令不會產生任何輸出。
不過，它會執行工作流程，工作流程可能會產生輸出。

## 注意

## 相關連結

[New-PSWorkflowExecutionOption](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[New-PSWorkflowSession](../PSWorkflow/New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_Workflow_Common_Parameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)
