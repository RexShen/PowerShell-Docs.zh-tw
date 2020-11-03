---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: c0ee5552e33792f208faba63dc05ddb93473bc49
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "93206095"
---
# Split-Path

## 概要
傳回路徑的指定部分。

## SYNTAX

### ParentSet (預設值)

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LeafSet

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### LeafBaseSet

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### ExtensionSet

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### QualifierSet

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### NoQualifierSet

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

此 `Split-Path` Cmdlet 只會傳回路徑的指定部分，例如上層資料夾、子資料夾或檔案名。 它也可以取得分割路徑所參照的項目，並分辨路徑是相對路徑或絕對路徑。

您可以使用這個 Cmdlet 來只取得或只送出路徑的選取部分。

## 範例

### 範例1：取得路徑的辨識符號

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

此命令只會傳回路徑的辨識符號。 辨識符號是磁片磁碟機。

### 範例2：顯示檔案名

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

這個命令會顯示分割路徑所參照的檔案。 因為此路徑會分割至最後一個專案（也稱為分葉），所以命令只會顯示檔案名。

**Resolve** 參數會告訴您 `Split-Path` 顯示分割路徑所參考的專案，而不是顯示分割路徑。

如同所有 `Split-Path` 命令，此命令會傳回字串。 它不會傳回代表檔案的 **FileInfo** 物件。

### 範例3：取得父容器

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

這個命令只會傳回路徑的父容器。 因為它不包含任何用來指定分割的參數，所以會 `Split-Path` 使用預設的分割位置，也就是 **父系** 。

### 範例4：判斷路徑是否為絕對路徑

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

這個命令會判斷路徑是相對路徑或絕對路徑。 在此情況下，因為路徑相對於目前的資料夾，而該資料夾是以點 (`.`) 表示，所以會傳回 `$False` 。

### 範例5：將位置變更為指定的路徑

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

此命令會將您的位置變更為包含 PowerShell 設定檔的資料夾。

括弧中的命令會使用 `Split-Path` ，只傳回內建變數中所儲存之路徑的父系 `$Profile` 。 **Parent** 參數是預設的分割位置參數。
因此，您可以在命令中省略它。 括弧直接 PowerShell 以執行命令。 這是移至具有完整路徑名稱之資料夾的實用方式。

### 範例6：使用管線分割路徑

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

此命令會使用管線運算子 (`|`) 傳送的路徑 `Split-Path` 。 此路徑是括在引號中來表示它是單一語彙基元。

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -擴充

指出這個 Cmdlet 只會傳回分葉的延伸。 例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 `.log` 。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IsAbsolute

指出如果路徑是絕對路徑，此 Cmdlet 會傳回 $True，如果是相對路徑，則會傳回 $False。 絕對路徑的長度大於零，且不會使用點 (`.`) 來指出目前的路徑。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Leaf

指出此 Cmdlet 只會傳回路徑中的最後一個專案或容器。 例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 pass1.log .log。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LeafBase

指出此 Cmdlet 只會傳回分葉的基底名稱。 例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 `Pass1` 。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

指定要分割的路徑。 與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoQualifier

指出此 Cmdlet 會傳回不含限定詞的路徑。 針對 FileSystem 或登錄提供者，限定詞是提供者路徑的磁片磁碟機，例如 `C:` 或 `HKCU:` 。 例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它只會傳回 `\Test\Logs\Pass1.log` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Parent

指出此 Cmdlet 只會傳回該路徑所指定之專案或容器的父容器。 例如，在路徑中 `C:\Test\Logs\Pass1.log` ，它會傳回 `C:\Test\Logs` 。
**Parent** 參數是預設的分割位置參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要分割的路徑。 允許使用萬用字元。 如果路徑包含空格，請將它括在引號中。 您也可以使用管線將路徑傳送至此 Cmdlet。

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Qualifier

指出此 Cmdlet 只會傳回指定路徑的辨識符號。 針對 FileSystem 或登錄提供者，限定詞是提供者路徑的磁片磁碟機，例如 `C:` 或 `HKCU:` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Resolve

指出此 Cmdlet 會顯示產生之分割路徑所參考的專案，而不是顯示路徑元素。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### System.String、System.Boolean

`Split-Path` 傳回文字字串。 當您指定 **Resolve** 參數時， `Split-Path` 會傳回描述專案位置的字串，而不會傳回代表專案的物件，例如 **FileInfo** 或 **RegistryKey** 物件。

當您指定 **IsAbsolute** 參數時，會傳回 `Split-Path` **布林** 值。

## 注意

- 分割位置參數 (辨識 **符號** 、 **父系** 、 **延伸** 模組、分 **葉** 、 **LeafBase** 和 **NoQualifier** ) 是專屬的。 在每個命令中只能使用一個。

- 包含路徑名詞 (Path **Cmdlet 的 Cmdlet** 會 **Path** ) 使用路徑名稱，並傳回所有 PowerShell 提供者都可解讀的精簡格式名稱。 它們是設計用於程式與指令碼，您可以在其中以特定格式顯示所有或部分路徑名稱。 使用 **Dirname** 、 **Normpath** 、 **Realpath** 、 **Join** 或其他路徑操作工具的方式來使用它們。

- 您可以搭配多個提供者使用 **Path** Cmdlet。 其中包括 FileSystem、Registry 和 Certificate provider。

- `Split-Path` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 about_Providers。

## 相關連結

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Test-Path](Test-Path.md)
