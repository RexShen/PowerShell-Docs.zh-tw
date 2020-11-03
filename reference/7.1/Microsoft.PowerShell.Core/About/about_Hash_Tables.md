---
description: 描述如何在 PowerShell 中建立、使用和排序雜湊表。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: 0c4c54ea0ac017f0238ea5766c3489a1918d8fdd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206735"
---
# <a name="about-hash-tables"></a>關於雜湊表

## <a name="short-description"></a>簡短描述
描述如何在 PowerShell 中建立、使用和排序雜湊表。

## <a name="long-description"></a>詳細描述

雜湊表（又稱為字典或關聯陣列）是一種精簡的資料結構，它會儲存一或多個索引鍵/值組。 例如，雜湊表可能包含一連串的 IP 位址和電腦名稱稱，其中 IP 位址是金鑰，而電腦名稱稱則是值，反之亦然。

在 PowerShell 中，每個雜湊表都是雜湊表 (System.object) 物件。 您可以在 PowerShell 中使用雜湊表物件的屬性和方法。

從 PowerShell 3.0 開始，您可以使用 [已排序] 屬性，在 PowerShell 中 (OrderedDictionary) 建立已排序的字典。

排序的字典與雜湊表不同之處在于，索引鍵一律會依列出的順序出現。 未判斷雜湊表中的索引鍵順序。

雜湊表中的索引鍵和值也是 .NET 物件。 它們最常是字串或整數，但可以有任何物件類型。 您也可以建立嵌套雜湊表，其中索引鍵的值是另一個雜湊表。

雜湊資料表經常會使用，因為它們對於尋找和取出資料非常有效率。 您可以使用雜湊表來儲存清單，並在 PowerShell 中建立計算屬性。 而且，PowerShell 有一個 Cmdlet Convertfrom-string-至 convertfrom-stringdata，可將字串轉換成雜湊表。

### <a name="syntax"></a>Syntax

雜湊表的語法如下所示：

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

已排序字典的語法如下所示：

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

[已排序] 屬性是在 PowerShell 3.0 中引進。

### <a name="creating-hash-tables"></a>建立雜湊表

若要建立雜湊表，請遵循下列指導方針：

- 使用 at sign ( @ ) 來開始雜湊表。
- 以大括弧括住雜湊表 ({}) 。
- 針對雜湊表的內容輸入一或多個索引鍵/值組。
- 使用等號 (=) ，將每個索引鍵與其值分隔開來。
- 使用分號 (; ) 或分行符號來分隔索引鍵/值組。
- 包含空格的索引鍵必須以引號括住。 值必須是有效的 PowerShell 運算式。 字串必須以引號出現，即使它們不包含空格。
- 若要管理雜湊表，請將它儲存在變數中。
- 將已排序的雜湊表指派給變數時，請將 [已排序] 屬性放在 "@" 符號前面。 如果您將它放在變數名稱之前，命令就會失敗。

若要在 $hash 的值中建立空白雜湊表，請輸入：

```powershell
$hash = @{}
```

您也可以在建立索引鍵和值時，將索引鍵和值加入至雜湊表。 例如，下列語句會建立含有三個索引鍵的雜湊表。

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a>建立已排序的字典

您可以藉由加入 OrderedDictionary 類型的物件來建立已排序的字典，但建立已排序字典最簡單的方式是使用 [已排序] 屬性。

[已排序] 屬性是在 PowerShell 3.0 中引進。

將屬性緊接在 "@" 符號前面。

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

您可以使用與雜湊資料表相同的方式來使用已排序的字典。
這兩種類型都可以當做參數值使用，這些參數會採用雜湊表或字典 (iDictionary) 。

您無法使用 [已排序] 屬性來轉換或轉換雜湊表。 如果您將已排序的屬性放在變數名稱之前，命令會失敗並出現下列錯誤訊息。

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

若要更正運算式，請移動 [已排序] 屬性。

```powershell
PS C:\> $hash = [ordered]@{}
```

您可以將已排序的字典轉換成雜湊表，但是即使您清除變數並輸入新值，也無法復原已排序的屬性。 若要重新建立順序，您必須移除並重新建立變數。

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a>顯示雜湊表

若要顯示儲存在變數中的雜湊表，請輸入變數名稱。
依預設，雜湊資料表會顯示為具有一個索引鍵資料行的資料表，以及一個值的資料行。

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

雜湊資料表有索引鍵和值屬性。 您可以使用點標記法來顯示所有的索引鍵或所有的值。

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

每個索引鍵名稱也是雜湊表的屬性，其值是索引鍵名稱屬性的值。 使用下列格式來顯示內容值。

```powershell
$hashtable.<key>
<value>
```

例如：

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

如果索引鍵名稱與雜湊表類型的其中一個屬性名稱衝突，您就可以使用 `PSBase` 來存取這些屬性。 例如，如果索引鍵名稱是， `keys` 而您想要傳回索引鍵的集合，請使用下列語法：

```powershell
$hashtable.PSBase.Keys
```

雜湊資料表有一個 Count 屬性，表示雜湊表中的索引鍵/值組數目。

```powershell
C:\PS> $hash.count
3
```

雜湊資料表資料表不是陣列，因此您不能使用整數做為雜湊表的索引，但您可以使用索引鍵名稱來編制雜湊表的索引。
如果索引鍵是字串值，請用引號括住索引鍵名稱。

例如：

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a>新增和移除索引鍵和值

若要將索引鍵和值新增至雜湊表，請使用下列命令格式。

```powershell
$hash["<key>"] = "<value>"
```

例如，若要將值為 "Now" 的 "Time" 索引鍵新增至雜湊表，請使用下列語句格式。

```powershell
$hash["Time"] = "Now"
```

您也可以使用 system.string 物件的 Add 方法，將索引鍵和值加入至雜湊表。 Add 方法具有下列語法：

```powershell
Add(Key, Value)
```

例如，若要將值為 "Now" 的 "Time" 索引鍵新增至雜湊表，請使用下列語句格式。

```powershell
$hash.Add("Time", "Now")
```

而且，您可以使用加法運算子 (+) 將索引鍵和值加入至雜湊表，以將雜湊資料表加入至現有的雜湊表。 例如，下列語句會將值為 "Now" 的 "Time" 索引鍵新增至 $hash 變數中的雜湊表。

```powershell
$hash = $hash + @{Time="Now"}
```

您也可以加入儲存在變數中的值。

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

您無法使用減法運算子來移除雜湊表中的索引鍵/值組，但您可以使用 Hashtable 物件的 Remove 方法。 Remove 方法會將索引鍵做為其值。

Remove 方法具有下列語法：

```
Remove(Key)
```

例如，若要從 $hash 變數值中的雜湊表移除時間 = 現在的索引鍵/值組，請輸入：

```powershell
$hash.Remove("Time")
```

您可以在 PowerShell 中使用雜湊表物件的所有屬性和方法，包括 Contains、Clear、Clone 和 CopyTo。 如需雜湊表物件的詳細資訊，請參閱 MSDN 上的 "system.string"。

### <a name="object-types-in-hashtables"></a>雜湊表中的物件類型

雜湊表中的索引鍵和值可以具有任何 .NET 物件類型，而單一雜湊資料表可以有多個類型的索引鍵和值。

下列語句會建立進程名稱字串和處理物件值的雜湊表，並將它儲存在 \$ p 變數中。

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

您可以在 p 中顯示雜湊表 \$ ，並使用索引鍵名稱屬性來顯示這些值。

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

雜湊表中的索引鍵也可以是任何 .NET 類型。 下列語句會將索引鍵/值組加入至 p 變數中的雜湊表 \$ 。 金鑰是代表 WinRM 服務的服務物件，而值則是服務的目前狀態。

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

您可以使用在雜湊表中用於其他配對的相同方法，來顯示和存取新的索引鍵/值組。

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

雜湊表中的索引鍵和值也可以是雜湊表物件。 下列語句會將索引鍵/值組加入至 p 變數中的雜湊表 \$ ，其中索引鍵是字串、Hash2，而值是具有三個索引鍵/值組的雜湊表。

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

您可以使用相同的方法來顯示及存取新的值。

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a>排序索引鍵和值

雜湊表中的專案本質上未排序。 每次您顯示索引鍵/值組時，這些索引鍵/值組可能會以不同的順序出現。

雖然您無法排序雜湊表，但您可以使用雜湊表的 GetEnumerator 方法來列舉索引鍵和值，然後使用 Sort-Object Cmdlet 來排序要顯示的列舉值。

例如，下列命令會列舉 p 變數中雜湊表中的索引鍵和值， \$ 然後依字母順序排序索引鍵。

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

下列命令會使用相同的程式，以遞減順序排序雜湊值。

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a>從雜湊表建立物件

從 PowerShell 3.0 開始，您可以從屬性和屬性值的雜湊表建立物件。

語法如下：

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

這個方法只適用於具有 null 建構函式 (也就是沒有參數的建構函式) 的類別。 物件屬性必須是公用而且可設定。

如需詳細資訊，請參閱 [about_Object_Creation](about_Object_Creation.md)。

### <a name="convertfrom-stringdata"></a>ConvertFrom-StringData

`ConvertFrom-StringData`Cmdlet 會將字串或此處的索引鍵/值組字串轉換成雜湊表。 您可以 `ConvertFrom-StringData` 在腳本的 [資料] 區段中安全地使用指令程式，您可以使用它搭配指令 `Import-LocalizedData` 程式，在使用者介面中顯示使用者訊息 (UI) 目前使用者的文化特性。

這裡-字串在雜湊表中的值包含引號時特別有用。 如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。

下列範例示範如何在上述範例中建立使用者訊息的這個字串，以及如何使用將 `ConvertFrom-StringData` 它們從字串轉換成雜湊表。

下列命令會建立此索引鍵/值組的字串，然後將它儲存在 \$ 字串變數中。

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

此命令會使用 ConvertFrom-StringData Cmdlet，將此字串轉換成雜湊表。

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](about_Quoting_Rules.md)。

## <a name="see-also"></a>另請參閱

[about_Arrays](about_Arrays.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[System.Collections.Hashtable](/dotnet/api/system.collections.hashtable)

