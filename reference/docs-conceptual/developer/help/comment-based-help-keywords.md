---
title: 註解型說明關鍵字
ms.date: 06/09/2020
ms.openlocfilehash: fb737c19d7b7f4d003af3ba36bb396bac52d94e7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893147"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="781f8-102">註解型說明關鍵字</span><span class="sxs-lookup"><span data-stu-id="781f8-102">Comment-Based Help Keywords</span></span>

<span data-ttu-id="781f8-103">本主題列出並描述以批註為基礎的說明中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-103">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="781f8-104">以批註為基礎的說明中的關鍵字</span><span class="sxs-lookup"><span data-stu-id="781f8-104">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="781f8-105">下列是以批註為基礎的有效說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-105">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="781f8-106">它們會依照其一般出現在說明主題中的順序來列出，以及其預期的用途。</span><span class="sxs-lookup"><span data-stu-id="781f8-106">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="781f8-107">這些關鍵字可以依任何順序出現在以批註為基礎的說明中，而且不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="781f8-107">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="781f8-108">請注意， `.EXTERNALHELP` 關鍵字的優先順序高於所有其他以批註為基礎的說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-108">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="781f8-109">當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也一樣。</span><span class="sxs-lookup"><span data-stu-id="781f8-109">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="781f8-110">.摘要</span><span class="sxs-lookup"><span data-stu-id="781f8-110">.SYNOPSIS</span></span>

<span data-ttu-id="781f8-111">函數或腳本的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-111">A brief description of the function or script.</span></span> <span data-ttu-id="781f8-112">這個關鍵字在每個主題中只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="781f8-112">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="781f8-113">.描述</span><span class="sxs-lookup"><span data-stu-id="781f8-113">.DESCRIPTION</span></span>

<span data-ttu-id="781f8-114">函數或腳本的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-114">A detailed description of the function or script.</span></span> <span data-ttu-id="781f8-115">這個關鍵字在每個主題中只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="781f8-115">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="781f8-116">.實參\<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="781f8-116">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="781f8-117">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-117">The description of a parameter.</span></span> <span data-ttu-id="781f8-118">您可以在函式 `.PARAMETER` 或腳本中包含每個參數的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-118">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="781f8-119">`.PARAMETER`關鍵字可以依任何順序出現在批註區塊中，但參數出現在 `Param` 語句或函式宣告中的順序會決定參數出現在說明主題中的順序。</span><span class="sxs-lookup"><span data-stu-id="781f8-119">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="781f8-120">若要變更說明主題中參數的順序，請變更 `Param` 語句或函式宣告中參數的順序。</span><span class="sxs-lookup"><span data-stu-id="781f8-120">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="781f8-121">您也可以將批註放在 `Param` 參數變數名稱前面的語句中，以指定參數描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-121">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="781f8-122">如果您同時使用 `Param` 語句批註和 `.PARAMETER` 關鍵字，則會使用與關鍵字相關聯的描述 `.PARAMETER` ，而 `Param` 語句批註會被忽略。</span><span class="sxs-lookup"><span data-stu-id="781f8-122">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="781f8-123">.實例</span><span class="sxs-lookup"><span data-stu-id="781f8-123">.EXAMPLE</span></span>

<span data-ttu-id="781f8-124">使用函式或腳本的範例命令，選擇性地後面接著範例輸出和描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-124">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="781f8-125">針對每個範例重複此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-125">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="781f8-126">.輸入</span><span class="sxs-lookup"><span data-stu-id="781f8-126">.INPUTS</span></span>

<span data-ttu-id="781f8-127">Microsoft .NET Framework 類型的物件，可透過管道傳送至函式或腳本。</span><span class="sxs-lookup"><span data-stu-id="781f8-127">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="781f8-128">您也可以包含輸入物件的描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-128">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="781f8-129">.產出</span><span class="sxs-lookup"><span data-stu-id="781f8-129">.OUTPUTS</span></span>

<span data-ttu-id="781f8-130">Cmdlet 所傳回之物件的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="781f8-130">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="781f8-131">您也可以包含傳回之物件的描述。</span><span class="sxs-lookup"><span data-stu-id="781f8-131">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="781f8-132">.紀錄</span><span class="sxs-lookup"><span data-stu-id="781f8-132">.NOTES</span></span>

<span data-ttu-id="781f8-133">函數或腳本的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="781f8-133">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="781f8-134">.LINK</span><span class="sxs-lookup"><span data-stu-id="781f8-134">.LINK</span></span>

<span data-ttu-id="781f8-135">相關主題的名稱。</span><span class="sxs-lookup"><span data-stu-id="781f8-135">The name of a related topic.</span></span> <span data-ttu-id="781f8-136">針對每個相關主題重複此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-136">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="781f8-137">此內容會出現在說明主題的 [相關連結] 區段中。</span><span class="sxs-lookup"><span data-stu-id="781f8-137">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="781f8-138">`.LINK`關鍵字內容也可以包含統一資源識別元（URI）至相同說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="781f8-138">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="781f8-139">當您使用的參數時，就會開啟線上版本 `Online` `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-139">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="781f8-140">URI 必須以 "HTTP" 或 "HTTPs" 開頭。</span><span class="sxs-lookup"><span data-stu-id="781f8-140">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="781f8-141">.成分</span><span class="sxs-lookup"><span data-stu-id="781f8-141">.COMPONENT</span></span>

<span data-ttu-id="781f8-142">函式或腳本所使用的技術或功能名稱，或其相關的。</span><span class="sxs-lookup"><span data-stu-id="781f8-142">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="781f8-143">的**元件**參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-143">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="781f8-144">.角色</span><span class="sxs-lookup"><span data-stu-id="781f8-144">.Role</span></span>

<span data-ttu-id="781f8-145">說明主題的使用者角色名稱。</span><span class="sxs-lookup"><span data-stu-id="781f8-145">The name of the user role for the help topic.</span></span> <span data-ttu-id="781f8-146">的**Role**參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-146">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="781f8-147">.功能</span><span class="sxs-lookup"><span data-stu-id="781f8-147">.FUNCTIONALITY</span></span>

<span data-ttu-id="781f8-148">描述函數用途的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-148">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="781f8-149">的**功能**參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-149">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="781f8-150">.FORWARDHELPTARGETNAME\<Command-Name></span><span class="sxs-lookup"><span data-stu-id="781f8-150">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="781f8-151">重新導向至指定之命令的說明主題。</span><span class="sxs-lookup"><span data-stu-id="781f8-151">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="781f8-152">您可以將使用者重新導向至任何說明主題，包括功能、腳本、Cmdlet 或提供者的說明主題。</span><span class="sxs-lookup"><span data-stu-id="781f8-152">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="781f8-153">.FORWARDHELPCATEGORY\<Category></span><span class="sxs-lookup"><span data-stu-id="781f8-153">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="781f8-154">指定中專案的 [說明] 分類 `.FORWARDHELPTARGETNAME` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-154">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="781f8-155">使用此關鍵字可在有相同名稱的命令時，避免發生衝突。</span><span class="sxs-lookup"><span data-stu-id="781f8-155">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="781f8-156">有效值為：</span><span class="sxs-lookup"><span data-stu-id="781f8-156">Valid values are:</span></span>

- <span data-ttu-id="781f8-157">Alias</span><span class="sxs-lookup"><span data-stu-id="781f8-157">Alias</span></span>
- <span data-ttu-id="781f8-158">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="781f8-158">Cmdlet</span></span>
- <span data-ttu-id="781f8-159">HelpFile</span><span class="sxs-lookup"><span data-stu-id="781f8-159">HelpFile</span></span>
- <span data-ttu-id="781f8-160">函式</span><span class="sxs-lookup"><span data-stu-id="781f8-160">Function</span></span>
- <span data-ttu-id="781f8-161">提供者</span><span class="sxs-lookup"><span data-stu-id="781f8-161">Provider</span></span>
- <span data-ttu-id="781f8-162">一般</span><span class="sxs-lookup"><span data-stu-id="781f8-162">General</span></span>
- <span data-ttu-id="781f8-163">常見問題集</span><span class="sxs-lookup"><span data-stu-id="781f8-163">FAQ</span></span>
- <span data-ttu-id="781f8-164">字彙表</span><span class="sxs-lookup"><span data-stu-id="781f8-164">Glossary</span></span>
- <span data-ttu-id="781f8-165">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="781f8-165">ScriptCommand</span></span>
- <span data-ttu-id="781f8-166">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="781f8-166">ExternalScript</span></span>
- <span data-ttu-id="781f8-167">Filter</span><span class="sxs-lookup"><span data-stu-id="781f8-167">Filter</span></span>
- <span data-ttu-id="781f8-168">全部</span><span class="sxs-lookup"><span data-stu-id="781f8-168">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="781f8-169">.REMOTEHELPRUNSPACE\<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="781f8-169">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="781f8-170">指定包含說明主題的會話。</span><span class="sxs-lookup"><span data-stu-id="781f8-170">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="781f8-171">輸入包含 PSSession 的變數。</span><span class="sxs-lookup"><span data-stu-id="781f8-171">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="781f8-172">Cmdlet 會使用這個關鍵字 `Export-PSSession` 來尋找已匯出命令的說明主題。</span><span class="sxs-lookup"><span data-stu-id="781f8-172">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="781f8-173">..EXTERNALHELP\<XML Help File></span><span class="sxs-lookup"><span data-stu-id="781f8-173">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="781f8-174">指定腳本或函式之 XML 架構說明檔的路徑和（或）名稱。</span><span class="sxs-lookup"><span data-stu-id="781f8-174">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="781f8-175">`.EXTERNALHELP`關鍵字會告知[GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet，以在 XML 檔案中取得腳本或函式的說明。</span><span class="sxs-lookup"><span data-stu-id="781f8-175">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="781f8-176">`.EXTERNALHELP`使用腳本或函式的 XML 說明檔時，需要關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-176">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="781f8-177">若沒有此功能，將找不到函式或腳本的說明檔 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-177">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="781f8-178">`.EXTERNALHELP`關鍵字優先于其他所有以批註為基礎的說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="781f8-178">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="781f8-179">當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也一樣。</span><span class="sxs-lookup"><span data-stu-id="781f8-179">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="781f8-180">當腳本模組匯出函數時，的值 `.EXTERNALHELP` 應該是不含路徑的檔案名。</span><span class="sxs-lookup"><span data-stu-id="781f8-180">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="781f8-181">`Get-Help`在模組目錄的地區設定特定子目錄中尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="781f8-181">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="781f8-182">檔案名沒有任何需求，但最佳作法是使用下列檔案名格式： `<ScriptModule>.psm1-help.xml` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-182">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="781f8-183">當函式未與模組相關聯時，請在關鍵字的值中包含路徑和檔案名 `.EXTERNALHELP` 。</span><span class="sxs-lookup"><span data-stu-id="781f8-183">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="781f8-184">如果指定的 XML 檔案路徑包含 UI 文化特性特定的子目錄，則 `Get-Help` 會以遞迴方式使用腳本或函式的名稱來搜尋子目錄中的 xml 檔案，就如同所有以 XML 為基礎的說明主題一樣。</span><span class="sxs-lookup"><span data-stu-id="781f8-184">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="781f8-185">如需有關 Cmdlet 說明 XML 型說明檔案格式的詳細資訊，請參閱[撰寫 Windows PowerShell Cmdlet](./writing-help-for-windows-powershell-cmdlets.md)說明。</span><span class="sxs-lookup"><span data-stu-id="781f8-185">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
