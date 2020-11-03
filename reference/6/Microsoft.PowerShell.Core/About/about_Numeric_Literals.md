---
description: 整數和實數常值都可以有型別和乘數尾碼。
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於數值常值
ms.openlocfilehash: 62f00ae9f3643724808146134fd03b6f01c29bce
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208631"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="b7d15-103">關於數值常值</span><span class="sxs-lookup"><span data-stu-id="b7d15-103">About numeric literals</span></span>

<span data-ttu-id="b7d15-104">數值常值有兩種：整數和實數。</span><span class="sxs-lookup"><span data-stu-id="b7d15-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="b7d15-105">兩者都可以有類型和乘數尾碼。</span><span class="sxs-lookup"><span data-stu-id="b7d15-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="b7d15-106">整數常值</span><span class="sxs-lookup"><span data-stu-id="b7d15-106">Integer literals</span></span>

<span data-ttu-id="b7d15-107">整數常值可以用十進位或十六進位標記法來撰寫。</span><span class="sxs-lookup"><span data-stu-id="b7d15-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="b7d15-108">十六進位常值的前面會加上 `0x` ，以區別它們與十進位數。</span><span class="sxs-lookup"><span data-stu-id="b7d15-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="b7d15-109">整數常值可以有型別尾碼和乘數尾碼。</span><span class="sxs-lookup"><span data-stu-id="b7d15-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="b7d15-110">後置詞</span><span class="sxs-lookup"><span data-stu-id="b7d15-110">Suffix</span></span> |            <span data-ttu-id="b7d15-111">意義</span><span class="sxs-lookup"><span data-stu-id="b7d15-111">Meaning</span></span>             |          <span data-ttu-id="b7d15-112">注意</span><span class="sxs-lookup"><span data-stu-id="b7d15-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="b7d15-113">y</span><span class="sxs-lookup"><span data-stu-id="b7d15-113">y</span></span>      | <span data-ttu-id="b7d15-114">帶正負號的位元組資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-114">signed byte data type</span></span>          | <span data-ttu-id="b7d15-115">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="b7d15-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="b7d15-116">uy</span><span class="sxs-lookup"><span data-stu-id="b7d15-116">uy</span></span>     | <span data-ttu-id="b7d15-117">不帶正負號的位元組資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-117">unsigned byte data type</span></span>        | <span data-ttu-id="b7d15-118">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="b7d15-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="b7d15-119">s</span><span class="sxs-lookup"><span data-stu-id="b7d15-119">s</span></span>      | <span data-ttu-id="b7d15-120">short 資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-120">short data type</span></span>                | <span data-ttu-id="b7d15-121">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="b7d15-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="b7d15-122">us</span><span class="sxs-lookup"><span data-stu-id="b7d15-122">us</span></span>     | <span data-ttu-id="b7d15-123">不帶正負號的 short 資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-123">unsigned short data type</span></span>       | <span data-ttu-id="b7d15-124">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="b7d15-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="b7d15-125">l</span><span class="sxs-lookup"><span data-stu-id="b7d15-125">l</span></span>      | <span data-ttu-id="b7d15-126">long 資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-126">long data type</span></span>                 |                         |
| <span data-ttu-id="b7d15-127">u</span><span class="sxs-lookup"><span data-stu-id="b7d15-127">u</span></span>      | <span data-ttu-id="b7d15-128">不帶正負號的 int 或 long 資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-128">unsigned int or long data type</span></span> | <span data-ttu-id="b7d15-129">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="b7d15-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="b7d15-130">ul</span><span class="sxs-lookup"><span data-stu-id="b7d15-130">ul</span></span>     | <span data-ttu-id="b7d15-131">不帶正負號的 long 資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-131">unsigned long data type</span></span>        | <span data-ttu-id="b7d15-132">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="b7d15-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="b7d15-133">kb</span><span class="sxs-lookup"><span data-stu-id="b7d15-133">kb</span></span>     | <span data-ttu-id="b7d15-134">千位元組乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-134">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="b7d15-135">mb</span><span class="sxs-lookup"><span data-stu-id="b7d15-135">mb</span></span>     | <span data-ttu-id="b7d15-136">mb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-136">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="b7d15-137">G b</span><span class="sxs-lookup"><span data-stu-id="b7d15-137">gb</span></span>     | <span data-ttu-id="b7d15-138">gb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-138">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="b7d15-139">結核病</span><span class="sxs-lookup"><span data-stu-id="b7d15-139">tb</span></span>     | <span data-ttu-id="b7d15-140">tb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-140">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="b7d15-141">鉛</span><span class="sxs-lookup"><span data-stu-id="b7d15-141">pb</span></span>     | <span data-ttu-id="b7d15-142">pb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-142">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="b7d15-143">整數常值的類型是由其值、類型尾碼和數位乘數尾碼來決定。</span><span class="sxs-lookup"><span data-stu-id="b7d15-143">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="b7d15-144">針對沒有類型尾碼的整數常值：</span><span class="sxs-lookup"><span data-stu-id="b7d15-144">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="b7d15-145">如果值可由類型表示 `[int]` ，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="b7d15-145">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="b7d15-146">否則，如果值可由類型表示 `[long]` ，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="b7d15-146">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="b7d15-147">否則，如果值可由類型表示 `[decimal]` ，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="b7d15-147">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="b7d15-148">否則，它會以類型表示 `[double]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-148">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="b7d15-149">針對具有類型尾碼的整數常值：</span><span class="sxs-lookup"><span data-stu-id="b7d15-149">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="b7d15-150">如果類型後置詞為 `u` ，而且值可由類型表示， `[uint]` 則其型別為 `[uint]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-150">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="b7d15-151">如果類型後置詞為 `u` ，而且值可由類型表示， `[ulong]` 則其型別為 `[ulong]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-151">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="b7d15-152">如果其值可由指定的類型表示，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="b7d15-152">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="b7d15-153">否則，該常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="b7d15-153">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="b7d15-154">實際常值</span><span class="sxs-lookup"><span data-stu-id="b7d15-154">Real literals</span></span>

<span data-ttu-id="b7d15-155">實際常值只能以十進位標記法撰寫。</span><span class="sxs-lookup"><span data-stu-id="b7d15-155">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="b7d15-156">此標記法可包含使用指數部分之後，以小數點和科學記號標記法之後的小數值。</span><span class="sxs-lookup"><span data-stu-id="b7d15-156">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="b7d15-157">指數部分包含 ' e '，後面接著選擇性的正負號 (+/-) 和代表指數的數位。</span><span class="sxs-lookup"><span data-stu-id="b7d15-157">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="b7d15-158">例如，常值 `1e2` 等於數位值100。</span><span class="sxs-lookup"><span data-stu-id="b7d15-158">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="b7d15-159">實際常值可以有型別尾碼和乘數尾碼。</span><span class="sxs-lookup"><span data-stu-id="b7d15-159">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="b7d15-160">後置詞</span><span class="sxs-lookup"><span data-stu-id="b7d15-160">Suffix</span></span> |       <span data-ttu-id="b7d15-161">意義</span><span class="sxs-lookup"><span data-stu-id="b7d15-161">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="b7d15-162">d</span><span class="sxs-lookup"><span data-stu-id="b7d15-162">d</span></span>      | <span data-ttu-id="b7d15-163">十進位資料類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-163">decimal data type</span></span>   |
| <span data-ttu-id="b7d15-164">kb</span><span class="sxs-lookup"><span data-stu-id="b7d15-164">kb</span></span>     | <span data-ttu-id="b7d15-165">千位元組乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-165">kilobyte multiplier</span></span> |
| <span data-ttu-id="b7d15-166">mb</span><span class="sxs-lookup"><span data-stu-id="b7d15-166">mb</span></span>     | <span data-ttu-id="b7d15-167">mb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-167">megabyte multiplier</span></span> |
| <span data-ttu-id="b7d15-168">G b</span><span class="sxs-lookup"><span data-stu-id="b7d15-168">gb</span></span>     | <span data-ttu-id="b7d15-169">gb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-169">gigabyte multiplier</span></span> |
| <span data-ttu-id="b7d15-170">結核病</span><span class="sxs-lookup"><span data-stu-id="b7d15-170">tb</span></span>     | <span data-ttu-id="b7d15-171">tb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-171">terabyte multiplier</span></span> |
| <span data-ttu-id="b7d15-172">鉛</span><span class="sxs-lookup"><span data-stu-id="b7d15-172">pb</span></span>     | <span data-ttu-id="b7d15-173">pb 乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-173">petabyte multiplier</span></span> |

<span data-ttu-id="b7d15-174">實際常值有兩種： double 和 decimal。</span><span class="sxs-lookup"><span data-stu-id="b7d15-174">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="b7d15-175">這些是以不存在或目前狀態來表示的十進位類型尾碼。</span><span class="sxs-lookup"><span data-stu-id="b7d15-175">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="b7d15-176">PowerShell 不支援值的常值標記法 `[float]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-176">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="b7d15-177">Double 實數常值具有類型 `[double]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-177">A double real literal has type `[double]`.</span></span> <span data-ttu-id="b7d15-178">Decimal 實數常值具有類型 `[decimal]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-178">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="b7d15-179">Decimal 實數常值小數部分的尾端零是很重要的。</span><span class="sxs-lookup"><span data-stu-id="b7d15-179">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="b7d15-180">如果實際常值中指數部分的位數值 `[double]` 小於支援的最小值，則該實數常值的值 `[double]` 為0。</span><span class="sxs-lookup"><span data-stu-id="b7d15-180">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="b7d15-181">如果實際常值中指數部分的位數值 `[decimal]` 小於支援的最小值，則常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="b7d15-181">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="b7d15-182">如果指數部分數位在或實數常值中的 `[double]` 值 `[decimal]` 大於支援的最大值，則常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="b7d15-182">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="b7d15-183">語法允許雙重實數常值具有長型別尾碼。</span><span class="sxs-lookup"><span data-stu-id="b7d15-183">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="b7d15-184">PowerShell 會將此案例視為整數常值，其值會以類型表示 `[long]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-184">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="b7d15-185">這項功能已保留，以便與舊版 PowerShell 回溯相容。</span><span class="sxs-lookup"><span data-stu-id="b7d15-185">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="b7d15-186">不過，程式設計人員不建議使用此表單的整數常值，因為它們可以輕鬆地遮蔽常值的實際值。</span><span class="sxs-lookup"><span data-stu-id="b7d15-186">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="b7d15-187">例如， `1.2L` 具有值1、 `1.2345e1L` 具有值12，而且 `1.2345e-5L` 值為0，則不會立即明顯。</span><span class="sxs-lookup"><span data-stu-id="b7d15-187">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="b7d15-188">數值乘數</span><span class="sxs-lookup"><span data-stu-id="b7d15-188">Numeric multipliers</span></span>

<span data-ttu-id="b7d15-189">為了方便起見，整數和實數常值可以包含數值乘數，這表示一組常用的2種常用電源。</span><span class="sxs-lookup"><span data-stu-id="b7d15-189">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="b7d15-190">您可以用任何大寫或小寫字母的組合來寫入數值乘數。</span><span class="sxs-lookup"><span data-stu-id="b7d15-190">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="b7d15-191">乘數尾碼可以與 `u` 、 `ul` 和 `l` 類型尾碼搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b7d15-191">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="b7d15-192">乘數範例</span><span class="sxs-lookup"><span data-stu-id="b7d15-192">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="b7d15-193">數數值型別加速器</span><span class="sxs-lookup"><span data-stu-id="b7d15-193">Numeric type accelerators</span></span>

<span data-ttu-id="b7d15-194">PowerShell 支援下列類型加速器：</span><span class="sxs-lookup"><span data-stu-id="b7d15-194">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="b7d15-195">加速器</span><span class="sxs-lookup"><span data-stu-id="b7d15-195">Accelerator</span></span> |         <span data-ttu-id="b7d15-196">注意</span><span class="sxs-lookup"><span data-stu-id="b7d15-196">Note</span></span>         |           <span data-ttu-id="b7d15-197">Description</span><span class="sxs-lookup"><span data-stu-id="b7d15-197">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="b7d15-198">Byte (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-198">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="b7d15-199">已簽署的位元組 () </span><span class="sxs-lookup"><span data-stu-id="b7d15-199">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="b7d15-200">16位整數</span><span class="sxs-lookup"><span data-stu-id="b7d15-200">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="b7d15-201">的別名 `[int16]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-201">alias for `[int16]`</span></span>  | <span data-ttu-id="b7d15-202">16位整數</span><span class="sxs-lookup"><span data-stu-id="b7d15-202">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="b7d15-203">16位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-203">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="b7d15-204">的別名 `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-204">alias for `[uint16]`</span></span> | <span data-ttu-id="b7d15-205">16位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-205">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="b7d15-206">32 位元整數</span><span class="sxs-lookup"><span data-stu-id="b7d15-206">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="b7d15-207">的別名 `[int32]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-207">alias for `[int32]`</span></span>  | <span data-ttu-id="b7d15-208">32 位元整數</span><span class="sxs-lookup"><span data-stu-id="b7d15-208">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="b7d15-209">32位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-209">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="b7d15-210">的別名 `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-210">alias for `[uint32]`</span></span> | <span data-ttu-id="b7d15-211">32位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-211">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="b7d15-212">64 位元整數</span><span class="sxs-lookup"><span data-stu-id="b7d15-212">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="b7d15-213">的別名 `[int64]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-213">alias for `[int64]`</span></span>  | <span data-ttu-id="b7d15-214">64 位元整數</span><span class="sxs-lookup"><span data-stu-id="b7d15-214">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="b7d15-215">64位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-215">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="b7d15-216">的別名 `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-216">alias for `[uint64]`</span></span> | <span data-ttu-id="b7d15-217">64位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b7d15-217">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="b7d15-218">請參閱 [BigInteger 結構][bigint]</span><span class="sxs-lookup"><span data-stu-id="b7d15-218">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="b7d15-219">單精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="b7d15-219">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="b7d15-220">的別名 `[single]`</span><span class="sxs-lookup"><span data-stu-id="b7d15-220">alias for `[single]`</span></span> | <span data-ttu-id="b7d15-221">單精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="b7d15-221">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="b7d15-222">雙精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="b7d15-222">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="b7d15-223">128位浮點數</span><span class="sxs-lookup"><span data-stu-id="b7d15-223">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="b7d15-224">PowerShell 6.2 中新增了下列型別加速器： `[short]` 、 `[ushort]` 、 `[uint]` 、 `[ulong]` 。</span><span class="sxs-lookup"><span data-stu-id="b7d15-224">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="b7d15-225">使用其他數數值型別</span><span class="sxs-lookup"><span data-stu-id="b7d15-225">Working with other numeric types</span></span>

<span data-ttu-id="b7d15-226">若要使用任何其他數數值型別，您必須使用類型加速器，而不會有一些問題。</span><span class="sxs-lookup"><span data-stu-id="b7d15-226">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="b7d15-227">例如，高整數值在轉換成任何其他類型之前，一律會剖析為雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="b7d15-227">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="b7d15-228">此值會先剖析為雙精度浮點數，並在較高的範圍中遺失有效位數。</span><span class="sxs-lookup"><span data-stu-id="b7d15-228">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="b7d15-229">若要避免這個問題，請將值輸入為字串，然後將它們轉換：</span><span class="sxs-lookup"><span data-stu-id="b7d15-229">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="b7d15-230">範例</span><span class="sxs-lookup"><span data-stu-id="b7d15-230">Examples</span></span>

<span data-ttu-id="b7d15-231">下表包含數個數值常值的範例，並列出其類型和值：</span><span class="sxs-lookup"><span data-stu-id="b7d15-231">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="b7d15-232">數字</span><span class="sxs-lookup"><span data-stu-id="b7d15-232">Number</span></span>  |  <span data-ttu-id="b7d15-233">類型</span><span class="sxs-lookup"><span data-stu-id="b7d15-233">Type</span></span>   |    <span data-ttu-id="b7d15-234">值</span><span class="sxs-lookup"><span data-stu-id="b7d15-234">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="b7d15-235">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-235">100</span></span> | <span data-ttu-id="b7d15-236">Int32</span><span class="sxs-lookup"><span data-stu-id="b7d15-236">Int32</span></span>   |          <span data-ttu-id="b7d15-237">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-237">100</span></span> |
|     <span data-ttu-id="b7d15-238">100D</span><span class="sxs-lookup"><span data-stu-id="b7d15-238">100D</span></span> | <span data-ttu-id="b7d15-239">Decimal</span><span class="sxs-lookup"><span data-stu-id="b7d15-239">Decimal</span></span> |          <span data-ttu-id="b7d15-240">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-240">100</span></span> |
|     <span data-ttu-id="b7d15-241">100l</span><span class="sxs-lookup"><span data-stu-id="b7d15-241">100l</span></span> | <span data-ttu-id="b7d15-242">Int64</span><span class="sxs-lookup"><span data-stu-id="b7d15-242">Int64</span></span>   |          <span data-ttu-id="b7d15-243">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-243">100</span></span> |
|    <span data-ttu-id="b7d15-244">100uL</span><span class="sxs-lookup"><span data-stu-id="b7d15-244">100uL</span></span> | <span data-ttu-id="b7d15-245">UInt64</span><span class="sxs-lookup"><span data-stu-id="b7d15-245">UInt64</span></span>  |          <span data-ttu-id="b7d15-246">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-246">100</span></span> |
|    <span data-ttu-id="b7d15-247">100us</span><span class="sxs-lookup"><span data-stu-id="b7d15-247">100us</span></span> | <span data-ttu-id="b7d15-248">UInt16</span><span class="sxs-lookup"><span data-stu-id="b7d15-248">UInt16</span></span>  |          <span data-ttu-id="b7d15-249">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-249">100</span></span> |
|    <span data-ttu-id="b7d15-250">100uy</span><span class="sxs-lookup"><span data-stu-id="b7d15-250">100uy</span></span> | <span data-ttu-id="b7d15-251">Byte</span><span class="sxs-lookup"><span data-stu-id="b7d15-251">Byte</span></span>    |          <span data-ttu-id="b7d15-252">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-252">100</span></span> |
|     <span data-ttu-id="b7d15-253">100y</span><span class="sxs-lookup"><span data-stu-id="b7d15-253">100y</span></span> | <span data-ttu-id="b7d15-254">SByte</span><span class="sxs-lookup"><span data-stu-id="b7d15-254">SByte</span></span>   |          <span data-ttu-id="b7d15-255">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-255">100</span></span> |
|      <span data-ttu-id="b7d15-256">1e2</span><span class="sxs-lookup"><span data-stu-id="b7d15-256">1e2</span></span> | <span data-ttu-id="b7d15-257">Double</span><span class="sxs-lookup"><span data-stu-id="b7d15-257">Double</span></span>  |          <span data-ttu-id="b7d15-258">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-258">100</span></span> |
|     <span data-ttu-id="b7d15-259">1. e2</span><span class="sxs-lookup"><span data-stu-id="b7d15-259">1.e2</span></span> | <span data-ttu-id="b7d15-260">Double</span><span class="sxs-lookup"><span data-stu-id="b7d15-260">Double</span></span>  |          <span data-ttu-id="b7d15-261">100</span><span class="sxs-lookup"><span data-stu-id="b7d15-261">100</span></span> |
|    <span data-ttu-id="b7d15-262">0x1e2</span><span class="sxs-lookup"><span data-stu-id="b7d15-262">0x1e2</span></span> | <span data-ttu-id="b7d15-263">Int32</span><span class="sxs-lookup"><span data-stu-id="b7d15-263">Int32</span></span>   |          <span data-ttu-id="b7d15-264">482</span><span class="sxs-lookup"><span data-stu-id="b7d15-264">482</span></span> |
|   <span data-ttu-id="b7d15-265">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="b7d15-265">0x1e2L</span></span> | <span data-ttu-id="b7d15-266">Int64</span><span class="sxs-lookup"><span data-stu-id="b7d15-266">Int64</span></span>   |          <span data-ttu-id="b7d15-267">482</span><span class="sxs-lookup"><span data-stu-id="b7d15-267">482</span></span> |
|   <span data-ttu-id="b7d15-268">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="b7d15-268">0x1e2D</span></span> | <span data-ttu-id="b7d15-269">Int32</span><span class="sxs-lookup"><span data-stu-id="b7d15-269">Int32</span></span>   |         <span data-ttu-id="b7d15-270">7725</span><span class="sxs-lookup"><span data-stu-id="b7d15-270">7725</span></span> |
|     <span data-ttu-id="b7d15-271">482D</span><span class="sxs-lookup"><span data-stu-id="b7d15-271">482D</span></span> | <span data-ttu-id="b7d15-272">Decimal</span><span class="sxs-lookup"><span data-stu-id="b7d15-272">Decimal</span></span> |          <span data-ttu-id="b7d15-273">482</span><span class="sxs-lookup"><span data-stu-id="b7d15-273">482</span></span> |
|    <span data-ttu-id="b7d15-274">482gb</span><span class="sxs-lookup"><span data-stu-id="b7d15-274">482gb</span></span> | <span data-ttu-id="b7d15-275">Int64</span><span class="sxs-lookup"><span data-stu-id="b7d15-275">Int64</span></span>   | <span data-ttu-id="b7d15-276">517543559168</span><span class="sxs-lookup"><span data-stu-id="b7d15-276">517543559168</span></span> |
| <span data-ttu-id="b7d15-277">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="b7d15-277">0x1e2lgb</span></span> | <span data-ttu-id="b7d15-278">Int64</span><span class="sxs-lookup"><span data-stu-id="b7d15-278">Int64</span></span>   | <span data-ttu-id="b7d15-279">517543559168</span><span class="sxs-lookup"><span data-stu-id="b7d15-279">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="b7d15-280">看起來像是數值常值的命令</span><span class="sxs-lookup"><span data-stu-id="b7d15-280">Commands that look like numeric literals</span></span>

<span data-ttu-id="b7d15-281">任何看起來像數值常值的命令都必須使用呼叫運算子 () 來執行 `&` ，否則會被解釋為相關聯類型的數位。</span><span class="sxs-lookup"><span data-stu-id="b7d15-281">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="b7d15-282">存取數值物件的屬性和方法</span><span class="sxs-lookup"><span data-stu-id="b7d15-282">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="b7d15-283">若要存取數值常值的成員，在某些情況下，您需要用括弧括住常值。</span><span class="sxs-lookup"><span data-stu-id="b7d15-283">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="b7d15-284">常值沒有小數點</span><span class="sxs-lookup"><span data-stu-id="b7d15-284">The literal does not have a decimal point</span></span>
- <span data-ttu-id="b7d15-285">常值在小數點後面沒有任何數位</span><span class="sxs-lookup"><span data-stu-id="b7d15-285">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="b7d15-286">常值沒有尾碼</span><span class="sxs-lookup"><span data-stu-id="b7d15-286">The literal does not have a suffix</span></span>

<span data-ttu-id="b7d15-287">例如，下列範例會失敗：</span><span class="sxs-lookup"><span data-stu-id="b7d15-287">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="b7d15-288">下列範例可運作：</span><span class="sxs-lookup"><span data-stu-id="b7d15-288">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="b7d15-289">前兩個範例的運作方式不會將常值括在括弧中，因為 PowerShell 剖析器可以判斷數值常值結束的位置，以及 **GetType** 方法的啟動位置。</span><span class="sxs-lookup"><span data-stu-id="b7d15-289">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
