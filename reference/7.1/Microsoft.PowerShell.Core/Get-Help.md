---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 1a4a3f7050c3da2a73ae0d5319938117284076b7
ms.sourcegitcommit: 05f578d3fca0d9663bb1e4f76e2f14604f5303ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "93206211"
---
# <span data-ttu-id="293e2-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="293e2-103">Get-Help</span></span>

## <span data-ttu-id="293e2-104">概要</span><span class="sxs-lookup"><span data-stu-id="293e2-104">SYNOPSIS</span></span>
<span data-ttu-id="293e2-105">顯示 PowerShell 命令和概念的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="293e2-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="293e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="293e2-106">SYNTAX</span></span>

### <span data-ttu-id="293e2-107">AllUsersView (預設) </span><span class="sxs-lookup"><span data-stu-id="293e2-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="293e2-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="293e2-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="293e2-109">範例</span><span class="sxs-lookup"><span data-stu-id="293e2-109">Examples</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="293e2-110">參數</span><span class="sxs-lookup"><span data-stu-id="293e2-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="293e2-111">線上</span><span class="sxs-lookup"><span data-stu-id="293e2-111">Online</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### <span data-ttu-id="293e2-112">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="293e2-112">ShowWindow</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## <span data-ttu-id="293e2-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="293e2-113">DESCRIPTION</span></span>

<span data-ttu-id="293e2-114">此 `Get-Help` Cmdlet 會顯示 PowerShell 概念和命令的相關資訊，包括 Cmdlet、函式、通用訊息模型 (CIM) 命令、工作流程、提供者、別名和腳本。</span><span class="sxs-lookup"><span data-stu-id="293e2-114">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="293e2-115">若要取得 PowerShell Cmdlet 的說明，請輸入 `Get-Help` 後面接著 Cmdlet 名稱，例如： `Get-Help Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-115">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="293e2-116">PowerShell 中的概念性說明文章的開頭是 **about_** ，例如 **about_Comparison_Operators** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-116">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators** .</span></span> <span data-ttu-id="293e2-117">若要查看所有 **about_** 文章，請輸入 `Get-Help about_*` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-117">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="293e2-118">若要查看特定的文章，請輸入 `Get-Help about_<article-name>` ，例如 `Get-Help about_Comparison_Operators` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-118">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="293e2-119">若要取得 PowerShell 提供者的說明，請輸入， `Get-Help` 後面接著提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="293e2-119">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="293e2-120">例如，若要取得憑證提供者的說明，請輸入 `Get-Help Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-120">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="293e2-121">您也可以輸入 `help` 或 `man` ，一次顯示一個螢幕的文字。</span><span class="sxs-lookup"><span data-stu-id="293e2-121">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="293e2-122">或者，與 `<cmdlet-name> -?` 相同 `Get-Help` ，但僅適用于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="293e2-122">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="293e2-123">`Get-Help` 取得從電腦的說明檔中顯示的說明內容。</span><span class="sxs-lookup"><span data-stu-id="293e2-123">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="293e2-124">如果沒有說明檔，則 `Get-Help` 只會顯示有關 Cmdlet 的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="293e2-124">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="293e2-125">有些 PowerShell 模組包含說明檔。</span><span class="sxs-lookup"><span data-stu-id="293e2-125">Some PowerShell modules include help files.</span></span> <span data-ttu-id="293e2-126">從 PowerShell 3.0 開始，Windows 作業系統隨附的模組不會包含說明檔。</span><span class="sxs-lookup"><span data-stu-id="293e2-126">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="293e2-127">若要下載或更新 PowerShell 3.0 中模組的說明檔，請使用 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="293e2-127">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="293e2-128">您也可以在 Microsoft Docs 的線上查看 PowerShell 說明文件。若要取得說明檔的線上版本，請使用 **online** 參數，例如： `Get-Help Get-Process -Online` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-128">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="293e2-129">若要閱讀所有的 PowerShell 檔，請參閱 Microsoft Docs [Powershell 檔](/powershell)集。</span><span class="sxs-lookup"><span data-stu-id="293e2-129">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="293e2-130">如果您輸入的 `Get-Help` 是說明文章的完整名稱，或說明文章的唯一單字，則會 `Get-Help` 顯示文章的內容。</span><span class="sxs-lookup"><span data-stu-id="293e2-130">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="293e2-131">如果您指定命令別名的完整名稱，則會 `Get-Help` 顯示原始命令的說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-131">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="293e2-132">如果您輸入在數個說明文章標題中出現的單字或單字模式，則會 `Get-Help` 顯示相符標題的清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-132">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="293e2-133">如果您輸入任何不會出現在任何說明文章標題中的文字，則會 `Get-Help` 顯示其內容中包含該文字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-133">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="293e2-134">`Get-Help` 可以取得所有支援的語言和地區設定的說明文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-134">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="293e2-135">`Get-Help` 先在 Windows 的地區設定中尋找說明檔，然後在父地區設定中尋找說明檔， **例如 pt** **-BR** ，然後在回溯地區設定中。</span><span class="sxs-lookup"><span data-stu-id="293e2-135">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="293e2-136">從 PowerShell 3.0 開始，如果在回溯 `Get-Help` 地區設定中找不到說明，則會在傳回錯誤訊息或顯示自動產生的說明之前，先尋找英文（ **en-us** ）的說明文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-136">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="293e2-137">如需 `Get-Help` 在命令語法圖表中顯示之符號的詳細資訊，請參閱 [about_Command_Syntax](./About/about_Command_Syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="293e2-137">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="293e2-138">如需參數屬性的相關資訊，例如 [ **必要** ] 和 [ **位置** ]，請參閱 [about_Parameters](./About/about_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="293e2-138">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="293e2-139">在 PowerShell 3.0 和 PowerShell 4.0 中， `Get-Help` 除非將模組匯入目前的會話，否則找不到模組中的 **相關** 文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-139">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="293e2-140">這是已知的問題。</span><span class="sxs-lookup"><span data-stu-id="293e2-140">This is a known issue.</span></span> <span data-ttu-id="293e2-141">若要取得模組中的 **相關** 文章，請使用 `Import-Module` Cmdlet 或執行模組中包含的 Cmdlet 來匯入模組。</span><span class="sxs-lookup"><span data-stu-id="293e2-141">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="293e2-142">範例</span><span class="sxs-lookup"><span data-stu-id="293e2-142">EXAMPLES</span></span>

### <span data-ttu-id="293e2-143">範例1：顯示有關 Cmdlet 的基本說明資訊</span><span class="sxs-lookup"><span data-stu-id="293e2-143">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="293e2-144">這些範例會顯示 Cmdlet 的基本說明資訊 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-144">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="293e2-145">`Get-Help <cmdlet-name>` 是 Cmdlet 的最簡單和預設語法 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-145">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="293e2-146">您可以省略 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="293e2-146">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="293e2-147">語法 `<cmdlet-name> -?` 只適用于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="293e2-147">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="293e2-148">範例2：一次顯示一個頁面的基本資訊</span><span class="sxs-lookup"><span data-stu-id="293e2-148">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="293e2-149">這些範例會 `Format-Table` 一次顯示一頁 Cmdlet 的基本說明資訊。</span><span class="sxs-lookup"><span data-stu-id="293e2-149">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="293e2-150">`help` 是一種函式，會在 `Get-Help` 內部執行 Cmdlet，並一次顯示一個頁面的結果。</span><span class="sxs-lookup"><span data-stu-id="293e2-150">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="293e2-151">`man` 這是函數的別名 `help` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-151">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="293e2-152">`Get-Help Format-Table` 將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="293e2-152">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="293e2-153">`Out-Host -Paging` 接收管線的輸出，並一次顯示一個頁面。</span><span class="sxs-lookup"><span data-stu-id="293e2-153">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="293e2-154">如需詳細資訊，請參閱 [Out-Host](Out-Host.md)。</span><span class="sxs-lookup"><span data-stu-id="293e2-154">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="293e2-155">範例3：顯示 Cmdlet 的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="293e2-155">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="293e2-156">這些範例會顯示更詳細的 Cmdlet 說明資訊 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-156">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="293e2-157">**詳細** 的參數會顯示說明文章的詳細資訊，其中包含參數說明和範例。</span><span class="sxs-lookup"><span data-stu-id="293e2-157">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="293e2-158">**Full** 參數會顯示說明文章的完整視圖，其中包含參數描述、範例、輸入和輸出物件類型，以及其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="293e2-158">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="293e2-159">**詳細** 的和 **完整** 參數只適用于電腦上已安裝說明檔的命令。</span><span class="sxs-lookup"><span data-stu-id="293e2-159">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="293e2-160">這些參數對概念 ( **about_** ) 說明文章而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="293e2-160">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="293e2-161">範例4：使用參數顯示 Cmdlet 的選取部分</span><span class="sxs-lookup"><span data-stu-id="293e2-161">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="293e2-162">這些範例會顯示 Cmdlet 說明的選取部分 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-162">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="293e2-163">**範例** 參數會顯示說明檔的 **名稱** 和 **概要** 區段，以及所有範例。</span><span class="sxs-lookup"><span data-stu-id="293e2-163">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="293e2-164">您無法指定範例編號，因為 **範例** 參數是切換參數。</span><span class="sxs-lookup"><span data-stu-id="293e2-164">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="293e2-165">**參數** 參數只會顯示指定參數的描述。</span><span class="sxs-lookup"><span data-stu-id="293e2-165">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="293e2-166">如果您只指定星號 (`*`) 萬用字元，則會顯示所有參數的描述。</span><span class="sxs-lookup"><span data-stu-id="293e2-166">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="293e2-167">當 **參數** 指定參數名稱（例如 **GroupBy** ）時，就會顯示該參數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="293e2-167">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="293e2-168">這些參數對概念 ( **about_** ) 說明文章而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="293e2-168">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="293e2-169">範例5：顯示線上版本的說明</span><span class="sxs-lookup"><span data-stu-id="293e2-169">Example 5: Display online version of help</span></span>

<span data-ttu-id="293e2-170">此範例會 `Format-Table` 在您的預設網頁瀏覽器中顯示此 Cmdlet 的說明文章的線上版本。</span><span class="sxs-lookup"><span data-stu-id="293e2-170">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="293e2-171">範例6：顯示 help 系統的說明</span><span class="sxs-lookup"><span data-stu-id="293e2-171">Example 6: Display help about the help system</span></span>

<span data-ttu-id="293e2-172">`Get-Help`沒有參數的 Cmdlet 會顯示 PowerShell 說明系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="293e2-172">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="293e2-173">範例7：顯示可用的說明文章</span><span class="sxs-lookup"><span data-stu-id="293e2-173">Example 7: Display available help articles</span></span>

<span data-ttu-id="293e2-174">此範例會顯示電腦上可用的所有說明文章清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-174">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="293e2-175">範例8：顯示概念性文章清單</span><span class="sxs-lookup"><span data-stu-id="293e2-175">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="293e2-176">此範例會顯示 PowerShell 說明中包含的概念性文章清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-176">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="293e2-177">這些文章都是以 **about_** 的字元開頭。</span><span class="sxs-lookup"><span data-stu-id="293e2-177">All these articles begin with the characters **about_** .</span></span> <span data-ttu-id="293e2-178">若要顯示特定的說明檔，請輸入 `Get-Help \<about_article-name\>` ，例如 `Get-Help about_Signing` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-178">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="293e2-179">只會顯示在您的電腦上安裝說明檔的概念性文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-179">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="293e2-180">如需有關在 PowerShell 3.0 中下載和安裝說明檔的詳細資訊，請參閱 [update-help](Update-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="293e2-180">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="293e2-181">範例9：在 Cmdlet 說明中搜尋單字</span><span class="sxs-lookup"><span data-stu-id="293e2-181">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="293e2-182">此範例示範如何在 Cmdlet 說明文章中搜尋單字。</span><span class="sxs-lookup"><span data-stu-id="293e2-182">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="293e2-183">`Get-Help` 使用 **Full** 參數來取得的說明資訊 `Add-Member` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-183">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="293e2-184">**MamlCommandHelpInfo** 物件會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="293e2-184">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="293e2-185">`Out-String` 使用 **資料流程** 參數將物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="293e2-185">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="293e2-186">`Select-String` 使用 **Pattern** 參數來搜尋字串以進行 **Clixml** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-186">`Select-String` uses the **Pattern** parameter to search the string for **Clixml** .</span></span>

### <span data-ttu-id="293e2-187">範例10：顯示包含單字的文章清單</span><span class="sxs-lookup"><span data-stu-id="293e2-187">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="293e2-188">此範例會顯示包含「 **遠端處理** 」一字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-188">This example displays a list of articles that include the word **remoting** .</span></span>

<span data-ttu-id="293e2-189">當您輸入未出現在任何文章標題中的單字時，會 `Get-Help` 顯示包含該單字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-189">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### <span data-ttu-id="293e2-190">範例11：顯示提供者特定說明</span><span class="sxs-lookup"><span data-stu-id="293e2-190">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="293e2-191">這個範例示範兩種取得提供者特定說明的方式 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-191">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="293e2-192">這些命令會取得說明如何 `Get-Item` 在 PowerShell SQL Server 提供者的 **DataCollection** 節點中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="293e2-192">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="293e2-193">第一個範例會使用 `Get-Help` **Path** 參數來指定 SQL Server 提供者的路徑。</span><span class="sxs-lookup"><span data-stu-id="293e2-193">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="293e2-194">由於已指定提供者的路徑，因此您可以從任何路徑位置執行此命令。</span><span class="sxs-lookup"><span data-stu-id="293e2-194">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="293e2-195">第二個範例會使用 `Set-Location` 來流覽至 SQL Server 提供者的路徑。</span><span class="sxs-lookup"><span data-stu-id="293e2-195">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="293e2-196">從該位置中，不需要 **Path** 參數 `Get-Help` 來取得提供者特定的說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-196">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### <span data-ttu-id="293e2-197">範例12：顯示腳本的說明</span><span class="sxs-lookup"><span data-stu-id="293e2-197">Example 12: Display help for a script</span></span>

<span data-ttu-id="293e2-198">這個範例會取得的說明 `MyScript.ps1 script` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-198">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="293e2-199">如需如何撰寫函數和腳本說明的相關資訊，請參閱 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="293e2-199">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="293e2-200">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="293e2-200">PARAMETERS</span></span>

### <span data-ttu-id="293e2-201">-Category</span><span class="sxs-lookup"><span data-stu-id="293e2-201">-Category</span></span>

<span data-ttu-id="293e2-202">僅針對指定類別中的項目顯示說明及其別名。</span><span class="sxs-lookup"><span data-stu-id="293e2-202">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="293e2-203">概念文章位於 [功能 **説明** ] 分類中。</span><span class="sxs-lookup"><span data-stu-id="293e2-203">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="293e2-204">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="293e2-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="293e2-205">Alias</span><span class="sxs-lookup"><span data-stu-id="293e2-205">Alias</span></span>
- <span data-ttu-id="293e2-206">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="293e2-206">Cmdlet</span></span>
- <span data-ttu-id="293e2-207">提供者</span><span class="sxs-lookup"><span data-stu-id="293e2-207">Provider</span></span>
- <span data-ttu-id="293e2-208">一般</span><span class="sxs-lookup"><span data-stu-id="293e2-208">General</span></span>
- <span data-ttu-id="293e2-209">常見問題集</span><span class="sxs-lookup"><span data-stu-id="293e2-209">FAQ</span></span>
- <span data-ttu-id="293e2-210">詞彙</span><span class="sxs-lookup"><span data-stu-id="293e2-210">Glossary</span></span>
- <span data-ttu-id="293e2-211">HelpFile</span><span class="sxs-lookup"><span data-stu-id="293e2-211">HelpFile</span></span>
- <span data-ttu-id="293e2-212">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="293e2-212">ScriptCommand</span></span>
- <span data-ttu-id="293e2-213">函式</span><span class="sxs-lookup"><span data-stu-id="293e2-213">Function</span></span>
- <span data-ttu-id="293e2-214">Filter</span><span class="sxs-lookup"><span data-stu-id="293e2-214">Filter</span></span>
- <span data-ttu-id="293e2-215">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="293e2-215">ExternalScript</span></span>
- <span data-ttu-id="293e2-216">全部</span><span class="sxs-lookup"><span data-stu-id="293e2-216">All</span></span>
- <span data-ttu-id="293e2-217">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="293e2-217">DefaultHelp</span></span>
- <span data-ttu-id="293e2-218">工作流程</span><span class="sxs-lookup"><span data-stu-id="293e2-218">Workflow</span></span>
- <span data-ttu-id="293e2-219">DscResource</span><span class="sxs-lookup"><span data-stu-id="293e2-219">DscResource</span></span>
- <span data-ttu-id="293e2-220">類別</span><span class="sxs-lookup"><span data-stu-id="293e2-220">Class</span></span>
- <span data-ttu-id="293e2-221">組態</span><span class="sxs-lookup"><span data-stu-id="293e2-221">Configuration</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="293e2-222">-元件</span><span class="sxs-lookup"><span data-stu-id="293e2-222">-Component</span></span>

<span data-ttu-id="293e2-223">顯示具有指定元件值的命令，例如 **Exchange** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-223">Displays commands with the specified component value, such as **Exchange** .</span></span> <span data-ttu-id="293e2-224">輸入元件名稱。</span><span class="sxs-lookup"><span data-stu-id="293e2-224">Enter a component name.</span></span>
<span data-ttu-id="293e2-225">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="293e2-225">Wildcard characters are permitted.</span></span> <span data-ttu-id="293e2-226">此參數不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="293e2-226">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="293e2-227">-Detailed</span><span class="sxs-lookup"><span data-stu-id="293e2-227">-Detailed</span></span>

<span data-ttu-id="293e2-228">將參數說明和範例新增到基本的說明顯示中。</span><span class="sxs-lookup"><span data-stu-id="293e2-228">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="293e2-229">只有當電腦上已安裝說明檔時，此參數才會生效。</span><span class="sxs-lookup"><span data-stu-id="293e2-229">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="293e2-230">它不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="293e2-230">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="293e2-231">-Examples</span><span class="sxs-lookup"><span data-stu-id="293e2-231">-Examples</span></span>

<span data-ttu-id="293e2-232">只顯示名稱、概要和範例。</span><span class="sxs-lookup"><span data-stu-id="293e2-232">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="293e2-233">若只要顯示範例，請輸入 `(Get-Help \<cmdlet-name\>).Examples` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-233">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="293e2-234">只有當電腦上已安裝說明檔時，此參數才會生效。</span><span class="sxs-lookup"><span data-stu-id="293e2-234">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="293e2-235">它不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="293e2-235">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="293e2-236">-Full</span><span class="sxs-lookup"><span data-stu-id="293e2-236">-Full</span></span>

<span data-ttu-id="293e2-237">顯示 Cmdlet 的整個說明文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-237">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="293e2-238">**Full** 包含參數說明和屬性、範例、輸入和輸出物件類型，以及其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="293e2-238">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="293e2-239">只有當電腦上已安裝說明檔時，此參數才會生效。</span><span class="sxs-lookup"><span data-stu-id="293e2-239">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="293e2-240">它不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="293e2-240">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="293e2-241">-功能</span><span class="sxs-lookup"><span data-stu-id="293e2-241">-Functionality</span></span>

<span data-ttu-id="293e2-242">顯示具有指定功能的項目說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-242">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="293e2-243">輸入功能。</span><span class="sxs-lookup"><span data-stu-id="293e2-243">Enter the functionality.</span></span> <span data-ttu-id="293e2-244">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="293e2-244">Wildcard characters are permitted.</span></span> <span data-ttu-id="293e2-245">此參數不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="293e2-245">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="293e2-246">-Name</span><span class="sxs-lookup"><span data-stu-id="293e2-246">-Name</span></span>

<span data-ttu-id="293e2-247">取得指定命令或概念的相關說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-247">Gets help about the specified command or concept.</span></span> <span data-ttu-id="293e2-248">輸入 Cmdlet、函式、提供者、腳本或工作流程的名稱，例如概念發行項 `Get-Member` 名稱（例如 `about_Objects` ）或別名（例如） `ls` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-248">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="293e2-249">Cmdlet 和提供者名稱中允許使用萬用字元，但是您不能使用萬用字元來尋找函式說明和腳本說明文章的名稱。</span><span class="sxs-lookup"><span data-stu-id="293e2-249">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="293e2-250">若要取得不是位於環境變數所列路徑中的腳本說明 `$env:Path` ，請輸入腳本的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="293e2-250">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="293e2-251">如果您輸入說明文章的完整名稱，則會 `Get-Help` 顯示文章內容。</span><span class="sxs-lookup"><span data-stu-id="293e2-251">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="293e2-252">如果您輸入在數個說明文章標題中出現的單字或單字模式，則會 `Get-Help` 顯示相符標題的清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-252">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="293e2-253">如果您輸入任何不符合任何說明文章標題的文字，則會 `Get-Help` 在其內容中顯示包含該文字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="293e2-253">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="293e2-254">概念文章的名稱（例如 `about_Objects` ）必須以英文輸入，即使是在非英文版的 PowerShell 中也一樣。</span><span class="sxs-lookup"><span data-stu-id="293e2-254">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="293e2-255">-Online</span><span class="sxs-lookup"><span data-stu-id="293e2-255">-Online</span></span>

<span data-ttu-id="293e2-256">在預設瀏覽器中顯示說明文章的線上版本。</span><span class="sxs-lookup"><span data-stu-id="293e2-256">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="293e2-257">此參數僅適用于 Cmdlet、函式、工作流程和腳本說明文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-257">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="293e2-258">您無法 **Online** `Get-Help` 在遠端會話中使用 Online 參數。</span><span class="sxs-lookup"><span data-stu-id="293e2-258">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="293e2-259">如需有關在您撰寫的說明文章中支援這項功能的詳細資訊，請參閱 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)和 [支援線上說明](/powershell/scripting/developer/module/supporting-online-help)，以及 [撰寫 PowerShell Cmdlet 的](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-259">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="293e2-260">-Parameter</span><span class="sxs-lookup"><span data-stu-id="293e2-260">-Parameter</span></span>

<span data-ttu-id="293e2-261">只顯示指定參數的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-261">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="293e2-262">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="293e2-262">Wildcards are permitted.</span></span> <span data-ttu-id="293e2-263">此參數不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="293e2-263">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="293e2-264">-Path</span><span class="sxs-lookup"><span data-stu-id="293e2-264">-Path</span></span>

<span data-ttu-id="293e2-265">取得說明 Cmdlet 如何在指定的提供者路徑中運作的說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-265">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="293e2-266">輸入 PowerShell 提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="293e2-266">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="293e2-267">此參數會取得 Cmdlet 說明文章的自訂版本，說明該 Cmdlet 如何在指定的 PowerShell 提供者路徑中運作。</span><span class="sxs-lookup"><span data-stu-id="293e2-267">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="293e2-268">此參數僅適用于提供者 Cmdlet 的說明，而且只有在提供者于其說明檔中包含自訂版本的提供者 Cmdlet 說明文章時才會生效。</span><span class="sxs-lookup"><span data-stu-id="293e2-268">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="293e2-269">若要使用這個參數，請針對包含提供者的模組安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="293e2-269">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="293e2-270">若要查看提供者路徑的自訂 Cmdlet 說明，請移至提供者路徑位置並輸入 `Get-Help` 命令，或從任何路徑位置，使用的 **path** 參數 `Get-Help` 指定提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="293e2-270">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="293e2-271">您也可以在 [說明] 文章的 [提供者說明] 區段中，線上找到自訂的 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-271">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="293e2-272">如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](./About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="293e2-272">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="293e2-273">-Role</span><span class="sxs-lookup"><span data-stu-id="293e2-273">-Role</span></span>

<span data-ttu-id="293e2-274">顯示針對指定使用者角色自訂的說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-274">Displays help customized for the specified user role.</span></span> <span data-ttu-id="293e2-275">輸入角色。</span><span class="sxs-lookup"><span data-stu-id="293e2-275">Enter a role.</span></span> <span data-ttu-id="293e2-276">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="293e2-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="293e2-277">輸入使用者在組織中扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="293e2-277">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="293e2-278">某些 Cmdlet 會根據這個參數值，在說明檔中顯示不同的文字。</span><span class="sxs-lookup"><span data-stu-id="293e2-278">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="293e2-279">這個參數不會對核心 Cmdlet 的說明產生任何影響。</span><span class="sxs-lookup"><span data-stu-id="293e2-279">This parameter has no effect on help for the core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="293e2-280">-ShowWindow</span><span class="sxs-lookup"><span data-stu-id="293e2-280">-ShowWindow</span></span>

<span data-ttu-id="293e2-281">在視窗中顯示說明主題，以便更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="293e2-281">Displays the help topic in a window for easier reading.</span></span> <span data-ttu-id="293e2-282">此視窗包含 [ **尋找** 搜尋] 功能和 **[設定]** 方塊，可讓您設定顯示器的選項，包括只顯示所選說明主題區段的選項。</span><span class="sxs-lookup"><span data-stu-id="293e2-282">The window includes a **Find** search feature and a **Settings** box that lets you set options for the display, including options to display only selected sections of a help topic.</span></span>

<span data-ttu-id="293e2-283">**ShowWindow** 參數支援命令的說明主題 (Cmdlet、函式、CIM 命令、腳本) 和概念 **相關** 的文章。</span><span class="sxs-lookup"><span data-stu-id="293e2-283">The **ShowWindow** parameter supports help topics for commands (cmdlets, functions, CIM commands, scripts) and conceptual **About** articles.</span></span> <span data-ttu-id="293e2-284">它不支援提供者說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-284">It does not support provider help.</span></span>

<span data-ttu-id="293e2-285">PowerShell 7.0 中已重新引入此參數。</span><span class="sxs-lookup"><span data-stu-id="293e2-285">This parameter was reintroduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="293e2-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="293e2-286">CommonParameters</span></span>

<span data-ttu-id="293e2-287">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="293e2-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="293e2-288">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="293e2-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="293e2-289">輸入</span><span class="sxs-lookup"><span data-stu-id="293e2-289">INPUTS</span></span>

### <span data-ttu-id="293e2-290">無</span><span class="sxs-lookup"><span data-stu-id="293e2-290">None</span></span>

<span data-ttu-id="293e2-291">您無法將物件沿著管線向下傳送至 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-291">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="293e2-292">輸出</span><span class="sxs-lookup"><span data-stu-id="293e2-292">OUTPUTS</span></span>

### <span data-ttu-id="293e2-293">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="293e2-293">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="293e2-294">如果您在沒有說明檔的 `Get-Help` 命令上執行，則會傳回代表自動產生說明的 `Get-Help` **ExtendedCmdletHelpInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="293e2-294">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="293e2-295">System.String</span><span class="sxs-lookup"><span data-stu-id="293e2-295">System.String</span></span>

<span data-ttu-id="293e2-296">如果您取得概念性說明文章，則 `Get-Help` 會以字串形式傳回。</span><span class="sxs-lookup"><span data-stu-id="293e2-296">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="293e2-297">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="293e2-297">MamlCommandHelpInfo</span></span>

<span data-ttu-id="293e2-298">如果您收到具有說明檔的命令，則會傳回 `Get-Help` **MamlCommandHelpInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="293e2-298">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="293e2-299">注意</span><span class="sxs-lookup"><span data-stu-id="293e2-299">NOTES</span></span>

<span data-ttu-id="293e2-300">PowerShell 3.0 不包含說明檔。</span><span class="sxs-lookup"><span data-stu-id="293e2-300">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="293e2-301">若要下載並安裝讀取的說明檔 `Get-Help` ，請使用 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="293e2-301">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="293e2-302">您可以使用指令程式 `Update-Help` 來下載並安裝 PowerShell 隨附的核心命令的說明檔，以及您安裝的任何模組。</span><span class="sxs-lookup"><span data-stu-id="293e2-302">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="293e2-303">您也可以使用它來更新說明檔，讓電腦上的說明永遠都不會過期。</span><span class="sxs-lookup"><span data-stu-id="293e2-303">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="293e2-304">您也可以閱讀有關 PowerShell online 命令的說明文章，從 [消費者入門與 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)開始。</span><span class="sxs-lookup"><span data-stu-id="293e2-304">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="293e2-305">`Get-Help` 在針對 Windows 作業系統設定的地區設定中，或在該地區設定的備用語言中顯示說明。</span><span class="sxs-lookup"><span data-stu-id="293e2-305">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="293e2-306">如果您沒有主要或備用地區設定的說明檔，其 `Get-Help` 行為就如同電腦上沒有說明檔一樣。</span><span class="sxs-lookup"><span data-stu-id="293e2-306">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="293e2-307">若要取得不同地區設定的說明，請使用主控台中的 **地區** 和 **語言** 來變更設定。</span><span class="sxs-lookup"><span data-stu-id="293e2-307">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="293e2-308">在 Windows 10、 **設定** 、 **時間 & 語言** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-308">On Windows 10, **Settings** , **Time & Language** .</span></span>

<span data-ttu-id="293e2-309">[說明] 的完整觀點包括參數的相關資訊表。</span><span class="sxs-lookup"><span data-stu-id="293e2-309">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="293e2-310">該表格包含下列欄位：</span><span class="sxs-lookup"><span data-stu-id="293e2-310">The table includes the following fields:</span></span>

- <span data-ttu-id="293e2-311">**必要** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-311">**Required** .</span></span> <span data-ttu-id="293e2-312">指出參數是否為必要 (true) 或選擇性 (false)。</span><span class="sxs-lookup"><span data-stu-id="293e2-312">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="293e2-313">**位置** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-313">**Position** .</span></span> <span data-ttu-id="293e2-314">指出參數的名稱是否為或 (數值) 的位置。</span><span class="sxs-lookup"><span data-stu-id="293e2-314">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="293e2-315">位置參數必須出現在命令中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="293e2-315">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="293e2-316">**指名** 的表示參數名稱是必要的，但參數可以出現在命令中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="293e2-316">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="293e2-317">**數值** 表示參數名稱是選擇性的，但若省略名稱，參數必須位於數位所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="293e2-317">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="293e2-318">例如， `2` 指出當省略參數名稱時，參數必須是命令中的第二個或唯一未命名的參數。</span><span class="sxs-lookup"><span data-stu-id="293e2-318">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="293e2-319">使用參數名稱時，參數可以出現在命令中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="293e2-319">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="293e2-320">**預設值** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-320">**Default value** .</span></span> <span data-ttu-id="293e2-321">如果您未在命令中包含參數，則 PowerShell 會使用的參數值或預設行為。</span><span class="sxs-lookup"><span data-stu-id="293e2-321">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="293e2-322">接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="293e2-322">Accepts pipeline input.</span></span> <span data-ttu-id="293e2-323">指出您是否可以 (true) 或無法 (false) 透過管線將物件傳送至參數。</span><span class="sxs-lookup"><span data-stu-id="293e2-323">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="293e2-324">**根據屬性名稱** ，表示管線物件必須具有與參數名稱相同名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="293e2-324">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="293e2-325">**接受萬用字元** 。</span><span class="sxs-lookup"><span data-stu-id="293e2-325">**Accepts wildcard characters** .</span></span> <span data-ttu-id="293e2-326">指出參數值是否可以包含萬用字元，例如星號 (`*`) 或 () 的問號 `?` 。</span><span class="sxs-lookup"><span data-stu-id="293e2-326">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="293e2-327">相關連結</span><span class="sxs-lookup"><span data-stu-id="293e2-327">RELATED LINKS</span></span>

[<span data-ttu-id="293e2-328">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="293e2-328">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="293e2-329">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="293e2-329">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="293e2-330">Get-Command</span><span class="sxs-lookup"><span data-stu-id="293e2-330">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="293e2-331">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="293e2-331">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="293e2-332">Update-Help</span><span class="sxs-lookup"><span data-stu-id="293e2-332">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="293e2-333">撰寫註解型說明主題</span><span class="sxs-lookup"><span data-stu-id="293e2-333">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="293e2-334">撰寫 PowerShell Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="293e2-334">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

