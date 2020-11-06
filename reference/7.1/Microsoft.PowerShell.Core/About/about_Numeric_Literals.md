---
description: 整數和實數常值都可以有型別和乘數尾碼。
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於數值常值
ms.openlocfilehash: 19ed71c2571a6cd343adf622a8cf71d6e5589aff
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354978"
---
# <a name="about-numeric-literals"></a>關於數值常值

數值常值有兩種：整數和實數。 兩者都可以有類型和乘數尾碼。

## <a name="integer-literals"></a>整數常值

整數常值可以用十進位、十六進位或二進位標記法來撰寫。
十六進位常值的前面會加上 `0x` ，而且二進位常值會加上前置詞， `0b` 以區別它們與十進位數。

整數常值可以有型別尾碼和乘數尾碼。

| 後置詞 |            意義             |          注意           |
| ------ | ------------------------------ | ----------------------- |
| y      | 帶正負號的位元組資料類型          | 已在 PowerShell 6.2 中新增 |
| uy     | 不帶正負號的位元組資料類型        | 已在 PowerShell 6.2 中新增 |
| s      | short 資料類型                | 已在 PowerShell 6.2 中新增 |
| us     | 不帶正負號的 short 資料類型       | 已在 PowerShell 6.2 中新增 |
| l      | long 資料類型                 |                         |
| u      | 不帶正負號的 int 或 long 資料類型 | 已在 PowerShell 6.2 中新增 |
| ul     | 不帶正負號的 long 資料類型        | 已在 PowerShell 6.2 中新增 |
| n      | BigInteger 資料類型           | 已在 PowerShell 7.0 中新增 |
| kb     | 千位元組乘數            |                         |
| mb     | mb 乘數            |                         |
| G b     | gb 乘數            |                         |
| 結核病     | tb 乘數            |                         |
| 鉛     | pb 乘數            |                         |

整數常值的類型是由其值、類型尾碼和數位乘數尾碼來決定。

針對沒有類型尾碼的整數常值：

- 如果值可由類型表示 `[int]` ，則為其類型。
- 否則，如果值可由類型表示 `[long]` ，則為其類型。
- 否則，如果值可由類型表示 `[decimal]` ，則為其類型。
- 否則，它會以類型表示 `[double]` 。

針對具有類型尾碼的整數常值：

- 如果類型後置詞為 `u` ，而且值可由類型表示， `[uint]` 則其型別為 `[uint]` 。
- 如果類型後置詞為 `u` ，而且值可由類型表示， `[ulong]` 則其型別為 `[ulong]` 。
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

乘數尾碼可以與任何類型尾碼搭配使用，但必須存在於型別尾碼之後。 例如，常值的 `100gbL` 格式不正確，但常 `100Lgb` 值有效。

如果乘數所建立的值超過後綴所指定之數數值型別的可能值，則常值的格式不正確。 例如，常值的 `1usgb` 格式不正確，因為該值大於尾碼所指定之類型所允許的值 `1gb` `[ushort]` `us` 。

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

| 加速器 |         注意         |           描述            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | Byte (不帶正負號的)                   |
| `[sbyte]`   |                      | 已簽署的位元組 ()                     |
| `[Int16]`   |                      | 16位整數                   |
| `[short]`   | 的別名 `[int16]`  | 16位整數                   |
| `[UInt16]`  |                      | 16位整數 (不帶正負號的)         |
| `[ushort]`  | 的別名 `[uint16]` | 16位整數 (不帶正負號的)         |
| `[Int32]`   |                      | 32 位元整數                   |
| `[int]`     | 的別名 `[int32]`  | 32 位元整數                   |
| `[UInt32]`  |                      | 32位整數 (不帶正負號的)         |
| `[uint]`    | 的別名 `[uint32]` | 32位整數 (不帶正負號的)         |
| `[Int64]`   |                      | 64 位元整數                   |
| `[long]`    | 的別名 `[int64]`  | 64 位元整數                   |
| `[UInt64]`  |                      | 64位整數 (不帶正負號的)         |
| `[ulong]`   | 的別名 `[uint64]` | 64位整數 (不帶正負號的)         |
| `[bigint]`  |                      | 請參閱 [BigInteger 結構][bigint]  |
| `[single]`  |                      | 單精確度浮點數  |
| `[float]`   | 的別名 `[single]` | 單精確度浮點數  |
| `[double]`  |                      | 雙精確度浮點數  |
| `[decimal]` |                      | 128位浮點數           |

> [!NOTE]
> PowerShell 6.2 中新增了下列型別加速器： `[short]` 、 `[ushort]` 、 `[uint]` 、 `[ulong]` 。

## <a name="examples"></a>範例

下表包含數個數值常值的範例，並列出其類型和值：

|   數字    |    類型    |    值     |
| ----------: | ---------- | -----------: |
|         100 | Int32      |          100 |
|        100u | UInt32     |          100 |
|        100D | Decimal    |          100 |
|        100l | Int64      |          100 |
|       100uL | UInt64     |          100 |
|       100us | UInt16     |          100 |
|       100uy | Byte       |          100 |
|        100y | SByte      |          100 |
|         1e2 | Double     |          100 |
|        1. e2 | Double     |          100 |
|       0x1e2 | Int32      |          482 |
|      0x1e2L | Int64      |          482 |
|      0x1e2D | Int32      |         7725 |
|        482D | Decimal    |          482 |
|       482gb | Int64      | 517543559168 |
|      482ngb | BigInteger | 517543559168 |
|    0x1e2lgb | Int64      | 517543559168 |
|   0b1011011 | Int32      |           91 |
|     0xFFFFs | Int16      |           -1 |
|  0xFFFFFFFF | Int32      |           -1 |
| -0xFFFFFFFF | Int32      |            1 |
| 0xFFFFFFFFu | UInt32     |   4294967295 |

### <a name="working-with-binary-or-hexadecimal-numbers"></a>使用二進位或十六進位數位

如果有指定後置詞，則過於大型的二進位或十六進位常值可能會傳回 `[bigint]` ，而不會使剖析失敗 `n` 。 但是，即使是範圍，仍會採用正負號位 `[decimal]` ，不過：

- 如果二進位字串是8位長的一部分，則會將最高位視為符號位。
- 如果十六進位字串（長度為8的倍數）具有第一個數位（8或以上），則會將數位視為負。

在二進位和十六進位常值上指定不帶正負號的尾碼會忽略正負號位。 例如，會 `0xFFFFFFFF` 傳回 `-1` ，但是會傳回 `0xFFFFFFFFu` `[uint]::MaxValue` 4294967295 的。

在 PowerShell 7.1 中，在十六進位常值上使用類型尾碼現在會傳回該類型的帶正負號值。 例如，在 PowerShell 7.0 中，運算式 `0xFFFFs` 會傳回錯誤，因為正數值對類型而言太大 `[int16]` 。
PowerShell 7.1 `-1` 會將其解釋為 `[int16]` 類型。

在常值前面加上 `0` 將會略過此值，並將其視為未簽署。
例如：`0b011111111`。 當使用範圍中的常值時，這是必要 `[bigint]` 的，因為 `u` 和 `n` 尾碼無法合併。

您也可以使用前置詞來否定二進位和十六進位常值 `-` 。 這可能會導致正數，因為允許使用正負號位。

符號位接受 BigInteger 尾碼數位：

- BigInteger 尾碼 hex 會將任何常值（長度為8個字元）的最高位視為符號位。 長度不包含 `0x` 前置詞或任何尾碼。
- BigInteger 尾碼二進位檔接受96和128字元的正負號位，以及之後每8個字元。

### <a name="commands-that-look-like-numeric-literals"></a>看起來像是數值常值的命令

任何看起來像有效數值常值的命令都必須使用呼叫運算子 () 來執行 `&` ，否則會被視為數位。 格式不正確的常值具有類似的有效語法 `1usgb` 會導致下列錯誤：

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

不過，使用無效語法的格式不正確的常值 `1gbus` 會被視為標準的字串，並可在可能呼叫命令的內容中解讀為有效的命令名稱。

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
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

前兩個範例的運作方式不會將常值括在括弧中，因為 PowerShell 剖析器可以判斷數值常值結束的位置，以及 **GetType** 方法的啟動位置。

## <a name="how-powershell-parses-numeric-literals"></a>PowerShell 如何剖析數值常值

PowerShell 7.0 變更了數值常值的剖析方式，以啟用新功能。

### <a name="parsing-real-numeric-literals"></a>剖析真正的數值常值

如果常值包含小數點或電子標記法，則會將常值字串剖析為實數。

- 如果出現小數尾碼，則直接放入 `[decimal]` 。
- 否則，請剖析 as， `[Double]` 然後將乘數套用至值。 然後檢查類型尾碼，並嘗試轉換成適當的類型。
- 如果字串沒有類型尾碼，則剖析為 `[Double]` 。

### <a name="paring-integer-numeric-literals"></a>配對整數數值常值

您可以使用下列步驟來剖析整數類型常值：

1. 判斷基數格式
   - 若為二進位格式，請將剖析為 `[BigInteger]` 。
   - 若是十六進位格式，請 `[BigInteger]` 使用特殊 casies 來剖析，以在值位於或範圍內時保留原始行為 `[int]` `[long]` 。
   - 如果二進位和十六進位都不是，則以一般方式剖析 `[BigInteger]` 。
2. 請在嘗試任何轉換之前套用乘數值，以確保可以適當地檢查類型界限，而不會發生溢位。
3. 檢查類型尾碼。
   - 請檢查類型界限，並嘗試剖析成該類型。
   - 如果未使用任何尾碼，則此值會以下列順序進行系結檢查，導致第一個成功的測試判斷數位的類型。
     - `[int]`
     - `[long]`
     - `[decimal]` 僅 (base-10 常值) 
     - `[double]` 僅 (base-10 常值) 
   - 如果值超出 `[long]` 十六進位和二進位數的範圍，則剖析會失敗。
   - 如果值超出 `[double]` 基底10數位的範圍，則剖析會失敗。
   - 您必須使用尾碼來明確寫入較高 `n` 的值，以將常值剖析為 `BigInteger` 。

### <a name="parsing-large-value-literals"></a>剖析大型值常值

先前，在轉換成任何其他類型之前，會將較高的整數值剖析為雙精度浮點數。 這會導致較高範圍的有效位數遺失。 例如︰

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

若要避免這個問題，您必須以字串的形式寫入值，然後轉換它們：

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

在 PowerShell 7.0 中，您必須使用 `N` 尾碼。

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

此外 `[ulong]::MaxValue` ，和之間 `[decimal]::MaxValue` 的值應該使用小數尾碼來表示 `D` 精確度。 如果沒有尾碼，這些值就會 `[Double]` 剖析為使用實際剖析模式。

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
