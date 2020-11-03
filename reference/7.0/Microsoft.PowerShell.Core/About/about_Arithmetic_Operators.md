---
description: 描述在 PowerShell 中執行算術的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 5c9118eaa166beffc9d7a24f77a730d637a36a00
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207500"
---
# <a name="about-arithmetic-operators"></a>關於算術運算子

## <a name="short-description"></a>簡短描述
描述在 PowerShell 中執行算術的運算子。

## <a name="long-description"></a>詳細描述

算術運算子會計算數位值。 您可以使用一或多個算術運算子來加入、減去、相乘和除以值，以及計算除法運算 (模數) 的餘數。

此外，加法運算子 (`+`) 和乘法運算子 (`*`) 也會在字串、陣列和雜湊表上運作。 加法運算子會串連輸入。 乘法運算子會傳回輸入的多個複本。 您甚至可以混搭算術語句中的物件類型。 用來評估語句的方法是由運算式中最左邊物件的型別所決定。

從 PowerShell 2.0 開始，所有算術運算子都可在64位的數位上運作。

從 PowerShell 3.0 開始， `-shr` 會加入 (右移) 和 `-shl` (左移) ，以支援 PowerShell 中的位運算。

PowerShell 支援下列算術運算子：

|運算子|描述                       |範例                      |
|--------|----------------------------------|-----------------------------|
| +      |新增整數;串連       |`6 + 2`                      |
|        |字串、陣列和雜湊表。 |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |從另一個值減去另一個值  |`6 - 2`                      |
|        |value                             |                             |
| -      |讓數位成為負數  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |數位或複製字串相乘  |`6 * 2`                      |
|        |和陣列指定的數位   |`@("!") * 4`                 |
|        |的次數。                         |`"!" * 3`                    |
| /      |兩個值相除。               |`6 / 2`                      |
| %      |模數-傳回其餘的|`7 % 2`                      |
|        |除法運算。             |                             |
|-寬線   |位元 AND                       |`5 -band 3`                  |
|-bnot   |位元 NOT                       |`-bnot 5`                    |
|-bor    |位元 OR                        |`5 -bor 0x03`                |
|-bxor   |位元 XOR                       |`5 -bxor 3`                  |
|-shl    |將位向左移位           |`102 -shl 2`                 |
|-shr    |將位向右移位          |`102 -shr 2`                 |

位運算子只適用于整數類型。

## <a name="operator-precedence"></a>運算子優先順序

PowerShell 會依下列連續處理算術運算子：

|優先順序|運算子          |描述                            |
|----------|------------------|---------------------------------------|
|1         | `()`             |括號                            |
|2         | `-`              |負數值或一元運算子|
|3         | `*`, `/`, `%`    |針對乘法和除法        |
|4         | `+`, `-`         |加法和減法           |
|5         | `-band`, `-bnot` |位運算的                 |
|5         | `-bor`, `-bxor`  |位運算的                 |
|5         | `-shr`, `-shl`   |位運算的                 |

PowerShell 會根據優先順序規則，從左至右處理運算式。 下列範例顯示優先順序規則的效果：

|運算式 |結果|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

PowerShell 評估運算式的順序可能與您所使用的其他程式設計和指令碼語言不同。 下列範例顯示覆雜的指派語句。

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

在此範例中， `$a++` 會先評估運算式 `$b[$a]` 。
評估 `$a++` 變更在 `$a` 語句中使用之後的值 `$c[$a++]` ，但在中使用它之前 `$b[$a]` 。 在 equals 中的變數不是， `$a` `$b[$a]` 因此語句會將 `1` `0` 值指派給 `$b[1]` ，而不是 `$b[0]` 。

上述程式碼相當於：

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a>除法和進位

當除法運算的商為整數時，PowerShell 會將值四捨五入為最接近的整數。 當值為時 `.5` ，會四捨五入為最接近的偶數整數。

下列範例顯示四捨五入至最接近的偶數整數的效果。

|運算式      |結果|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

請注意 **_5/2_ = 2.5** 如何舍入為 **2** 。 但是， **_7/2_ = 3.5** 會舍入為 **4** 。

您可以使用 `[Math]` 類別來取得不同的舍入行為。

|                          運算式                          | 結果 |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

如需詳細資訊，請參閱 [數學. Round](/dotnet/api/system.math.round) 方法。

## <a name="adding-and-multiplying-non-numeric-types"></a>加入和相乘非數數值型別

您可以加入數位、字串、陣列和雜湊表。 而且，您可以將數位、字串和陣列相乘。 不過，您不能將雜湊資料表相乘。

當您加入字串、陣列或雜湊表時，會串連這些元素。 當您串連集合（例如陣列或雜湊表）時，會建立新的物件，其中包含兩個集合中的物件。 如果您嘗試串連具有相同索引鍵的雜湊表，作業就會失敗。

例如，下列命令會建立兩個數組，然後新增它們：

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

您也可以在不同類型的物件上執行算數運算。
PowerShell 執行的作業取決於作業中最左邊物件的 Microsoft .NET Framework 類型。 PowerShell 會嘗試將作業中的所有物件轉換為第一個物件的 .NET Framework 類型。 如果成功轉換物件，它會執行適合第一個物件之 .NET Framework 類型的作業。 如果無法轉換任何物件，則作業會失敗。

下列範例示範加法和乘法運算子的用法;在包含不同物件類型的作業中。 假設 `$array = 1,2,3` ：

|運算式       |結果                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |`1`,`2`,`3`,`16`       |
|`$array + "file"`|`1`,`2`,`3`,`file`     |
|`$array * 2`     |`1`,`2`,`3`,`1`,`2`,`3`|
|`"file" * 3`     |`filefilefile`         |

因為用來評估語句的方法是由最左邊的物件所決定，所以 PowerShell 中的加法和乘法並未完全交換。 例如，不 `(a + b)` 一定會相等 `(b + a)` ，而且不 `(ab)` 一定會相等 `(ba)` 。

下列範例示範此原則：

|運算式   |結果                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |+ 16 + "file" '                                       |

雜湊表是稍微不同的案例。 您可以將雜湊表加入至另一個雜湊表，只要加入的雜湊表沒有重複的索引鍵。

下列範例示範如何將雜湊表新增至其他雜湊表。

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

下列範例會擲回錯誤，因為兩個雜湊表中的其中一個索引鍵重複。

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

此外，您可以將雜湊表加入至陣列;而且整個雜湊資料表都會變成陣列中的專案。

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

不過，您無法將任何其他類型加入至雜湊表。

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

雖然加法運算子非常有用，但請使用指派運算子將專案加入至雜湊資料表和陣列。 如需詳細資訊，請參閱 [about_assignment_operators](about_Assignment_Operators.md)。 下列範例會使用 `+=` 指派運算子將專案加入至陣列：

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a>輸入轉換以容納結果

PowerShell 會自動選取最能表達結果的 .NET Framework 數數值型別，而不會失去精確度。 例如：

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

如果作業的結果對該類型而言太大，結果的類型會加寬以容納結果，如下列範例所示：

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

結果的型別不一定會與其中一個運算元相同。 在下列範例中，負值無法轉換成不帶正負號的整數，而且不帶正負號的整數太大而無法轉換成 `Int32` ：

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

在此範例中， `Int64` 可以容納這兩種類型。

此 `System.Decimal` 類型為例外狀況。 如果任一個運算元具有 Decimal 類型，則結果會是 Decimal 類型。 如果結果對 Decimal 類型而言太大，則不會轉換成 Double。 相反地，會產生錯誤。

|運算式               |結果                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a>算術運算子和變數

您也可以搭配變數來使用算術運算子。 運算子會對變數的值採取動作。 下列範例示範如何使用算術運算子搭配變數：

| 運算式                                    |結果      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a>算術運算子和命令

一般而言，您會在具有數位、字串和陣列的運算式中使用算術運算子。 不過，您也可以搭配命令傳回的物件和這些物件的屬性來使用算術運算子。

下列範例示範如何使用運算式中的算術運算子搭配 PowerShell 命令：

```powershell
(get-date) + (new-timespan -day 1)
```

括弧運算子會依序強制評估 `get-date` Cmdlet 和 `new-timespan -day 1` Cmdlet 運算式的評估。 這兩個結果接著會使用 `+` 運算子來新增。

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

在上述運算式中，每個處理常式工作空間 (`$_.ws`) 會乘以， `2` 而結果會與比較， `50mb` 以查看它是否大於該值。

## <a name="bitwise-operators"></a>位元運算子

PowerShell 支援標準的位運算子，包括位 and (`-bAnd`) 、包含和排除的位 or 運算子 (`-bOr` 和 `-bXor`) ，以及位 NOT (`-bNot`) 。

從 PowerShell 2.0 開始，所有位運算子都會使用64位整數。

從 PowerShell 3.0 開始， `-shr` 引進了 (右移) 和 `-shl` (shift 左) ，以支援 PowerShell 中的位運算。

PowerShell 支援下列位運算子。

| 運算子 | 描述            | 運算是   | 結果 |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | 位元 AND            | `10 -band 3` | 2      |
| `-bor`   | 位 OR (內含)  | `10 -bor 3`  | 11     |
| `-bxor`  | 位或 (獨佔)  | `10 -bxor 3` | 9      |
| `-bnot`  | 位元 NOT            | `-bNot 10`   | -11    |
| `-shl`   | 左移             | `102 -shl 2` | 408    |
| `-shr`   | 向右移位            | `102 -shr 1` | 51     |

位運算子會對值的二進位格式執行動作。 例如，數位10的位結構是 00001010 (根據1個位元組) ，而數位3的位結構是00000011。 當您使用位運算子比較10到3時，會比較每個位元組中的個別位。

在位 AND 運算中，只有當兩個輸入位都是1時，才會將產生的位設定為1。

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

在位 OR (內含) 運算中，如果其中一個或兩個輸入位為1，則產生的位會設定為1。 只有當兩個輸入位都設定為0時，才會將產生的位設定為0。

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

在位或 (專有) 運算中，只有當一個輸入位為1時，才會將產生的位設定為1。

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

位 NOT 運算子是一元運算子，會產生值的二進位補數。 1位設定為0，而位0設定為1。

例如，0的二進位補數為-1、最大不帶正負號整數 (0xffffffff) ，而-1 的二進位補數為0。

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

在位左移位運算中，所有位都會移至左邊的 "n" 位置，其中 "n" 是右運算元的值。 在一個位置插入零。

當左運算元是整數 (32 位) 值時，右邊運算元的較低5個位會決定要移位的左運算元位數。

當左運算元是 Long (64 位) 值時，右邊運算元的較低6位會決定要移位的左運算元位數。

|運算式 |結果|二進位結果|
|-----------|------|-------------|
|`21 -shl 0`|21    |0001 0101    |
|`21 -shl 1`|42    |0010 1010    |
|`21 -shl 2`|84    |0101 0100    |

在位右移作業中，所有位都會移至右邊的 "n" 位置，其中 "n" 是由右運算元所指定。 右移運算子 (-shr) 將正值或不帶正負號的值向右移動時，在最左邊的位置插入零。

當左運算元是整數 (32 位) 值時，右邊運算元的較低5個位會決定要移位的左運算元位數。

當左運算元是 Long (64 位) 值時，右邊運算元的較低6位會決定要移位的左運算元位數。

|運算式              |結果      |Binary     |Hex         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | 21         | 0001 0101 | 0x15       |
|`21 -shr 1`             | 10         | 0000 1010 | 0x0A       |
|`21 -shr 2`             | 5          | 0000 0101 | 0x05       |
|`21 -shr 31`            | 0          | 0000 0000 | 0x00       |
|`21 -shr 32`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 64`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 65`            | 10         | 0000 1010 | 0x0A       |
|`21 -shr 66`            | 5          | 0000 0101 | 0x05       |
|`[int]::MaxValue -shr 1`| 1073741823 |           | 0x3FFFFFFF |
|`[int]::MinValue -shr 1`| -1073741824|           | 0xC0000000 |
|`-1 -shr 1`             | -1         |           | 0xFFFFFFFF |

## <a name="see-also"></a>另請參閱

- [about_arrays](about_Arrays.md)
- [about_assignment_operators](about_Assignment_Operators.md)
- [about_comparison_operators](about_Comparison_Operators.md)
- [about_hash_tables](about_Hash_Tables.md)
- [about_operators](about_Operators.md)
- [about_variables](about_Variables.md)
- [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date)
- [New-TimeSpan](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
