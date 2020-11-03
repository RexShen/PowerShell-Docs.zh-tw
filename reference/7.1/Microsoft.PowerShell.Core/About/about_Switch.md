---
description: 說明如何使用參數來處理多個 `If` 語句。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 4d70d765086ad49ed0e5cd955fc3be3094fc79a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208296"
---
# <a name="about-switch"></a><span data-ttu-id="c0c68-104">關於切換</span><span class="sxs-lookup"><span data-stu-id="c0c68-104">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="c0c68-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="c0c68-105">Short description</span></span>
<span data-ttu-id="c0c68-106">說明如何使用參數來處理多個 `If` 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-106">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="c0c68-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="c0c68-107">Long description</span></span>

<span data-ttu-id="c0c68-108">若要檢查腳本或函數中的條件，請使用 `If` 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-108">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="c0c68-109">`If`語句可以檢查許多類型的條件，包括變數的值和物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="c0c68-109">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="c0c68-110">若要檢查多個條件，請使用 `Switch` 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-110">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="c0c68-111">`Switch`語句相當於一連串的 `If` 語句，但比較簡單。</span><span class="sxs-lookup"><span data-stu-id="c0c68-111">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="c0c68-112">此 `Switch` 語句會列出每個條件和一個選擇性的動作。</span><span class="sxs-lookup"><span data-stu-id="c0c68-112">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="c0c68-113">如果條件獲得，則會執行動作。</span><span class="sxs-lookup"><span data-stu-id="c0c68-113">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="c0c68-114">`Switch`語句可以使用 `$_` 和 `$switch` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-114">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="c0c68-115">如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c0c68-115">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="c0c68-116">基本 `Switch` 語句的格式如下：</span><span class="sxs-lookup"><span data-stu-id="c0c68-116">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="c0c68-117">例如，下列語句會將 `Switch` 測試值3與每個條件進行比較。</span><span class="sxs-lookup"><span data-stu-id="c0c68-117">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="c0c68-118">當測試值符合條件時，便會執行動作。</span><span class="sxs-lookup"><span data-stu-id="c0c68-118">When the test value matches the condition, the action is performed.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

<span data-ttu-id="c0c68-119">在這個簡單的範例中，會將值與清單中的每個條件進行比較，即使值3有相符的值也一樣。</span><span class="sxs-lookup"><span data-stu-id="c0c68-119">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="c0c68-120">下列 `Switch` 語句有兩個值3的條件。</span><span class="sxs-lookup"><span data-stu-id="c0c68-120">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="c0c68-121">它會示範根據預設，所有條件都會進行測試。</span><span class="sxs-lookup"><span data-stu-id="c0c68-121">It demonstrates that, by default, all conditions are tested.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

<span data-ttu-id="c0c68-122">若要指示在比對 `Switch` 之後停止比較，請使用 `Break` 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-122">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="c0c68-123">`Break`語句會終止 `Switch` 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-123">The `Break` statement terminates the `Switch` statement.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

<span data-ttu-id="c0c68-124">如果測試值為集合（例如陣列），則集合中的每個專案都會依照其出現的順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="c0c68-124">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="c0c68-125">下列範例會評估4然後2。</span><span class="sxs-lookup"><span data-stu-id="c0c68-125">The following examples evaluates 4 and then 2.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

<span data-ttu-id="c0c68-126">任何 `Break` 語句都會套用至集合，而不是每個值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c0c68-126">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="c0c68-127">語句 `Switch` 是由 `Break` 值4的條件中的語句所終止。</span><span class="sxs-lookup"><span data-stu-id="c0c68-127">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a><span data-ttu-id="c0c68-128">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0c68-128">Syntax</span></span>

<span data-ttu-id="c0c68-129">完整的 `Switch` 語句語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="c0c68-129">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="c0c68-130">或</span><span class="sxs-lookup"><span data-stu-id="c0c68-130">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="c0c68-131">如果未使用任何參數，其行為會與 `Switch` 使用 **確切** 的參數相同。</span><span class="sxs-lookup"><span data-stu-id="c0c68-131">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="c0c68-132">它會對值執行不區分大小寫的比對。</span><span class="sxs-lookup"><span data-stu-id="c0c68-132">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="c0c68-133">如果值是集合，每個專案都會依其出現的順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="c0c68-133">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="c0c68-134">`Switch`語句必須包含至少一個 condition 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-134">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="c0c68-135">`Default`當值不符合任何條件時，就會觸發子句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-135">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="c0c68-136">它相當於 `Else` 語句中的子句 `If` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-136">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="c0c68-137">`Default`每個語句中只允許一個子句 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-137">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="c0c68-138">`Switch` 具有下列參數：</span><span class="sxs-lookup"><span data-stu-id="c0c68-138">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="c0c68-139">**萬用字元** -表示條件是萬用字元字串。</span><span class="sxs-lookup"><span data-stu-id="c0c68-139">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="c0c68-140">如果 match 子句不是字串，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-140">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="c0c68-141">此比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c0c68-141">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="c0c68-142">**Exact** -指出 match 子句（如果它是字串）必須完全相符。</span><span class="sxs-lookup"><span data-stu-id="c0c68-142">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="c0c68-143">如果 match 子句不是字串，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-143">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="c0c68-144">此比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c0c68-144">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="c0c68-145">**CaseSensitive** -執行區分大小寫的比對。</span><span class="sxs-lookup"><span data-stu-id="c0c68-145">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="c0c68-146">如果 match 子句不是字串，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-146">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="c0c68-147">**File** -接受來自檔案的輸入，而不是值語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-147">**File** - Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="c0c68-148">如果包含 **多個** 檔案參數，則只會使用最後一個。</span><span class="sxs-lookup"><span data-stu-id="c0c68-148">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="c0c68-149">檔案的每一行都是由語句讀取和評估 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-149">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="c0c68-150">此比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c0c68-150">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="c0c68-151">**Regex** -執行符合條件之值的正則運算式比對。</span><span class="sxs-lookup"><span data-stu-id="c0c68-151">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="c0c68-152">如果 match 子句不是字串，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-152">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="c0c68-153">此比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c0c68-153">The comparison is case-insensitive.</span></span> <span data-ttu-id="c0c68-154">`$matches`自動變數可在相符的語句區塊內使用。</span><span class="sxs-lookup"><span data-stu-id="c0c68-154">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="c0c68-155">指定衝突的值（例如 **Regex** 和 **萬用字元** ）時，會優先使用指定的最後一個參數，且會忽略所有衝突的參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-155">When specifying conflicting values, like **Regex** and **Wildcard** , the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="c0c68-156">也可以使用多個參數的實例。</span><span class="sxs-lookup"><span data-stu-id="c0c68-156">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="c0c68-157">不過，只有最後使用的參數才有效。</span><span class="sxs-lookup"><span data-stu-id="c0c68-157">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="c0c68-158">在此範例中，不是字串或數值資料的物件會傳遞至 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-158">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="c0c68-159">會 `Switch` 在物件上執行字串強制型轉，並評估結果。</span><span class="sxs-lookup"><span data-stu-id="c0c68-159">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

<span data-ttu-id="c0c68-160">在此範例中，沒有任何相符的案例，因此沒有任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c0c68-160">In this example, there is no matching case so there is no output.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

<span data-ttu-id="c0c68-161">藉由新增 `Default` 子句，您可以在沒有其他條件成功時執行動作。</span><span class="sxs-lookup"><span data-stu-id="c0c68-161">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

<span data-ttu-id="c0c68-162">若要讓 "十四" 這個字元合大小寫，您必須使用 `-Wildcard` 或 `-Regex` 參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-162">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

<span data-ttu-id="c0c68-163">下列範例會使用 `-Regex` 參數。</span><span class="sxs-lookup"><span data-stu-id="c0c68-163">The following example uses the `-Regex` parameter.</span></span>

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

<span data-ttu-id="c0c68-164">Switch 語句條件可以是：</span><span class="sxs-lookup"><span data-stu-id="c0c68-164">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="c0c68-165">其值與輸入值比較的運算式</span><span class="sxs-lookup"><span data-stu-id="c0c68-165">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="c0c68-166">如果符合條件，則應傳回的腳本區塊 `$true` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-166">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="c0c68-167">`$_`自動變數包含傳遞給 switch 語句的值，而且可以在條件陳述式的範圍內進行評估和使用。</span><span class="sxs-lookup"><span data-stu-id="c0c68-167">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="c0c68-168">每個條件的動作與其他條件中的動作無關。</span><span class="sxs-lookup"><span data-stu-id="c0c68-168">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="c0c68-169">下列範例示範如何使用腳本區塊做為 `Switch` 語句條件。</span><span class="sxs-lookup"><span data-stu-id="c0c68-169">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

<span data-ttu-id="c0c68-170">如果值符合多個條件，則會執行每個條件的動作。</span><span class="sxs-lookup"><span data-stu-id="c0c68-170">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="c0c68-171">若要變更此行為，請使用 `Break` 或 `Continue` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c0c68-171">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="c0c68-172">`Break`關鍵字會停止處理並結束 `Switch` 語句。</span><span class="sxs-lookup"><span data-stu-id="c0c68-172">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="c0c68-173">`Continue`關鍵字會停止處理目前的值，但會繼續處理任何後續的值。</span><span class="sxs-lookup"><span data-stu-id="c0c68-173">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="c0c68-174">下列範例會處理數位的陣列，如果它們是奇數或偶數，則會顯示。</span><span class="sxs-lookup"><span data-stu-id="c0c68-174">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="c0c68-175">使用關鍵字略過負數 `Continue` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-175">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="c0c68-176">如果遇到非數位，則會以關鍵字結束執行 `Break` 。</span><span class="sxs-lookup"><span data-stu-id="c0c68-176">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a><span data-ttu-id="c0c68-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c68-177">See also</span></span>

[<span data-ttu-id="c0c68-178">about_Break</span><span class="sxs-lookup"><span data-stu-id="c0c68-178">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="c0c68-179">about_Continue</span><span class="sxs-lookup"><span data-stu-id="c0c68-179">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="c0c68-180">about_If</span><span class="sxs-lookup"><span data-stu-id="c0c68-180">about_If</span></span>](about_If.md)

[<span data-ttu-id="c0c68-181">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="c0c68-181">about_Script_Blocks</span></span>](about_Script_Blocks.md)
