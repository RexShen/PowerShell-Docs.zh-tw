---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: c45b234445a7bc2b54aefb080d2d3da65433d412
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201667"
---
# <span data-ttu-id="6a299-103">Get-Random</span><span class="sxs-lookup"><span data-stu-id="6a299-103">Get-Random</span></span>

## <span data-ttu-id="6a299-104">概要</span><span class="sxs-lookup"><span data-stu-id="6a299-104">SYNOPSIS</span></span>
<span data-ttu-id="6a299-105">取得一個隨機數字，或從集合隨機選擇物件。</span><span class="sxs-lookup"><span data-stu-id="6a299-105">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="6a299-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a299-106">SYNTAX</span></span>

### <span data-ttu-id="6a299-107">RandomNumberParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="6a299-107">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="6a299-108">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a299-108">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="6a299-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6a299-109">DESCRIPTION</span></span>

<span data-ttu-id="6a299-110">`Get-Random`Cmdlet 會取得隨機選取的數位。</span><span class="sxs-lookup"><span data-stu-id="6a299-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="6a299-111">如果您將物件集合提交到 `Get-Random` ，它會從集合中取得一或多個隨機選取的物件。</span><span class="sxs-lookup"><span data-stu-id="6a299-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="6a299-112">如果沒有參數或輸入， `Get-Random` 命令會傳回隨機選取的32位不帶正負號整數，介於 0 **Int32.MaxValue** (零) 和 int32.maxvalue (`0x7FFFFFFF` ， `2,147,483,647`) 。</span><span class="sxs-lookup"><span data-stu-id="6a299-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="6a299-113">您可以使用的參數 `Get-Random` 來指定種子數、最小值和最大值，以及從提交的集合中傳回的物件數目。</span><span class="sxs-lookup"><span data-stu-id="6a299-113">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, and the number of objects returned from a submitted collection.</span></span>

## <span data-ttu-id="6a299-114">範例</span><span class="sxs-lookup"><span data-stu-id="6a299-114">EXAMPLES</span></span>

### <span data-ttu-id="6a299-115">範例1：取得隨機整數</span><span class="sxs-lookup"><span data-stu-id="6a299-115">Example 1: Get a random integer</span></span>

<span data-ttu-id="6a299-116">此命令會取得介於 0 (零 **) 和 int32.maxvalue** 之間的隨機整數。</span><span class="sxs-lookup"><span data-stu-id="6a299-116">This command gets a random integer between 0 (zero) and **Int32.MaxValue** .</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="6a299-117">範例2：取得0到99之間的隨機整數</span><span class="sxs-lookup"><span data-stu-id="6a299-117">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="6a299-118">範例3：取得介於-100 和99之間的隨機整數</span><span class="sxs-lookup"><span data-stu-id="6a299-118">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="6a299-119">範例4：取得隨機浮點數</span><span class="sxs-lookup"><span data-stu-id="6a299-119">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="6a299-120">此命令會取得大於或等於 10.7 且小於 20.92 的隨機浮點數。</span><span class="sxs-lookup"><span data-stu-id="6a299-120">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="6a299-121">範例5：從陣列取得隨機整數</span><span class="sxs-lookup"><span data-stu-id="6a299-121">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="6a299-122">這個命令會從指定的陣列取得隨機選取的數字。</span><span class="sxs-lookup"><span data-stu-id="6a299-122">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="6a299-123">範例6：從陣列取得數個隨機整數</span><span class="sxs-lookup"><span data-stu-id="6a299-123">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="6a299-124">此命令會從陣列中以隨機順序取得三個隨機選取的數位。</span><span class="sxs-lookup"><span data-stu-id="6a299-124">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="6a299-125">範例7：隨機化整個集合</span><span class="sxs-lookup"><span data-stu-id="6a299-125">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="6a299-126">此命令會以隨機順序傳回整個集合。</span><span class="sxs-lookup"><span data-stu-id="6a299-126">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="6a299-127">**Count** 參數的值是 **整數的 int32.maxvalue 靜態屬性** 。</span><span class="sxs-lookup"><span data-stu-id="6a299-127">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="6a299-128">如果要以隨機順序傳回整個集合，請輸入任何會大於或等於集合中物件數目的數字。</span><span class="sxs-lookup"><span data-stu-id="6a299-128">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="6a299-129">範例8：取得隨機的非數值</span><span class="sxs-lookup"><span data-stu-id="6a299-129">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="6a299-130">此命令會從非數字集合中傳回隨機值。</span><span class="sxs-lookup"><span data-stu-id="6a299-130">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="6a299-131">範例9：使用 SetSeed 參數</span><span class="sxs-lookup"><span data-stu-id="6a299-131">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="6a299-132">此範例顯示使用 **SetSeed** 參數的效果。</span><span class="sxs-lookup"><span data-stu-id="6a299-132">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="6a299-133">因為 **SetSeed** 會產生非隨機的行為，所以通常只會用來重現結果，例如在偵錯工具或分析腳本時。</span><span class="sxs-lookup"><span data-stu-id="6a299-133">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### <span data-ttu-id="6a299-134">範例10：取得隨機檔案</span><span class="sxs-lookup"><span data-stu-id="6a299-134">Example 10: Get random files</span></span>

<span data-ttu-id="6a299-135">這些命令會從本機電腦的磁片磁碟機取得隨機選取的50檔案範例 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-135">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="6a299-136">範例11：擲出公平骰子</span><span class="sxs-lookup"><span data-stu-id="6a299-136">Example 11: Roll fair dice</span></span>

<span data-ttu-id="6a299-137">此範例會匯總一個公平的骰子1200次，並計算結果。</span><span class="sxs-lookup"><span data-stu-id="6a299-137">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="6a299-138">第一個命令會 `For-EachObject` `Get-Random` 從管道中的數位 (1-6) 重複呼叫。</span><span class="sxs-lookup"><span data-stu-id="6a299-138">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="6a299-139">結果會依據其值來分組 `Group-Object` ，並以具有的資料表格式化 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-139">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### <span data-ttu-id="6a299-140">範例12：使用 Count 參數</span><span class="sxs-lookup"><span data-stu-id="6a299-140">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="6a299-141">您現在可以使用 **Count** 參數，而不需要將物件輸送至 `Get-Random` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-141">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="6a299-142">下列範例會取得三個小於10的亂數字。</span><span class="sxs-lookup"><span data-stu-id="6a299-142">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="6a299-143">範例13：使用 InputObject 參數搭配空字串或 $null</span><span class="sxs-lookup"><span data-stu-id="6a299-143">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="6a299-144">在此範例中， **InputObject** 參數會指定包含空字串的陣列 (`''`) 和 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-144">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="6a299-145">`Get-Random` 會傳回 `a` 、空字串或 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-145">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="6a299-146">空的字串會顯示為空白行，並 `$null` 返回 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="6a299-146">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="6a299-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a299-147">PARAMETERS</span></span>

### <span data-ttu-id="6a299-148">-Count</span><span class="sxs-lookup"><span data-stu-id="6a299-148">-Count</span></span>

<span data-ttu-id="6a299-149">指定要傳回的隨機物件或數位數目。</span><span class="sxs-lookup"><span data-stu-id="6a299-149">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="6a299-150">預設值是 1。</span><span class="sxs-lookup"><span data-stu-id="6a299-150">The default is 1.</span></span>

<span data-ttu-id="6a299-151">搭配使用時 `InputObject` ，如果 **Count** 的值超過集合中的物件數目，就會 `Get-Random` 以隨機順序傳回所有物件。</span><span class="sxs-lookup"><span data-stu-id="6a299-151">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a299-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6a299-152">-InputObject</span></span>

<span data-ttu-id="6a299-153">指定物件的集合。</span><span class="sxs-lookup"><span data-stu-id="6a299-153">Specifies a collection of objects.</span></span> <span data-ttu-id="6a299-154">`Get-Random` 從集合中隨機選取的物件（依 **計數** 指定的數目）取得隨機選取的物件。</span><span class="sxs-lookup"><span data-stu-id="6a299-154">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count** .</span></span> <span data-ttu-id="6a299-155">輸入物件、包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="6a299-155">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="6a299-156">您也可以使用管線將物件的集合傳送至 `Get-Random` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-156">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="6a299-157">從 PowerShell 7 開始， **InputObject** 參數會接受可包含空字串或的陣列 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-157">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="6a299-158">陣列可以沿著管線或 **InputObject** 參數值來傳送。</span><span class="sxs-lookup"><span data-stu-id="6a299-158">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6a299-159">-Maximum</span><span class="sxs-lookup"><span data-stu-id="6a299-159">-Maximum</span></span>

<span data-ttu-id="6a299-160">指定隨機數字的最大值。</span><span class="sxs-lookup"><span data-stu-id="6a299-160">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="6a299-161">`Get-Random` 傳回小於 (不等於) 最大值的值。</span><span class="sxs-lookup"><span data-stu-id="6a299-161">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="6a299-162">輸入整數、雙精確度浮點數，或是可以轉換為整數或雙精確度的物件，例如 ( "100" ) 的數值字串。</span><span class="sxs-lookup"><span data-stu-id="6a299-162">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="6a299-163">**Maximum** 的值必須大於 (不等於) **Minimum** 的值。</span><span class="sxs-lookup"><span data-stu-id="6a299-163">The value of **Maximum** must be greater than (not equal to) the value of **Minimum** .</span></span> <span data-ttu-id="6a299-164">如果 **最大** 或 **最小** 值為浮點數，則會傳回 `Get-Random` 隨機選取的浮點數。</span><span class="sxs-lookup"><span data-stu-id="6a299-164">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="6a299-165">在64位電腦上，如果 **最小** 值是32位整數，則 **最大** 值的預設 **值為 int32.maxvalue。**</span><span class="sxs-lookup"><span data-stu-id="6a299-165">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue** .</span></span>

<span data-ttu-id="6a299-166">如果 **最小** 值是雙精度浮點數 () ， **最大** 值的預設值就是 **雙** 點。</span><span class="sxs-lookup"><span data-stu-id="6a299-166">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue** .</span></span> <span data-ttu-id="6a299-167">否則，預設 **值為 int32.maxvalue。**</span><span class="sxs-lookup"><span data-stu-id="6a299-167">Otherwise, the default value is **Int32.MaxValue** .</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a299-168">-Minimum</span><span class="sxs-lookup"><span data-stu-id="6a299-168">-Minimum</span></span>

<span data-ttu-id="6a299-169">指定隨機數字的最小值。</span><span class="sxs-lookup"><span data-stu-id="6a299-169">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="6a299-170">輸入整數、雙精確度浮點數，或是可以轉換為整數或雙精確度的物件，例如 ( "100" ) 的數值字串。</span><span class="sxs-lookup"><span data-stu-id="6a299-170">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="6a299-171">預設值是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="6a299-171">The default value is 0 (zero).</span></span>

<span data-ttu-id="6a299-172">**Minimum** 的值必須小於 (不等於) **Maximum** 的值。</span><span class="sxs-lookup"><span data-stu-id="6a299-172">The value of **Minimum** must be less than (not equal to) the value of **Maximum** .</span></span> <span data-ttu-id="6a299-173">如果 **最大** 或 **最小** 值為浮點數，則會傳回 `Get-Random` 隨機選取的浮點數。</span><span class="sxs-lookup"><span data-stu-id="6a299-173">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a299-174">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="6a299-174">-SetSeed</span></span>

<span data-ttu-id="6a299-175">指定隨機數字產生器的種子值。</span><span class="sxs-lookup"><span data-stu-id="6a299-175">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="6a299-176">這個種子值會用於目前的命令，以及 `Get-Random` 目前會話中所有後續的命令，直到您再次使用 **SetSeed** 或關閉會話為止。</span><span class="sxs-lookup"><span data-stu-id="6a299-176">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="6a299-177">您無法將種子重設為其預設值。</span><span class="sxs-lookup"><span data-stu-id="6a299-177">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="6a299-178">不需要 **SetSeed** 參數。</span><span class="sxs-lookup"><span data-stu-id="6a299-178">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="6a299-179">根據預設，會 `Get-Random` 使用 [RandomNumberGenerator ( # B1 ](/dotnet/api/system.security.cryptography.randomnumbergenerator) 方法來產生種子值。</span><span class="sxs-lookup"><span data-stu-id="6a299-179">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="6a299-180">因為 **SetSeed** 會產生非隨機的行為，所以通常只會在嘗試重現行為時使用，例如在偵錯工具或分析包含命令的腳本時 `Get-Random` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-180">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a299-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a299-181">CommonParameters</span></span>

<span data-ttu-id="6a299-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6a299-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a299-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6a299-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a299-184">輸入</span><span class="sxs-lookup"><span data-stu-id="6a299-184">INPUTS</span></span>

### <span data-ttu-id="6a299-185">System.Object</span><span class="sxs-lookup"><span data-stu-id="6a299-185">System.Object</span></span>

<span data-ttu-id="6a299-186">您可以透過管線傳送一個或多個物件。</span><span class="sxs-lookup"><span data-stu-id="6a299-186">You can pipe one or more objects.</span></span> <span data-ttu-id="6a299-187">`Get-Random` 從輸送的物件隨機選取值。</span><span class="sxs-lookup"><span data-stu-id="6a299-187">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="6a299-188">輸出</span><span class="sxs-lookup"><span data-stu-id="6a299-188">OUTPUTS</span></span>

### <span data-ttu-id="6a299-189">System.Int32、System.Int64、System.Double</span><span class="sxs-lookup"><span data-stu-id="6a299-189">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="6a299-190">`Get-Random` 傳回整數或浮點數，或從提交的集合中隨機選取的物件。</span><span class="sxs-lookup"><span data-stu-id="6a299-190">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="6a299-191">注意</span><span class="sxs-lookup"><span data-stu-id="6a299-191">NOTES</span></span>

<span data-ttu-id="6a299-192">`Get-Random` 根據會話開始時的系統時間時鐘，設定每個會話的預設種子。</span><span class="sxs-lookup"><span data-stu-id="6a299-192">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="6a299-193">`Get-Random` 不一定會傳回與輸入值相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6a299-193">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="6a299-194">下表顯示每個數值輸入類型的輸出類型。</span><span class="sxs-lookup"><span data-stu-id="6a299-194">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="6a299-195">輸入類型</span><span class="sxs-lookup"><span data-stu-id="6a299-195">Input Type</span></span> | <span data-ttu-id="6a299-196">輸出類型</span><span class="sxs-lookup"><span data-stu-id="6a299-196">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="6a299-197">SByte</span><span class="sxs-lookup"><span data-stu-id="6a299-197">SByte</span></span>    |   <span data-ttu-id="6a299-198">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-198">Double</span></span>    |
|    <span data-ttu-id="6a299-199">Byte</span><span class="sxs-lookup"><span data-stu-id="6a299-199">Byte</span></span>    |   <span data-ttu-id="6a299-200">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-200">Double</span></span>    |
|   <span data-ttu-id="6a299-201">Int16</span><span class="sxs-lookup"><span data-stu-id="6a299-201">Int16</span></span>    |   <span data-ttu-id="6a299-202">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-202">Double</span></span>    |
|   <span data-ttu-id="6a299-203">UInt16</span><span class="sxs-lookup"><span data-stu-id="6a299-203">UInt16</span></span>   |   <span data-ttu-id="6a299-204">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-204">Double</span></span>    |
|   <span data-ttu-id="6a299-205">Int32</span><span class="sxs-lookup"><span data-stu-id="6a299-205">Int32</span></span>    |    <span data-ttu-id="6a299-206">Int32</span><span class="sxs-lookup"><span data-stu-id="6a299-206">Int32</span></span>    |
|   <span data-ttu-id="6a299-207">UInt32</span><span class="sxs-lookup"><span data-stu-id="6a299-207">UInt32</span></span>   |   <span data-ttu-id="6a299-208">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-208">Double</span></span>    |
|   <span data-ttu-id="6a299-209">Int64</span><span class="sxs-lookup"><span data-stu-id="6a299-209">Int64</span></span>    |    <span data-ttu-id="6a299-210">Int64</span><span class="sxs-lookup"><span data-stu-id="6a299-210">Int64</span></span>    |
|   <span data-ttu-id="6a299-211">UInt64</span><span class="sxs-lookup"><span data-stu-id="6a299-211">UInt64</span></span>   |   <span data-ttu-id="6a299-212">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-212">Double</span></span>    |
|   <span data-ttu-id="6a299-213">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-213">Double</span></span>   |   <span data-ttu-id="6a299-214">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-214">Double</span></span>    |
|   <span data-ttu-id="6a299-215">Single</span><span class="sxs-lookup"><span data-stu-id="6a299-215">Single</span></span>   |   <span data-ttu-id="6a299-216">Double</span><span class="sxs-lookup"><span data-stu-id="6a299-216">Double</span></span>    |

<span data-ttu-id="6a299-217">從 Windows PowerShell 3.0 開始， `Get-Random` 支援64位的整數。</span><span class="sxs-lookup"><span data-stu-id="6a299-217">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="6a299-218">在 Windows PowerShell 2.0 中，所有值都會轉換 **為 system.string。**</span><span class="sxs-lookup"><span data-stu-id="6a299-218">In Windows PowerShell 2.0, all values are cast to **System.Int32** .</span></span>

<span data-ttu-id="6a299-219">從 PowerShell 7 開始， **RandomListItemParameterSet** 參數集中的 **InputObject** 參數會接受包含空字串或的陣列 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-219">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="6a299-220">在舊版 PowerShell 中，只有 **RandomNumberParameterSet** 參數集內的 **最大** 參數會接受空字串或 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="6a299-220">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="6a299-221">相關連結</span><span class="sxs-lookup"><span data-stu-id="6a299-221">RELATED LINKS</span></span>
