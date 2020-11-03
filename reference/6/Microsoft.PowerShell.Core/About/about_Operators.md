---
description: 描述 PowerShell 所支援的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 9668e635b17f8cbe9f6639e8a13b95d4b9387fbb
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208940"
---
# <a name="about-operators"></a><span data-ttu-id="b7846-104">關於運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="b7846-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b7846-105">Short description</span></span>
<span data-ttu-id="b7846-106">描述 PowerShell 所支援的運算子。</span><span class="sxs-lookup"><span data-stu-id="b7846-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b7846-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="b7846-107">Long description</span></span>

<span data-ttu-id="b7846-108">操作員是可在命令或運算式中使用的語言元素。</span><span class="sxs-lookup"><span data-stu-id="b7846-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="b7846-109">PowerShell 支援數種可協助您操作值的運算子類型。</span><span class="sxs-lookup"><span data-stu-id="b7846-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="b7846-110">算術運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-110">Arithmetic Operators</span></span>

<span data-ttu-id="b7846-111">使用算術運算子 (`+` 、 `-` 、 `*` 、 `/` `%`) 來計算命令或運算式中的值。</span><span class="sxs-lookup"><span data-stu-id="b7846-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="b7846-112">您可以使用這些運算子來加、減、乘或除值，並計算除法運算 (模數) 的餘數。</span><span class="sxs-lookup"><span data-stu-id="b7846-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="b7846-113">加法運算子串連元素。</span><span class="sxs-lookup"><span data-stu-id="b7846-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="b7846-114">乘法運算子會傳回每個專案的指定複本數目。</span><span class="sxs-lookup"><span data-stu-id="b7846-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="b7846-115">您可以將算術運算子用於任何執行它們的 .net 型別，例如： `Int` 、 `String` 、 `DateTime` 、 `Hashtable` 和陣列。</span><span class="sxs-lookup"><span data-stu-id="b7846-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="b7846-116">位運算子 (`-band` 、 `-bor` 、 `-bxor` 、 `-bnot` 、 `-shl` `-shr`) 操作值中的位模式。</span><span class="sxs-lookup"><span data-stu-id="b7846-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="b7846-117">如需詳細資訊，請參閱 [about_Arithmetic_Operators](about_Arithmetic_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="b7846-118">指派運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-118">Assignment Operators</span></span>

<span data-ttu-id="b7846-119">使用指派運算子 (`=` 、 `+=` 、 `-=` 、 `*=` 、 `/=` `%=`) ，將值指派、變更或附加到變數。</span><span class="sxs-lookup"><span data-stu-id="b7846-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="b7846-120">您可以結合算術運算子與指派，將算數運算的結果指派給變數。</span><span class="sxs-lookup"><span data-stu-id="b7846-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="b7846-121">如需詳細資訊，請參閱 [about_Assignment_Operators](about_Assignment_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="b7846-122">比較運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-122">Comparison Operators</span></span>

<span data-ttu-id="b7846-123">使用比較運算子 (`-eq` 、 `-ne` 、 `-gt` 、 `-lt` 、 `-le` `-ge`) 來比較值和測試條件。</span><span class="sxs-lookup"><span data-stu-id="b7846-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="b7846-124">例如，您可以比較兩個字串值，判斷它們是否相等。</span><span class="sxs-lookup"><span data-stu-id="b7846-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="b7846-125">比較運算子也包含尋找或取代文字中之模式的運算子。</span><span class="sxs-lookup"><span data-stu-id="b7846-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="b7846-126"> (`-match` 、 `-notmatch` 、 `-replace`) 運算子會使用正則運算式，並 `-like` (`-notlike`) 使用萬用字元 `*` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="b7846-127">內含專案比較運算子會判斷測試值是否出現在參考集 (`-in` 、 `-notin` 、 `-contains` `-notcontains`) 。</span><span class="sxs-lookup"><span data-stu-id="b7846-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="b7846-128">類型比較運算子 (`-is` ， `-isnot`) 判斷物件是否為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="b7846-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="b7846-129">如需詳細資訊，請參閱 [about_Comparison_Operators](about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="b7846-130">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-130">Logical Operators</span></span>

<span data-ttu-id="b7846-131">使用邏輯運算子 (`-and` 、 `-or` 、 `-xor` 、) ，將 `-not` `!` 條件陳述式連接到單一複雜的條件。</span><span class="sxs-lookup"><span data-stu-id="b7846-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="b7846-132">例如，您可以使用邏輯 `-and` 運算子來建立具有兩個不同條件的物件篩選。</span><span class="sxs-lookup"><span data-stu-id="b7846-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="b7846-133">如需詳細資訊，請參閱 [about_Logical_Operators](about_logical_operators.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="b7846-134">重新導向運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-134">Redirection Operators</span></span>

<span data-ttu-id="b7846-135">使用重新導向運算子 (`>` 、、 `>>` `2>` 、和) ，將 `2>>` `2>&1` 命令或運算式的輸出傳送至文字檔。</span><span class="sxs-lookup"><span data-stu-id="b7846-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="b7846-136">重新導向運算子的運作方式就像 `Out-File` Cmdlet (沒有參數) 但也可讓您將錯誤輸出重新導向至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="b7846-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="b7846-137">您也可以使用 `Tee-Object` Cmdlet 來重新導向輸出。</span><span class="sxs-lookup"><span data-stu-id="b7846-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="b7846-138">如需詳細資訊，請參閱 [about_Redirection](about_Redirection.md)</span><span class="sxs-lookup"><span data-stu-id="b7846-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="b7846-139">分割和聯結運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-139">Split and Join Operators</span></span>

<span data-ttu-id="b7846-140">`-split`和運算子會將 `-join` 子字串相除併合並。</span><span class="sxs-lookup"><span data-stu-id="b7846-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="b7846-141">運算子會將 `-split` 字串分割成子字串。</span><span class="sxs-lookup"><span data-stu-id="b7846-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="b7846-142">運算子會將 `-join` 多個字串串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="b7846-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="b7846-143">如需詳細資訊，請參閱 [about_Split](about_Split.md) 和 [about_Join](about_Join.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="b7846-144">運算子型別</span><span class="sxs-lookup"><span data-stu-id="b7846-144">Type Operators</span></span>

<span data-ttu-id="b7846-145">使用類型運算子 (`-is` 、 `-isnot` 、 `-as`) 來尋找或變更物件的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="b7846-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="b7846-146">如需詳細資訊，請參閱 [about_Type_Operators](about_Type_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="b7846-147">一元運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-147">Unary Operators</span></span>

<span data-ttu-id="b7846-148">您可以使用一元運算子來遞增或遞減變數或物件屬性，以及將整數設定為正數或負數。</span><span class="sxs-lookup"><span data-stu-id="b7846-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="b7846-149">例如，若要將變數 `$a` 從遞增 `9` 到 `10` ，請輸入 `$a++` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="b7846-150">特殊運算子</span><span class="sxs-lookup"><span data-stu-id="b7846-150">Special Operators</span></span>

<span data-ttu-id="b7846-151">特殊運算子具有不符合任何其他操作員群組的特定使用案例。</span><span class="sxs-lookup"><span data-stu-id="b7846-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="b7846-152">例如，特殊運算子可讓您執行命令、變更值的資料類型，或從陣列中取出元素。</span><span class="sxs-lookup"><span data-stu-id="b7846-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="b7846-153">群組運算子 `( )`</span><span class="sxs-lookup"><span data-stu-id="b7846-153">Grouping operator `( )`</span></span>

<span data-ttu-id="b7846-154">在其他語言中，則是用 `(...)` 來覆寫運算式中的運算子優先順序。</span><span class="sxs-lookup"><span data-stu-id="b7846-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="b7846-155">例如：`(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="b7846-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="b7846-156">不過，在 PowerShell 中還有其他行為。</span><span class="sxs-lookup"><span data-stu-id="b7846-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="b7846-157">`(...)` 允許您讓 _命令_ 的輸出參與運算式。</span><span class="sxs-lookup"><span data-stu-id="b7846-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="b7846-158">例如：</span><span class="sxs-lookup"><span data-stu-id="b7846-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="b7846-159">當做管線的第一個區段使用時，以括弧括住命令或運算式，會造成運算式結果的 _列舉_ 。</span><span class="sxs-lookup"><span data-stu-id="b7846-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="b7846-160">如果括弧包裝一個 _命令_ ，則會使用 _記憶體中收集_ 到的所有輸出來執行完成，然後才會透過管線傳送結果。</span><span class="sxs-lookup"><span data-stu-id="b7846-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="b7846-161">將命令包裝在括弧中會使自動變數 `$?` 設定為 `$true` ，即使已括住的命令本身設為也是一樣 `$?` `$false` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-161">Wrapping a command in parentheses causes the automatic variable `$?` to be set to `$true`, even when the enclosed command itself set `$?` to `$false`.</span></span>
> <span data-ttu-id="b7846-162">例如， `(Get-Item /Nosuch); $?` 意外產生 **True** 。</span><span class="sxs-lookup"><span data-stu-id="b7846-162">For example, `(Get-Item /Nosuch); $?` unexpectedly yields **True**.</span></span> <span data-ttu-id="b7846-163">如需的詳細資訊 `$?` ，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-163">For more information about `$?`, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="b7846-164">子運算式運算子 `$( )`</span><span class="sxs-lookup"><span data-stu-id="b7846-164">Subexpression operator `$( )`</span></span>

<span data-ttu-id="b7846-165">傳回一或多個語句的結果。</span><span class="sxs-lookup"><span data-stu-id="b7846-165">Returns the result of one or more statements.</span></span> <span data-ttu-id="b7846-166">針對單一結果，會傳回純量。</span><span class="sxs-lookup"><span data-stu-id="b7846-166">For a single result, returns a scalar.</span></span> <span data-ttu-id="b7846-167">針對多個結果，會傳回陣列。</span><span class="sxs-lookup"><span data-stu-id="b7846-167">For multiple results, returns an array.</span></span> <span data-ttu-id="b7846-168">當您想要在另一個運算式中使用運算式時，請使用此語句。</span><span class="sxs-lookup"><span data-stu-id="b7846-168">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="b7846-169">例如，將命令的結果內嵌在字串運算式中。</span><span class="sxs-lookup"><span data-stu-id="b7846-169">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="b7846-170">陣列子運算式運算子 `@( )`</span><span class="sxs-lookup"><span data-stu-id="b7846-170">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="b7846-171">傳回一個或多個語句的結果做為陣列。</span><span class="sxs-lookup"><span data-stu-id="b7846-171">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="b7846-172">如果只有一個專案，則陣列只有一個成員。</span><span class="sxs-lookup"><span data-stu-id="b7846-172">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a><span data-ttu-id="b7846-173">呼叫運算子 `&`</span><span class="sxs-lookup"><span data-stu-id="b7846-173">Call operator `&`</span></span>

<span data-ttu-id="b7846-174">執行命令、腳本或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="b7846-174">Runs a command, script, or script block.</span></span> <span data-ttu-id="b7846-175">呼叫運算子也稱為「調用運算子」，可讓您執行儲存在變數中，並以字串或腳本區塊表示的命令。</span><span class="sxs-lookup"><span data-stu-id="b7846-175">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="b7846-176">呼叫運算子會在子範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="b7846-176">The call operator executes in a child scope.</span></span> <span data-ttu-id="b7846-177">如需範圍的詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-177">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="b7846-178">此範例會將命令儲存在字串中，並使用 call 運算子來執行它。</span><span class="sxs-lookup"><span data-stu-id="b7846-178">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="b7846-179">呼叫運算子不會剖析字串。</span><span class="sxs-lookup"><span data-stu-id="b7846-179">The call operator does not parse strings.</span></span> <span data-ttu-id="b7846-180">這表示當您使用呼叫運算子時，不能在字串中使用命令參數。</span><span class="sxs-lookup"><span data-stu-id="b7846-180">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="b7846-181">叫用 [運算式](xref:Microsoft.PowerShell.Utility.Invoke-Expression) Cmdlet 可以執行程式碼，以在使用呼叫運算子時產生剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7846-181">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

<span data-ttu-id="b7846-182">您可以使用呼叫運算子來執行使用其檔案名的腳本。</span><span class="sxs-lookup"><span data-stu-id="b7846-182">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="b7846-183">下列範例顯示包含空格的指令檔名。</span><span class="sxs-lookup"><span data-stu-id="b7846-183">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="b7846-184">當您嘗試執行腳本時，PowerShell 會改為顯示包含檔案名之加上引號的字串內容。</span><span class="sxs-lookup"><span data-stu-id="b7846-184">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="b7846-185">呼叫運算子可讓您執行包含檔案名的字串內容。</span><span class="sxs-lookup"><span data-stu-id="b7846-185">The call operator allows you to execute the contents of the string containing the filename.</span></span>

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

<span data-ttu-id="b7846-186">如需腳本區塊的詳細資訊，請參閱 [about_Script_Blocks](about_Script_Blocks.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-186">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="b7846-187">背景運算子 `&`</span><span class="sxs-lookup"><span data-stu-id="b7846-187">Background operator `&`</span></span>

<span data-ttu-id="b7846-188">在 PowerShell 作業中，于背景執行管線。</span><span class="sxs-lookup"><span data-stu-id="b7846-188">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="b7846-189">這個運算子的運作方式類似于 UNIX 控制運算子符號 (`&`) ，它會在 subshell 中以非同步方式執行命令，以做為作業。</span><span class="sxs-lookup"><span data-stu-id="b7846-189">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="b7846-190">這個運算子在功能上相當於 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-190">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="b7846-191">下列範例示範背景工作運算子的基本使用方式。</span><span class="sxs-lookup"><span data-stu-id="b7846-191">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="b7846-192">該命令的功能相當於下列用途 `Start-Job` ：</span><span class="sxs-lookup"><span data-stu-id="b7846-192">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="b7846-193">就像 `Start-Job` ， `&` background 運算子會傳回 `Job` 物件。</span><span class="sxs-lookup"><span data-stu-id="b7846-193">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="b7846-194">這個物件可以與和一起 `Receive-Job` 使用 `Remove-Job` ，就像您用 `Start-Job` 來啟動作業一樣。</span><span class="sxs-lookup"><span data-stu-id="b7846-194">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

<span data-ttu-id="b7846-195">`&`背景運算子也是語句結束字元，就像 UNIX 控制運算子符號 (`&`) 一樣。</span><span class="sxs-lookup"><span data-stu-id="b7846-195">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="b7846-196">這可讓您在背景運算子之後叫用其他命令 `&` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-196">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="b7846-197">下列範例示範如何在背景運算子之後叫用其他命令 `&` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-197">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

<span data-ttu-id="b7846-198">這相當於下列腳本：</span><span class="sxs-lookup"><span data-stu-id="b7846-198">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="b7846-199">如果您想要執行多個命令，每個命令都在各自的背景進程中，但全都在同一行，只要在 `&` 每個命令的前後放置。</span><span class="sxs-lookup"><span data-stu-id="b7846-199">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="b7846-200">如需 PowerShell 工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="b7846-200">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="b7846-201">Cast 運算子 `[ ]`</span><span class="sxs-lookup"><span data-stu-id="b7846-201">Cast operator `[ ]`</span></span>

<span data-ttu-id="b7846-202">將物件轉換或限制為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="b7846-202">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="b7846-203">如果無法轉換物件，PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b7846-203">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="b7846-204">當指派變數給使用 [cast 標記法](about_Variables.md)時，也可以執行轉換。</span><span class="sxs-lookup"><span data-stu-id="b7846-204">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="b7846-205">逗點運算子 `,`</span><span class="sxs-lookup"><span data-stu-id="b7846-205">Comma operator `,`</span></span>

<span data-ttu-id="b7846-206">作為二元運算子，逗號會建立陣列或附加至所建立的陣列。</span><span class="sxs-lookup"><span data-stu-id="b7846-206">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="b7846-207">在運算式模式中，以一元運算子的形式，逗號會建立只包含一個成員的陣列。</span><span class="sxs-lookup"><span data-stu-id="b7846-207">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="b7846-208">將逗號放在成員前面。</span><span class="sxs-lookup"><span data-stu-id="b7846-208">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="b7846-209">由於 `Write-Object` 需要引數，因此您必須將運算式放在括弧中。</span><span class="sxs-lookup"><span data-stu-id="b7846-209">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="b7846-210">點來源運算子 `.`</span><span class="sxs-lookup"><span data-stu-id="b7846-210">Dot sourcing operator `.`</span></span>

<span data-ttu-id="b7846-211">在目前的範圍中執行腳本，以便將腳本所建立的任何函式、別名和變數新增至目前的範圍，並覆寫現有的範圍。</span><span class="sxs-lookup"><span data-stu-id="b7846-211">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="b7846-212">腳本所宣告的參數會成為變數。</span><span class="sxs-lookup"><span data-stu-id="b7846-212">Parameters declared by the script become variables.</span></span> <span data-ttu-id="b7846-213">未指定任何值的參數會成為沒有值的變數。</span><span class="sxs-lookup"><span data-stu-id="b7846-213">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="b7846-214">不過，自動變數 `$args` 會保留下來。</span><span class="sxs-lookup"><span data-stu-id="b7846-214">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="b7846-215">點來源運算子後面接著空格。</span><span class="sxs-lookup"><span data-stu-id="b7846-215">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="b7846-216">使用空格來區分點與 `.` 代表目前的目錄的點 () 符號。</span><span class="sxs-lookup"><span data-stu-id="b7846-216">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="b7846-217">在下列範例中，目前目錄中的 Sample.ps1 腳本會在目前的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="b7846-217">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="b7846-218">格式運算子 `-f`</span><span class="sxs-lookup"><span data-stu-id="b7846-218">Format operator `-f`</span></span>

<span data-ttu-id="b7846-219">使用 string 物件的 format 方法來格式化字串。</span><span class="sxs-lookup"><span data-stu-id="b7846-219">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="b7846-220">輸入運算子左邊的格式字串，以及要在運算子右邊格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="b7846-220">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="b7846-221">如果您需要 `{}` 在格式化的字串中保留大括弧 () ，您可以將大括弧換成一倍來將其取消。</span><span class="sxs-lookup"><span data-stu-id="b7846-221">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="b7846-222">如需詳細資訊，請參閱 [字串。格式](/dotnet/api/system.string.format) 方法和 [複合格式](/dotnet/standard/base-types/composite-formatting)。</span><span class="sxs-lookup"><span data-stu-id="b7846-222">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="b7846-223">索引運算子 `[ ]`</span><span class="sxs-lookup"><span data-stu-id="b7846-223">Index operator `[ ]`</span></span>

<span data-ttu-id="b7846-224">從索引集合中選取物件，例如陣列和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b7846-224">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="b7846-225">陣列索引是以零為基底，因此第一個物件的索引為 `[0]` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-225">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="b7846-226">針對僅) 的陣列 (，您也可以使用負索引來取得最後的值。</span><span class="sxs-lookup"><span data-stu-id="b7846-226">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="b7846-227">雜湊表是依索引鍵值來編制索引。</span><span class="sxs-lookup"><span data-stu-id="b7846-227">Hash tables are indexed by key value.</span></span>

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a><span data-ttu-id="b7846-228">管線運算子 `|`</span><span class="sxs-lookup"><span data-stu-id="b7846-228">Pipeline operator `|`</span></span>

<span data-ttu-id="b7846-229">傳送 ( "pipe" ) 命令前面的命令輸出到其後的命令。</span><span class="sxs-lookup"><span data-stu-id="b7846-229">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="b7846-230">當輸出包含一個以上的物件 ("collection" ) 時，管線運算子會一次傳送一個物件。</span><span class="sxs-lookup"><span data-stu-id="b7846-230">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a><span data-ttu-id="b7846-231">範圍運算子 `..`</span><span class="sxs-lookup"><span data-stu-id="b7846-231">Range operator `..`</span></span>

<span data-ttu-id="b7846-232">表示整數陣列中的連續整數，指定上限和下限。</span><span class="sxs-lookup"><span data-stu-id="b7846-232">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="b7846-233">您也可以依相反順序建立範圍。</span><span class="sxs-lookup"><span data-stu-id="b7846-233">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="b7846-234">從 PowerShell 6 開始，範圍運算子適用于 **字元** 和 **整數** 。</span><span class="sxs-lookup"><span data-stu-id="b7846-234">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="b7846-235">若要建立字元範圍，請將界限字元括在引號中。</span><span class="sxs-lookup"><span data-stu-id="b7846-235">To create a range of characters, enclose the boundary characters in quotes.</span></span>

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a><span data-ttu-id="b7846-236">成員存取運算子 `.`</span><span class="sxs-lookup"><span data-stu-id="b7846-236">Member access operator `.`</span></span>

<span data-ttu-id="b7846-237">存取物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="b7846-237">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="b7846-238">成員名稱可以是運算式。</span><span class="sxs-lookup"><span data-stu-id="b7846-238">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="b7846-239">靜態成員運算子 `::`</span><span class="sxs-lookup"><span data-stu-id="b7846-239">Static member operator `::`</span></span>

<span data-ttu-id="b7846-240">呼叫 .NET Framework 類別的靜態屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="b7846-240">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="b7846-241">若要尋找物件的靜態屬性和方法，請使用 Cmdlet 的靜態參數 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="b7846-241">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="b7846-242">成員名稱可以是運算式。</span><span class="sxs-lookup"><span data-stu-id="b7846-242">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a><span data-ttu-id="b7846-243">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7846-243">See also</span></span>

[<span data-ttu-id="b7846-244">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="b7846-244">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="b7846-245">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="b7846-245">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="b7846-246">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="b7846-246">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="b7846-247">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="b7846-247">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="b7846-248">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="b7846-248">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="b7846-249">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="b7846-249">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="b7846-250">about_Split</span><span class="sxs-lookup"><span data-stu-id="b7846-250">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="b7846-251">about_Join</span><span class="sxs-lookup"><span data-stu-id="b7846-251">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="b7846-252">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="b7846-252">about_Redirection</span></span>](about_Redirection.md)
