---
description: 描述如何使用運算子將值指派給變數。
keywords: powershell,cmdlet
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 06c68066b82bc4d8aec4d1a51c39e16fa52c2956
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207812"
---
# <a name="about-assignment-operators"></a><span data-ttu-id="bf8f2-104">關於指派運算子</span><span class="sxs-lookup"><span data-stu-id="bf8f2-104">About Assignment Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="bf8f2-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="bf8f2-105">Short description</span></span>
<span data-ttu-id="bf8f2-106">描述如何使用運算子將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-106">Describes how to use operators to assign values to variables.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf8f2-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="bf8f2-107">Long description</span></span>

<span data-ttu-id="bf8f2-108">指派運算子會將一個或多個值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-108">Assignment operators assign one or more values to a variable.</span></span> <span data-ttu-id="bf8f2-109">它們可以對指派之前的值執行數值運算。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-109">They can perform numeric operations on the values before the assignment.</span></span>

<span data-ttu-id="bf8f2-110">PowerShell 支援下列指派運算子。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-110">PowerShell supports the following assignment operators.</span></span>

|<span data-ttu-id="bf8f2-111">運算子</span><span class="sxs-lookup"><span data-stu-id="bf8f2-111">Operator</span></span>|<span data-ttu-id="bf8f2-112">描述</span><span class="sxs-lookup"><span data-stu-id="bf8f2-112">Description</span></span>                                                  |
|--------|-------------------------------------------------------------|
|=       |<span data-ttu-id="bf8f2-113">將變數的值設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-113">Sets the value of a variable to the specified value.</span></span>         |
|+=      |<span data-ttu-id="bf8f2-114">以指定的值增加變數的值，或</span><span class="sxs-lookup"><span data-stu-id="bf8f2-114">Increases the value of a variable by the specified value, or</span></span> |
|        |<span data-ttu-id="bf8f2-115">將指定的值附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-115">appends the specified value to the existing value.</span></span>           |
|-=      |<span data-ttu-id="bf8f2-116">將變數的值減少為指定的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-116">Decreases the value of a variable by the specified value.</span></span>    |
|*=      |<span data-ttu-id="bf8f2-117">將變數的值乘以指定的值，或</span><span class="sxs-lookup"><span data-stu-id="bf8f2-117">Multiplies the value of a variable by the specified value, or</span></span>|
|        |<span data-ttu-id="bf8f2-118">將指定的值附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-118">appends the specified value to the existing value.</span></span>           |
|/=      |<span data-ttu-id="bf8f2-119">將變數的值除以指定的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-119">Divides the value of a variable by the specified value.</span></span>      |
|%=      |<span data-ttu-id="bf8f2-120">將變數的值除以指定的值，然後</span><span class="sxs-lookup"><span data-stu-id="bf8f2-120">Divides the value of a variable by the specified value and</span></span>   |
|        |<span data-ttu-id="bf8f2-121">然後，將餘數 (模數) 指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-121">then assigns the remainder (modulus) to the variable.</span></span>        |
|++      |<span data-ttu-id="bf8f2-122">增加變數的值、可指派的屬性，或</span><span class="sxs-lookup"><span data-stu-id="bf8f2-122">Increases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="bf8f2-123">陣列元素，1。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-123">array element by 1.</span></span>                                          |
|--      |<span data-ttu-id="bf8f2-124">減少變數的值、可指派的屬性，或</span><span class="sxs-lookup"><span data-stu-id="bf8f2-124">Decreases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="bf8f2-125">陣列元素，1。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-125">array element by 1.</span></span>                                          |

## <a name="syntax"></a><span data-ttu-id="bf8f2-126">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf8f2-126">Syntax</span></span>

<span data-ttu-id="bf8f2-127">指派運算子的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-127">The syntax of the assignment operators is as follows:</span></span>

<span data-ttu-id="bf8f2-128">`<assignable-expression>` `<assignment-operator>` `<value>`</span><span class="sxs-lookup"><span data-stu-id="bf8f2-128">`<assignable-expression>` `<assignment-operator>` `<value>`</span></span>

<span data-ttu-id="bf8f2-129">可指派的運算式包括變數和屬性。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-129">Assignable expressions include variables and properties.</span></span> <span data-ttu-id="bf8f2-130">此值可以是單一值、值的陣列，或是命令、運算式或語句。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-130">The value can be a single value, an array of values, or a command, expression, or statement.</span></span>

<span data-ttu-id="bf8f2-131">遞增和遞減運算子是一元運算子。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-131">The increment and decrement operators are unary operators.</span></span> <span data-ttu-id="bf8f2-132">每個都有前置和後置版本。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-132">Each has prefix and postfix versions.</span></span>

`<assignable-expression><operator>`
`<operator><assignable-expression>`

<span data-ttu-id="bf8f2-133">可指派的運算式必須是數位，或者必須可轉換成數位。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-133">The assignable expression must be a number or it must be convertible to a number.</span></span>

## <a name="assigning-values"></a><span data-ttu-id="bf8f2-134">指派值</span><span class="sxs-lookup"><span data-stu-id="bf8f2-134">Assigning values</span></span>

<span data-ttu-id="bf8f2-135">變數稱為儲存值的記憶體空間。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-135">Variables are named memory spaces that store values.</span></span> <span data-ttu-id="bf8f2-136">您可以使用指派運算子，將值儲存在變數中 `=` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-136">You store the values in variables by using the assignment operator `=`.</span></span> <span data-ttu-id="bf8f2-137">新的值可以取代變數的現有值，您也可以將新值附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-137">The new value can replace the existing value of the variable, or you can append a new value to the existing value.</span></span>

<span data-ttu-id="bf8f2-138">基本指派運算子是等號 `=` `(ASCII 61)` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-138">The basic assignment operator is the equal sign `=` `(ASCII 61)`.</span></span> <span data-ttu-id="bf8f2-139">例如，下列語句會將 PowerShell 值指派給 `$MyShell` 變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-139">For example, the following statement assigns the value PowerShell to the `$MyShell` variable:</span></span>

```powershell
$MyShell = "PowerShell"
```

<span data-ttu-id="bf8f2-140">當您在 PowerShell 中將值指派給變數時，如果變數不存在，就會建立變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-140">When you assign a value to a variable in PowerShell, the variable is created if it did not already exist.</span></span> <span data-ttu-id="bf8f2-141">例如，下列兩個指派語句中的第一個會建立 `$a` 變數，並將值6指派給 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-141">For example, the first of the following two assignment statements creates the `$a` variable and assigns a value of 6 to `$a`.</span></span> <span data-ttu-id="bf8f2-142">第二個指派語句將值12指派給 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-142">The second assignment statement assigns a value of 12 to `$a`.</span></span> <span data-ttu-id="bf8f2-143">第一個語句會建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-143">The first statement creates a new variable.</span></span> <span data-ttu-id="bf8f2-144">第二個語句只會變更它的值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-144">The second statement changes only its value:</span></span>

```powershell
$a = 6
$a = 12
```

<span data-ttu-id="bf8f2-145">除非您將變數轉換，否則 PowerShell 中的變數不會有特定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-145">Variables in PowerShell do not have a specific data type unless you cast them.</span></span>
<span data-ttu-id="bf8f2-146">當變數僅包含一個物件時，變數會採用該物件的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-146">When a variable contains only one object, the variable takes the data type of that object.</span></span> <span data-ttu-id="bf8f2-147">當變數包含物件的集合時，變數會有 System.object 資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-147">When a variable contains a collection of objects, the variable has the System.Object data type.</span></span> <span data-ttu-id="bf8f2-148">因此，您可以將任何類型的物件指派給集合。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-148">Therefore, you can assign any type of object to the collection.</span></span> <span data-ttu-id="bf8f2-149">下列範例顯示您可以在不產生錯誤的情況下，將處理常式物件、服務物件、字串和整數新增至變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-149">The following example shows that you can add process objects, service objects, strings, and integers to a variable without generating an error:</span></span>

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

<span data-ttu-id="bf8f2-150">因為指派運算子的 `=` 優先順序比管線運算子低 `|` ，所以不需要括弧將命令管線的結果指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-150">Because the assignment operator `=` has a lower precedence than the pipeline operator `|`, parentheses are not required to assign the result of a command pipeline to a variable.</span></span> <span data-ttu-id="bf8f2-151">例如，下列命令會排序電腦上的服務，然後將排序的服務指派給 `$a` 變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-151">For example, the following command sorts the services on the computer and then assigns the sorted services to the `$a` variable:</span></span>

```powershell
$a = Get-Service | Sort-Object -Property name
```

<span data-ttu-id="bf8f2-152">您也可以將語句所建立的值指派給變數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-152">You can also assign the value created by a statement to a variable, as in the following example:</span></span>

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

<span data-ttu-id="bf8f2-153">如果的值小於零，此範例會將零指派給 `$a` 變數 `$b` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-153">This example assigns zero to the `$a` variable if the value of `$b` is less than zero.</span></span> <span data-ttu-id="bf8f2-154">`$b` `$a` 如果的值不小於零，則會將的值指派給 `$b` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-154">It assigns the value of `$b` to `$a` if the value of `$b` is not less than zero.</span></span>

### <a name="the-assignment-operator"></a><span data-ttu-id="bf8f2-155">指派運算子</span><span class="sxs-lookup"><span data-stu-id="bf8f2-155">The assignment operator</span></span>

<span data-ttu-id="bf8f2-156">指派運算子會 `=` 將值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-156">The assignment operator `=` assigns values to variables.</span></span> <span data-ttu-id="bf8f2-157">如果變數已經有值，指派運算子 `=` 就會取代值而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-157">If the variable already has a value, the assignment operator `=` replaces the value without warning.</span></span>

<span data-ttu-id="bf8f2-158">下列語句會將整數值6指派給 `$a` 變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-158">The following statement assigns the integer value 6 to the `$a` variable:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="bf8f2-159">若要將字串值指派給變數，請用引號括住字串值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-159">To assign a string value to a variable, enclose the string value in quotation marks, as follows:</span></span>

```powershell
$a = "baseball"
```

<span data-ttu-id="bf8f2-160">若要將陣列 (多個值) 指派給變數，請以逗號分隔值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-160">To assign an array (multiple values) to a variable, separate the values with commas, as follows:</span></span>

```powershell
$a = "apple", "orange", "lemon", "grape"
```

<span data-ttu-id="bf8f2-161">若要將雜湊表指派給變數，請在 PowerShell 中使用標準雜湊表標記法。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-161">To assign a hash table to a variable, use the standard hash table notation in PowerShell.</span></span> <span data-ttu-id="bf8f2-162">輸入 `@` 後面接著索引鍵/值組（以分號分隔） `;` ，並以大括弧括住的加號 `{ }` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-162">Type an at sign `@` followed by key/value pairs that are separated by semicolons `;` and enclosed in braces `{ }`.</span></span> <span data-ttu-id="bf8f2-163">例如，若要將雜湊表指派給 `$a` 變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-163">For example, to assign a hash table to the `$a` variable, type:</span></span>

```powershell
$a = @{one=1; two=2; three=3}
```

<span data-ttu-id="bf8f2-164">若要將十六進位值指派給變數，請在值的前面加上 `0x` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-164">To assign hexadecimal values to a variable, precede the value with `0x`.</span></span>
<span data-ttu-id="bf8f2-165">PowerShell 會將十六進位值 (0x10) 轉換為十進位值 (在此案例中為 16) ，並將該值指派給 `$a` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-165">PowerShell converts the hexadecimal value (0x10) to a decimal value (in this case, 16) and assigns that value to the `$a` variable.</span></span> <span data-ttu-id="bf8f2-166">例如，若要將0x10 的值指派給 `$a` 變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-166">For example, to assign a value of 0x10 to the `$a` variable, type:</span></span>

```powershell
$a = 0x10
```

<span data-ttu-id="bf8f2-167">若要將指數值指派給變數，請輸入根數位、字母 `e` 和表示10的倍數的數位。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-167">To assign an exponential value to a variable, type the root number, the letter `e`, and a number that represents a multiple of 10.</span></span> <span data-ttu-id="bf8f2-168">例如，若要將值3.1415 指派給變數的1000乘冪 `$a` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-168">For example, to assign a value of 3.1415 to the power of 1,000 to the `$a` variable, type:</span></span>

```powershell
$a = 3.1415e3
```

<span data-ttu-id="bf8f2-169">PowerShell 也可以將 kb `KB` 、mb `MB` 和 gb 轉換 `GB` 成位元組。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-169">PowerShell can also convert kilobytes `KB`, megabytes `MB`, and gigabytes `GB` into bytes.</span></span> <span data-ttu-id="bf8f2-170">例如，若要將 10 kb 的值指派給 `$a` 變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-170">For example, to assign a value of 10 kilobytes to the `$a` variable, type:</span></span>

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a><span data-ttu-id="bf8f2-171">依加法運算子的指派</span><span class="sxs-lookup"><span data-stu-id="bf8f2-171">The assignment by addition operator</span></span>

<span data-ttu-id="bf8f2-172">指派 by 加法運算子會 `+=` 遞增變數的值，或將指定的值附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-172">The assignment by addition operator `+=` either increments the value of a variable or appends the specified value to the existing value.</span></span> <span data-ttu-id="bf8f2-173">動作取決於變數是否有數值或字串類型，以及變數是否包含單一值 (純量) 或 () 集合的多個值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-173">The action depends on whether the variable has a numeric or string type and whether the variable contains a single value (a scalar) or multiple values (a collection).</span></span>

<span data-ttu-id="bf8f2-174">`+=`運算子結合兩個作業。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-174">The `+=` operator combines two operations.</span></span> <span data-ttu-id="bf8f2-175">首先，它會新增，然後再指派。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-175">First, it adds, and then it assigns.</span></span>
<span data-ttu-id="bf8f2-176">因此，下列語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-176">Therefore, the following statements are equivalent:</span></span>

```powershell
$a += 2
$a = ($a + 2)
```

<span data-ttu-id="bf8f2-177">當變數包含單一數值時， `+=` 運算子會依據運算子右邊的數量遞增現有的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-177">When the variable contains a single numeric value, the `+=` operator increments the existing value by the amount on the right side of the operator.</span></span> <span data-ttu-id="bf8f2-178">然後，運算子會將產生的值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-178">Then, the operator assigns the resulting value to the variable.</span></span> <span data-ttu-id="bf8f2-179">下列範例顯示如何使用 `+=` 運算子來增加變數的值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-179">The following example shows how to use the `+=` operator to increase the value of a variable:</span></span>

```powershell
$a = 4
$a += 2
$a
```

```
6
```

<span data-ttu-id="bf8f2-180">當變數的值是字串時，運算子右邊的值會附加至字串，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-180">When the value of the variable is a string, the value on the right side of the operator is appended to the string, as follows:</span></span>

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

<span data-ttu-id="bf8f2-181">當變數的值是陣列時，運算子會將 `+=` 運算子右邊的值附加到陣列。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-181">When the value of the variable is an array, the `+=` operator appends the values on the right side of the operator to the array.</span></span> <span data-ttu-id="bf8f2-182">除非透過轉換來明確地輸入陣列，否則您可以將任何類型的值附加至陣列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-182">Unless the array is explicitly typed by casting, you can append any type of value to the array, as follows:</span></span>

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

<span data-ttu-id="bf8f2-183">及</span><span class="sxs-lookup"><span data-stu-id="bf8f2-183">and</span></span>

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

<span data-ttu-id="bf8f2-184">當變數的值是雜湊表時，運算子會將 `+=` 運算子右邊的值附加到雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-184">When the value of a variable is a hash table, the `+=` operator appends the value on the right side of the operator to the hash table.</span></span> <span data-ttu-id="bf8f2-185">不過，因為唯一可以加入至雜湊表的類型是另一個雜湊表，所以所有其他指派都會失敗。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-185">However, because the only type that you can add to a hash table is another hash table, all other assignments fail.</span></span>

<span data-ttu-id="bf8f2-186">例如，下列命令會將雜湊表指派給 `$a` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-186">For example, the following command assigns a hash table to the `$a` variable.</span></span>
<span data-ttu-id="bf8f2-187">然後，它會使用 `+=` 運算子將另一個雜湊表附加至現有的雜湊表，有效地將新的索引鍵/值組新增至現有的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-187">Then, it uses the `+=` operator to append another hash table to the existing hash table, effectively adding a new key/value pair to the existing hash table.</span></span>
<span data-ttu-id="bf8f2-188">此命令會成功，如下列輸出所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-188">This command succeeds, as shown in the output:</span></span>

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

<span data-ttu-id="bf8f2-189">下列命令會嘗試將整數 "1" 附加至變數中的雜湊表 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-189">The following command attempts to append an integer "1" to the hash table in the `$a` variable.</span></span> <span data-ttu-id="bf8f2-190">此命令會失敗：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-190">This command fails:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a><span data-ttu-id="bf8f2-191">由減法運算子指派</span><span class="sxs-lookup"><span data-stu-id="bf8f2-191">The assignment by subtraction operator</span></span>

<span data-ttu-id="bf8f2-192">由減法運算子指派， `-=` 會依據運算子右邊指定的值來遞減變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-192">The assignment by subtraction operator `-=` decrements the value of a variable by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="bf8f2-193">這個運算子不能與字串變數一起使用，也不能用來移除集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-193">This operator cannot be used with string variables, and it cannot be used to remove an element from a collection.</span></span>

<span data-ttu-id="bf8f2-194">`-=`運算子結合兩個作業。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-194">The `-=` operator combines two operations.</span></span> <span data-ttu-id="bf8f2-195">首先，它會減去，然後再指派。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-195">First, it subtracts, and then it assigns.</span></span> <span data-ttu-id="bf8f2-196">因此，下列語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-196">Therefore, the following statements are equivalent:</span></span>

```powershell
$a -= 2
$a = ($a - 2)
```

<span data-ttu-id="bf8f2-197">下列範例顯示如何使用 `-=` 運算子來減少變數的值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-197">The following example shows how to use of the `-=` operator to decrease the value of a variable:</span></span>

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

<span data-ttu-id="bf8f2-198">您也可以使用 `-=` 指派運算子來減少數值陣列成員的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-198">You can also use the `-=` assignment operator to decrease the value of a member of a numeric array.</span></span> <span data-ttu-id="bf8f2-199">若要這樣做，請指定您想要變更之陣列元素的索引。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-199">To do this, specify the index of the array element that you want to change.</span></span> <span data-ttu-id="bf8f2-200">在下列範例中，陣列的第三個元素的值 (元素 2) 會減少1：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-200">In the following example, the value of the third element of an array (element 2) is decreased by 1:</span></span>

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

<span data-ttu-id="bf8f2-201">您無法使用 `-=` 運算子來刪除變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-201">You cannot use the `-=` operator to delete the values of a variable.</span></span> <span data-ttu-id="bf8f2-202">若要刪除指派給變數的所有值，請使用 [清除專案](xref:Microsoft.PowerShell.Management.Clear-Item) 或 [清除變數](xref:Microsoft.PowerShell.Utility.Clear-Variable) 的 Cmdlet，將或的值指派給 `$null` `""` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-202">To delete all the values that are assigned to a variable, use the [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) or [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlets to assign a value of `$null` or `""` to the variable.</span></span>

```powershell
$a = $null
```

<span data-ttu-id="bf8f2-203">若要刪除陣列中的特定值，請使用陣列標記法，將的值指派給 `$null` 特定的專案。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-203">To delete a particular value from an array, use array notation to assign a value of `$null` to the particular item.</span></span> <span data-ttu-id="bf8f2-204">例如，下列語句會刪除陣列中的第二個值 (索引位置 1) ：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-204">For example, the following statement deletes the second value (index position 1) from an array:</span></span>

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

<span data-ttu-id="bf8f2-205">若要刪除變數，請使用 [移除變數](xref:Microsoft.PowerShell.Utility.Remove-Variable) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-205">To delete a variable, use the [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet.</span></span> <span data-ttu-id="bf8f2-206">當變數明確地轉換為特定的資料類型，而且您想要不具類型的變數時，這個方法很有用。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-206">This method is useful when the variable is explicitly cast to a particular data type, and you want an untyped variable.</span></span> <span data-ttu-id="bf8f2-207">下列命令會刪除 `$a` 變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-207">The following command deletes the `$a` variable:</span></span>

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a><span data-ttu-id="bf8f2-208">依乘法運算子的指派</span><span class="sxs-lookup"><span data-stu-id="bf8f2-208">The assignment by multiplication operator</span></span>

<span data-ttu-id="bf8f2-209">依乘法運算子的指派會將 `*=` 數值相乘，或附加變數之字串值的指定複本數目。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-209">The assignment by multiplication operator `*=` multiplies a numeric value or appends the specified number of copies of the string value of a variable.</span></span>

<span data-ttu-id="bf8f2-210">當變數包含單一數值時，該值會乘以運算子右邊的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-210">When a variable contains a single numeric value, that value is multiplied by the value on the right side of the operator.</span></span> <span data-ttu-id="bf8f2-211">例如，下列範例顯示如何使用 `*=` 運算子來乘以變數的值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-211">For example, the following example shows how to use the `*=` operator to multiply the value of a variable:</span></span>

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

<span data-ttu-id="bf8f2-212">在此情況下， `*=` 運算子會合並兩個作業。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-212">In this case, the `*=` operator combines two operations.</span></span> <span data-ttu-id="bf8f2-213">首先，它會相乘，然後再指派。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-213">First, it multiplies, and then it assigns.</span></span> <span data-ttu-id="bf8f2-214">因此，下列語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-214">Therefore, the following statements are equivalent:</span></span>

```powershell
$a *= 2
$a = ($a * 2)
```

<span data-ttu-id="bf8f2-215">當變數包含字串值時，PowerShell 會將指定的字串數目附加至值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-215">When a variable contains a string value, PowerShell appends the specified number of strings to the value, as follows:</span></span>

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

<span data-ttu-id="bf8f2-216">若要乘以陣列的元素，請使用索引來識別您想要相乘的元素。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-216">To multiply an element of an array, use an index to identify the element that you want to multiply.</span></span> <span data-ttu-id="bf8f2-217">例如，下列命令會將陣列中的第一個元素乘以2的索引位置 0)  (：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-217">For example, the following command multiplies the first element in the array (index position 0) by 2:</span></span>

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a><span data-ttu-id="bf8f2-218">依除法運算子的指派</span><span class="sxs-lookup"><span data-stu-id="bf8f2-218">The assignment by division operator</span></span>

<span data-ttu-id="bf8f2-219">依除法運算子指派的值 `/=` 會將數值除以運算子右邊所指定的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-219">The assignment by division operator `/=` divides a numeric value by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="bf8f2-220">運算子不能與字串變數一起使用。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-220">The operator cannot be used with string variables.</span></span>

<span data-ttu-id="bf8f2-221">`/=`運算子結合兩個作業。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-221">The `/=` operator combines two operations.</span></span> <span data-ttu-id="bf8f2-222">首先，它會分割，然後再指派。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-222">First, it divides, and then it assigns.</span></span> <span data-ttu-id="bf8f2-223">因此，下列兩個語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-223">Therefore, the following two statements are equivalent:</span></span>

```powershell
$a /= 2
$a = ($a / 2)
```

<span data-ttu-id="bf8f2-224">例如，下列命令會使用 `/=` 運算子來分割變數的值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-224">For example, the following command uses the `/=` operator to divide the value of a variable:</span></span>

```powershell
$a = 8
$a /=2
$a
```

```
4
```

<span data-ttu-id="bf8f2-225">若要分割陣列的元素，請使用索引來識別您想要變更的元素。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-225">To divide an element of an array, use an index to identify the element that you want to change.</span></span> <span data-ttu-id="bf8f2-226">例如，下列命令會將陣列中的第二個元素分割 (索引位置 1) 除以2：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-226">For example, the following command divides the second element in the array (index position 1) by 2:</span></span>

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a><span data-ttu-id="bf8f2-227">依模數運算子的指派</span><span class="sxs-lookup"><span data-stu-id="bf8f2-227">The assignment by modulus operator</span></span>

<span data-ttu-id="bf8f2-228">依模數運算子指派會將 `%=` 變數的值除以運算子右邊的值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-228">The assignment by modulus operator `%=` divides the value of a variable by the value on the right side of the operator.</span></span> <span data-ttu-id="bf8f2-229">然後，運算子會將 `%=` (稱為模數) 的餘數指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-229">Then, the `%=` operator assigns the remainder (known as the modulus) to the variable.</span></span> <span data-ttu-id="bf8f2-230">只有當變數包含單一數值時，您才能使用這個運算子。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-230">You can use this operator only when a variable contains a single numeric value.</span></span> <span data-ttu-id="bf8f2-231">當變數包含字串變數或陣列時，不能使用這個運算子。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-231">You cannot use this operator when a variable contains a string variable or an array.</span></span>

<span data-ttu-id="bf8f2-232">`%=`運算子結合兩個作業。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-232">The `%=` operator combines two operations.</span></span> <span data-ttu-id="bf8f2-233">首先，它會分割並決定餘數，然後將餘數指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-233">First, it divides and determines the remainder, and then it assigns the remainder to the variable.</span></span> <span data-ttu-id="bf8f2-234">因此，下列語句是相等的：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-234">Therefore, the following statements are equivalent:</span></span>

```powershell
$a %= 2
$a = ($a % 2)
```

<span data-ttu-id="bf8f2-235">下列範例顯示如何使用 `%=` 運算子來儲存商的模數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-235">The following example shows how to use the `%=` operator to save the modulus of a quotient:</span></span>

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a><span data-ttu-id="bf8f2-236">遞增和遞減運算子</span><span class="sxs-lookup"><span data-stu-id="bf8f2-236">The increment and decrement operators</span></span>

<span data-ttu-id="bf8f2-237">遞增運算子 `++` 會將變數的值增加1。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-237">The increment operator `++` increases the value of a variable by 1.</span></span> <span data-ttu-id="bf8f2-238">當您在簡單的語句中使用遞增運算子時，不會傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-238">When you use the increment operator in a simple statement, no value is returned.</span></span> <span data-ttu-id="bf8f2-239">若要查看結果，請顯示變數的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-239">To view the result, display the value of the variable, as follows:</span></span>

```powershell
$a = 7
++$a
$a
```

```
8
```

<span data-ttu-id="bf8f2-240">若要強制傳回值，請以括弧括住變數和運算子，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-240">To force a value to be returned, enclose the variable and the operator in parentheses, as follows:</span></span>

```powershell
$a = 7
(++$a)
```

```
8
```

<span data-ttu-id="bf8f2-241">遞增運算子可放置在 (前置詞) 之前，或 (後置) 變數之後。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-241">The increment operator can be placed before (prefix) or after (postfix) a variable.</span></span> <span data-ttu-id="bf8f2-242">運算子的前置詞版本會在語句中使用變數的值之前遞增變數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-242">The prefix version of the operator increments a variable before its value is used in the statement, as follows:</span></span>

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

<span data-ttu-id="bf8f2-243">運算子的後置版本會在語句中使用變數的值之後，遞增變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-243">The postfix version of the operator increments a variable after its value is used in the statement.</span></span> <span data-ttu-id="bf8f2-244">在下列範例中， `$c` 和 `$a` 變數有不同的值，因為此值會在 `$c` 變更之前指派給 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-244">In the following example, the `$c` and `$a` variables have different values because the value is assigned to `$c` before `$a` changes:</span></span>

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

<span data-ttu-id="bf8f2-245">遞減運算子會將 `--` 變數的值減少1。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-245">The decrement operator `--` decreases the value of a variable by 1.</span></span> <span data-ttu-id="bf8f2-246">如同遞增運算子一樣，當您在簡單的語句中使用運算子時，不會傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-246">As with the increment operator, no value is returned when you use the operator in a simple statement.</span></span> <span data-ttu-id="bf8f2-247">使用括弧傳回值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-247">Use parentheses to return a value, as follows:</span></span>

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

<span data-ttu-id="bf8f2-248">運算子的前置詞版本會在語句中使用變數值之前遞減變數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-248">The prefix version of the operator decrements a variable before its value is used in the statement, as follows:</span></span>

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

<span data-ttu-id="bf8f2-249">運算子的後置版本會在語句中使用變數的值之後遞減變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-249">The postfix version of the operator decrements a variable after its value is used in the statement.</span></span> <span data-ttu-id="bf8f2-250">在下列範例中， `$d` 和 `$a` 變數有不同的值，因為此值會在 `$d` 變更之前指派給 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-250">In the following example, the `$d` and `$a` variables have different values because the value is assigned to `$d` before `$a` changes:</span></span>

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

## <a name="microsoft-net-framework-types"></a><span data-ttu-id="bf8f2-251">Microsoft .NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="bf8f2-251">Microsoft .NET Framework types</span></span>

<span data-ttu-id="bf8f2-252">根據預設，當變數只有一個值時，指派給變數的值會決定變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-252">By default, when a variable has only one value, the value that is assigned to the variable determines the data type of the variable.</span></span> <span data-ttu-id="bf8f2-253">例如，下列命令會建立一個變數，此變數的 "Integer" (system.string) 類型：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-253">For example, the following command creates a variable that has the "Integer" (System.Int32) type:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="bf8f2-254">若要尋找變數的 .NET Framework 類型，請使用 **GetType** 方法及其 **FullName** 屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-254">To find the .NET Framework type of a variable, use the **GetType** method and its **FullName** property, as follows.</span></span> <span data-ttu-id="bf8f2-255">請務必在 **GetType** 方法名稱後面加上括弧，即使方法呼叫沒有引數也一樣：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-255">Be sure to include the parentheses after the **GetType** method name, even though the method call has no arguments:</span></span>

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

<span data-ttu-id="bf8f2-256">若要建立包含字串的變數，請將字串值指派給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-256">To create a variable that contains a string, assign a string value to the variable.</span></span> <span data-ttu-id="bf8f2-257">若要指出值為字串，請將它括在引號中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-257">To indicate that the value is a string, enclose it in quotation marks, as follows:</span></span>

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

<span data-ttu-id="bf8f2-258">如果指派給變數的第一個值為字串，則 PowerShell 會將所有作業視為字串作業，並將新的值轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-258">If the first value that is assigned to the variable is a string, PowerShell treats all operations as string operations and casts new values to strings.</span></span>
<span data-ttu-id="bf8f2-259">這會發生在下列範例中：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-259">This occurs in the following example:</span></span>

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

<span data-ttu-id="bf8f2-260">如果第一個值是整數，則 PowerShell 會將所有作業視為整數運算，並將新的值轉換成整數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-260">If the first value is an integer, PowerShell treats all operations as integer operations and casts new values to integers.</span></span> <span data-ttu-id="bf8f2-261">這會發生在下列範例中：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-261">This occurs in the following example:</span></span>

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

<span data-ttu-id="bf8f2-262">您可以將新的純量變數作為任何 .NET Framework 類型，方法是將類型名稱放在變數名稱或第一個指派值之前的括弧中。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-262">You can cast a new scalar variable as any .NET Framework type by placing the type name in brackets that precede either the variable name or the first assignment value.</span></span> <span data-ttu-id="bf8f2-263">當您轉換變數時，可以決定變數中可儲存的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-263">When you cast a variable, you can determine the types of data that can be stored in the variable.</span></span> <span data-ttu-id="bf8f2-264">而且，您可以決定當您操作變數時，變數的行為。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-264">And, you can determine how the variable behaves when you manipulate it.</span></span>

<span data-ttu-id="bf8f2-265">例如，下列命令會將變數轉換成字串類型：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-265">For example, the following command casts the variable as a string type:</span></span>

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

<span data-ttu-id="bf8f2-266">下列範例會轉換第一個值，而不是轉換變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-266">The following example casts the first value, instead of casting the variable:</span></span>

```powershell
$a = [string]27
```

<span data-ttu-id="bf8f2-267">當您將變數轉換成特定型別時，常見的慣例是轉換變數，而不是值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-267">When you cast a variable to a specific type, the common convention is to cast the variable, not the value.</span></span> <span data-ttu-id="bf8f2-268">但是，如果不能將現有變數的值轉換成新的資料類型，就無法重新轉換其資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-268">However, you cannot recast the data type of an existing variable if its value cannot be converted to the new data type.</span></span> <span data-ttu-id="bf8f2-269">若要變更資料類型，您必須取代其值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-269">To change the data type, you must replace its value, as follows:</span></span>

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

<span data-ttu-id="bf8f2-270">此外，如果您在變數名稱之前加上資料類型，則該變數的類型會被鎖定，除非您指定其他資料類型來明確覆寫該類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-270">In addition, when you precede a variable name with a data type, the type of that variable is locked unless you explicitly override the type by specifying another data type.</span></span> <span data-ttu-id="bf8f2-271">如果您嘗試指派的值與現有的型別不相容，而且您未明確覆寫該型別，則 PowerShell 會顯示錯誤，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-271">If you try to assign a value that is incompatible with the existing type, and you do not explicitly override the type, PowerShell displays an error, as shown in the following example:</span></span>

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

<span data-ttu-id="bf8f2-272">在 PowerShell 中，包含陣列中多個專案之變數的資料類型處理方式，與包含單一專案之變數的資料類型不同。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-272">In PowerShell, the data types of variables that contain multiple items in an array are handled differently from the data types of variables that contain a single item.</span></span> <span data-ttu-id="bf8f2-273">除非將資料類型明確指派給陣列變數，否則資料類型一律為 `System.Object []` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-273">Unless a data type is specifically assigned to an array variable, the data type is always `System.Object []`.</span></span> <span data-ttu-id="bf8f2-274">這是陣列專屬的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-274">This data type is specific to arrays.</span></span>

<span data-ttu-id="bf8f2-275">有時候，您可以藉由指定另一種類型來覆寫預設型別。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-275">Sometimes, you can override the default type by specifying another type.</span></span> <span data-ttu-id="bf8f2-276">例如，下列命令會將變數轉換成 `string []` 陣列類型：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-276">For example, the following command casts the variable as a `string []` array type:</span></span>

```powershell
[string []] $a = "one", "two", "three"
```

<span data-ttu-id="bf8f2-277">PowerShell 變數可以是任何 .NET Framework 資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-277">PowerShell variables can be any .NET Framework data type.</span></span> <span data-ttu-id="bf8f2-278">此外，您可以指派目前進程中可用的任何完整 .NET Framework 資料類型。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-278">In addition, you can assign any fully qualified .NET Framework data type that is available in the current process.</span></span> <span data-ttu-id="bf8f2-279">例如，下列命令會指定 `System.DateTime` 資料類型：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-279">For example, the following command specifies a `System.DateTime` data type:</span></span>

```powershell
[System.DateTime]$a = "5/31/2005"
```

<span data-ttu-id="bf8f2-280">系統會將符合資料類型的值指派給變數 `System.DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-280">The variable will be assigned a value that conforms to the `System.DateTime` data type.</span></span> <span data-ttu-id="bf8f2-281">變數的值如下 `$a` 所示：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-281">The value of the `$a` variable would be the following:</span></span>

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a><span data-ttu-id="bf8f2-282">指派多個變數</span><span class="sxs-lookup"><span data-stu-id="bf8f2-282">Assigning multiple variables</span></span>

<span data-ttu-id="bf8f2-283">在 PowerShell 中，您可以使用單一命令將值指派給多個變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-283">In PowerShell, you can assign values to multiple variables by using a single command.</span></span> <span data-ttu-id="bf8f2-284">指派值的第一個專案會指派給第一個變數，第二個元素會指派給第二個變數、第三個元素到第三個變數，依此類推。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-284">The first element of the assignment value is assigned to the first variable, the second element is assigned to the second variable, the third element to the third variable, and so on.</span></span> <span data-ttu-id="bf8f2-285">例如，下列命令會將值1指派給變數、將值2指派給變數 `$a` `$b` ，並將值3指派給 `$c` 變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-285">For example, the following command assigns the value 1 to the `$a` variable, the value 2 to the `$b` variable, and the value 3 to the `$c` variable:</span></span>

```powershell
$a, $b, $c = 1, 2, 3
```

<span data-ttu-id="bf8f2-286">如果指派值包含的元素多於變數數目，則會將所有剩餘的值指派給最後一個變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-286">If the assignment value contains more elements than variables, all the remaining values are assigned to the last variable.</span></span> <span data-ttu-id="bf8f2-287">例如，下列命令包含三個變數和五個值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-287">For example, the following command contains three variables and five values:</span></span>

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

<span data-ttu-id="bf8f2-288">因此，PowerShell 會將值1指派給變數 `$a` ，並將值2指派 `$b` 給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-288">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="bf8f2-289">它會將值3、4和5指派給 `$c` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-289">It assigns the values 3, 4, and 5 to the `$c` variable.</span></span>
<span data-ttu-id="bf8f2-290">若要將變數中的值指派 `$c` 給其他三個變數，請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-290">To assign the values in the `$c` variable to three other variables, use the following format:</span></span>

```powershell
$d, $e, $f = $c
```

<span data-ttu-id="bf8f2-291">此命令會將值3指派給變數，將值4指派給變數 `$d` `$e` ，並將值5指派給 `$f` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-291">This command assigns the value 3 to the `$d` variable, the value 4 to the `$e` variable, and the value 5 to the `$f` variable.</span></span>

<span data-ttu-id="bf8f2-292">如果指派值包含的元素數目少於變數，則結尾的所有變數都不會指派任何值。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-292">If the assignment value contains less elements than variables, all the remaining variables at the end are not assigned any values.</span></span> <span data-ttu-id="bf8f2-293">例如，下列命令包含三個變數和兩個值：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-293">For example, the following command contains three variables and two values:</span></span>

```powershell
$a, $b, $c = 1, 2
```

<span data-ttu-id="bf8f2-294">因此，PowerShell 會將值1指派給變數 `$a` ，並將值2指派 `$b` 給變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-294">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="bf8f2-295">它不會將任何值指派給 `$c` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-295">It will not assign any value to the `$c` variable.</span></span>

<span data-ttu-id="bf8f2-296">您也可以藉由連結變數，將單一值指派給多個變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-296">You can also assign a single value to multiple variables by chaining the variables.</span></span> <span data-ttu-id="bf8f2-297">例如，下列命令會將 "3" 的值指派給所有四個變數：</span><span class="sxs-lookup"><span data-stu-id="bf8f2-297">For example, the following command assigns a value of "three" to all four variables:</span></span>

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a><span data-ttu-id="bf8f2-298">變數相關的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bf8f2-298">Variable-related cmdlets</span></span>

<span data-ttu-id="bf8f2-299">除了使用指派作業來設定變數值以外，您也可以使用 [集合變數](xref:Microsoft.PowerShell.Utility.Set-Variable) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-299">In addition to using an assignment operation to set a variable value, you can also use the [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet.</span></span> <span data-ttu-id="bf8f2-300">例如，下列命令會使用將 `Set-Variable` 1、2、3的陣列指派給 `$a` 變數。</span><span class="sxs-lookup"><span data-stu-id="bf8f2-300">For example, the following command uses `Set-Variable` to assign an array of 1, 2, 3 to the `$a` variable.</span></span>

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a><span data-ttu-id="bf8f2-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf8f2-301">See also</span></span>

[<span data-ttu-id="bf8f2-302">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="bf8f2-302">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="bf8f2-303">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="bf8f2-303">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="bf8f2-304">about_Variables</span><span class="sxs-lookup"><span data-stu-id="bf8f2-304">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="bf8f2-305">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="bf8f2-305">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[<span data-ttu-id="bf8f2-306">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="bf8f2-306">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[<span data-ttu-id="bf8f2-307">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="bf8f2-307">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)

