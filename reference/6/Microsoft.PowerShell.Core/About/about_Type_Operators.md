---
description: 描述可搭配 Microsoft .NET 類型使用的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 6b4b0f2eea28ddd5544174d01359491808e2e653
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208404"
---
# <a name="about-type-operators"></a>關於類型運算子

## <a name="short-description"></a>簡短描述
描述可搭配 Microsoft .NET 類型使用的運算子。

## <a name="long-description"></a>詳細描述

布林型別運算子 `-is` 會 (， `-isNot`) 判斷物件是否為指定之 .net 型別的實例。 `-is`如果類型相符，運算子會傳回 **TRUE** 值，否則會傳回 **FALSE** 值。 `-isNot`如果類型相符，運算子會傳回 **FALSE** 的值，否則會傳回 **TRUE** 值。

`-as`運算子會嘗試將輸入物件轉換成指定的 .net 型別。 如果成功，它會傳回已轉換的物件。 如果失敗，則會傳回 `$null`。 它不會傳回錯誤。

下表列出 PowerShell 中的型別運算子。

|運算子|描述                |範例                          |
|--------|---------------------------|---------------------------------|
|`-is`   |當輸入時傳回 TRUE|`(get-date) -is [DateTime]`      |
|        |是的實例。      |`True`                           |
|        |指定的 .NET 類型。       |                                 |
|`-isNot`|當輸入時傳回 TRUE|`(get-date) -isNot [DateTime]`   |
|        |不是的實例。     |`False`                          |
|        |specified.NET 類型。        |                                 |
|`-as`   |將輸入轉換為  |`"5/7/07" -as [DateTime]`        |
|        |指定的 .NET 類型。       |`Monday, May 7, 2007 12:00:00 AM`|

型別運算子的語法如下所示：

```powershell
<input> <operator> [.NET type]
```

您也可以使用下列語法：

```powershell
<input> <operator> ".NET type"
```

.NET 類型可以用方括弧或字串的形式（例如或 system.string）撰寫為類型名稱 `[DateTime]` `"DateTime"` 。 **System.DateTime** 如果類型不在 system 命名空間的根目錄中，請指定物件類型的完整名稱。 您可以省略 "System."。 例如，若要指定 **system.object** ，請輸入 `[System.Diagnostics.Process]` 、 `[Diagnostics.Process]` 或 `"Diagnostics.Process"` 。

型別運算子一律會以整體的形式在輸入物件上運作。 也就是說，如果輸入物件是集合，它就是經過測試的 _集合_ 型別，而不是集合的 _元素_ 類型。

### <a name="-isisnot-operators"></a>-是/isNot 運算子

**布林** 型別運算子 (`-is` 和 `-isNot`) 一律會傳回 **布林** 值，即使輸入是物件的集合也一樣。

如果的型別與 `<input>` 或 _衍生_ 自 .net 型別，則運算子會傳回 `-is` `$True` 。

例如， **DirectoryInfo** 型別衍生自 **FileSystemInfo** 型別。 因此，這兩個範例都會傳回 **True** 。

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

`-is`如果在比較中實作為介面，運算子也可以符合介面 `<input>` 。 在此範例中，輸入是陣列。 陣列會執行 **system.object** 介面。

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a>-as 運算子

`-as`運算子會嘗試將輸入物件轉換成指定的 .net 型別。 如果成功，它會傳回已轉換的物件。 如果失敗，則會傳回 `$null` 。 它不會傳回錯誤。

如果 `<input>` 是 _衍生_ 自 .net 型別的型別，則會 `-as` _傳回_ 未變更的輸入物件。 例如， **DirectoryInfo** 型別衍生自 **FileSystemInfo** 型別。 因此，在下列範例中，物件類型會保持不變：

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a>轉換 DateTime 類型會區分文化特性

不同于型別轉換， `[DateTime]` 使用運算子轉換成型別 `-as` 只適用于根據目前文化特性的規則格式化的字串。

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

若要尋找物件的 .NET 類型，請使用 `Get-Member` Cmdlet。 或者，將所有物件的 **GetType** 方法與這個方法的 **FullName** 屬性一起使用。 例如，下列語句會取得命令的傳回數值型別 `Get-Culture` ：

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a>範例

下列範例示範型別運算子的一些用法：

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

下列範例顯示當輸入是物件的集合時，相符的型別是集合的 .NET 型別，而不是集合中個別物件的型別。

在此範例中，雖然和 Cmdlet 都會傳回 system.string `Get-Culture` `Get-UICulture` 物件，但這些物件的集合是 system.object 陣列。 **System.Globalization.CultureInfo**

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

下列範例示範如何使用 `-as` 運算子。

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

下列範例顯示當 `-as` 運算子無法將輸入物件轉換成 .net 型別時，它會傳回 `$null` 。

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a>另請參閱

[about_Operators](about_Operators.md)
