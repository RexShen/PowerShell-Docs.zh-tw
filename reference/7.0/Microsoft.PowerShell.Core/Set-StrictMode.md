---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: ef80c2c63855bffcd23f51474009b241f8f4b3ba
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201219"
---
# Set-StrictMode

## 概要
在運算式、指令碼和指令碼區塊中建立並強制執行編碼規則。

## SYNTAX

### Version (預設值)

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### 關閉

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## DESCRIPTION

`Set-StrictMode`Cmdlet 會為目前的範圍和所有子範圍設定 strict 模式，並將其開啟或關閉。 當 strict 模式開啟時，如果運算式、腳本或腳本區塊的內容違反基本最佳作法編碼規則，則 PowerShell 會產生終止錯誤。

使用 **Version** 參數來決定要強制執行哪些編碼規則。

`Set-PSDebug -Strict` Cmdlet 會開啟全域範圍的 strict 模式。 `Set-StrictMode` 只會影響目前的範圍及其子範圍。 因此，您可以在腳本或函式中使用它來覆寫繼承自全域範圍的設定。

當 `Set-StrictMode` 關閉時，PowerShell 會有下列行為：

- 未初始化的變數會假設值為 0 (零) 或 `$Null` （視類型而定）
- 參考不存在的屬性會傳回 `$Null`
- 不當函數語法的結果會隨著錯誤狀況而有所不同
- 嘗試在陣列中使用不正確索引來取得值 `$Null`

## 範例

### 範例 1︰開啟 strict 模式為 1.0 版

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

當 strict 模式設定為1.0 版時，嘗試參考未初始化的變數將會失敗。

### 範例 2︰開啟 strict 模式為 2.0 版

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$string.Month -eq $null
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$string.Month -eq $null
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

此命令會開啟 strict 模式，並將它設定為 2.0 版。 因此，如果您針對函式呼叫使用方法語法（使用括弧和逗號）或參考未初始化的變數或不存在的屬性，則 PowerShell 會傳回錯誤。

範例輸出顯示 2.0 版之 strict 模式的作用。

如果不是 2.0 版的 strict 模式，"(3,4)" 值會解譯為不新增任何項目的單一陣列物件。 如果使用 2.0 版的 strict 模式，則會正確解譯為提交兩個值的錯誤語法。

如果沒有2.0 版，則只會傳回字串中不存在之 **Month** 屬性的參考 `$Null` 。 如果使用 2.0 版，則會正確解譯為參考錯誤。

### 範例3：開啟 strict 模式為3.0 版

如果 strict 模式設定為 **Off** ，則無效或超出界限索引結果會傳回 null 值。

```powershell
# Strict mode is off by default.
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $a[2] -eq $null
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $a['abc'] -eq $null
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

如果 strict 模式設定為第3版或更高版本，則無效或超出範圍索引會導致錯誤。

## PARAMETERS

### -Off

指出此 Cmdlet 會針對目前的範圍和所有子範圍關閉 strict 模式。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

指定在 strict 模式中導致錯誤的條件。 此參數會接受任何有效的 PowerShell 版本號碼。 任何大於3的數位都會視為 **最新** 的。

此參數的有效值為：

- 1.0
  - 禁止參考未初始化的變數，但字串中未初始化的變數除外。
- 2.0
  - 禁止參考未初始化的變數。 這包括字串中未初始化的變數。
  - 禁止參考不存在的物件屬性。
  - 禁止使用呼叫方法語法的函式呼叫。
- 3.0
  - 禁止參考未初始化的變數。 這包括字串中未初始化的變數。
  - 禁止參考不存在的物件屬性。
  - 禁止使用呼叫方法語法的函式呼叫。
  - 禁止超出範圍或無法解析的陣列索引。
- Latest
  - 選取可用的最新版本。 最新的版本是最嚴格的。 使用此值可確保腳本會使用最嚴格的可用版本（即使將新版本新增至 PowerShell 亦同）。

> [!CAUTION]
> 使用腳本中的 **最新****版本** 。 新版本的 PowerShell 可能會變更 **最新** 版本的意義。 因此，針對舊版 PowerShell 所撰寫的腳本，在 `Set-StrictMode -Version Latest` 較新版本的 powershell 中執行時，會受限於更嚴格的規則。

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

`Set-StrictMode` 只有在設定的範圍及其子範圍中才有效。 如需 PowerShell 中之範圍的詳細資訊，請參閱 [about_Scopes](about/about_Scopes.md)。

## 相關連結

[Set-PSDebug](Set-PSDebug.md)
