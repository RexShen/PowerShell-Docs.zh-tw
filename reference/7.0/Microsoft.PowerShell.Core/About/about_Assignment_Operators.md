---
description: 描述如何使用運算子將值指派給變數。
keywords: powershell,cmdlet
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: fba0c5f5e5263af15eb3d56f1c42a881057afc46
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207776"
---
# <a name="about-assignment-operators"></a>關於指派運算子

## <a name="short-description"></a>簡短描述
描述如何使用運算子將值指派給變數。

## <a name="long-description"></a>完整描述

指派運算子會將一個或多個值指派給變數。 它們可以對指派之前的值執行數值運算。

PowerShell 支援下列指派運算子。

|運算子|描述                                                  |
|--------|-------------------------------------------------------------|
|=       |將變數的值設定為指定的值。         |
|+=      |以指定的值增加變數的值，或 |
|        |將指定的值附加至現有的值。           |
|-=      |將變數的值減少為指定的值。    |
|*=      |將變數的值乘以指定的值，或|
|        |將指定的值附加至現有的值。           |
|/=      |將變數的值除以指定的值。      |
|%=      |將變數的值除以指定的值，然後   |
|        |然後，將餘數 (模數) 指派給變數。        |
|++      |增加變數的值、可指派的屬性，或   |
|        |陣列元素，1。                                          |
|--      |減少變數的值、可指派的屬性，或   |
|        |陣列元素，1。                                          |

## <a name="syntax"></a>Syntax

指派運算子的語法如下所示：

`<assignable-expression>` `<assignment-operator>` `<value>`

可指派的運算式包括變數和屬性。 此值可以是單一值、值的陣列，或是命令、運算式或語句。

遞增和遞減運算子是一元運算子。 每個都有前置和後置版本。

`<assignable-expression><operator>`
`<operator><assignable-expression>`

可指派的運算式必須是數位，或者必須可轉換成數位。

## <a name="assigning-values"></a>指派值

變數稱為儲存值的記憶體空間。 您可以使用指派運算子，將值儲存在變數中 `=` 。 新的值可以取代變數的現有值，您也可以將新值附加至現有的值。

基本指派運算子是等號 `=` `(ASCII 61)` 。 例如，下列語句會將 PowerShell 值指派給 `$MyShell` 變數：

```powershell
$MyShell = "PowerShell"
```

當您在 PowerShell 中將值指派給變數時，如果變數不存在，就會建立變數。 例如，下列兩個指派語句中的第一個會建立 `$a` 變數，並將值6指派給 `$a` 。 第二個指派語句將值12指派給 `$a` 。 第一個語句會建立新的變數。 第二個語句只會變更它的值：

```powershell
$a = 6
$a = 12
```

除非您將變數轉換，否則 PowerShell 中的變數不會有特定的資料類型。
當變數僅包含一個物件時，變數會採用該物件的資料類型。 當變數包含物件的集合時，變數會有 System.object 資料類型。 因此，您可以將任何類型的物件指派給集合。 下列範例顯示您可以在不產生錯誤的情況下，將處理常式物件、服務物件、字串和整數新增至變數：

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

因為指派運算子的 `=` 優先順序比管線運算子低 `|` ，所以不需要括弧將命令管線的結果指派給變數。 例如，下列命令會排序電腦上的服務，然後將排序的服務指派給 `$a` 變數：

```powershell
$a = Get-Service | Sort-Object -Property name
```

您也可以將語句所建立的值指派給變數，如下列範例所示：

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

如果的值小於零，此範例會將零指派給 `$a` 變數 `$b` 。 `$b` `$a` 如果的值不小於零，則會將的值指派給 `$b` 。

### <a name="the-assignment-operator"></a>指派運算子

指派運算子會 `=` 將值指派給變數。 如果變數已經有值，指派運算子 `=` 就會取代值而不發出警告。

下列語句會將整數值6指派給 `$a` 變數：

```powershell
$a = 6
```

若要將字串值指派給變數，請用引號括住字串值，如下所示：

```powershell
$a = "baseball"
```

若要將陣列 (多個值) 指派給變數，請以逗號分隔值，如下所示：

```powershell
$a = "apple", "orange", "lemon", "grape"
```

若要將雜湊表指派給變數，請在 PowerShell 中使用標準雜湊表標記法。 輸入 `@` 後面接著索引鍵/值組（以分號分隔） `;` ，並以大括弧括住的加號 `{ }` 。 例如，若要將雜湊表指派給 `$a` 變數，請輸入：

```powershell
$a = @{one=1; two=2; three=3}
```

若要將十六進位值指派給變數，請在值的前面加上 `0x` 。
PowerShell 會將十六進位值 (0x10) 轉換為十進位值 (在此案例中為 16) ，並將該值指派給 `$a` 變數。 例如，若要將0x10 的值指派給 `$a` 變數，請輸入：

```powershell
$a = 0x10
```

若要將指數值指派給變數，請輸入根數位、字母 `e` 和表示10的倍數的數位。 例如，若要將值3.1415 指派給變數的1000乘冪 `$a` ，請輸入：

```powershell
$a = 3.1415e3
```

PowerShell 也可以將 kb `KB` 、mb `MB` 和 gb 轉換 `GB` 成位元組。 例如，若要將 10 kb 的值指派給 `$a` 變數，請輸入：

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a>依加法運算子的指派

指派 by 加法運算子會 `+=` 遞增變數的值，或將指定的值附加至現有的值。 動作取決於變數是否有數值或字串類型，以及變數是否包含單一值 (純量) 或 () 集合的多個值。

`+=`運算子結合兩個作業。 首先，它會新增，然後再指派。
因此，下列語句是相等的：

```powershell
$a += 2
$a = ($a + 2)
```

當變數包含單一數值時， `+=` 運算子會依據運算子右邊的數量遞增現有的值。 然後，運算子會將產生的值指派給變數。 下列範例顯示如何使用 `+=` 運算子來增加變數的值：

```powershell
$a = 4
$a += 2
$a
```

```
6
```

當變數的值是字串時，運算子右邊的值會附加至字串，如下所示：

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

當變數的值是陣列時，運算子會將 `+=` 運算子右邊的值附加到陣列。 除非透過轉換來明確地輸入陣列，否則您可以將任何類型的值附加至陣列，如下所示：

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

及

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

當變數的值是雜湊表時，運算子會將 `+=` 運算子右邊的值附加到雜湊表。 不過，因為唯一可以加入至雜湊表的類型是另一個雜湊表，所以所有其他指派都會失敗。

例如，下列命令會將雜湊表指派給 `$a` 變數。
然後，它會使用 `+=` 運算子將另一個雜湊表附加至現有的雜湊表，有效地將新的索引鍵/值組新增至現有的雜湊表。
此命令會成功，如下列輸出所示：

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

下列命令會嘗試將整數 "1" 附加至變數中的雜湊表 `$a` 。 此命令會失敗：

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a>由減法運算子指派

由減法運算子指派， `-=` 會依據運算子右邊指定的值來遞減變數的值。 這個運算子不能與字串變數一起使用，也不能用來移除集合中的元素。

`-=`運算子結合兩個作業。 首先，它會減去，然後再指派。 因此，下列語句是相等的：

```powershell
$a -= 2
$a = ($a - 2)
```

下列範例顯示如何使用 `-=` 運算子來減少變數的值：

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

您也可以使用 `-=` 指派運算子來減少數值陣列成員的值。 若要這樣做，請指定您想要變更之陣列元素的索引。 在下列範例中，陣列的第三個元素的值 (元素 2) 會減少1：

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

您無法使用 `-=` 運算子來刪除變數的值。 若要刪除指派給變數的所有值，請使用 [清除專案](xref:Microsoft.PowerShell.Management.Clear-Item) 或 [清除變數](xref:Microsoft.PowerShell.Utility.Clear-Variable) 的 Cmdlet，將或的值指派給 `$null` `""` 變數。

```powershell
$a = $null
```

若要刪除陣列中的特定值，請使用陣列標記法，將的值指派給 `$null` 特定的專案。 例如，下列語句會刪除陣列中的第二個值 (索引位置 1) ：

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

若要刪除變數，請使用 [移除變數](xref:Microsoft.PowerShell.Utility.Remove-Variable) Cmdlet。 當變數明確地轉換為特定的資料類型，而且您想要不具類型的變數時，這個方法很有用。 下列命令會刪除 `$a` 變數：

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a>依乘法運算子的指派

依乘法運算子的指派會將 `*=` 數值相乘，或附加變數之字串值的指定複本數目。

當變數包含單一數值時，該值會乘以運算子右邊的值。 例如，下列範例顯示如何使用 `*=` 運算子來乘以變數的值：

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

在此情況下， `*=` 運算子會合並兩個作業。 首先，它會相乘，然後再指派。 因此，下列語句是相等的：

```powershell
$a *= 2
$a = ($a * 2)
```

當變數包含字串值時，PowerShell 會將指定的字串數目附加至值，如下所示：

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

若要乘以陣列的元素，請使用索引來識別您想要相乘的元素。 例如，下列命令會將陣列中的第一個元素乘以2的索引位置 0)  (：

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a>依除法運算子的指派

依除法運算子指派的值 `/=` 會將數值除以運算子右邊所指定的值。 運算子不能與字串變數一起使用。

`/=`運算子結合兩個作業。 首先，它會分割，然後再指派。 因此，下列兩個語句是相等的：

```powershell
$a /= 2
$a = ($a / 2)
```

例如，下列命令會使用 `/=` 運算子來分割變數的值：

```powershell
$a = 8
$a /=2
$a
```

```
4
```

若要分割陣列的元素，請使用索引來識別您想要變更的元素。 例如，下列命令會將陣列中的第二個元素分割 (索引位置 1) 除以2：

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a>依模數運算子的指派

依模數運算子指派會將 `%=` 變數的值除以運算子右邊的值。 然後，運算子會將 `%=` (稱為模數) 的餘數指派給變數。 只有當變數包含單一數值時，您才能使用這個運算子。 當變數包含字串變數或陣列時，不能使用這個運算子。

`%=`運算子結合兩個作業。 首先，它會分割並決定餘數，然後將餘數指派給變數。 因此，下列語句是相等的：

```powershell
$a %= 2
$a = ($a % 2)
```

下列範例顯示如何使用 `%=` 運算子來儲存商的模數：

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a>遞增和遞減運算子

遞增運算子 `++` 會將變數的值增加1。 當您在簡單的語句中使用遞增運算子時，不會傳回任何值。 若要查看結果，請顯示變數的值，如下所示：

```powershell
$a = 7
++$a
$a
```

```
8
```

若要強制傳回值，請以括弧括住變數和運算子，如下所示：

```powershell
$a = 7
(++$a)
```

```
8
```

遞增運算子可放置在 (前置詞) 之前，或 (後置) 變數之後。 運算子的前置詞版本會在語句中使用變數的值之前遞增變數，如下所示：

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

運算子的後置版本會在語句中使用變數的值之後，遞增變數。 在下列範例中， `$c` 和 `$a` 變數有不同的值，因為此值會在 `$c` 變更之前指派給 `$a` ：

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

遞減運算子會將 `--` 變數的值減少1。 如同遞增運算子一樣，當您在簡單的語句中使用運算子時，不會傳回任何值。 使用括弧傳回值，如下所示：

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

運算子的前置詞版本會在語句中使用變數值之前遞減變數，如下所示：

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

運算子的後置版本會在語句中使用變數的值之後遞減變數。 在下列範例中， `$d` 和 `$a` 變數有不同的值，因為此值會在 `$d` 變更之前指派給 `$a` ：

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a>Microsoft .NET Framework 類型

根據預設，當變數只有一個值時，指派給變數的值會決定變數的資料類型。 例如，下列命令會建立一個變數，此變數的 "Integer" (system.string) 類型：

```powershell
$a = 6
```

若要尋找變數的 .NET Framework 類型，請使用 **GetType** 方法及其 **FullName** 屬性，如下所示。 請務必在 **GetType** 方法名稱後面加上括弧，即使方法呼叫沒有引數也一樣：

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

若要建立包含字串的變數，請將字串值指派給變數。 若要指出值為字串，請將它括在引號中，如下所示：

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

如果指派給變數的第一個值為字串，則 PowerShell 會將所有作業視為字串作業，並將新的值轉換成字串。
這會發生在下列範例中：

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

如果第一個值是整數，則 PowerShell 會將所有作業視為整數運算，並將新的值轉換成整數。 這會發生在下列範例中：

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

您可以將新的純量變數作為任何 .NET Framework 類型，方法是將類型名稱放在變數名稱或第一個指派值之前的括弧中。 當您轉換變數時，可以決定變數中可儲存的資料類型。 而且，您可以決定當您操作變數時，變數的行為。

例如，下列命令會將變數轉換成字串類型：

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

下列範例會轉換第一個值，而不是轉換變數：

```powershell
$a = [string]27
```

當您將變數轉換成特定型別時，常見的慣例是轉換變數，而不是值。 但是，如果不能將現有變數的值轉換成新的資料類型，就無法重新轉換其資料類型。 若要變更資料類型，您必須取代其值，如下所示：

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

此外，如果您在變數名稱之前加上資料類型，則該變數的類型會被鎖定，除非您指定其他資料類型來明確覆寫該類型。 如果您嘗試指派的值與現有的型別不相容，而且您未明確覆寫該型別，則 PowerShell 會顯示錯誤，如下列範例所示：

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

在 PowerShell 中，包含陣列中多個專案之變數的資料類型處理方式，與包含單一專案之變數的資料類型不同。 除非將資料類型明確指派給陣列變數，否則資料類型一律為 `System.Object []` 。 這是陣列專屬的資料類型。

有時候，您可以藉由指定另一種類型來覆寫預設型別。 例如，下列命令會將變數轉換成 `string []` 陣列類型：

```powershell
[string []] $a = "one", "two", "three"
```

PowerShell 變數可以是任何 .NET Framework 資料類型。 此外，您可以指派目前進程中可用的任何完整 .NET Framework 資料類型。 例如，下列命令會指定 `System.DateTime` 資料類型：

```powershell
[System.DateTime]$a = "5/31/2005"
```

系統會將符合資料類型的值指派給變數 `System.DateTime` 。 變數的值如下 `$a` 所示：

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a>指派多個變數

在 PowerShell 中，您可以使用單一命令將值指派給多個變數。 指派值的第一個專案會指派給第一個變數，第二個元素會指派給第二個變數、第三個元素到第三個變數，依此類推。 例如，下列命令會將值1指派給變數、將值2指派給變數 `$a` `$b` ，並將值3指派給 `$c` 變數：

```powershell
$a, $b, $c = 1, 2, 3
```

如果指派值包含的元素多於變數數目，則會將所有剩餘的值指派給最後一個變數。 例如，下列命令包含三個變數和五個值：

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

因此，PowerShell 會將值1指派給變數 `$a` ，並將值2指派 `$b` 給變數。 它會將值3、4和5指派給 `$c` 變數。
若要將變數中的值指派 `$c` 給其他三個變數，請使用下列格式：

```powershell
$d, $e, $f = $c
```

此命令會將值3指派給變數，將值4指派給變數 `$d` `$e` ，並將值5指派給 `$f` 變數。

如果指派值包含的元素數目少於變數，則結尾的所有變數都不會指派任何值。 例如，下列命令包含三個變數和兩個值：

```powershell
$a, $b, $c = 1, 2
```

因此，PowerShell 會將值1指派給變數 `$a` ，並將值2指派 `$b` 給變數。 它不會將任何值指派給 `$c` 變數。

您也可以藉由連結變數，將單一值指派給多個變數。 例如，下列命令會將 "3" 的值指派給所有四個變數：

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a>變數相關的 Cmdlet

除了使用指派作業來設定變數值以外，您也可以使用 [集合變數](xref:Microsoft.PowerShell.Utility.Set-Variable) Cmdlet。 例如，下列命令會使用將 `Set-Variable` 1、2、3的陣列指派給 `$a` 變數。

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a>另請參閱

[about_Arrays](about_Arrays.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Variables](about_Variables.md)

[Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
