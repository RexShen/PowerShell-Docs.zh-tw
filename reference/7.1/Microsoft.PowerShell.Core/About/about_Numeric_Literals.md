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
# <a name="about-numeric-literals"></a><span data-ttu-id="648ca-103">關於數值常值</span><span class="sxs-lookup"><span data-stu-id="648ca-103">About numeric literals</span></span>

<span data-ttu-id="648ca-104">數值常值有兩種：整數和實數。</span><span class="sxs-lookup"><span data-stu-id="648ca-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="648ca-105">兩者都可以有類型和乘數尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="648ca-106">整數常值</span><span class="sxs-lookup"><span data-stu-id="648ca-106">Integer literals</span></span>

<span data-ttu-id="648ca-107">整數常值可以用十進位、十六進位或二進位標記法來撰寫。</span><span class="sxs-lookup"><span data-stu-id="648ca-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="648ca-108">十六進位常值的前面會加上 `0x` ，而且二進位常值會加上前置詞， `0b` 以區別它們與十進位數。</span><span class="sxs-lookup"><span data-stu-id="648ca-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="648ca-109">整數常值可以有型別尾碼和乘數尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="648ca-110">後置詞</span><span class="sxs-lookup"><span data-stu-id="648ca-110">Suffix</span></span> |            <span data-ttu-id="648ca-111">意義</span><span class="sxs-lookup"><span data-stu-id="648ca-111">Meaning</span></span>             |          <span data-ttu-id="648ca-112">注意</span><span class="sxs-lookup"><span data-stu-id="648ca-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="648ca-113">y</span><span class="sxs-lookup"><span data-stu-id="648ca-113">y</span></span>      | <span data-ttu-id="648ca-114">帶正負號的位元組資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-114">signed byte data type</span></span>          | <span data-ttu-id="648ca-115">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="648ca-116">uy</span><span class="sxs-lookup"><span data-stu-id="648ca-116">uy</span></span>     | <span data-ttu-id="648ca-117">不帶正負號的位元組資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-117">unsigned byte data type</span></span>        | <span data-ttu-id="648ca-118">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="648ca-119">s</span><span class="sxs-lookup"><span data-stu-id="648ca-119">s</span></span>      | <span data-ttu-id="648ca-120">short 資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-120">short data type</span></span>                | <span data-ttu-id="648ca-121">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="648ca-122">us</span><span class="sxs-lookup"><span data-stu-id="648ca-122">us</span></span>     | <span data-ttu-id="648ca-123">不帶正負號的 short 資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-123">unsigned short data type</span></span>       | <span data-ttu-id="648ca-124">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="648ca-125">l</span><span class="sxs-lookup"><span data-stu-id="648ca-125">l</span></span>      | <span data-ttu-id="648ca-126">long 資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-126">long data type</span></span>                 |                         |
| <span data-ttu-id="648ca-127">u</span><span class="sxs-lookup"><span data-stu-id="648ca-127">u</span></span>      | <span data-ttu-id="648ca-128">不帶正負號的 int 或 long 資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-128">unsigned int or long data type</span></span> | <span data-ttu-id="648ca-129">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="648ca-130">ul</span><span class="sxs-lookup"><span data-stu-id="648ca-130">ul</span></span>     | <span data-ttu-id="648ca-131">不帶正負號的 long 資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-131">unsigned long data type</span></span>        | <span data-ttu-id="648ca-132">已在 PowerShell 6.2 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="648ca-133">n</span><span class="sxs-lookup"><span data-stu-id="648ca-133">n</span></span>      | <span data-ttu-id="648ca-134">BigInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-134">BigInteger data type</span></span>           | <span data-ttu-id="648ca-135">已在 PowerShell 7.0 中新增</span><span class="sxs-lookup"><span data-stu-id="648ca-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="648ca-136">kb</span><span class="sxs-lookup"><span data-stu-id="648ca-136">kb</span></span>     | <span data-ttu-id="648ca-137">千位元組乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="648ca-138">mb</span><span class="sxs-lookup"><span data-stu-id="648ca-138">mb</span></span>     | <span data-ttu-id="648ca-139">mb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="648ca-140">G b</span><span class="sxs-lookup"><span data-stu-id="648ca-140">gb</span></span>     | <span data-ttu-id="648ca-141">gb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="648ca-142">結核病</span><span class="sxs-lookup"><span data-stu-id="648ca-142">tb</span></span>     | <span data-ttu-id="648ca-143">tb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="648ca-144">鉛</span><span class="sxs-lookup"><span data-stu-id="648ca-144">pb</span></span>     | <span data-ttu-id="648ca-145">pb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="648ca-146">整數常值的類型是由其值、類型尾碼和數位乘數尾碼來決定。</span><span class="sxs-lookup"><span data-stu-id="648ca-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="648ca-147">針對沒有類型尾碼的整數常值：</span><span class="sxs-lookup"><span data-stu-id="648ca-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="648ca-148">如果值可由類型表示 `[int]` ，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="648ca-149">否則，如果值可由類型表示 `[long]` ，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="648ca-150">否則，如果值可由類型表示 `[decimal]` ，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="648ca-151">否則，它會以類型表示 `[double]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="648ca-152">針對具有類型尾碼的整數常值：</span><span class="sxs-lookup"><span data-stu-id="648ca-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="648ca-153">如果類型後置詞為 `u` ，而且值可由類型表示， `[uint]` 則其型別為 `[uint]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="648ca-154">如果類型後置詞為 `u` ，而且值可由類型表示， `[ulong]` 則其型別為 `[ulong]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="648ca-155">如果其值可由指定的類型表示，則為其類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="648ca-156">否則，該常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="648ca-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="648ca-157">實際常值</span><span class="sxs-lookup"><span data-stu-id="648ca-157">Real literals</span></span>

<span data-ttu-id="648ca-158">實際常值只能以十進位標記法撰寫。</span><span class="sxs-lookup"><span data-stu-id="648ca-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="648ca-159">此標記法可包含使用指數部分之後，以小數點和科學記號標記法之後的小數值。</span><span class="sxs-lookup"><span data-stu-id="648ca-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="648ca-160">指數部分包含 ' e '，後面接著選擇性的正負號 (+/-) 和代表指數的數位。</span><span class="sxs-lookup"><span data-stu-id="648ca-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="648ca-161">例如，常值 `1e2` 等於數位值100。</span><span class="sxs-lookup"><span data-stu-id="648ca-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="648ca-162">實際常值可以有型別尾碼和乘數尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="648ca-163">後置詞</span><span class="sxs-lookup"><span data-stu-id="648ca-163">Suffix</span></span> |       <span data-ttu-id="648ca-164">意義</span><span class="sxs-lookup"><span data-stu-id="648ca-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="648ca-165">d</span><span class="sxs-lookup"><span data-stu-id="648ca-165">d</span></span>      | <span data-ttu-id="648ca-166">十進位資料類型</span><span class="sxs-lookup"><span data-stu-id="648ca-166">decimal data type</span></span>   |
| <span data-ttu-id="648ca-167">kb</span><span class="sxs-lookup"><span data-stu-id="648ca-167">kb</span></span>     | <span data-ttu-id="648ca-168">千位元組乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="648ca-169">mb</span><span class="sxs-lookup"><span data-stu-id="648ca-169">mb</span></span>     | <span data-ttu-id="648ca-170">mb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-170">megabyte multiplier</span></span> |
| <span data-ttu-id="648ca-171">G b</span><span class="sxs-lookup"><span data-stu-id="648ca-171">gb</span></span>     | <span data-ttu-id="648ca-172">gb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="648ca-173">結核病</span><span class="sxs-lookup"><span data-stu-id="648ca-173">tb</span></span>     | <span data-ttu-id="648ca-174">tb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-174">terabyte multiplier</span></span> |
| <span data-ttu-id="648ca-175">鉛</span><span class="sxs-lookup"><span data-stu-id="648ca-175">pb</span></span>     | <span data-ttu-id="648ca-176">pb 乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-176">petabyte multiplier</span></span> |

<span data-ttu-id="648ca-177">實際常值有兩種： double 和 decimal。</span><span class="sxs-lookup"><span data-stu-id="648ca-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="648ca-178">這些是以不存在或目前狀態來表示的十進位類型尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="648ca-179">PowerShell 不支援值的常值標記法 `[float]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="648ca-180">Double 實數常值具有類型 `[double]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="648ca-181">Decimal 實數常值具有類型 `[decimal]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="648ca-182">Decimal 實數常值小數部分的尾端零是很重要的。</span><span class="sxs-lookup"><span data-stu-id="648ca-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="648ca-183">如果實際常值中指數部分的位數值 `[double]` 小於支援的最小值，則該實數常值的值 `[double]` 為0。</span><span class="sxs-lookup"><span data-stu-id="648ca-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="648ca-184">如果實際常值中指數部分的位數值 `[decimal]` 小於支援的最小值，則常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="648ca-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="648ca-185">如果指數部分數位在或實數常值中的 `[double]` 值 `[decimal]` 大於支援的最大值，則常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="648ca-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="648ca-186">語法允許雙重實數常值具有長型別尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="648ca-187">PowerShell 會將此案例視為整數常值，其值會以類型表示 `[long]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="648ca-188">這項功能已保留，以便與舊版 PowerShell 回溯相容。</span><span class="sxs-lookup"><span data-stu-id="648ca-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="648ca-189">不過，程式設計人員不建議使用此表單的整數常值，因為它們可以輕鬆地遮蔽常值的實際值。</span><span class="sxs-lookup"><span data-stu-id="648ca-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="648ca-190">例如， `1.2L` 具有值1、 `1.2345e1L` 具有值12，而且 `1.2345e-5L` 值為0，則不會立即明顯。</span><span class="sxs-lookup"><span data-stu-id="648ca-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="648ca-191">數值乘數</span><span class="sxs-lookup"><span data-stu-id="648ca-191">Numeric multipliers</span></span>

<span data-ttu-id="648ca-192">為了方便起見，整數和實數常值可以包含數值乘數，這表示一組常用的2種常用電源。</span><span class="sxs-lookup"><span data-stu-id="648ca-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="648ca-193">您可以用任何大寫或小寫字母的組合來寫入數值乘數。</span><span class="sxs-lookup"><span data-stu-id="648ca-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="648ca-194">乘數尾碼可以與任何類型尾碼搭配使用，但必須存在於型別尾碼之後。</span><span class="sxs-lookup"><span data-stu-id="648ca-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="648ca-195">例如，常值的 `100gbL` 格式不正確，但常 `100Lgb` 值有效。</span><span class="sxs-lookup"><span data-stu-id="648ca-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="648ca-196">如果乘數所建立的值超過後綴所指定之數數值型別的可能值，則常值的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="648ca-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="648ca-197">例如，常值的 `1usgb` 格式不正確，因為該值大於尾碼所指定之類型所允許的值 `1gb` `[ushort]` `us` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="648ca-198">乘數範例</span><span class="sxs-lookup"><span data-stu-id="648ca-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="648ca-199">數數值型別加速器</span><span class="sxs-lookup"><span data-stu-id="648ca-199">Numeric type accelerators</span></span>

<span data-ttu-id="648ca-200">PowerShell 支援下列類型加速器：</span><span class="sxs-lookup"><span data-stu-id="648ca-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="648ca-201">加速器</span><span class="sxs-lookup"><span data-stu-id="648ca-201">Accelerator</span></span> |         <span data-ttu-id="648ca-202">注意</span><span class="sxs-lookup"><span data-stu-id="648ca-202">Note</span></span>         |           <span data-ttu-id="648ca-203">描述</span><span class="sxs-lookup"><span data-stu-id="648ca-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="648ca-204">Byte (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="648ca-205">已簽署的位元組 () </span><span class="sxs-lookup"><span data-stu-id="648ca-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="648ca-206">16位整數</span><span class="sxs-lookup"><span data-stu-id="648ca-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="648ca-207">的別名 `[int16]`</span><span class="sxs-lookup"><span data-stu-id="648ca-207">alias for `[int16]`</span></span>  | <span data-ttu-id="648ca-208">16位整數</span><span class="sxs-lookup"><span data-stu-id="648ca-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="648ca-209">16位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="648ca-210">的別名 `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="648ca-210">alias for `[uint16]`</span></span> | <span data-ttu-id="648ca-211">16位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="648ca-212">32 位元整數</span><span class="sxs-lookup"><span data-stu-id="648ca-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="648ca-213">的別名 `[int32]`</span><span class="sxs-lookup"><span data-stu-id="648ca-213">alias for `[int32]`</span></span>  | <span data-ttu-id="648ca-214">32 位元整數</span><span class="sxs-lookup"><span data-stu-id="648ca-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="648ca-215">32位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="648ca-216">的別名 `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="648ca-216">alias for `[uint32]`</span></span> | <span data-ttu-id="648ca-217">32位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="648ca-218">64 位元整數</span><span class="sxs-lookup"><span data-stu-id="648ca-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="648ca-219">的別名 `[int64]`</span><span class="sxs-lookup"><span data-stu-id="648ca-219">alias for `[int64]`</span></span>  | <span data-ttu-id="648ca-220">64 位元整數</span><span class="sxs-lookup"><span data-stu-id="648ca-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="648ca-221">64位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="648ca-222">的別名 `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="648ca-222">alias for `[uint64]`</span></span> | <span data-ttu-id="648ca-223">64位整數 (不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="648ca-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="648ca-224">請參閱 [BigInteger 結構][bigint]</span><span class="sxs-lookup"><span data-stu-id="648ca-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="648ca-225">單精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="648ca-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="648ca-226">的別名 `[single]`</span><span class="sxs-lookup"><span data-stu-id="648ca-226">alias for `[single]`</span></span> | <span data-ttu-id="648ca-227">單精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="648ca-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="648ca-228">雙精確度浮點數</span><span class="sxs-lookup"><span data-stu-id="648ca-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="648ca-229">128位浮點數</span><span class="sxs-lookup"><span data-stu-id="648ca-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="648ca-230">PowerShell 6.2 中新增了下列型別加速器： `[short]` 、 `[ushort]` 、 `[uint]` 、 `[ulong]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="648ca-231">範例</span><span class="sxs-lookup"><span data-stu-id="648ca-231">Examples</span></span>

<span data-ttu-id="648ca-232">下表包含數個數值常值的範例，並列出其類型和值：</span><span class="sxs-lookup"><span data-stu-id="648ca-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="648ca-233">數字</span><span class="sxs-lookup"><span data-stu-id="648ca-233">Number</span></span>    |    <span data-ttu-id="648ca-234">類型</span><span class="sxs-lookup"><span data-stu-id="648ca-234">Type</span></span>    |    <span data-ttu-id="648ca-235">值</span><span class="sxs-lookup"><span data-stu-id="648ca-235">Value</span></span>     |
| ----------: | ---------- | -----------: |
|         <span data-ttu-id="648ca-236">100</span><span class="sxs-lookup"><span data-stu-id="648ca-236">100</span></span> | <span data-ttu-id="648ca-237">Int32</span><span class="sxs-lookup"><span data-stu-id="648ca-237">Int32</span></span>      |          <span data-ttu-id="648ca-238">100</span><span class="sxs-lookup"><span data-stu-id="648ca-238">100</span></span> |
|        <span data-ttu-id="648ca-239">100u</span><span class="sxs-lookup"><span data-stu-id="648ca-239">100u</span></span> | <span data-ttu-id="648ca-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="648ca-240">UInt32</span></span>     |          <span data-ttu-id="648ca-241">100</span><span class="sxs-lookup"><span data-stu-id="648ca-241">100</span></span> |
|        <span data-ttu-id="648ca-242">100D</span><span class="sxs-lookup"><span data-stu-id="648ca-242">100D</span></span> | <span data-ttu-id="648ca-243">Decimal</span><span class="sxs-lookup"><span data-stu-id="648ca-243">Decimal</span></span>    |          <span data-ttu-id="648ca-244">100</span><span class="sxs-lookup"><span data-stu-id="648ca-244">100</span></span> |
|        <span data-ttu-id="648ca-245">100l</span><span class="sxs-lookup"><span data-stu-id="648ca-245">100l</span></span> | <span data-ttu-id="648ca-246">Int64</span><span class="sxs-lookup"><span data-stu-id="648ca-246">Int64</span></span>      |          <span data-ttu-id="648ca-247">100</span><span class="sxs-lookup"><span data-stu-id="648ca-247">100</span></span> |
|       <span data-ttu-id="648ca-248">100uL</span><span class="sxs-lookup"><span data-stu-id="648ca-248">100uL</span></span> | <span data-ttu-id="648ca-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="648ca-249">UInt64</span></span>     |          <span data-ttu-id="648ca-250">100</span><span class="sxs-lookup"><span data-stu-id="648ca-250">100</span></span> |
|       <span data-ttu-id="648ca-251">100us</span><span class="sxs-lookup"><span data-stu-id="648ca-251">100us</span></span> | <span data-ttu-id="648ca-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="648ca-252">UInt16</span></span>     |          <span data-ttu-id="648ca-253">100</span><span class="sxs-lookup"><span data-stu-id="648ca-253">100</span></span> |
|       <span data-ttu-id="648ca-254">100uy</span><span class="sxs-lookup"><span data-stu-id="648ca-254">100uy</span></span> | <span data-ttu-id="648ca-255">Byte</span><span class="sxs-lookup"><span data-stu-id="648ca-255">Byte</span></span>       |          <span data-ttu-id="648ca-256">100</span><span class="sxs-lookup"><span data-stu-id="648ca-256">100</span></span> |
|        <span data-ttu-id="648ca-257">100y</span><span class="sxs-lookup"><span data-stu-id="648ca-257">100y</span></span> | <span data-ttu-id="648ca-258">SByte</span><span class="sxs-lookup"><span data-stu-id="648ca-258">SByte</span></span>      |          <span data-ttu-id="648ca-259">100</span><span class="sxs-lookup"><span data-stu-id="648ca-259">100</span></span> |
|         <span data-ttu-id="648ca-260">1e2</span><span class="sxs-lookup"><span data-stu-id="648ca-260">1e2</span></span> | <span data-ttu-id="648ca-261">Double</span><span class="sxs-lookup"><span data-stu-id="648ca-261">Double</span></span>     |          <span data-ttu-id="648ca-262">100</span><span class="sxs-lookup"><span data-stu-id="648ca-262">100</span></span> |
|        <span data-ttu-id="648ca-263">1. e2</span><span class="sxs-lookup"><span data-stu-id="648ca-263">1.e2</span></span> | <span data-ttu-id="648ca-264">Double</span><span class="sxs-lookup"><span data-stu-id="648ca-264">Double</span></span>     |          <span data-ttu-id="648ca-265">100</span><span class="sxs-lookup"><span data-stu-id="648ca-265">100</span></span> |
|       <span data-ttu-id="648ca-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="648ca-266">0x1e2</span></span> | <span data-ttu-id="648ca-267">Int32</span><span class="sxs-lookup"><span data-stu-id="648ca-267">Int32</span></span>      |          <span data-ttu-id="648ca-268">482</span><span class="sxs-lookup"><span data-stu-id="648ca-268">482</span></span> |
|      <span data-ttu-id="648ca-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="648ca-269">0x1e2L</span></span> | <span data-ttu-id="648ca-270">Int64</span><span class="sxs-lookup"><span data-stu-id="648ca-270">Int64</span></span>      |          <span data-ttu-id="648ca-271">482</span><span class="sxs-lookup"><span data-stu-id="648ca-271">482</span></span> |
|      <span data-ttu-id="648ca-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="648ca-272">0x1e2D</span></span> | <span data-ttu-id="648ca-273">Int32</span><span class="sxs-lookup"><span data-stu-id="648ca-273">Int32</span></span>      |         <span data-ttu-id="648ca-274">7725</span><span class="sxs-lookup"><span data-stu-id="648ca-274">7725</span></span> |
|        <span data-ttu-id="648ca-275">482D</span><span class="sxs-lookup"><span data-stu-id="648ca-275">482D</span></span> | <span data-ttu-id="648ca-276">Decimal</span><span class="sxs-lookup"><span data-stu-id="648ca-276">Decimal</span></span>    |          <span data-ttu-id="648ca-277">482</span><span class="sxs-lookup"><span data-stu-id="648ca-277">482</span></span> |
|       <span data-ttu-id="648ca-278">482gb</span><span class="sxs-lookup"><span data-stu-id="648ca-278">482gb</span></span> | <span data-ttu-id="648ca-279">Int64</span><span class="sxs-lookup"><span data-stu-id="648ca-279">Int64</span></span>      | <span data-ttu-id="648ca-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="648ca-280">517543559168</span></span> |
|      <span data-ttu-id="648ca-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="648ca-281">482ngb</span></span> | <span data-ttu-id="648ca-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="648ca-282">BigInteger</span></span> | <span data-ttu-id="648ca-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="648ca-283">517543559168</span></span> |
|    <span data-ttu-id="648ca-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="648ca-284">0x1e2lgb</span></span> | <span data-ttu-id="648ca-285">Int64</span><span class="sxs-lookup"><span data-stu-id="648ca-285">Int64</span></span>      | <span data-ttu-id="648ca-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="648ca-286">517543559168</span></span> |
|   <span data-ttu-id="648ca-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="648ca-287">0b1011011</span></span> | <span data-ttu-id="648ca-288">Int32</span><span class="sxs-lookup"><span data-stu-id="648ca-288">Int32</span></span>      |           <span data-ttu-id="648ca-289">91</span><span class="sxs-lookup"><span data-stu-id="648ca-289">91</span></span> |
|     <span data-ttu-id="648ca-290">0xFFFFs</span><span class="sxs-lookup"><span data-stu-id="648ca-290">0xFFFFs</span></span> | <span data-ttu-id="648ca-291">Int16</span><span class="sxs-lookup"><span data-stu-id="648ca-291">Int16</span></span>      |           <span data-ttu-id="648ca-292">-1</span><span class="sxs-lookup"><span data-stu-id="648ca-292">-1</span></span> |
|  <span data-ttu-id="648ca-293">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="648ca-293">0xFFFFFFFF</span></span> | <span data-ttu-id="648ca-294">Int32</span><span class="sxs-lookup"><span data-stu-id="648ca-294">Int32</span></span>      |           <span data-ttu-id="648ca-295">-1</span><span class="sxs-lookup"><span data-stu-id="648ca-295">-1</span></span> |
| <span data-ttu-id="648ca-296">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="648ca-296">-0xFFFFFFFF</span></span> | <span data-ttu-id="648ca-297">Int32</span><span class="sxs-lookup"><span data-stu-id="648ca-297">Int32</span></span>      |            <span data-ttu-id="648ca-298">1</span><span class="sxs-lookup"><span data-stu-id="648ca-298">1</span></span> |
| <span data-ttu-id="648ca-299">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="648ca-299">0xFFFFFFFFu</span></span> | <span data-ttu-id="648ca-300">UInt32</span><span class="sxs-lookup"><span data-stu-id="648ca-300">UInt32</span></span>     |   <span data-ttu-id="648ca-301">4294967295</span><span class="sxs-lookup"><span data-stu-id="648ca-301">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="648ca-302">使用二進位或十六進位數位</span><span class="sxs-lookup"><span data-stu-id="648ca-302">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="648ca-303">如果有指定後置詞，則過於大型的二進位或十六進位常值可能會傳回 `[bigint]` ，而不會使剖析失敗 `n` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-303">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="648ca-304">但是，即使是範圍，仍會採用正負號位 `[decimal]` ，不過：</span><span class="sxs-lookup"><span data-stu-id="648ca-304">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="648ca-305">如果二進位字串是8位長的一部分，則會將最高位視為符號位。</span><span class="sxs-lookup"><span data-stu-id="648ca-305">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="648ca-306">如果十六進位字串（長度為8的倍數）具有第一個數位（8或以上），則會將數位視為負。</span><span class="sxs-lookup"><span data-stu-id="648ca-306">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="648ca-307">在二進位和十六進位常值上指定不帶正負號的尾碼會忽略正負號位。</span><span class="sxs-lookup"><span data-stu-id="648ca-307">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="648ca-308">例如，會 `0xFFFFFFFF` 傳回 `-1` ，但是會傳回 `0xFFFFFFFFu` `[uint]::MaxValue` 4294967295 的。</span><span class="sxs-lookup"><span data-stu-id="648ca-308">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="648ca-309">在 PowerShell 7.1 中，在十六進位常值上使用類型尾碼現在會傳回該類型的帶正負號值。</span><span class="sxs-lookup"><span data-stu-id="648ca-309">In PowerShell 7.1, using a type suffix on a hex literal now returns a signed value of that type.</span></span> <span data-ttu-id="648ca-310">例如，在 PowerShell 7.0 中，運算式 `0xFFFFs` 會傳回錯誤，因為正數值對類型而言太大 `[int16]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-310">For example, in PowerShell 7.0 the expression `0xFFFFs` returns an error because the positive value is too large for an `[int16]` type.</span></span>
<span data-ttu-id="648ca-311">PowerShell 7.1 `-1` 會將其解釋為 `[int16]` 類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-311">PowerShell 7.1 interprets this as `-1` that is an `[int16]` type.</span></span>

<span data-ttu-id="648ca-312">在常值前面加上 `0` 將會略過此值，並將其視為未簽署。</span><span class="sxs-lookup"><span data-stu-id="648ca-312">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="648ca-313">例如：`0b011111111`。</span><span class="sxs-lookup"><span data-stu-id="648ca-313">For example: `0b011111111`.</span></span> <span data-ttu-id="648ca-314">當使用範圍中的常值時，這是必要 `[bigint]` 的，因為 `u` 和 `n` 尾碼無法合併。</span><span class="sxs-lookup"><span data-stu-id="648ca-314">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="648ca-315">您也可以使用前置詞來否定二進位和十六進位常值 `-` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-315">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="648ca-316">這可能會導致正數，因為允許使用正負號位。</span><span class="sxs-lookup"><span data-stu-id="648ca-316">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="648ca-317">符號位接受 BigInteger 尾碼數位：</span><span class="sxs-lookup"><span data-stu-id="648ca-317">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="648ca-318">BigInteger 尾碼 hex 會將任何常值（長度為8個字元）的最高位視為符號位。</span><span class="sxs-lookup"><span data-stu-id="648ca-318">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="648ca-319">長度不包含 `0x` 前置詞或任何尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-319">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="648ca-320">BigInteger 尾碼二進位檔接受96和128字元的正負號位，以及之後每8個字元。</span><span class="sxs-lookup"><span data-stu-id="648ca-320">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="648ca-321">看起來像是數值常值的命令</span><span class="sxs-lookup"><span data-stu-id="648ca-321">Commands that look like numeric literals</span></span>

<span data-ttu-id="648ca-322">任何看起來像有效數值常值的命令都必須使用呼叫運算子 () 來執行 `&` ，否則會被視為數位。</span><span class="sxs-lookup"><span data-stu-id="648ca-322">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="648ca-323">格式不正確的常值具有類似的有效語法 `1usgb` 會導致下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="648ca-323">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="648ca-324">不過，使用無效語法的格式不正確的常值 `1gbus` 會被視為標準的字串，並可在可能呼叫命令的內容中解讀為有效的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="648ca-324">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="648ca-325">存取數值物件的屬性和方法</span><span class="sxs-lookup"><span data-stu-id="648ca-325">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="648ca-326">若要存取數值常值的成員，在某些情況下，您需要用括弧括住常值。</span><span class="sxs-lookup"><span data-stu-id="648ca-326">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="648ca-327">常值沒有小數點</span><span class="sxs-lookup"><span data-stu-id="648ca-327">The literal does not have a decimal point</span></span>
- <span data-ttu-id="648ca-328">常值在小數點後面沒有任何數位</span><span class="sxs-lookup"><span data-stu-id="648ca-328">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="648ca-329">常值沒有尾碼</span><span class="sxs-lookup"><span data-stu-id="648ca-329">The literal does not have a suffix</span></span>

<span data-ttu-id="648ca-330">例如，下列範例會失敗：</span><span class="sxs-lookup"><span data-stu-id="648ca-330">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="648ca-331">下列範例可運作：</span><span class="sxs-lookup"><span data-stu-id="648ca-331">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="648ca-332">前兩個範例的運作方式不會將常值括在括弧中，因為 PowerShell 剖析器可以判斷數值常值結束的位置，以及 **GetType** 方法的啟動位置。</span><span class="sxs-lookup"><span data-stu-id="648ca-332">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="648ca-333">PowerShell 如何剖析數值常值</span><span class="sxs-lookup"><span data-stu-id="648ca-333">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="648ca-334">PowerShell 7.0 變更了數值常值的剖析方式，以啟用新功能。</span><span class="sxs-lookup"><span data-stu-id="648ca-334">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="648ca-335">剖析真正的數值常值</span><span class="sxs-lookup"><span data-stu-id="648ca-335">Parsing real numeric literals</span></span>

<span data-ttu-id="648ca-336">如果常值包含小數點或電子標記法，則會將常值字串剖析為實數。</span><span class="sxs-lookup"><span data-stu-id="648ca-336">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="648ca-337">如果出現小數尾碼，則直接放入 `[decimal]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-337">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="648ca-338">否則，請剖析 as， `[Double]` 然後將乘數套用至值。</span><span class="sxs-lookup"><span data-stu-id="648ca-338">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="648ca-339">然後檢查類型尾碼，並嘗試轉換成適當的類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-339">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="648ca-340">如果字串沒有類型尾碼，則剖析為 `[Double]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-340">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="648ca-341">配對整數數值常值</span><span class="sxs-lookup"><span data-stu-id="648ca-341">Paring integer numeric literals</span></span>

<span data-ttu-id="648ca-342">您可以使用下列步驟來剖析整數類型常值：</span><span class="sxs-lookup"><span data-stu-id="648ca-342">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="648ca-343">判斷基數格式</span><span class="sxs-lookup"><span data-stu-id="648ca-343">Determine the radix format</span></span>
   - <span data-ttu-id="648ca-344">若為二進位格式，請將剖析為 `[BigInteger]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-344">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="648ca-345">若是十六進位格式，請 `[BigInteger]` 使用特殊 casies 來剖析，以在值位於或範圍內時保留原始行為 `[int]` `[long]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-345">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="648ca-346">如果二進位和十六進位都不是，則以一般方式剖析 `[BigInteger]` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-346">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="648ca-347">請在嘗試任何轉換之前套用乘數值，以確保可以適當地檢查類型界限，而不會發生溢位。</span><span class="sxs-lookup"><span data-stu-id="648ca-347">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="648ca-348">檢查類型尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-348">Check type suffixes.</span></span>
   - <span data-ttu-id="648ca-349">請檢查類型界限，並嘗試剖析成該類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-349">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="648ca-350">如果未使用任何尾碼，則此值會以下列順序進行系結檢查，導致第一個成功的測試判斷數位的類型。</span><span class="sxs-lookup"><span data-stu-id="648ca-350">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="648ca-351">`[decimal]` 僅 (base-10 常值) </span><span class="sxs-lookup"><span data-stu-id="648ca-351">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="648ca-352">`[double]` 僅 (base-10 常值) </span><span class="sxs-lookup"><span data-stu-id="648ca-352">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="648ca-353">如果值超出 `[long]` 十六進位和二進位數的範圍，則剖析會失敗。</span><span class="sxs-lookup"><span data-stu-id="648ca-353">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="648ca-354">如果值超出 `[double]` 基底10數位的範圍，則剖析會失敗。</span><span class="sxs-lookup"><span data-stu-id="648ca-354">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="648ca-355">您必須使用尾碼來明確寫入較高 `n` 的值，以將常值剖析為 `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="648ca-355">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="648ca-356">剖析大型值常值</span><span class="sxs-lookup"><span data-stu-id="648ca-356">Parsing large value literals</span></span>

<span data-ttu-id="648ca-357">先前，在轉換成任何其他類型之前，會將較高的整數值剖析為雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="648ca-357">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="648ca-358">這會導致較高範圍的有效位數遺失。</span><span class="sxs-lookup"><span data-stu-id="648ca-358">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="648ca-359">例如︰</span><span class="sxs-lookup"><span data-stu-id="648ca-359">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="648ca-360">若要避免這個問題，您必須以字串的形式寫入值，然後轉換它們：</span><span class="sxs-lookup"><span data-stu-id="648ca-360">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="648ca-361">在 PowerShell 7.0 中，您必須使用 `N` 尾碼。</span><span class="sxs-lookup"><span data-stu-id="648ca-361">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="648ca-362">此外 `[ulong]::MaxValue` ，和之間 `[decimal]::MaxValue` 的值應該使用小數尾碼來表示 `D` 精確度。</span><span class="sxs-lookup"><span data-stu-id="648ca-362">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="648ca-363">如果沒有尾碼，這些值就會 `[Double]` 剖析為使用實際剖析模式。</span><span class="sxs-lookup"><span data-stu-id="648ca-363">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
