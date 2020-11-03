---
description: 說明如何撰寫函式和腳本的批註式說明主題。
keywords: powershell,cmdlet
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: eaf1ea3eaacf944e9489292ea46822d655f2068b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207684"
---
# <a name="about-comment-based-help"></a><span data-ttu-id="d2b27-104">關於以批註為基礎的說明</span><span class="sxs-lookup"><span data-stu-id="d2b27-104">About Comment-based Help</span></span>

## <a name="short-description"></a><span data-ttu-id="d2b27-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d2b27-105">Short description</span></span>
<span data-ttu-id="d2b27-106">說明如何撰寫函式和腳本的批註式說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-106">Describes how to write comment-based help topics for functions and scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="d2b27-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="d2b27-107">Long description</span></span>

<span data-ttu-id="d2b27-108">您可以使用特殊的說明批註關鍵字來撰寫函數和腳本的批註式說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-108">You can write comment-based help topics for functions and scripts by using special help comment keywords.</span></span>

<span data-ttu-id="d2b27-109">[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) Cmdlet 會顯示以批註為基礎的說明，其格式會顯示從 XML 檔案產生的 Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-109">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) cmdlet displays comment-based help in the same format in which it displays the cmdlet help topics that are generated from XML files.</span></span> <span data-ttu-id="d2b27-110">使用者可以使用的所有參數（ `Get-Help` 如 **詳細** 、 **完整** 、 **範例** 和 **線上** ）來顯示以批註為基礎的說明內容。</span><span class="sxs-lookup"><span data-stu-id="d2b27-110">Users can use all of the parameters of `Get-Help`, such as **Detailed** , **Full** , **Examples** , and **Online** , to display the contents of comment-based help.</span></span>

<span data-ttu-id="d2b27-111">您也可以針對函式和腳本撰寫以 XML 為基礎的說明檔。</span><span class="sxs-lookup"><span data-stu-id="d2b27-111">You can also write XML-based help files for functions and scripts.</span></span> <span data-ttu-id="d2b27-112">若要啟用 `Get-Help` Cmdlet 來尋找函式或腳本的 XML 型說明檔，請使用 `.ExternalHelp` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-112">To enable the `Get-Help` cmdlet to find the XML-based help file for a function or script, use the `.ExternalHelp` keyword.</span></span> <span data-ttu-id="d2b27-113">如果沒有這個關鍵字，則找 `Get-Help` 不到函數或腳本的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-113">Without this keyword, `Get-Help` cannot find XML-based help topics for functions or scripts.</span></span>

<span data-ttu-id="d2b27-114">本主題說明如何撰寫函數和腳本的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-114">This topic explains how to write help topics for functions and scripts.</span></span> <span data-ttu-id="d2b27-115">如需有關如何顯示函式和腳本的說明主題的詳細資訊，請參閱 [get-help](xref:Microsoft.PowerShell.Core.Get-Help)。</span><span class="sxs-lookup"><span data-stu-id="d2b27-115">For information about how to display help topics for functions and scripts, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).</span></span>

<span data-ttu-id="d2b27-116">[Update-help](xref:Microsoft.PowerShell.Core.Update-Help)和[Save help](xref:Microsoft.PowerShell.Core.Save-Help) CMDLET 只適用于 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d2b27-116">The [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) and [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) cmdlets work only on XML files.</span></span> <span data-ttu-id="d2b27-117">可更新的說明不支援以批註為基礎的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-117">Updatable Help does not support comment-based help topics.</span></span>

## <a name="syntax-for-comment-based-help"></a><span data-ttu-id="d2b27-118">以批註為基礎的說明語法</span><span class="sxs-lookup"><span data-stu-id="d2b27-118">Syntax for comment-based help</span></span>

<span data-ttu-id="d2b27-119">以批註為基礎的說明語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="d2b27-119">The syntax for comment-based help is as follows:</span></span>

```
# .<help keyword>
# <help content>
```

<span data-ttu-id="d2b27-120">或</span><span class="sxs-lookup"><span data-stu-id="d2b27-120">or</span></span>

```
<#
.<help keyword>
<help content>
#>
```

<span data-ttu-id="d2b27-121">以批註為基礎的說明會以一系列的批註撰寫。</span><span class="sxs-lookup"><span data-stu-id="d2b27-121">Comment-based help is written as a series of comments.</span></span> <span data-ttu-id="d2b27-122">您可以在 `#` 每一行批註之前輸入批註符號，也可以使用 `<#` 和 `#>` 符號來建立批註區塊。</span><span class="sxs-lookup"><span data-stu-id="d2b27-122">You can type a comment symbol `#` before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="d2b27-123">批註區塊內的所有行都會轉譯為批註。</span><span class="sxs-lookup"><span data-stu-id="d2b27-123">All the lines within the comment block are interpreted as comments.</span></span>

<span data-ttu-id="d2b27-124">以批註為基礎的說明主題中的所有程式列都必須是連續的。</span><span class="sxs-lookup"><span data-stu-id="d2b27-124">All of the lines in a comment-based help topic must be contiguous.</span></span> <span data-ttu-id="d2b27-125">如果以批註為基礎的說明主題遵循的批註不在說明主題中，則最後一個非說明批註行和批註式說明的開頭至少必須有一個空白行。</span><span class="sxs-lookup"><span data-stu-id="d2b27-125">If a comment-based help topic follows a comment that is not part of the help topic, there must be at least one blank line between the last non-help comment line and the beginning of the comment-based help.</span></span>

<span data-ttu-id="d2b27-126">關鍵字會定義以批註為基礎的說明的每個區段。</span><span class="sxs-lookup"><span data-stu-id="d2b27-126">Keywords define each section of comment-based help.</span></span> <span data-ttu-id="d2b27-127">每個以批註為基礎的說明關鍵字之前都是點 `.` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-127">Each comment-based help keyword is preceded by a dot `.`.</span></span> <span data-ttu-id="d2b27-128">關鍵字可以依任何順序出現。</span><span class="sxs-lookup"><span data-stu-id="d2b27-128">The keywords can appear in any order.</span></span> <span data-ttu-id="d2b27-129">關鍵字名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d2b27-129">The keyword names are not case-sensitive.</span></span>

<span data-ttu-id="d2b27-130">例如，關鍵字會在 `.Description` 函數或腳本的描述之前。</span><span class="sxs-lookup"><span data-stu-id="d2b27-130">For example, the `.Description` keyword precedes a description of a function or script.</span></span>

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

<span data-ttu-id="d2b27-131">批註區塊必須至少包含一個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-131">The comment block must contain at least one keyword.</span></span> <span data-ttu-id="d2b27-132">某些關鍵字（例如 `.EXAMPLE` ）可能會在相同的批註區塊中出現多次。</span><span class="sxs-lookup"><span data-stu-id="d2b27-132">Some of the keywords, such as `.EXAMPLE`, can appear many times in the same comment block.</span></span> <span data-ttu-id="d2b27-133">每個關鍵字的說明內容都是在關鍵字後面的那一行開始，而且可以橫跨多行。</span><span class="sxs-lookup"><span data-stu-id="d2b27-133">The help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

## <a name="syntax-for-comment-based-help-in-functions"></a><span data-ttu-id="d2b27-134">函數中以批註為基礎的說明語法</span><span class="sxs-lookup"><span data-stu-id="d2b27-134">Syntax for comment-based help in functions</span></span>

<span data-ttu-id="d2b27-135">以批註為基礎的函式說明可以出現在下列三個位置的其中一個位置：</span><span class="sxs-lookup"><span data-stu-id="d2b27-135">Comment-based help for a function can appear in one of three locations:</span></span>

- <span data-ttu-id="d2b27-136">在函數主體的開頭。</span><span class="sxs-lookup"><span data-stu-id="d2b27-136">At the beginning of the function body.</span></span>
- <span data-ttu-id="d2b27-137">在函數主體的結尾。</span><span class="sxs-lookup"><span data-stu-id="d2b27-137">At the end of the function body.</span></span>
- <span data-ttu-id="d2b27-138">關鍵字之前 `function` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-138">Before the `function` keyword.</span></span> <span data-ttu-id="d2b27-139">函數說明和關鍵字的最後一行之間不能有一個以上的空白行 `function` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-139">There cannot be more than one blank line between the last line of the function help and the `function` keyword.</span></span>

<span data-ttu-id="d2b27-140">例如：</span><span class="sxs-lookup"><span data-stu-id="d2b27-140">For example:</span></span>

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

<span data-ttu-id="d2b27-141">或</span><span class="sxs-lookup"><span data-stu-id="d2b27-141">or</span></span>

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

<span data-ttu-id="d2b27-142">或</span><span class="sxs-lookup"><span data-stu-id="d2b27-142">or</span></span>

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a><span data-ttu-id="d2b27-143">腳本中以批註為基礎的說明語法</span><span class="sxs-lookup"><span data-stu-id="d2b27-143">Syntax for comment-based help in scripts</span></span>

<span data-ttu-id="d2b27-144">腳本的批註式說明可以出現在腳本中的下列兩個位置的其中一個位置。</span><span class="sxs-lookup"><span data-stu-id="d2b27-144">Comment-based help for a script can appear in one of the following two locations in the script.</span></span>

- <span data-ttu-id="d2b27-145">指令檔的開頭。</span><span class="sxs-lookup"><span data-stu-id="d2b27-145">At the beginning of the script file.</span></span> <span data-ttu-id="d2b27-146">腳本說明可以在腳本中的前面加上批註和空白行。</span><span class="sxs-lookup"><span data-stu-id="d2b27-146">Script help can be preceded in the script only by comments and blank lines.</span></span>

  <span data-ttu-id="d2b27-147">如果腳本主體中的第一個專案 (在 [說明]) 之後是函式宣告，則腳本說明和函式宣告的結尾必須至少有兩個空白行。</span><span class="sxs-lookup"><span data-stu-id="d2b27-147">If the first item in the script body (after the help) is a function declaration, there must be at least two blank lines between the end of the script help and the function declaration.</span></span> <span data-ttu-id="d2b27-148">否則，說明會被視為函數的說明，而不是腳本的說明。</span><span class="sxs-lookup"><span data-stu-id="d2b27-148">Otherwise, the help is interpreted as being help for the function, not help for the script.</span></span>

- <span data-ttu-id="d2b27-149">指令檔的結尾。</span><span class="sxs-lookup"><span data-stu-id="d2b27-149">At the end of the script file.</span></span> <span data-ttu-id="d2b27-150">但是，如果腳本已簽署，請在腳本檔案的開頭放置批註式說明。</span><span class="sxs-lookup"><span data-stu-id="d2b27-150">However, if the script is signed, place Comment-based help at the beginning of the script file.</span></span> <span data-ttu-id="d2b27-151">腳本的結尾是由簽章區塊所佔用。</span><span class="sxs-lookup"><span data-stu-id="d2b27-151">The end of the script is occupied by the signature block.</span></span>

<span data-ttu-id="d2b27-152">例如：</span><span class="sxs-lookup"><span data-stu-id="d2b27-152">For example:</span></span>

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

<span data-ttu-id="d2b27-153">或</span><span class="sxs-lookup"><span data-stu-id="d2b27-153">or</span></span>

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a><span data-ttu-id="d2b27-154">腳本模組中以批註為基礎的說明語法</span><span class="sxs-lookup"><span data-stu-id="d2b27-154">Syntax for comment-based help in script modules</span></span>

<span data-ttu-id="d2b27-155">在腳本模組中 `.psm1` ，以批註為基礎的說明會使用函數的語法，而非腳本的語法。</span><span class="sxs-lookup"><span data-stu-id="d2b27-155">In a script module `.psm1`, comment-based help uses the syntax for functions, not the syntax for scripts.</span></span> <span data-ttu-id="d2b27-156">您無法使用腳本語法為腳本模組中定義的所有函式提供說明。</span><span class="sxs-lookup"><span data-stu-id="d2b27-156">You cannot use the script syntax to provide help for all functions defined in a script module.</span></span>

<span data-ttu-id="d2b27-157">例如，如果您使用 `.ExternalHelp` 關鍵字來識別腳本模組中函式的 XML 架構說明檔，則必須將 `.ExternalHelp` 批註加入至每個函數。</span><span class="sxs-lookup"><span data-stu-id="d2b27-157">For example, if you are using the `.ExternalHelp` keyword to identify the XML-based help files for the functions in a script module, you must add an `.ExternalHelp` comment to each function.</span></span>

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a><span data-ttu-id="d2b27-158">以批註為基礎的說明關鍵字</span><span class="sxs-lookup"><span data-stu-id="d2b27-158">Comment-based help keywords</span></span>

<span data-ttu-id="d2b27-159">以下是以批註為基礎的有效說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-159">The following are valid comment-based help keywords.</span></span> <span data-ttu-id="d2b27-160">這些清單會依照它們一般出現在說明主題中的順序列出，以及其預期的用途。</span><span class="sxs-lookup"><span data-stu-id="d2b27-160">They are listed in the order in which they typically appear in a help topic along with their intended use.</span></span> <span data-ttu-id="d2b27-161">這些關鍵字在批註式說明中可依任何順序出現，而且不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d2b27-161">These keywords can appear in any order in the comment-based help, and they are not case-sensitive.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d2b27-162">.簡介</span><span class="sxs-lookup"><span data-stu-id="d2b27-162">.SYNOPSIS</span></span>

<span data-ttu-id="d2b27-163">函數或腳本的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-163">A brief description of the function or script.</span></span> <span data-ttu-id="d2b27-164">在每個主題中，這個關鍵字只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="d2b27-164">This keyword can be used only once in each topic.</span></span>

### <a name="description"></a><span data-ttu-id="d2b27-165">.描述</span><span class="sxs-lookup"><span data-stu-id="d2b27-165">.DESCRIPTION</span></span>

<span data-ttu-id="d2b27-166">函數或腳本的詳細描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-166">A detailed description of the function or script.</span></span> <span data-ttu-id="d2b27-167">在每個主題中，這個關鍵字只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="d2b27-167">This keyword can be used only once in each topic.</span></span>

### <a name="parameter"></a><span data-ttu-id="d2b27-168">.參數</span><span class="sxs-lookup"><span data-stu-id="d2b27-168">.PARAMETER</span></span>

<span data-ttu-id="d2b27-169">參數的描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-169">The description of a parameter.</span></span> <span data-ttu-id="d2b27-170">針對函式 `.PARAMETER` 或腳本語法中的每個參數新增關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-170">Add a `.PARAMETER` keyword for each parameter in the function or script syntax.</span></span>

<span data-ttu-id="d2b27-171">在與關鍵字相同的行上輸入參數名稱 `.PARAMETER` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-171">Type the parameter name on the same line as the `.PARAMETER` keyword.</span></span> <span data-ttu-id="d2b27-172">在關鍵字後面的行上輸入參數描述 `.PARAMETER` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-172">Type the parameter description on the lines following the `.PARAMETER` keyword.</span></span> <span data-ttu-id="d2b27-173">Windows PowerShell 會將 `.PARAMETER` 行和下一個關鍵字之間的所有文字或批註區塊的結尾，視為參數描述的一部分來解讀。</span><span class="sxs-lookup"><span data-stu-id="d2b27-173">Windows PowerShell interprets all text between the `.PARAMETER` line and the next keyword or the end of the comment block as part of the parameter description.</span></span>
<span data-ttu-id="d2b27-174">描述可包含段落分隔。</span><span class="sxs-lookup"><span data-stu-id="d2b27-174">The description can include paragraph breaks.</span></span>

```
.PARAMETER  <Parameter-Name>
```

<span data-ttu-id="d2b27-175">參數關鍵字可以在批註區塊中以任何順序出現，但函數或腳本語法會決定參數 (的順序，而其描述) 出現在說明主題中。</span><span class="sxs-lookup"><span data-stu-id="d2b27-175">The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters (and their descriptions) appear in help topic.</span></span> <span data-ttu-id="d2b27-176">若要變更順序，請變更語法。</span><span class="sxs-lookup"><span data-stu-id="d2b27-176">To change the order, change the syntax.</span></span>

<span data-ttu-id="d2b27-177">您也可以將批註放在函數或腳本語法中，緊接在參數變數名稱之前，以指定參數描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-177">You can also specify a parameter description by placing a comment in the function or script syntax immediately before the parameter variable name.</span></span> <span data-ttu-id="d2b27-178">若要這樣做，您也必須具有至少一個關鍵字的批註區塊。</span><span class="sxs-lookup"><span data-stu-id="d2b27-178">For this to work, you must also have a comment block with at least one keyword.</span></span>

<span data-ttu-id="d2b27-179">如果您同時使用語法批註和 `.PARAMETER` 關鍵字，則會使用與關鍵字相關聯的描述 `.PARAMETER` ，而語法批註會被忽略。</span><span class="sxs-lookup"><span data-stu-id="d2b27-179">If you use both a syntax comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the syntax comment is ignored.</span></span>

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a><span data-ttu-id="d2b27-180">.例子</span><span class="sxs-lookup"><span data-stu-id="d2b27-180">.EXAMPLE</span></span>

<span data-ttu-id="d2b27-181">使用函數或腳本的範例命令，選擇性地接著範例輸出和描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-181">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="d2b27-182">針對每個範例重複此關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-182">Repeat this keyword for each example.</span></span>

### <a name="inputs"></a><span data-ttu-id="d2b27-183">.輸入</span><span class="sxs-lookup"><span data-stu-id="d2b27-183">.INPUTS</span></span>

<span data-ttu-id="d2b27-184">可以輸送至函式或腳本之物件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d2b27-184">The .NET types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="d2b27-185">您也可以包含輸入物件的描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-185">You can also include a description of the input objects.</span></span>

### <a name="outputs"></a><span data-ttu-id="d2b27-186">.輸出</span><span class="sxs-lookup"><span data-stu-id="d2b27-186">.OUTPUTS</span></span>

<span data-ttu-id="d2b27-187">Cmdlet 傳回之物件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d2b27-187">The .NET type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="d2b27-188">您也可以包含所傳回物件的描述。</span><span class="sxs-lookup"><span data-stu-id="d2b27-188">You can also include a description of the returned objects.</span></span>

### <a name="notes"></a><span data-ttu-id="d2b27-189">.筆記</span><span class="sxs-lookup"><span data-stu-id="d2b27-189">.NOTES</span></span>

<span data-ttu-id="d2b27-190">函數或腳本的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d2b27-190">Additional information about the function or script.</span></span>

### <a name="link"></a><span data-ttu-id="d2b27-191">.連結</span><span class="sxs-lookup"><span data-stu-id="d2b27-191">.LINK</span></span>

<span data-ttu-id="d2b27-192">相關主題的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2b27-192">The name of a related topic.</span></span> <span data-ttu-id="d2b27-193">值會出現在 ". 底下的行。LINK "關鍵字，且前面必須加上批註符號 `#` 或包含在批註區塊中。</span><span class="sxs-lookup"><span data-stu-id="d2b27-193">The value appears on the line below the ".LINK" keyword and must be preceded by a comment symbol `#` or included in the comment block.</span></span>

<span data-ttu-id="d2b27-194">`.LINK`針對每個相關主題重複關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-194">Repeat the `.LINK` keyword for each related topic.</span></span>

<span data-ttu-id="d2b27-195">此內容會顯示在說明主題的 [相關連結] 區段中。</span><span class="sxs-lookup"><span data-stu-id="d2b27-195">This content appears in the Related Links section of the help topic.</span></span>

<span data-ttu-id="d2b27-196">`.Link`關鍵字內容也可以包含統一資源識別項 (URI) 至相同說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="d2b27-196">The `.Link` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same help topic.</span></span> <span data-ttu-id="d2b27-197">當您使用的 **online** 參數時，就會開啟線上版本 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-197">The online version opens when you use the **Online** parameter of `Get-Help`.</span></span> <span data-ttu-id="d2b27-198">URI 的開頭必須是 "HTTP" 或 "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="d2b27-198">The URI must begin with "http" or "https".</span></span>

### <a name="component"></a><span data-ttu-id="d2b27-199">.元件</span><span class="sxs-lookup"><span data-stu-id="d2b27-199">.COMPONENT</span></span>

<span data-ttu-id="d2b27-200">函數或腳本所使用的技術或功能名稱，或其相關的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2b27-200">The name of the technology or feature that the function or script uses, or to which it is related.</span></span> <span data-ttu-id="d2b27-201">的 **元件** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-201">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="role"></a><span data-ttu-id="d2b27-202">.作用</span><span class="sxs-lookup"><span data-stu-id="d2b27-202">.ROLE</span></span>

<span data-ttu-id="d2b27-203">說明主題的使用者角色名稱。</span><span class="sxs-lookup"><span data-stu-id="d2b27-203">The name of the user role for the help topic.</span></span> <span data-ttu-id="d2b27-204">的 **Role** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-204">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="functionality"></a><span data-ttu-id="d2b27-205">.功能</span><span class="sxs-lookup"><span data-stu-id="d2b27-205">.FUNCTIONALITY</span></span>

<span data-ttu-id="d2b27-206">描述函式用途的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-206">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="d2b27-207">的 **功能** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-207">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="forwardhelptargetname"></a><span data-ttu-id="d2b27-208">.FORWARDHELPTARGETNAME</span><span class="sxs-lookup"><span data-stu-id="d2b27-208">.FORWARDHELPTARGETNAME</span></span>

<span data-ttu-id="d2b27-209">重新導向至指定命令的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-209">Redirects to the help topic for the specified command.</span></span> <span data-ttu-id="d2b27-210">您可以將使用者重新導向至任何說明主題，包括函數、腳本、Cmdlet 或提供者的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-210">You can redirect users to any help topic, including help topics for a function, script, cmdlet, or provider.</span></span>

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a><span data-ttu-id="d2b27-211">.FORWARDHELPCATEGORY</span><span class="sxs-lookup"><span data-stu-id="d2b27-211">.FORWARDHELPCATEGORY</span></span>

<span data-ttu-id="d2b27-212">指定中專案的 [說明] 類別 `.ForwardHelpTargetName` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-212">Specifies the help category of the item in `.ForwardHelpTargetName`.</span></span> <span data-ttu-id="d2b27-213">有效的值為 `Alias` 、、、、、、、、、、 `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` 或 `All` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-213">Valid values are `Alias`, `Cmdlet`, `HelpFile`, `Function`, `Provider`, `General`, `FAQ`, `Glossary`, `ScriptCommand`, `ExternalScript`, `Filter`, or `All`.</span></span> <span data-ttu-id="d2b27-214">使用這個關鍵字可避免在具有相同名稱的命令時產生衝突。</span><span class="sxs-lookup"><span data-stu-id="d2b27-214">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a><span data-ttu-id="d2b27-215">.REMOTEHELPRUNSPACE</span><span class="sxs-lookup"><span data-stu-id="d2b27-215">.REMOTEHELPRUNSPACE</span></span>

<span data-ttu-id="d2b27-216">指定包含說明主題的會話。</span><span class="sxs-lookup"><span data-stu-id="d2b27-216">Specifies a session that contains the help topic.</span></span> <span data-ttu-id="d2b27-217">輸入包含 **PSSession** 物件的變數。</span><span class="sxs-lookup"><span data-stu-id="d2b27-217">Enter a variable that contains a **PSSession** object.</span></span> <span data-ttu-id="d2b27-218">這個關鍵字是由 [匯出-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) Cmdlet 用來尋找匯出命令的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-218">This keyword is used by the [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet to find the help topics for the exported commands.</span></span>

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a><span data-ttu-id="d2b27-219">..EXTERNALHELP</span><span class="sxs-lookup"><span data-stu-id="d2b27-219">.EXTERNALHELP</span></span>

<span data-ttu-id="d2b27-220">為腳本或函式指定以 XML 為基礎的說明檔。</span><span class="sxs-lookup"><span data-stu-id="d2b27-220">Specifies an XML-based help file for the script or function.</span></span>

```powershell
# .EXTERNALHELP <XML Help File>
```

<span data-ttu-id="d2b27-221">在 `.ExternalHelp` XML 檔案中記載函式或腳本時，需要關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-221">The `.ExternalHelp` keyword is required when a function or script is documented in XML files.</span></span> <span data-ttu-id="d2b27-222">如果沒有這個關鍵字，則找不到函 `Get-Help` 式或腳本的 XML 架構說明檔。</span><span class="sxs-lookup"><span data-stu-id="d2b27-222">Without this keyword, `Get-Help` cannot find the XML-based help file for the function or script.</span></span>

<span data-ttu-id="d2b27-223">`.ExternalHelp`關鍵字優先于其他以批註為基礎的說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-223">The `.ExternalHelp` keyword takes precedence over other comment-based help keywords.</span></span> <span data-ttu-id="d2b27-224">如果 `.ExternalHelp` 存在， `Get-Help` 即使找不到符合關鍵字值的說明主題，也不會顯示以批註為基礎的說明 `.ExternalHelp` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-224">If `.ExternalHelp` is present, `Get-Help` does not display comment-based help, even if it cannot find a help topic that matches the value of the `.ExternalHelp` keyword.</span></span>

<span data-ttu-id="d2b27-225">如果函式是由模組匯出，請將關鍵字的值設定 `.ExternalHelp` 為沒有路徑的檔案名。</span><span class="sxs-lookup"><span data-stu-id="d2b27-225">If the function is exported by a module, set the value of the `.ExternalHelp` keyword to a filename without a path.</span></span> <span data-ttu-id="d2b27-226">`Get-Help` 在模組目錄的特定語言子目錄中尋找指定的檔案名。</span><span class="sxs-lookup"><span data-stu-id="d2b27-226">`Get-Help` looks for the specified file name in a language-specific subdirectory of the module directory.</span></span> <span data-ttu-id="d2b27-227">函式的 XML 說明檔名稱沒有任何需求，但最佳做法是使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="d2b27-227">There are no requirements for the name of the XML-based help file for a function, but a best practice is to use the following format:</span></span>

```
<ScriptModule.psm1>-help.xml
```

<span data-ttu-id="d2b27-228">如果函式不包含在模組中，請包含以 XML 為基礎的說明檔路徑。</span><span class="sxs-lookup"><span data-stu-id="d2b27-228">If the function is not included in a module, include a path to the XML-based help file.</span></span> <span data-ttu-id="d2b27-229">如果值包含路徑，且路徑包含 UI 文化特性特定子目錄，則會以 `Get-Help` 遞迴方式在子目錄中搜尋具有腳本或函式名稱的 XML 檔案，就像在模組目錄中所建立的語言回溯標準一樣。</span><span class="sxs-lookup"><span data-stu-id="d2b27-229">If the value includes a path and the path contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does in a module directory.</span></span>

<span data-ttu-id="d2b27-230">如需有關 Cmdlet 說明 XML 架構說明檔案格式的詳細資訊，請參閱 MSDN library 中的 [如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-230">For more information about the cmdlet help XML-based help file format, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="autogenerated-content"></a><span data-ttu-id="d2b27-231">自動產生的內容</span><span class="sxs-lookup"><span data-stu-id="d2b27-231">Autogenerated content</span></span>

<span data-ttu-id="d2b27-232">Cmdlet 會自動產生名稱、語法、參數清單、參數屬性資料表、一般參數和備註 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-232">The name, syntax, parameter list, parameter attribute table, common parameters, and remarks are automatically generated by the `Get-Help` cmdlet.</span></span>

### <a name="name"></a><span data-ttu-id="d2b27-233">Name</span><span class="sxs-lookup"><span data-stu-id="d2b27-233">Name</span></span>

<span data-ttu-id="d2b27-234">函數說明主題的 **名稱** 區段取自函數語法中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="d2b27-234">The **Name** section of a function help topic is taken from the function name in the function syntax.</span></span> <span data-ttu-id="d2b27-235">腳本說明主題的 **名稱** 取自指令檔名。</span><span class="sxs-lookup"><span data-stu-id="d2b27-235">The **Name** of a script help topic is taken from the script filename.</span></span> <span data-ttu-id="d2b27-236">若要變更名稱或其大小寫，請變更函數語法或指令檔名。</span><span class="sxs-lookup"><span data-stu-id="d2b27-236">To change the name or its capitalization, change the function syntax or the script filename.</span></span>

### <a name="syntax"></a><span data-ttu-id="d2b27-237">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2b27-237">Syntax</span></span>

<span data-ttu-id="d2b27-238">說明主題的 **語法** 區段是從函數或腳本語法產生的。</span><span class="sxs-lookup"><span data-stu-id="d2b27-238">The **Syntax** section of the help topic is generated from the function or script syntax.</span></span> <span data-ttu-id="d2b27-239">若要將詳細資料新增至說明主題語法，例如參數的 .NET 型別，請將詳細資料新增至語法。</span><span class="sxs-lookup"><span data-stu-id="d2b27-239">To add detail to the help topic syntax, such as the .NET type of a parameter, add the detail to the syntax.</span></span> <span data-ttu-id="d2b27-240">如果您未指定參數類型，則會將 **物件** 類型插入為預設值。</span><span class="sxs-lookup"><span data-stu-id="d2b27-240">If you do not specify a parameter type, the **Object** type is inserted as the default value.</span></span>

### <a name="parameter-list"></a><span data-ttu-id="d2b27-241">參數清單</span><span class="sxs-lookup"><span data-stu-id="d2b27-241">Parameter List</span></span>

<span data-ttu-id="d2b27-242">說明主題中的參數清單是從函式或腳本語法，以及您使用關鍵字加入的描述所產生 `.Parameter` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-242">The parameter list in the help topic is generated from the function or script syntax and from the descriptions that you add by using the `.Parameter` keyword.</span></span> <span data-ttu-id="d2b27-243">函數參數會出現在說明主題的 **parameters** 區段中，其順序與函式或腳本語法中的順序相同。</span><span class="sxs-lookup"><span data-stu-id="d2b27-243">The function parameters appear in the **Parameters** section of the help topic in the same order that they appear in the function or script syntax.</span></span> <span data-ttu-id="d2b27-244">參數名稱的拼寫和大小寫也取自語法。</span><span class="sxs-lookup"><span data-stu-id="d2b27-244">The spelling and capitalization of parameter names is also taken from the syntax.</span></span> <span data-ttu-id="d2b27-245">它不會受到關鍵字所指定之參數名稱的影響 `.Parameter` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-245">It is not affected by the parameter name specified by the `.Parameter` keyword.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="d2b27-246">一般參數</span><span class="sxs-lookup"><span data-stu-id="d2b27-246">Common Parameters</span></span>

<span data-ttu-id="d2b27-247">**一般參數** 會加入至說明主題的語法和參數清單中，即使它們沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="d2b27-247">The **Common parameters** are added to the syntax and parameter list of the help topic, even if they have no effect.</span></span> <span data-ttu-id="d2b27-248">如需一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="d2b27-248">For more information about the common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="d2b27-249">參數屬性工作表</span><span class="sxs-lookup"><span data-stu-id="d2b27-249">Parameter Attribute Table</span></span>

<span data-ttu-id="d2b27-250">`Get-Help` 產生當您使用的 **Full** 或 **parameter** 參數時，所顯示的參數屬性資料表 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-250">`Get-Help` generates the table of parameter attributes that appears when you use the **Full** or **Parameter** parameter of `Get-Help`.</span></span> <span data-ttu-id="d2b27-251">**必要** 的、 **位置** 和 **預設** 值屬性的值取自函數或腳本語法。</span><span class="sxs-lookup"><span data-stu-id="d2b27-251">The value of the **Required** , **Position** , and **Default** value attributes is taken from the function or script syntax.</span></span>

<span data-ttu-id="d2b27-252">預設值和 **接受萬用字元** 的值不會出現在參數屬性工作表中，即使它們是在函式或腳本中定義也一樣。</span><span class="sxs-lookup"><span data-stu-id="d2b27-252">Default values and a value for **Accept Wildcard characters** do not appear in the parameter attribute table even when they are defined in the function or script.</span></span> <span data-ttu-id="d2b27-253">若要協助使用者，請在參數描述中提供這項資訊。</span><span class="sxs-lookup"><span data-stu-id="d2b27-253">To help users, provide this information in the parameter description.</span></span>

### <a name="remarks"></a><span data-ttu-id="d2b27-254">備註</span><span class="sxs-lookup"><span data-stu-id="d2b27-254">Remarks</span></span>

<span data-ttu-id="d2b27-255">[ **說明** ] 主題的 [備註] 區段會從函數或腳本名稱自動產生。</span><span class="sxs-lookup"><span data-stu-id="d2b27-255">The **Remarks** section of the help topic is automatically generated from the function or script name.</span></span> <span data-ttu-id="d2b27-256">您無法變更或影響其內容。</span><span class="sxs-lookup"><span data-stu-id="d2b27-256">You cannot change or affect its content.</span></span>

## <a name="examples"></a><span data-ttu-id="d2b27-257">範例</span><span class="sxs-lookup"><span data-stu-id="d2b27-257">Examples</span></span>

### <a name="comment-based-help-for-a-function"></a><span data-ttu-id="d2b27-258">函式以批註為基礎的說明</span><span class="sxs-lookup"><span data-stu-id="d2b27-258">Comment-based Help for a Function</span></span>

<span data-ttu-id="d2b27-259">下列範例函數包含以批註為基礎的說明：</span><span class="sxs-lookup"><span data-stu-id="d2b27-259">The following sample function includes comment-based help:</span></span>

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

<span data-ttu-id="d2b27-260">結果如下所示：</span><span class="sxs-lookup"><span data-stu-id="d2b27-260">The results are as follows:</span></span>

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a><span data-ttu-id="d2b27-261">函數語法中的參數描述</span><span class="sxs-lookup"><span data-stu-id="d2b27-261">Parameter Descriptions in Function Syntax</span></span>

<span data-ttu-id="d2b27-262">這個範例與上一個範例相同，不同之處在于參數描述會以函數語法插入。</span><span class="sxs-lookup"><span data-stu-id="d2b27-262">This example is the same as the previous one, except that the parameter descriptions are inserted in the function syntax.</span></span> <span data-ttu-id="d2b27-263">當描述很簡單時，此格式最有用。</span><span class="sxs-lookup"><span data-stu-id="d2b27-263">This format is most useful when the descriptions are brief.</span></span>

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a><span data-ttu-id="d2b27-264">以批註為基礎的腳本說明</span><span class="sxs-lookup"><span data-stu-id="d2b27-264">Comment-based Help for a Script</span></span>

<span data-ttu-id="d2b27-265">下列範例腳本包含以批註為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="d2b27-265">The following sample script includes comment-based help.</span></span> <span data-ttu-id="d2b27-266">請注意結尾和語句之間的空白行 `#>` `Param` 。</span><span class="sxs-lookup"><span data-stu-id="d2b27-266">Notice the blank lines between the closing `#>` and the `Param` statement.</span></span> <span data-ttu-id="d2b27-267">在沒有語句的腳本中，[ `Param` 說明] 主題和第一個函式宣告中的最後一個批註之間必須至少有兩個空白行。</span><span class="sxs-lookup"><span data-stu-id="d2b27-267">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the help topic and the first function declaration.</span></span> <span data-ttu-id="d2b27-268">如果沒有這些空白行，請 `Get-Help` 將說明主題與函式相關聯，而不是腳本。</span><span class="sxs-lookup"><span data-stu-id="d2b27-268">Without these blank lines, `Get-Help` associates the help topic with the function, not the script.</span></span>

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

<span data-ttu-id="d2b27-269">下列命令會取得腳本說明。</span><span class="sxs-lookup"><span data-stu-id="d2b27-269">The following command gets the script help.</span></span> <span data-ttu-id="d2b27-270">因為腳本不在環境變數中所列的目錄中 `$env:Path` ，所以 `Get-Help` 取得腳本說明的命令必須指定腳本路徑。</span><span class="sxs-lookup"><span data-stu-id="d2b27-270">Because the script is not in a directory that is listed in the `$env:Path` environment variable, the `Get-Help` command that gets the script help must specify the script path.</span></span>

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a><span data-ttu-id="d2b27-271">重新導向至 XML 檔案</span><span class="sxs-lookup"><span data-stu-id="d2b27-271">Redirecting to an XML File</span></span>

<span data-ttu-id="d2b27-272">您可以撰寫函數和腳本的 XML 型說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-272">You can write XML-based help topics for functions and scripts.</span></span> <span data-ttu-id="d2b27-273">雖然以批註為基礎的說明比較容易執行，但可更新的說明需要以 XML 為基礎的說明，並提供多種語言的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-273">Although comment-based help is easier to implement, XML-based help is required for Updatable Help and to provide help topics in multiple languages.</span></span>

<span data-ttu-id="d2b27-274">下列範例顯示 Update-Month.ps1 腳本的前幾行。</span><span class="sxs-lookup"><span data-stu-id="d2b27-274">The following example shows the first few lines of the Update-Month.ps1 script.</span></span>
<span data-ttu-id="d2b27-275">腳本會使用 `.ExternalHelp` 關鍵字來指定腳本的 XML 型說明主題的路徑。</span><span class="sxs-lookup"><span data-stu-id="d2b27-275">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based help topic for the script.</span></span>

<span data-ttu-id="d2b27-276">請注意，關鍵字的值 `.ExternalHelp` 會出現在與關鍵字相同的行上。</span><span class="sxs-lookup"><span data-stu-id="d2b27-276">Note that the value of the `.ExternalHelp` keyword appears on the same line as the keyword.</span></span> <span data-ttu-id="d2b27-277">任何其他位置都是不正確。</span><span class="sxs-lookup"><span data-stu-id="d2b27-277">Any other placement is ineffective.</span></span>

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

<span data-ttu-id="d2b27-278">下列範例會顯示函式中關鍵字的三個有效 `.ExternalHelp` 位置。</span><span class="sxs-lookup"><span data-stu-id="d2b27-278">The following examples show three valid placements of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a><span data-ttu-id="d2b27-279">重新導向至不同的說明主題</span><span class="sxs-lookup"><span data-stu-id="d2b27-279">Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="d2b27-280">下列程式碼是 PowerShell 中內建說明函式開頭的摘要，它會一次顯示一屏解說文字。</span><span class="sxs-lookup"><span data-stu-id="d2b27-280">The following code is an excerpt from the beginning of the built-in help function in PowerShell, which displays one screen of help text at a time.</span></span>
<span data-ttu-id="d2b27-281">由於 Cmdlet 的說明主題會描述 help 函式，因此 help 函式會 `Get-Help` 使用 `.ForwardHelpTargetName` 和 `.ForwardHelpCategory` 關鍵字將使用者重新導向至 `Get-Help` Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2b27-281">Because the help topic for the `Get-Help` cmdlet describes the help function, the help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the `Get-Help` cmdlet help topic.</span></span>

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

<span data-ttu-id="d2b27-282">下列命令會使用這項功能：</span><span class="sxs-lookup"><span data-stu-id="d2b27-282">The following command uses this feature:</span></span>

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a><span data-ttu-id="d2b27-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2b27-283">See also</span></span>

[<span data-ttu-id="d2b27-284">about_Functions</span><span class="sxs-lookup"><span data-stu-id="d2b27-284">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="d2b27-285">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="d2b27-285">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="d2b27-286">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="d2b27-286">about_Scripts</span></span>](about_Scripts.md)

[<span data-ttu-id="d2b27-287">如何撰寫 Cmdlet 說明</span><span class="sxs-lookup"><span data-stu-id="d2b27-287">How to Write Cmdlet Help</span></span>](https://go.microsoft.com/fwlink/?LinkID=123415)
