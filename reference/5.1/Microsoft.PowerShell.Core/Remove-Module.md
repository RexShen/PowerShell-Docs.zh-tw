---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: a1052c357f19fd8f06eb39a14f8e8eded0c881a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202680"
---
# Remove-Module

## 概要
移除目前工作階段的模組。

## SYNTAX

### NAME

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FullyQualifiedName

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModuleInfo

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**Remove-Module** Cmdlet 會從目前的工作階段移除模組的成員，例如 Cmdlet 和函式。

如果模組包含組件 (.dll)，則會移除組件所實作的所有成員，但不會將組件解除載入。

此 Cmdlet 不會將模組解除安裝，或將它從電腦中刪除。
它只會影響目前的 PowerShell 會話。

## 範例

### 範例 1：移除模組

```powershell
Remove-Module -Name "BitsTransfer"
```

此命令從目前的工作階段移除 BitsTransfer 模組。

### 範例 2：移除所有模組

```powershell
Get-Module | Remove-Module
```

此命令從目前的工作階段移除所有模組。

### 範例 3︰使用管線移除模組

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

此命令從目前的工作階段移除 BitsTransfer 和 PSDiagnostics 模組。

命令使用管線運算子 (|) 將模組名稱傳送至 **Remove-Module** 。
它使用 *Verbose* 一般參數，取得所移除之成員的詳細資訊。

*Verbose* 訊息會顯示已移除的項目。
這些訊息會有所不同，因為 BitsTransfer 模組包含一個實作其 Cmdlet 的組件，以及一個含有自己的組件的巢狀模組。
PSDiagnostics 模組則包含可匯出函式的模組指令檔 (.psm1)。

### 範例 4︰使用 ModuleInfo 移除模組

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

此命令會使用 *ModuleInfo* 參數移除 BitsTransfer 模組。

## PARAMETERS

### -Force

指出此 Cmdlet 會移除唯讀模組。
**Remove-Module** 預設只會移除讀寫模組。

**ReadOnly** 和 **ReadWrite** 值是儲存在模組的 **AccessMode** 屬性中。

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

### -FullyQualifiedName

指定要移除之模組的完整名稱。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ModuleInfo

指定要移除的模組物件。
輸入包含模組物件 ( **PSModuleInfo** ) 的變數，或輸入可取得模組物件的命令，例如 Get-Module 命令。
您也可以使用管線將模組物件傳送至 **Remove-Module** 。

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要移除之模組的名稱。
允許使用萬用字元。
您也可以使用管線將名稱字串傳送至 **Remove-Module** 。

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
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

### System.String、System.Management.Automation.PSModuleInfo

您可以使用管線將模組名稱和模組物件傳送至 **Remove-Module** 。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[about_Modules](About/about_Modules.md)
