---
ms.date: 06/09/2020
ms.topic: reference
title: 註解型說明關鍵字
description: 註解型說明關鍵字
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645465"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="f6703-103">註解型說明關鍵字</span><span class="sxs-lookup"><span data-stu-id="f6703-103">Comment-Based Help Keywords</span></span>

<span data-ttu-id="f6703-104">本主題會列出並描述以批註為基礎的說明中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-104">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="f6703-105">Comment-Based 說明中的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f6703-105">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="f6703-106">以下是以批註為基礎的有效說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-106">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="f6703-107">這些清單會依照它們一般出現在說明主題中的順序列出，以及其預期的用途。</span><span class="sxs-lookup"><span data-stu-id="f6703-107">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="f6703-108">這些關鍵字在批註式說明中可依任何順序出現，而且不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f6703-108">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="f6703-109">請注意， `.EXTERNALHELP` 關鍵字優先于所有其他以批註為基礎的說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-109">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="f6703-110">當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也是如此。</span><span class="sxs-lookup"><span data-stu-id="f6703-110">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6703-111">.簡介</span><span class="sxs-lookup"><span data-stu-id="f6703-111">.SYNOPSIS</span></span>

<span data-ttu-id="f6703-112">函數或腳本的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-112">A brief description of the function or script.</span></span> <span data-ttu-id="f6703-113">在每個主題中，這個關鍵字只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="f6703-113">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="f6703-114">.描述</span><span class="sxs-lookup"><span data-stu-id="f6703-114">.DESCRIPTION</span></span>

<span data-ttu-id="f6703-115">函數或腳本的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-115">A detailed description of the function or script.</span></span> <span data-ttu-id="f6703-116">在每個主題中，這個關鍵字只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="f6703-116">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="f6703-117">.參數 \<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="f6703-117">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="f6703-118">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-118">The description of a parameter.</span></span> <span data-ttu-id="f6703-119">您可以 `.PARAMETER` 針對函數或腳本中的每個參數包含關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-119">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="f6703-120">`.PARAMETER`關鍵字可以依任何順序出現在批註區塊中，但參數出現在 `Param` 語句或函式宣告中的順序會決定參數在說明主題中的出現順序。</span><span class="sxs-lookup"><span data-stu-id="f6703-120">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="f6703-121">若要變更說明主題中參數的順序，請變更 `Param` 語句或函式宣告中參數的順序。</span><span class="sxs-lookup"><span data-stu-id="f6703-121">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="f6703-122">您也可以將批註放在 `Param` 參數變數名稱之前的語句中，以指定參數描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-122">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="f6703-123">如果您同時使用 `Param` 語句批註和 `.PARAMETER` 關鍵字，則會使用與關鍵字相關聯的描述 `.PARAMETER` ，而 `Param` 語句批註會被忽略。</span><span class="sxs-lookup"><span data-stu-id="f6703-123">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="f6703-124">.例子</span><span class="sxs-lookup"><span data-stu-id="f6703-124">.EXAMPLE</span></span>

<span data-ttu-id="f6703-125">使用函數或腳本的範例命令，選擇性地接著範例輸出和描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-125">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="f6703-126">針對每個範例重複此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-126">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="f6703-127">.輸入</span><span class="sxs-lookup"><span data-stu-id="f6703-127">.INPUTS</span></span>

<span data-ttu-id="f6703-128">Microsoft .NET Framework 可輸送至函式或腳本的物件類型。</span><span class="sxs-lookup"><span data-stu-id="f6703-128">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="f6703-129">您也可以包含輸入物件的描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-129">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="f6703-130">.輸出</span><span class="sxs-lookup"><span data-stu-id="f6703-130">.OUTPUTS</span></span>

<span data-ttu-id="f6703-131">Cmdlet 傳回之物件的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="f6703-131">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="f6703-132">您也可以包含所傳回物件的描述。</span><span class="sxs-lookup"><span data-stu-id="f6703-132">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="f6703-133">.筆記</span><span class="sxs-lookup"><span data-stu-id="f6703-133">.NOTES</span></span>

<span data-ttu-id="f6703-134">函數或腳本的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f6703-134">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="f6703-135">.連結</span><span class="sxs-lookup"><span data-stu-id="f6703-135">.LINK</span></span>

<span data-ttu-id="f6703-136">相關主題的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6703-136">The name of a related topic.</span></span> <span data-ttu-id="f6703-137">針對每個相關主題重複此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-137">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="f6703-138">此內容會顯示在說明主題的 [相關連結] 區段中。</span><span class="sxs-lookup"><span data-stu-id="f6703-138">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="f6703-139">`.LINK`關鍵字內容也可以包含統一資源識別項 (URI) 至相同說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="f6703-139">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="f6703-140">當您使用的參數時，就會開啟線上版本 `Online` `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-140">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="f6703-141">URI 的開頭必須是 "HTTP" 或 "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="f6703-141">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="f6703-142">.元件</span><span class="sxs-lookup"><span data-stu-id="f6703-142">.COMPONENT</span></span>

<span data-ttu-id="f6703-143">函數或腳本所使用的技術或功能名稱，或其相關的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6703-143">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="f6703-144">的 **元件** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-144">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="f6703-145">.作用</span><span class="sxs-lookup"><span data-stu-id="f6703-145">.Role</span></span>

<span data-ttu-id="f6703-146">說明主題的使用者角色名稱。</span><span class="sxs-lookup"><span data-stu-id="f6703-146">The name of the user role for the help topic.</span></span> <span data-ttu-id="f6703-147">的 **Role** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-147">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="f6703-148">.功能</span><span class="sxs-lookup"><span data-stu-id="f6703-148">.FUNCTIONALITY</span></span>

<span data-ttu-id="f6703-149">描述函式用途的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-149">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="f6703-150">的 **功能** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-150">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="f6703-151">.FORWARDHELPTARGETNAME \<Command-Name></span><span class="sxs-lookup"><span data-stu-id="f6703-151">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="f6703-152">重新導向至指定命令的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f6703-152">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="f6703-153">您可以將使用者重新導向至任何說明主題，包括函數、腳本、Cmdlet 或提供者的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f6703-153">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="f6703-154">.FORWARDHELPCATEGORY \<Category></span><span class="sxs-lookup"><span data-stu-id="f6703-154">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="f6703-155">指定中專案的 [說明] 類別 `.FORWARDHELPTARGETNAME` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-155">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="f6703-156">使用這個關鍵字可避免在具有相同名稱的命令時產生衝突。</span><span class="sxs-lookup"><span data-stu-id="f6703-156">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="f6703-157">有效值為：</span><span class="sxs-lookup"><span data-stu-id="f6703-157">Valid values are:</span></span>

- <span data-ttu-id="f6703-158">Alias</span><span class="sxs-lookup"><span data-stu-id="f6703-158">Alias</span></span>
- <span data-ttu-id="f6703-159">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6703-159">Cmdlet</span></span>
- <span data-ttu-id="f6703-160">HelpFile</span><span class="sxs-lookup"><span data-stu-id="f6703-160">HelpFile</span></span>
- <span data-ttu-id="f6703-161">函式</span><span class="sxs-lookup"><span data-stu-id="f6703-161">Function</span></span>
- <span data-ttu-id="f6703-162">提供者</span><span class="sxs-lookup"><span data-stu-id="f6703-162">Provider</span></span>
- <span data-ttu-id="f6703-163">一般</span><span class="sxs-lookup"><span data-stu-id="f6703-163">General</span></span>
- <span data-ttu-id="f6703-164">常見問題集</span><span class="sxs-lookup"><span data-stu-id="f6703-164">FAQ</span></span>
- <span data-ttu-id="f6703-165">詞彙</span><span class="sxs-lookup"><span data-stu-id="f6703-165">Glossary</span></span>
- <span data-ttu-id="f6703-166">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="f6703-166">ScriptCommand</span></span>
- <span data-ttu-id="f6703-167">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="f6703-167">ExternalScript</span></span>
- <span data-ttu-id="f6703-168">篩選</span><span class="sxs-lookup"><span data-stu-id="f6703-168">Filter</span></span>
- <span data-ttu-id="f6703-169">全部</span><span class="sxs-lookup"><span data-stu-id="f6703-169">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="f6703-170">.REMOTEHELPRUNSPACE \<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="f6703-170">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="f6703-171">指定包含說明主題的會話。</span><span class="sxs-lookup"><span data-stu-id="f6703-171">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="f6703-172">輸入包含 PSSession 的變數。</span><span class="sxs-lookup"><span data-stu-id="f6703-172">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="f6703-173">Cmdlet 會使用這個關鍵字 `Export-PSSession` 來尋找匯出命令的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f6703-173">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="f6703-174">..EXTERNALHELP \<XML Help File></span><span class="sxs-lookup"><span data-stu-id="f6703-174">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="f6703-175">指定腳本或函式之 XML 架構說明檔的路徑和（或）名稱。</span><span class="sxs-lookup"><span data-stu-id="f6703-175">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="f6703-176">`.EXTERNALHELP`關鍵字會告訴[GetHelpCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand)程式，以取得以 XML 為基礎之檔案中的腳本或函數的說明。</span><span class="sxs-lookup"><span data-stu-id="f6703-176">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="f6703-177">`.EXTERNALHELP`針對腳本或函式使用以 XML 為基礎的說明檔時，需要關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-177">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="f6703-178">如果沒有它， `Get-Help` 就不會找到函數或腳本的說明檔。</span><span class="sxs-lookup"><span data-stu-id="f6703-178">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="f6703-179">`.EXTERNALHELP`關鍵字優先于所有其他以批註為基礎的說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f6703-179">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="f6703-180">當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也是如此。</span><span class="sxs-lookup"><span data-stu-id="f6703-180">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="f6703-181">當腳本模組匯出函式時，的值 `.EXTERNALHELP` 應該是沒有路徑的檔案名。</span><span class="sxs-lookup"><span data-stu-id="f6703-181">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="f6703-182">`Get-Help` 在模組目錄的地區設定特定子目錄中尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="f6703-182">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="f6703-183">檔案名沒有任何需求，但最佳做法是使用下列檔案名格式： `<ScriptModule>.psm1-help.xml` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-183">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="f6703-184">當函數未與模組相關聯時，請在關鍵字的值中包含路徑和檔案名 `.EXTERNALHELP` 。</span><span class="sxs-lookup"><span data-stu-id="f6703-184">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="f6703-185">如果 XML 檔案的指定路徑包含 UI 文化特性特定的子目錄，則 `Get-Help` 會以遞迴方式在子目錄中搜尋具有腳本或函式名稱的 xml 檔案，就像是針對所有以 XML 為基礎的說明主題所建立的語言回溯標準一樣。</span><span class="sxs-lookup"><span data-stu-id="f6703-185">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="f6703-186">如需有關 Cmdlet 說明 XML 架構說明檔格式的詳細資訊，請參閱 [撰寫 Windows PowerShell Cmdlet](./writing-help-for-windows-powershell-cmdlets.md)說明。</span><span class="sxs-lookup"><span data-stu-id="f6703-186">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
