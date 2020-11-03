---
description: 整數和實數常值都可以有型別和乘數尾碼。
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於數值常值
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208767"
---
# <a name="about-numeric-literals"></a>關於數值常值

數值常值有兩種：整數和實數。 兩者都可以有類型和乘數尾碼。

## <a name="integer-literals"></a>整數常值

整數常值可以用十進位或十六進位標記法來撰寫。 十六進位常值的前面會加上 `0x` ，以區別它們與十進位數。

整數常值可以有型別尾碼和乘數尾碼。

| 後置詞 |       意義       |
| ------ | ------------------- |
| l      | long 資料類型      |
| kb     | 千位元組乘數 |
| mb     | mb 乘數 |
| G b     | gb 乘數 |
| 結核病     | tb 乘數 |
| 鉛     | pb 乘數 |

整數常值的類型是由其值、類型尾碼和數位乘數尾碼來決定。

針對沒有類型尾碼的整數常值：

- 如果值可由類型表示 `[int]` ，則為其類型。
- 否則，如果值可由類型表示 `[long]` ，則為其類型。
- 否則，如果值可由類型表示 `[decimal]` ，則為其類型。
- 否則，它會以類型表示 `[double]` 。

針對具有類型尾碼的整數常值：

- 如果類型後置詞為 `u` ，而且值可由類型表示， `[int]` 則其型別為 `[int]` 。
- 如果類型後置詞為 `u` ，而且值可由類型表示， `[long]` 則其型別為 `[long]` 。
- 如果其值可由指定的類型表示，則為其類型。
- 否則，該常值的格式不正確。

## <a name="real-literals"></a>實際常值

實際常值只能以十進位標記法撰寫。 此標記法可包含使用指數部分之後，以小數點和科學記號標記法之後的小數值。

指數部分包含 ' e '，後面接著選擇性的正負號 (+/-) 和代表指數的數位。 例如，常值 `1e2` 等於數位值100。

實際常值可以有型別尾碼和乘數尾碼。

| 後置詞 |       意義       |
| ------ | ------------------- |
| d      | 十進位資料類型   |
| kb     | 千位元組乘數 |
| mb     | mb 乘數 |
| G b     | gb 乘數 |
| 結核病     | tb 乘數 |
| 鉛     | pb 乘數 |

實際常值有兩種： double 和 decimal。 這些是以不存在或目前狀態來表示的十進位類型尾碼。 PowerShell 不支援值的常值標記法 `[float]` 。 Double 實數常值具有類型 `[double]` 。 Decimal 實數常值具有類型 `[decimal]` 。
Decimal 實數常值小數部分的尾端零是很重要的。

如果實際常值中指數部分的位數值 `[double]` 小於支援的最小值，則該實數常值的值 `[double]` 為0。 如果實際常值中指數部分的位數值 `[decimal]` 小於支援的最小值，則常值的格式不正確。 如果指數部分數位在或實數常值中的 `[double]` 值 `[decimal]` 大於支援的最大值，則常值的格式不正確。

> [!NOTE]
> 語法允許雙重實數常值具有長型別尾碼。
> PowerShell 會將此案例視為整數常值，其值會以類型表示 `[long]` 。 這項功能已保留，以便與舊版 PowerShell 回溯相容。 不過，程式設計人員不建議使用此表單的整數常值，因為它們可以輕鬆地遮蔽常值的實際值。 例如， `1.2L` 具有值1、 `1.2345e1L` 具有值12，而且 `1.2345e-5L` 值為0，則不會立即明顯。

## <a name="numeric-multipliers"></a>數值乘數

為了方便起見，整數和實數常值可以包含數值乘數，這表示一組常用的2種常用電源。 您可以用任何大寫或小寫字母的組合來寫入數值乘數。

乘數尾碼可以與 `u` 、 `ul` 和 `l` 類型尾碼搭配使用。

### <a name="multiplier-examples"></a>乘數範例

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a>數數值型別加速器

PowerShell 支援下列類型加速器：

| 加速器 |         注意         |           Description            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | Byte (不帶正負號的)                   |
| `[sbyte]`   |                      | 已簽署的位元組 ()                     |
| `[Int16]`   |                      | 16位整數                   |
| `[UInt16]`  |                      | 16位整數 (不帶正負號的)         |
| `[Int32]`   |                      | 32 位元整數                   |
| `[int]`     | 的別名 `[int32]`  | 32 位元整數                   |
| `[UInt32]`  |                      | 32位整數 (不帶正負號的)         |
| `[Int64]`   |                      | 64 位元整數                   |
| `[long]`    | 的別名 `[int64]`  | 64 位元整數                   |
| `[UInt64]`  |                      | 64位整數 (不帶正負號的)         |
| `[bigint]`  |                      | 請參閱 [BigInteger 結構][bigint]  |
| `[single]`  |                      | 單精確度浮點數  |
| `[float]`   | 的別名 `[single]` | 單精確度浮點數  |
| `[double]`  |                      | 雙精確度浮點數  |
| `[decimal]` |                      | 128位浮點數           |

### <a name="working-with-other-numeric-types"></a>使用其他數數值型別

若要使用任何其他數數值型別，您必須使用類型加速器，而不會有一些問題。 例如，高整數值在轉換成任何其他類型之前，一律會剖析為雙精度浮點數。

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

此值會先剖析為雙精度浮點數，並在較高的範圍中遺失有效位數。
若要避免這個問題，請將值輸入為字串，然後將它們轉換：

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a>範例

下表包含數個數值常值的範例，並列出其類型和值：

|  數字  |  類型   |    值     |
| -------: | ------- | -----------: |
|      100 | Int32   |          100 |
|     100D | Decimal |          100 |
|     100l | Int64   |          100 |
|      1e2 | Double  |          100 |
|     1. e2 | Double  |          100 |
|    0x1e2 | Int32   |          482 |
|   0x1e2L | Int64   |          482 |
|   0x1e2D | Int32   |         7725 |
|     482D | Decimal |          482 |
|    482gb | Int64   | 517543559168 |
| 0x1e2lgb | Int64   | 517543559168 |

### <a name="commands-that-look-like-numeric-literals"></a>看起來像是數值常值的命令

任何看起來像數值常值的命令都必須使用呼叫運算子 () 來執行 `&` ，否則會被解釋為相關聯類型的數位。

### <a name="access-properties-and-methods-of-numeric-objects"></a>存取數值物件的屬性和方法

若要存取數值常值的成員，在某些情況下，您需要用括弧括住常值。

- 常值沒有小數點
- 常值在小數點後面沒有任何數位
- 常值沒有尾碼

例如，下列範例會失敗：

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

下列範例可運作：

```
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

前兩個範例的運作方式不會將常值括在括弧中，因為 PowerShell 剖析器可以判斷數值常值結束的位置，以及 **GetType** 方法的啟動位置。

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
