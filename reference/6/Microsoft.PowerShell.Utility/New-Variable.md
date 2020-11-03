---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: faf8bc399185da402bebb678b02927e0e5628662
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204320"
---
# New-Variable

## 概要
建立新變數。

## SYNTAX

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**新的-Variable** Cmdlet 會在 PowerShell 中建立新的變數。
您可以在建立變數時指派值給變數，或者在建立後指派或變更變數的值。

您可以使用 **New-Variable** 的參數來設定變數的屬性、設定變數的範圍，以及決定變數是公開或私用變數。

您通常會透過輸入變數名稱及其值來建立新的變數 (例如 `$Var = 3`)，但您可以使用 **New-Variable** Cmdlet 來使用其參數。

## 範例

### 範例 1︰建立變數

```
PS C:\> New-Variable days
```

此命令會建立名為 days 的新參數。
您不需要輸入 *Name* 參數。

### 範例 2︰建立變數並指派其值

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

此命令會建立名為 zipcode 的變數，並指派 98033 做為其值。

### 範例 3︰使用 ReadOnly 選項建立變數

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

此範例示範如何使用 **New-Variable** 的 ReadOnly 選項來保護變數不會遭到覆寫。

第一個命令會建立名為 Max 的新變數，並將它的值設為 256。
它會使用值為 ReadOnly 的 *Option* 參數。

第二個命令會嘗試建立名稱相同的第二個變數。
此命令會傳回錯誤，因為變數上已設定唯讀選項。

第三個命令會使用 *Force* 參數來覆寫變數上的唯讀保護。
在此情況下，使用相同名稱建立新變數的命令可以成功執行。

### 範例 4︰建立私用變數

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

此命令示範模組中私用變數的行為。
此模組包含 Get-Counter Cmdlet，它具有名為 Counter 的私用變數。
此命令會使用值為 Private 的 *Visibility* 參數來建立變數。

範例輸出會顯示私用變數的行為。
載入模組的使用者無法檢視或變更 Counter 變數的值，但模組中的命令可以讀取及變更 Counter 變數。

### 範例5：建立具有空格的變數

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

此命令示範可以建立具有空格的變數。
您可以使用「 **取得變數** 」 Cmdlet 或直接以大括弧分隔變數來存取這些變數。

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

### -Force
指出 Cmdlet 會使用和現有唯讀變數相同的名稱建立新變數。

根據預設，您可以覆寫變數，除非該變數具有 ReadOnly 或 Constant 的選項值。
如需詳細資訊，請參閱 *Option* 參數。

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

### -Name
指定新變數的名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Option
指定變數的 **Options** 屬性值。此參數可接受的值包括：

- 無。
不設定任何選項。
(None 為預設值。)
- ReadOnly。
可以刪除。
除非使用 *Force* 參數，否則無法變更。
- 私人。
變數只能在目前的範圍中使用。
- AllScope。
將複製變數到任何新建立的範圍。
- Constant。
不能刪除或變更。
Constant 只在您建立變數時有效。
您不能將現有變數的選項變更為 Constant。

若要查看工作階段中所有變數的 **Options** 屬性，請輸入 `Get-Variable | Format-Table -Property name, options -autosize`。

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
傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Scope
指定新變數的範圍。
此參數可接受的值為：

- 全域。
在全域範圍中建立的變數可在 PowerShell 處理常式中隨處存取。
- 本機。
區域範圍是指目前的範圍，這可以是任何範圍（視內容而定）。
- 指令碼：
在腳本範圍中建立的變數只能在其建立所在的腳本檔案或模組中進行存取。
- 私人。
在私用範圍中建立的變數無法在其存在的範圍之外存取。
您可以使用私用範圍，在其他範圍中建立具有相同名稱的專案私用版本。
- 相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父系，2是父範圍的父系，依此類推) 。
無法使用負數。

當未指定 scope 參數時，Local 是預設範圍。

如需詳細資訊，請參閱 about_Scopes。

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

### -Value
指定變數的初始值。

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
決定是否可在變數建立所在的工作階段之外看見變數。
此參數是針對將傳遞給其他使用者的指令碼和命令中使用所設計。
此參數可接受的值為：

- 公用。
可看見變數。
(Public 為預設值)。
- 私人。
看不到變數。

當變數為私用變數時，它不會顯示在變數清單中 (例如由 Get-Variable 傳回的清單) 或顯示在 Variable: 磁碟機的顯示畫面中。
讀取或變更私用變數值的命令會傳回錯誤。
但是，如果命令是寫入在定義變數的工作階段中，使用者就可以執行使用私用變數的命令。

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

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

### System.Object
您可以使用管線將值傳送至 **New-Variable** 。

## 輸出

### 無或 System.Management.Automation.PSVariable
使用 *PassThru* 參數時， **New-Variable** 會產生代表新變數的 **System.Management.Automation.PSVariable** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
