---
description: 描述可處理終止錯誤的關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 9627c632769cb87e790cc421c09d1103b90acf1d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207523"
---
# <a name="about-trap"></a><span data-ttu-id="d20f6-104">關於陷阱</span><span class="sxs-lookup"><span data-stu-id="d20f6-104">About Trap</span></span>

## <a name="short-description"></a><span data-ttu-id="d20f6-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d20f6-105">Short description</span></span>

<span data-ttu-id="d20f6-106">描述可處理終止錯誤的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d20f6-106">Describes a keyword that handles a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="d20f6-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="d20f6-107">Long description</span></span>

<span data-ttu-id="d20f6-108">終止錯誤會停止執行語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-108">A terminating error stops a statement from running.</span></span> <span data-ttu-id="d20f6-109">如果 PowerShell 沒有以某種方式處理終止錯誤，PowerShell 也會停止在目前的管線中執行函式或腳本。</span><span class="sxs-lookup"><span data-stu-id="d20f6-109">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script in the current pipeline.</span></span> <span data-ttu-id="d20f6-110">在其他語言中（例如 c #），終止錯誤稱為例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d20f6-110">In other languages, such as C#, terminating errors are known as exceptions.</span></span>

<span data-ttu-id="d20f6-111">`trap`關鍵字會指定在終止錯誤發生時要執行的語句清單。</span><span class="sxs-lookup"><span data-stu-id="d20f6-111">The `trap` keyword specifies a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="d20f6-112">`trap` 語句會以下列方式處理終止錯誤：</span><span class="sxs-lookup"><span data-stu-id="d20f6-112">`trap` statements handle the terminating errors in the following ways:</span></span>

- <span data-ttu-id="d20f6-113">在處理語句區塊之後顯示錯誤 `trap` ，並繼續執行包含的腳本或函式 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-113">Display the error after processing the `trap` statement block and continuing execution of the script or function containing the `trap`.</span></span> <span data-ttu-id="d20f6-114">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="d20f6-114">This is the default behavior.</span></span>

- <span data-ttu-id="d20f6-115">顯示錯誤，並中止執行語句中包含 using 的腳本或 `trap` 函數 `break` `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-115">Display the error and abort execution of the script or function containing the `trap` using `break` in the `trap` statement.</span></span>

- <span data-ttu-id="d20f6-116">將錯誤靜音，但是 `trap` `continue` 在語句中使用，繼續執行包含的腳本或函數 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-116">Silence the error, but continue execution of the script or function containing the `trap` by using `continue` in the `trap` statement.</span></span>

<span data-ttu-id="d20f6-117">的語句清單 `trap` 可以包含多個條件或函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="d20f6-117">The statement list of the `trap` can include multiple conditions or function calls.</span></span> <span data-ttu-id="d20f6-118">`trap`可以撰寫記錄檔、測試條件，或甚至執行另一個程式。</span><span class="sxs-lookup"><span data-stu-id="d20f6-118">A `trap` can write logs, test conditions, or even run another program.</span></span>

### <a name="syntax"></a><span data-ttu-id="d20f6-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="d20f6-119">Syntax</span></span>

<span data-ttu-id="d20f6-120">`trap`語句具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="d20f6-120">The `trap` statement has the following syntax:</span></span>

```powershell
trap [[<error type>]] {<statement list>}
```

<span data-ttu-id="d20f6-121">`trap`語句包含終止錯誤發生時要執行的語句清單。</span><span class="sxs-lookup"><span data-stu-id="d20f6-121">The `trap` statement includes a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="d20f6-122">`trap`語句是由 `trap` 關鍵字（選擇性地接著型別運算式），以及包含在發生錯誤時所要執行之語句清單的語句區塊所組成。</span><span class="sxs-lookup"><span data-stu-id="d20f6-122">A `trap` statement consists of the `trap` keyword, optionally followed by a type expression, and the statement block containing the list of statements to run when an error is trapped.</span></span> <span data-ttu-id="d20f6-123">型別運算式會調整捕捉的錯誤類型 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-123">The type expression refines the types of errors the `trap` catches.</span></span>

<span data-ttu-id="d20f6-124">腳本或命令可以有多個 `trap` 語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-124">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="d20f6-125">`trap` 語句可以出現在腳本或命令中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="d20f6-125">`trap` statements can appear anywhere in the script or command.</span></span>

### <a name="trapping-all-terminating-errors"></a><span data-ttu-id="d20f6-126">將所有終止錯誤全部捕獲</span><span class="sxs-lookup"><span data-stu-id="d20f6-126">Trapping all terminating errors</span></span>

<span data-ttu-id="d20f6-127">當在腳本或命令中未以另一種方式處理的終止錯誤發生時，PowerShell 會檢查 `trap` 處理錯誤的語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-127">When a terminating error occurs that is not handled in another way in a script or command, PowerShell checks for a `trap` statement that handles the error.</span></span> <span data-ttu-id="d20f6-128">如果有 `trap` 語句，則 PowerShell 會繼續執行語句中的腳本或命令 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-128">If a `trap` statement is present, PowerShell continues running the script or command in the `trap` statement.</span></span>

<span data-ttu-id="d20f6-129">下列範例是非常簡單的 `trap` 語句：</span><span class="sxs-lookup"><span data-stu-id="d20f6-129">The following example is a very simple `trap` statement:</span></span>

```powershell
trap {"Error found."}
```

<span data-ttu-id="d20f6-130">此 `trap` 語句會捕捉任何終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-130">This `trap` statement traps any terminating error.</span></span>

<span data-ttu-id="d20f6-131">在下列範例中，函式包含會造成執行階段錯誤的不實用字串。</span><span class="sxs-lookup"><span data-stu-id="d20f6-131">In the following example, the function includes a nonsense string that causes a runtime error.</span></span>

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="d20f6-132">執行此函數會傳回下列各項：</span><span class="sxs-lookup"><span data-stu-id="d20f6-132">Running this function returns the following:</span></span>

```Output
Error found.
nonsenseString : The term 'nonsenseString' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:3 char:5
+     nonsenseString
+     ~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (nonsenseString:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="d20f6-133">下列範例包含 `trap` 使用自動變數顯示錯誤的語句 `$_` ：</span><span class="sxs-lookup"><span data-stu-id="d20f6-133">The following example includes a `trap` statement that displays the error by using the `$_` automatic variable:</span></span>

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="d20f6-134">執行此版本的函式會傳回下列各項：</span><span class="sxs-lookup"><span data-stu-id="d20f6-134">Running this version of the function returns the following:</span></span>

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
nonsenseString : The term 'nonsenseString' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:3 char:5
+     nonsenseString
+     ~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (nonsenseString:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

> [!IMPORTANT]
> <span data-ttu-id="d20f6-135">`trap` 語句可以定義于指定範圍內的任何位置，但一律會套用至該範圍內的所有語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-135">`trap` statements may be defined anywhere within a given scope, but always apply to all statements in that scope.</span></span> <span data-ttu-id="d20f6-136">在執行時間， `trap` 區塊中的語句會在執行任何其他語句之前定義。</span><span class="sxs-lookup"><span data-stu-id="d20f6-136">At runtime, `trap` statements in a block are defined before any other statements are executed.</span></span> <span data-ttu-id="d20f6-137">在 JavaScript 中，這就是所謂的 [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)。</span><span class="sxs-lookup"><span data-stu-id="d20f6-137">In JavaScript, this is known as [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting).</span></span> <span data-ttu-id="d20f6-138">這表示語句會套用 `trap` 至該區塊中的所有語句，即使執行尚未事先定義的時間點也一樣。</span><span class="sxs-lookup"><span data-stu-id="d20f6-138">This means that `trap` statements apply to all statements in that block even if execution has not advanced past the point at which they are defined.</span></span> <span data-ttu-id="d20f6-139">例如， `trap` 在腳本結尾定義，並在第一個語句中擲回錯誤，仍然會觸發該 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-139">For example, defining a `trap` at the end of a script and throwing an error in the first statement still triggers that `trap`.</span></span>

### <a name="trapping-specific-errors"></a><span data-ttu-id="d20f6-140">捕捉特定錯誤</span><span class="sxs-lookup"><span data-stu-id="d20f6-140">Trapping specific errors</span></span>

<span data-ttu-id="d20f6-141">腳本或命令可以有多個 `trap` 語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-141">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="d20f6-142">`trap`可以定義來處理特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-142">A `trap` can be defined to handle specific errors.</span></span>

<span data-ttu-id="d20f6-143">下列範例是會將 `trap` 特定錯誤 **system.management.automation.commandnotfoundexception** 陷阱的語句：</span><span class="sxs-lookup"><span data-stu-id="d20f6-143">The following example is a `trap` statement that traps the specific error **CommandNotFoundException** :</span></span>

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

<span data-ttu-id="d20f6-144">當函數或腳本遇到不符合已知命令的字串時，此語句會顯示「命令錯誤被攔截」 `trap` 字串。</span><span class="sxs-lookup"><span data-stu-id="d20f6-144">When a function or script encounters a string that does not match a known command, this `trap` statement displays the "Command error trapped" string.</span></span>
<span data-ttu-id="d20f6-145">執行 `trap` 語句清單之後，PowerShell 會將錯誤物件寫入錯誤資料流程，然後繼續執行腳本。</span><span class="sxs-lookup"><span data-stu-id="d20f6-145">After running the `trap` statement list, PowerShell writes the error object to the error stream and then continues the script.</span></span>

<span data-ttu-id="d20f6-146">PowerShell 使用 .NET 例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="d20f6-146">PowerShell uses .NET exception types.</span></span> <span data-ttu-id="d20f6-147">下列範例會指定 **system.object** 錯誤類型：</span><span class="sxs-lookup"><span data-stu-id="d20f6-147">The following example specifies the **System.Exception** error type:</span></span>

```powershell
trap [System.Exception] {"An error trapped"}
```

<span data-ttu-id="d20f6-148">**System.management.automation.commandnotfoundexception** **錯誤類型繼承自 system.string 類型。**</span><span class="sxs-lookup"><span data-stu-id="d20f6-148">The **CommandNotFoundException** error type inherits from the **System.Exception** type.</span></span> <span data-ttu-id="d20f6-149">此語句會攔截由未知命令所建立的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-149">This statement traps an error that is created by an unknown command.</span></span> <span data-ttu-id="d20f6-150">它也會捕捉其他錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="d20f6-150">It also traps other error types.</span></span>

<span data-ttu-id="d20f6-151">腳本中可以有一個以上的 `trap` 語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-151">You can have more than one `trap` statement in a script.</span></span> <span data-ttu-id="d20f6-152">每個錯誤類型只能由一個語句來攔截 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-152">Each error type can be trapped by only one `trap` statement.</span></span> <span data-ttu-id="d20f6-153">當結束錯誤發生時，PowerShell 會搜尋 `trap` 具有最特定相符的，從目前的執行範圍開始。</span><span class="sxs-lookup"><span data-stu-id="d20f6-153">When a terminating error occurs, PowerShell searches for the `trap` with the most specific match, starting in the current scope of execution.</span></span>

<span data-ttu-id="d20f6-154">下列腳本範例包含錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-154">The following script example contains an error.</span></span> <span data-ttu-id="d20f6-155">腳本包含的一般 `trap` 語句會將任何終止錯誤和 `trap` 指定 **system.management.automation.commandnotfoundexception** 類型的特定語句進行陷阱。</span><span class="sxs-lookup"><span data-stu-id="d20f6-155">The script includes a general `trap` statement that traps any terminating error and a specific `trap` statement that specifies the **CommandNotFoundException** type.</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

<span data-ttu-id="d20f6-156">執行此腳本會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="d20f6-156">Running this script produces the following result:</span></span>

```Output
Command error trapped
nonsenseString : The term 'nonsenseString' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At C:\Temp\traptest.ps1:5 char:1
+ nonsenseString
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (nonsenseString:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="d20f6-157">因為 PowerShell 無法辨識 "nonsenseString" 作為 Cmdlet 或其他專案，所以會傳回 **system.management.automation.commandnotfoundexception** 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-157">Because PowerShell does not recognize "nonsenseString" as a cmdlet or other item, it returns a **CommandNotFoundException** error.</span></span> <span data-ttu-id="d20f6-158">特定語句會攔截這個終止錯誤 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-158">This terminating error is trapped by the specific `trap` statement.</span></span>

<span data-ttu-id="d20f6-159">下列腳本範例包含 `trap` 具有不同錯誤的相同語句：</span><span class="sxs-lookup"><span data-stu-id="d20f6-159">The following script example contains the same `trap` statements with a different error:</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

<span data-ttu-id="d20f6-160">執行此腳本會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="d20f6-160">Running this script produces the following result:</span></span>

```Output
Attempted to divide by zero.
At C:\temp\traptest.ps1:4 char:1
+ 1/$null
+ ~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], RuntimeException
    + FullyQualifiedErrorId : RuntimeException
```

<span data-ttu-id="d20f6-161">嘗試零除不會產生 **system.management.automation.commandnotfoundexception** 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-161">The attempt to divide by zero does not create a **CommandNotFoundException** error.</span></span> <span data-ttu-id="d20f6-162">相反地，這個錯誤會被另一個語句所攔截，而此語句會攔截 `trap` 任何終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-162">Instead, that error is trapped by the other `trap` statement, which traps any terminating error.</span></span>

### <a name="trapping-errors-and-scope"></a><span data-ttu-id="d20f6-163">陷印錯誤和範圍</span><span class="sxs-lookup"><span data-stu-id="d20f6-163">Trapping errors and scope</span></span>

<span data-ttu-id="d20f6-164">如果終止錯誤發生在與語句相同的範圍中 `trap` ，則 PowerShell 會執行所定義的語句清單 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-164">If a terminating error occurs in the same scope as the `trap` statement, PowerShell runs the list of statements defined by the `trap`.</span></span> <span data-ttu-id="d20f6-165">執行會在錯誤之後的語句繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d20f6-165">Execution continues at the statement after the error.</span></span> <span data-ttu-id="d20f6-166">如果 `trap` 語句與錯誤的範圍不同，則會在與語句相同範圍中的下一個語句繼續執行 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-166">If the `trap` statement is in a different scope from the error, execution continues at the next statement that is in the same scope as the `trap` statement.</span></span>

<span data-ttu-id="d20f6-167">例如，如果函式中發生錯誤，且 `trap` 語句在函式中，則腳本會繼續執行下一個語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-167">For example, if an error occurs in a function, and the `trap` statement is in the function, the script continues at the next statement.</span></span> <span data-ttu-id="d20f6-168">下列腳本包含錯誤和 `trap` 語句：</span><span class="sxs-lookup"><span data-stu-id="d20f6-168">The following script contains an error and a `trap` statement:</span></span>

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

<span data-ttu-id="d20f6-169">執行此腳本會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="d20f6-169">Running this script produces the following result:</span></span>

```Output
An error:
NonsenseString : The term 'NonsenseString' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:3 char:5
+     NonsenseString
+     ~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (NonsenseString:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

function1 was completed
```

<span data-ttu-id="d20f6-170">`trap`函數中的語句會攔截錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-170">The `trap` statement in the function traps the error.</span></span> <span data-ttu-id="d20f6-171">顯示訊息之後，PowerShell 會繼續執行函式。</span><span class="sxs-lookup"><span data-stu-id="d20f6-171">After displaying the message, PowerShell resumes running the function.</span></span> <span data-ttu-id="d20f6-172">請注意， `Function1` 已完成。</span><span class="sxs-lookup"><span data-stu-id="d20f6-172">Note that `Function1` was completed.</span></span>

<span data-ttu-id="d20f6-173">將這個範例與下列範例（具有相同的錯誤和語句）進行比較 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-173">Compare this with the following example, which has the same error and `trap` statement.</span></span> <span data-ttu-id="d20f6-174">在此範例中， `trap` 語句會出現在函式之外：</span><span class="sxs-lookup"><span data-stu-id="d20f6-174">In this example, the `trap` statement occurs outside the function:</span></span>

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

<span data-ttu-id="d20f6-175">`Function2`執行函數會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="d20f6-175">Running the `Function2` function produces the following result:</span></span>

```Output
An error:
NonsenseString : The term 'NonsenseString' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At C:\temp\traptest.ps1:2 char:5
+     NonsenseString
+     ~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (NonsenseString:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="d20f6-176">在此範例中，「function2 已完成」命令未執行。</span><span class="sxs-lookup"><span data-stu-id="d20f6-176">In this example, the "function2 was completed" command was not run.</span></span> <span data-ttu-id="d20f6-177">在這兩個範例中，函式內都會發生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-177">In both examples, the terminating error occurs within the function.</span></span> <span data-ttu-id="d20f6-178">不過，在這個範例中， `trap` 語句是在函式之外。</span><span class="sxs-lookup"><span data-stu-id="d20f6-178">In this example, however, the `trap` statement is outside the function.</span></span> <span data-ttu-id="d20f6-179">PowerShell 不會在語句執行之後回到函式 `trap` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-179">PowerShell does not go back into the function after the `trap` statement runs.</span></span>

> [!CAUTION]
> <span data-ttu-id="d20f6-180">針對相同的錯誤狀況定義多個陷阱時， `trap` 會使用範圍) 中第一個定義的詞法 (最高。</span><span class="sxs-lookup"><span data-stu-id="d20f6-180">When multiple traps are defined for the same error condition, the first `trap` defined lexically (highest in the scope) is used.</span></span>

<span data-ttu-id="d20f6-181">在下列範例中，只 `trap` 會執行 "唉啊 1"。</span><span class="sxs-lookup"><span data-stu-id="d20f6-181">In the following example, only the `trap` with "whoops 1" is run.</span></span>

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> <span data-ttu-id="d20f6-182">Trap 語句的範圍設定為編譯的位置。</span><span class="sxs-lookup"><span data-stu-id="d20f6-182">A Trap statement is scoped to where it compiles.</span></span> <span data-ttu-id="d20f6-183">如果您在函式 `trap` 或點式的來源腳本內有語句，則當函式或點出的腳本結束時，內的所有 `trap` 語句都會被移除。</span><span class="sxs-lookup"><span data-stu-id="d20f6-183">If you have a `trap` statement inside a function or dot sourced script, when the function or dot sourced script exits, all `trap` statements inside are removed.</span></span>

### <a name="using-the-break-and-continue-keywords"></a><span data-ttu-id="d20f6-184">使用 break 和 continue 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d20f6-184">Using the break and continue keywords</span></span>

<span data-ttu-id="d20f6-185">您可以 `break` `continue` 在語句中使用和關鍵字 `trap` ，判斷腳本或命令是否會在終止錯誤之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d20f6-185">You can use the `break` and `continue` keywords in a `trap` statement to determine whether a script or command continues to run after a terminating error.</span></span>

<span data-ttu-id="d20f6-186">如果您 `break` 在語句清單中包含語句 `trap` ，則 PowerShell 會停止函數或腳本。</span><span class="sxs-lookup"><span data-stu-id="d20f6-186">If you include a `break` statement in a `trap` statement list, PowerShell stops the function or script.</span></span> <span data-ttu-id="d20f6-187">下列範例函數會 `break` 在語句中使用關鍵字 `trap` ：</span><span class="sxs-lookup"><span data-stu-id="d20f6-187">The following sample function uses the `break` keyword in a `trap` statement:</span></span>

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
Attempted to divide by zero.
At line:6 char:5
+     1/$null
+     ~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RuntimeException
```

<span data-ttu-id="d20f6-188">因為 `trap` 語句包含關鍵字，所以函式不 `break` 會繼續執行，且不會執行「函式已完成」行。</span><span class="sxs-lookup"><span data-stu-id="d20f6-188">Because the `trap` statement included the `break` keyword, the function does not continue to run, and the "Function completed" line is not run.</span></span>

<span data-ttu-id="d20f6-189">如果您 `continue` 在語句中包含關鍵字 `trap` ，PowerShell 會在造成錯誤的語句之後繼續執行，就如同沒有或一樣 `break` `continue` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-189">If you include a `continue` keyword in a `trap` statement, PowerShell resumes after the statement that caused the error, just as it would without `break` or `continue`.</span></span> <span data-ttu-id="d20f6-190">`continue`不過，使用關鍵字時，PowerShell 不會將錯誤寫入錯誤串流。</span><span class="sxs-lookup"><span data-stu-id="d20f6-190">With the `continue` keyword, however, PowerShell does not write an error to the error stream.</span></span>

<span data-ttu-id="d20f6-191">下列範例函數會 `continue` 在語句中使用關鍵字 `trap` ：</span><span class="sxs-lookup"><span data-stu-id="d20f6-191">The following sample function uses the `continue` keyword in a `trap` statement:</span></span>

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

<span data-ttu-id="d20f6-192">函數會在攔截到錯誤之後繼續執行，並執行 "Function completed" 語句。</span><span class="sxs-lookup"><span data-stu-id="d20f6-192">The function resumes after the error is trapped, and the "Function completed" statement runs.</span></span> <span data-ttu-id="d20f6-193">錯誤資料流程未寫入錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-193">No error is written to the error stream.</span></span>

## <a name="notes"></a><span data-ttu-id="d20f6-194">備忘稿</span><span class="sxs-lookup"><span data-stu-id="d20f6-194">Notes</span></span>

<span data-ttu-id="d20f6-195">`trap` 語句提供了一種簡單的方式，可廣泛確保處理範圍內的所有終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d20f6-195">`trap` statements provide a simple way to broadly ensure all terminating errors within a scope are handled.</span></span> <span data-ttu-id="d20f6-196">如需更細微的錯誤處理，請使用使用 `try` / `catch` 語句定義陷阱的區塊 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-196">For more finer-grained error handling, use `try`/`catch` blocks where traps are defined using `catch` statements.</span></span> <span data-ttu-id="d20f6-197">`catch`語句只適用于相關語句內的程式碼 `try` 。</span><span class="sxs-lookup"><span data-stu-id="d20f6-197">The `catch` statements only apply to the code inside the associated `try` statement.</span></span> <span data-ttu-id="d20f6-198">如需詳細資訊，請參閱 [about_Try_Catch_Finally](about_Try_Catch_Finally.md)。</span><span class="sxs-lookup"><span data-stu-id="d20f6-198">For more information, see [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d20f6-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d20f6-199">See also</span></span>

[<span data-ttu-id="d20f6-200">about_Break</span><span class="sxs-lookup"><span data-stu-id="d20f6-200">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="d20f6-201">about_Continue</span><span class="sxs-lookup"><span data-stu-id="d20f6-201">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="d20f6-202">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="d20f6-202">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="d20f6-203">about_Throw</span><span class="sxs-lookup"><span data-stu-id="d20f6-203">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="d20f6-204">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="d20f6-204">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
