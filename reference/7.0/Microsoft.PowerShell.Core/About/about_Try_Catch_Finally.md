---
description: 描述如何使用 `Try` 、 `Catch` 和 `Finally` 區塊來處理終止錯誤。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: 1bb6974e1ba42861a4f411777be237685d2becbc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206551"
---
# <a name="about-try-catch-finally"></a><span data-ttu-id="33a94-104">關於 Try Catch Finally</span><span class="sxs-lookup"><span data-stu-id="33a94-104">About Try Catch Finally</span></span>

## <a name="short-description"></a><span data-ttu-id="33a94-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="33a94-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="33a94-106">描述如何使用 `Try` 、 `Catch` 和 `Finally` 區塊來處理終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-106">Describes how to use the `Try`, `Catch`, and `Finally` blocks to handle terminating errors.</span></span>

## <a name="long-description"></a><span data-ttu-id="33a94-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="33a94-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="33a94-108">使用 `Try` 、 `Catch` 和 `Finally` 區塊來回應或處理腳本中的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-108">Use `Try`, `Catch`, and `Finally` blocks to respond to or handle terminating errors in scripts.</span></span> <span data-ttu-id="33a94-109">`Trap`語句也可以用來處理腳本中的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-109">The `Trap` statement can also be used to handle terminating errors in scripts.</span></span> <span data-ttu-id="33a94-110">如需詳細資訊，請參閱 [about_Trap](about_Trap.md)。</span><span class="sxs-lookup"><span data-stu-id="33a94-110">For more information, see [about_Trap](about_Trap.md).</span></span>

<span data-ttu-id="33a94-111">終止錯誤會停止執行語句。</span><span class="sxs-lookup"><span data-stu-id="33a94-111">A terminating error stops a statement from running.</span></span> <span data-ttu-id="33a94-112">如果 PowerShell 沒有以某種方式處理終止錯誤，PowerShell 也會停止使用目前的管線來執行函式或腳本。</span><span class="sxs-lookup"><span data-stu-id="33a94-112">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script using the current pipeline.</span></span> <span data-ttu-id="33a94-113">在其他語言中（例如 C \# ），終止錯誤稱為例外狀況。</span><span class="sxs-lookup"><span data-stu-id="33a94-113">In other languages, such as C\#, terminating errors are referred to as exceptions.</span></span>

<span data-ttu-id="33a94-114">使用 `Try` 區塊來定義腳本的區段，讓 PowerShell 監視錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-114">Use the `Try` block to define a section of a script in which you want PowerShell to monitor for errors.</span></span> <span data-ttu-id="33a94-115">當區塊內發生錯誤時 `Try` ，會先將錯誤儲存至 `$Error` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="33a94-115">When an error occurs within the `Try` block, the error is first saved to the `$Error` automatic variable.</span></span> <span data-ttu-id="33a94-116">PowerShell 接著會搜尋 `Catch` 區塊以處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-116">PowerShell then searches for a `Catch` block to handle the error.</span></span> <span data-ttu-id="33a94-117">如果 `Try` 語句沒有相符的 `Catch` 區塊，則 PowerShell 會繼續 `Catch` 在父範圍中搜尋適當的區塊或 `Trap` 語句。</span><span class="sxs-lookup"><span data-stu-id="33a94-117">If the `Try` statement does not have a matching `Catch` block, PowerShell continues to search for an appropriate `Catch` block or `Trap` statement in the parent scopes.</span></span> <span data-ttu-id="33a94-118">`Catch`區塊完成之後，或如果 `Catch` 找不到適當的區塊或 `Trap` 語句，則 `Finally` 會執行區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-118">After a `Catch` block is completed or if no appropriate `Catch` block or `Trap` statement is found, the `Finally` block is run.</span></span> <span data-ttu-id="33a94-119">如果無法處理錯誤，就會將錯誤寫入錯誤串流。</span><span class="sxs-lookup"><span data-stu-id="33a94-119">If the error cannot be handled, the error is written to the error stream.</span></span>

<span data-ttu-id="33a94-120">`Catch`區塊可以包含用來追蹤錯誤或復原預期腳本流程的命令。</span><span class="sxs-lookup"><span data-stu-id="33a94-120">A `Catch` block can include commands for tracking the error or for recovering the expected flow of the script.</span></span> <span data-ttu-id="33a94-121">`Catch`區塊可以指定它所攔截的錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="33a94-121">A `Catch` block can specify which error types it catches.</span></span> <span data-ttu-id="33a94-122">`Try`語句可以 `Catch` 針對不同種類的錯誤，包含多個區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-122">A `Try` statement can include multiple `Catch` blocks for different kinds of errors.</span></span>

<span data-ttu-id="33a94-123">`Finally`區塊可以用來釋放腳本不再需要的任何資源。</span><span class="sxs-lookup"><span data-stu-id="33a94-123">A `Finally` block can be used to free any resources that are no longer needed by your script.</span></span>

<span data-ttu-id="33a94-124">`Try`、 `Catch` 和 `Finally` 類似于 `Try` C 程式 `Catch` `Finally` 設計語言中使用的、和關鍵字 \# 。</span><span class="sxs-lookup"><span data-stu-id="33a94-124">`Try`, `Catch`, and `Finally` resemble the `Try`, `Catch`, and `Finally` keywords used in the C\# programming language.</span></span>

### <a name="syntax"></a><span data-ttu-id="33a94-125">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33a94-125">SYNTAX</span></span>

<span data-ttu-id="33a94-126">`Try`語句包含 `Try` 區塊、零個或多個 `Catch` 區塊，以及零或一個 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-126">A `Try` statement contains a `Try` block, zero or more `Catch` blocks, and zero or one `Finally` block.</span></span> <span data-ttu-id="33a94-127">`Try`語句至少必須有一個 `Catch` 區塊或一個 `Finally` 區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-127">A `Try` statement must have at least one `Catch` block or one `Finally` block.</span></span>

<span data-ttu-id="33a94-128">以下顯示 `Try` 區塊語法：</span><span class="sxs-lookup"><span data-stu-id="33a94-128">The following shows the `Try` block syntax:</span></span>

```powershell
try {<statement list>}
```

<span data-ttu-id="33a94-129">`Try`關鍵字後面接著以大括弧括住的語句清單。</span><span class="sxs-lookup"><span data-stu-id="33a94-129">The `Try` keyword is followed by a statement list in braces.</span></span> <span data-ttu-id="33a94-130">如果在執行語句清單中的語句時，發生終止錯誤，腳本會將錯誤物件從 `Try` 區塊傳遞到適當的 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-130">If a terminating error occurs while the statements in the statement list are being run, the script passes the error object from the `Try` block to an appropriate `Catch` block.</span></span>

<span data-ttu-id="33a94-131">以下顯示 `Catch` 區塊語法：</span><span class="sxs-lookup"><span data-stu-id="33a94-131">The following shows the `Catch` block syntax:</span></span>

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

<span data-ttu-id="33a94-132">錯誤類型會顯示在括弧中。</span><span class="sxs-lookup"><span data-stu-id="33a94-132">Error types appear in brackets.</span></span> <span data-ttu-id="33a94-133">最外層的括弧表示元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="33a94-133">The outermost brackets indicate the element is optional.</span></span>

<span data-ttu-id="33a94-134">`Catch`關鍵字後面接著選擇性的錯誤類型規格清單和語句清單。</span><span class="sxs-lookup"><span data-stu-id="33a94-134">The `Catch` keyword is followed by an optional list of error type specifications and a statement list.</span></span> <span data-ttu-id="33a94-135">如果區塊中發生終止錯誤 `Try` ，則 PowerShell 會搜尋適當的 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-135">If a terminating error occurs in the `Try` block, PowerShell searches for an appropriate `Catch` block.</span></span> <span data-ttu-id="33a94-136">如果找到一個，就 `Catch` 會執行區塊中的語句。</span><span class="sxs-lookup"><span data-stu-id="33a94-136">If one is found, the statements in the `Catch` block are executed.</span></span>

<span data-ttu-id="33a94-137">`Catch`區塊可以指定一或多個錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="33a94-137">The `Catch` block can specify one or more error types.</span></span> <span data-ttu-id="33a94-138">錯誤類型是 Microsoft .NET Framework 例外狀況或衍生自 .NET Framework 例外狀況的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="33a94-138">An error type is a Microsoft .NET Framework exception or an exception that is derived from a .NET Framework exception.</span></span> <span data-ttu-id="33a94-139">`Catch`區塊會處理指定之 .NET Framework 例外狀況類別或衍生自指定類別之任何類別的錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-139">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span>

<span data-ttu-id="33a94-140">如果 `Catch` 區塊指定錯誤類型，該區塊會 `Catch` 處理該錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="33a94-140">If a `Catch` block specifies an error type, that `Catch` block handles that type of error.</span></span> <span data-ttu-id="33a94-141">如果 `Catch` 區塊未指定錯誤類型，該 `Catch` 區塊會處理區塊中發生的任何錯誤 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-141">If a `Catch` block does not specify an error type, that `Catch` block handles any error encountered in the `Try` block.</span></span> <span data-ttu-id="33a94-142">`Try`語句可以 `Catch` 針對不同的指定錯誤類型包含多個區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-142">A `Try` statement can include multiple `Catch` blocks for the different specified error types.</span></span>

<span data-ttu-id="33a94-143">以下顯示 `Finally` 區塊語法：</span><span class="sxs-lookup"><span data-stu-id="33a94-143">The following shows the `Finally` block syntax:</span></span>

```powershell
finally {<statement list>}
```

<span data-ttu-id="33a94-144">`Finally`關鍵字後面接著會在每次執行腳本時執行的語句清單，即使執行的 `Try` 語句沒有錯誤或在語句中攔截到錯誤 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-144">The `Finally` keyword is followed by a statement list that runs every time the script is run, even if the `Try` statement ran without error or an error was caught in a `Catch` statement.</span></span>

<span data-ttu-id="33a94-145">請注意，按下<kbd>CTRL</kbd> + <kbd>C</kbd>會停止管線。</span><span class="sxs-lookup"><span data-stu-id="33a94-145">Note that pressing <kbd>CTRL</kbd>+<kbd>C</kbd> stops the pipeline.</span></span> <span data-ttu-id="33a94-146">傳送至管線的物件將不會顯示為輸出。</span><span class="sxs-lookup"><span data-stu-id="33a94-146">Objects that are sent to the pipeline will not be displayed as output.</span></span> <span data-ttu-id="33a94-147">因此，如果您包含要顯示的語句，例如 "Finally block run"，就不會在您按下<kbd>CTRL</kbd>C 之後顯示它，即使區塊已執行也一樣 + <kbd>C</kbd> `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-147">Therefore, if you include a statement to be displayed, such as "Finally block has run", it will not be displayed after you press <kbd>CTRL</kbd>+<kbd>C</kbd>, even if the `Finally` block ran.</span></span>

### <a name="catching-errors"></a><span data-ttu-id="33a94-148">捕捉錯誤</span><span class="sxs-lookup"><span data-stu-id="33a94-148">CATCHING ERRORS</span></span>

<span data-ttu-id="33a94-149">下列範例腳本會顯示 `Try` 具有區塊的區塊 `Catch` ：</span><span class="sxs-lookup"><span data-stu-id="33a94-149">The following sample script shows a `Try` block with a `Catch` block:</span></span>

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

<span data-ttu-id="33a94-150">`Catch`關鍵字必須緊接在 `Try` 區塊或另一個 `Catch` 區塊之後。</span><span class="sxs-lookup"><span data-stu-id="33a94-150">The `Catch` keyword must immediately follow the `Try` block or another `Catch` block.</span></span>

<span data-ttu-id="33a94-151">PowerShell 無法將 "NonsenseString" 辨識為 Cmdlet 或其他專案。</span><span class="sxs-lookup"><span data-stu-id="33a94-151">PowerShell does not recognize "NonsenseString" as a cmdlet or other item.</span></span>
<span data-ttu-id="33a94-152">執行此腳本會傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="33a94-152">Running this script returns the following result:</span></span>

```powershell
An error occurred.
```

<span data-ttu-id="33a94-153">當腳本遇到 "NonsenseString" 時，會造成終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-153">When the script encounters "NonsenseString", it causes a terminating error.</span></span> <span data-ttu-id="33a94-154">區塊會執行 `Catch` 區塊內的語句清單，以處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-154">The `Catch` block handles the error by running the statement list inside the block.</span></span>

### <a name="using-multiple-catch-statements"></a><span data-ttu-id="33a94-155">使用多個 CATCH 語句</span><span class="sxs-lookup"><span data-stu-id="33a94-155">USING MULTIPLE CATCH STATEMENTS</span></span>

<span data-ttu-id="33a94-156">`Try`語句可以有任意數目的 `Catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-156">A `Try` statement can have any number of `Catch` blocks.</span></span> <span data-ttu-id="33a94-157">例如，下列腳本具有 `Try` 下載的區塊 `MyDoc.doc` ，其中包含兩個 `Catch` 區塊：</span><span class="sxs-lookup"><span data-stu-id="33a94-157">For example, the following script has a `Try` block that downloads `MyDoc.doc`, and it contains two `Catch` blocks:</span></span>

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

<span data-ttu-id="33a94-158">第一個 `Catch` 區塊會處理 **系統 WebException** 和 **IOException** 類型的錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-158">The first `Catch` block handles errors of the **System.Net.WebException** and **System.IO.IOException** types.</span></span> <span data-ttu-id="33a94-159">第二個 `Catch` 區塊未指定錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="33a94-159">The second `Catch` block does not specify an error type.</span></span> <span data-ttu-id="33a94-160">第二個 `Catch` 區塊會處理發生的任何其他終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-160">The second `Catch` block handles any other terminating errors that occur.</span></span>

<span data-ttu-id="33a94-161">PowerShell 會依繼承比對錯誤類型。</span><span class="sxs-lookup"><span data-stu-id="33a94-161">PowerShell matches error types by inheritance.</span></span> <span data-ttu-id="33a94-162">`Catch`區塊會處理指定之 .NET Framework 例外狀況類別或衍生自指定類別之任何類別的錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-162">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span> <span data-ttu-id="33a94-163">下列範例包含攔截「找 `Catch` 不到命令」錯誤的區塊：</span><span class="sxs-lookup"><span data-stu-id="33a94-163">The following example contains a `Catch` block that catches a "Command Not Found" error:</span></span>

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

<span data-ttu-id="33a94-164">指定的錯誤類型 **system.management.automation.commandnotfoundexception** 繼承自 **System.SystemException** 類型。</span><span class="sxs-lookup"><span data-stu-id="33a94-164">The specified error type, **CommandNotFoundException** , inherits from the **System.SystemException** type.</span></span> <span data-ttu-id="33a94-165">下列範例也會捕捉找不到命令錯誤：</span><span class="sxs-lookup"><span data-stu-id="33a94-165">The following example also catches a Command Not Found error:</span></span>

```powershell
catch [System.SystemException] {"Base Exception" }
```

<span data-ttu-id="33a94-166">此 `Catch` 區塊會處理「找不到命令」錯誤，以及繼承自 **SystemException** 類型的其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="33a94-166">This `Catch` block handles the "Command Not Found" error and other errors that inherit from the **SystemException** type.</span></span>

<span data-ttu-id="33a94-167">如果您指定 error 類別和它的其中一個衍生類別，請將 `Catch` 衍生類別的區塊放在 `Catch` 一般類別的區塊之前。</span><span class="sxs-lookup"><span data-stu-id="33a94-167">If you specify an error class and one of its derived classes, place the `Catch` block for the derived class before the `Catch` block for the general class.</span></span>

### <a name="using-traps-in-a-try-catch"></a><span data-ttu-id="33a94-168">在 Try Catch 中使用陷阱</span><span class="sxs-lookup"><span data-stu-id="33a94-168">Using Traps in a Try Catch</span></span>

<span data-ttu-id="33a94-169">在區塊中 `Try` 定義的區塊中發生終止錯誤 `Trap` `Try` ，即使有相符的 `Catch` 區塊， `Trap` 語句還是會取得控制權。</span><span class="sxs-lookup"><span data-stu-id="33a94-169">When a terminating error occurs in a `Try` block with a `Trap` defined within the `Try` block, even if there is a matching `Catch` block, the `Trap` statement takes control.</span></span>

<span data-ttu-id="33a94-170">如果 `Trap` 存在於較高的區塊 `Try` 中，而且 `Catch` 目前的範圍內沒有相符的區塊，則即使有 `Trap` 任何父範圍具有相符的區塊，也會取得控制權 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-170">If a `Trap` exists at a higher block than the `Try`, and there is no matching `Catch` block within the current scope, the `Trap` will take control, even if any parent scope has a matching `Catch` block.</span></span>

### <a name="accessing-exception-information"></a><span data-ttu-id="33a94-171">存取例外狀況資訊</span><span class="sxs-lookup"><span data-stu-id="33a94-171">ACCESSING EXCEPTION INFORMATION</span></span>

<span data-ttu-id="33a94-172">在 `Catch` 區塊內，可以使用來存取目前的錯誤 `$_` ，也就是所謂的 `$PSItem` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-172">Within a `Catch` block, the current error can be accessed using `$_`, which is also known as `$PSItem`.</span></span> <span data-ttu-id="33a94-173">物件的類型為 **ErrorRecord** 。</span><span class="sxs-lookup"><span data-stu-id="33a94-173">The object is of type **ErrorRecord** .</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

<span data-ttu-id="33a94-174">執行此腳本會傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="33a94-174">Running this script returns the following result:</span></span>

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

<span data-ttu-id="33a94-175">還有其他可以存取的屬性，例如 **ScriptStackTrace** 、 **Exception** 和 **ErrorDetails** 。</span><span class="sxs-lookup"><span data-stu-id="33a94-175">There are additional properties that can be accessed, such as **ScriptStackTrace** , **Exception** , and **ErrorDetails** .</span></span>  <span data-ttu-id="33a94-176">例如，如果我們將腳本變更為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="33a94-176">For example, if we change the script to the following:</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

<span data-ttu-id="33a94-177">結果會類似于：</span><span class="sxs-lookup"><span data-stu-id="33a94-177">The result will be similar to:</span></span>

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a><span data-ttu-id="33a94-178">使用 FINALLY 釋放資源</span><span class="sxs-lookup"><span data-stu-id="33a94-178">FREEING RESOURCES BY USING FINALLY</span></span>

<span data-ttu-id="33a94-179">若要釋放腳本所使用的資源，請在 `Finally` 和區塊之後加入區塊 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-179">To free resources used by a script, add a `Finally` block after the `Try` and `Catch` blocks.</span></span> <span data-ttu-id="33a94-180">`Finally`無論 `Try` 區塊是否遇到終止錯誤，區塊語句都會執行。</span><span class="sxs-lookup"><span data-stu-id="33a94-180">The `Finally` block statements run regardless of whether the `Try` block encounters a terminating error.</span></span> <span data-ttu-id="33a94-181">PowerShell 會在 `Finally` 腳本結束之前或目前區塊超出範圍之前執行區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-181">PowerShell runs the `Finally` block before the script terminates or before the current block goes out of scope.</span></span>

<span data-ttu-id="33a94-182">`Finally`即使您使用<kbd>CTRL</kbd> + <kbd>C</kbd>停止腳本，還是會執行區塊。</span><span class="sxs-lookup"><span data-stu-id="33a94-182">A `Finally` block runs even if you use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop the script.</span></span> <span data-ttu-id="33a94-183">`Finally`如果 Exit 關鍵字在區塊內停止腳本，也會執行區塊 `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="33a94-183">A `Finally` block also runs if an Exit keyword stops the script from within a `Catch` block.</span></span>

### <a name="see-also"></a><span data-ttu-id="33a94-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33a94-184">SEE ALSO</span></span>

[<span data-ttu-id="33a94-185">about_Break</span><span class="sxs-lookup"><span data-stu-id="33a94-185">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="33a94-186">about_Continue</span><span class="sxs-lookup"><span data-stu-id="33a94-186">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="33a94-187">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="33a94-187">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="33a94-188">about_Throw</span><span class="sxs-lookup"><span data-stu-id="33a94-188">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="33a94-189">about_Trap</span><span class="sxs-lookup"><span data-stu-id="33a94-189">about_Trap</span></span>](about_Trap.md)
