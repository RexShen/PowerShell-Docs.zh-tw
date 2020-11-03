---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 2041d40803aac1afafad2a0855aa39ebba9ad814
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239859"
---
# Set-Variable

## 概要
設定變數的值。 如果要求的名稱的變數不存在，便會建立變數。

## SYNTAX

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Set-Variable` 值指派給指定的變數，或變更目前的值。 如果變數不存在，Cmdlet 就會建立變數。

## 範例

### 範例 1︰設定變數，並取得其值

這些命令會將變數的值設定 `$desc` 為 `A description` ，然後取得變數的值。

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### 範例 2︰設定全域、唯讀變數

這個範例會建立全域的唯讀變數，其中包含系統上的所有處理常式，然後顯示該變數的所有屬性。

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

此命令會使用 `Set-Variable` Cmdlet 來建立變數。 它使用 **PassThru** 參數建立代表新變數的物件，並使用管線運算子 (`|`) 將物件傳遞給 `Format-List` Cmdlet。 它會使用的 **屬性** 參數搭配 `Format-List` 所有 () 的值 `*` ，以顯示新建立之變數的所有屬性。

值是以 `(Get-Process)` 括弧括住，以確保它會在儲存于變數之前執行。 否則，變數會包含 " **Get-Process** " 單字。

### 範例 3︰了解公用與私用變數

此範例示範如何將變數的可見度變更為 `Private` 。 此變數可以由有必要權限的指令碼讀取和變更，但使用者看不到此變數。

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

此命令會顯示如何將變數的可見性變更為「私用」。 此變數可以由有必要權限的指令碼讀取和變更，但使用者看不到此變數。

## PARAMETERS

### -Description

指定變數的描述。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

指定此 Cmdlet 從作業排除之項目的陣列。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

允許您建立與現有唯讀變數同名的變數，或變更唯讀變數的值。

根據預設，您可以覆寫變數，除非變數有或的選項值 `ReadOnly` `Constant` 。 如需詳細資訊，請參閱 **Option** 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

指定此 Cmdlet 在作業中納入之項目的陣列。 此參數的值會限定 **Name** 參數。 輸入名稱或名稱模式，例如 `c*`。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

指定變數名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option

指定變數的 **Options** 屬性值。

有效值為：

- `None`：不設定任何選項。 ("None" 為預設值。)
- `ReadOnly`：可以刪除。 除非使用 Force 參數，否則無法變更。
- `Constant`：無法刪除或變更。 `Constant` 只有在您建立變數時才有效。 您無法將現有變數的選項變更為 `Constant` 。
- `Private`：變數僅適用于目前的範圍。
- `AllScope`：變數會複製到所建立的任何新範圍。

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表新變數的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定變數的範圍。此參數可接受的值包括：

- 全球
- 本機
- 指令碼
- 私人
- 相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。

Local 為預設值。

如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定變數的值。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Visibility

決定是否可在變數建立所在的工作階段之外看見變數。 此參數是針對將傳遞給其他使用者的指令碼和命令中使用所設計。

有效值為：

- Public：可看見變數。 ("Public" 為預設值。)
- Private：看不到變數。

當變數為私用時，它不會出現在變數的清單中，例如傳回的變數， `Get-Variable` 或變數 **：** 磁片磁碟機的顯示中。 讀取或變更私用變數值的命令會傳回錯誤。 但是，如果命令是寫入在定義變數的工作階段中，使用者就可以執行使用私用變數的命令。

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
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

### System.Object

您可以使用管線將代表變數值的物件傳送至 `Set-Variable` 。

## 輸出

### 無或 System.Management.Automation.PSVariable

當您使用 **PassThru** 參數時，會 `Set-Variable` 產生代表新變數或已變更變數的 **system.management.automation.psvariable** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)
