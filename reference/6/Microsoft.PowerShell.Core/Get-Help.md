---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 691709fe3f5e4908ab3203df73f636981adf560c
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205799"
---
# <span data-ttu-id="d0f7a-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="d0f7a-103">Get-Help</span></span>

## <span data-ttu-id="d0f7a-104">概要</span><span class="sxs-lookup"><span data-stu-id="d0f7a-104">SYNOPSIS</span></span>
<span data-ttu-id="d0f7a-105">顯示 PowerShell 命令和概念的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="d0f7a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d0f7a-106">SYNTAX</span></span>

### <span data-ttu-id="d0f7a-107">AllUsersView (預設) </span><span class="sxs-lookup"><span data-stu-id="d0f7a-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d0f7a-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="d0f7a-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] -Detailed [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d0f7a-109">範例</span><span class="sxs-lookup"><span data-stu-id="d0f7a-109">Examples</span></span>

```
Get-Help [[-Name] <String>] -Examples [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d0f7a-110">參數</span><span class="sxs-lookup"><span data-stu-id="d0f7a-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] -Parameter <String[]> [-Path <String>] [-Category <String[]>]
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d0f7a-111">線上</span><span class="sxs-lookup"><span data-stu-id="d0f7a-111">Online</span></span>

```
Get-Help [[-Name] <String>] -Online [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d0f7a-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d0f7a-112">DESCRIPTION</span></span>

<span data-ttu-id="d0f7a-113">此 `Get-Help` Cmdlet 會顯示 PowerShell 概念和命令的相關資訊，包括 Cmdlet、函式、通用訊息模型 (CIM) 命令、工作流程、提供者、別名和腳本。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-113">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="d0f7a-114">若要取得 PowerShell Cmdlet 的說明，請輸入 `Get-Help` 後面接著 Cmdlet 名稱，例如： `Get-Help Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-114">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="d0f7a-115">PowerShell 中的概念性說明文章的開頭是 **about_** ，例如 **about_Comparison_Operators** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-115">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators** .</span></span> <span data-ttu-id="d0f7a-116">若要查看所有 **about_** 文章，請輸入 `Get-Help about_*` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-116">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="d0f7a-117">若要查看特定的文章，請輸入 `Get-Help about_<article-name>` ，例如 `Get-Help about_Comparison_Operators` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-117">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="d0f7a-118">若要取得 PowerShell 提供者的說明，請輸入， `Get-Help` 後面接著提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-118">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="d0f7a-119">例如，若要取得憑證提供者的說明，請輸入 `Get-Help Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-119">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="d0f7a-120">您也可以輸入 `help` 或 `man` ，一次顯示一個螢幕的文字。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-120">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="d0f7a-121">或者，與 `<cmdlet-name> -?` 相同 `Get-Help` ，但僅適用于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-121">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="d0f7a-122">`Get-Help` 取得從電腦的說明檔中顯示的說明內容。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-122">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="d0f7a-123">如果沒有說明檔，則 `Get-Help` 只會顯示有關 Cmdlet 的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-123">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="d0f7a-124">有些 PowerShell 模組包含說明檔。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-124">Some PowerShell modules include help files.</span></span> <span data-ttu-id="d0f7a-125">從 PowerShell 3.0 開始，Windows 作業系統隨附的模組不會包含說明檔。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-125">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="d0f7a-126">若要下載或更新 PowerShell 3.0 中模組的說明檔，請使用 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-126">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="d0f7a-127">您也可以在 Microsoft Docs 的線上查看 PowerShell 說明文件。若要取得說明檔的線上版本，請使用 **online** 參數，例如： `Get-Help Get-Process -Online` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-127">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="d0f7a-128">若要閱讀所有的 PowerShell 檔，請參閱 Microsoft Docs [Powershell 檔](/powershell)集。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-128">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="d0f7a-129">如果您輸入的 `Get-Help` 是說明文章的完整名稱，或說明文章的唯一單字，則會 `Get-Help` 顯示文章的內容。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-129">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="d0f7a-130">如果您指定命令別名的完整名稱，則會 `Get-Help` 顯示原始命令的說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-130">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="d0f7a-131">如果您輸入在數個說明文章標題中出現的單字或單字模式，則會 `Get-Help` 顯示相符標題的清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-131">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="d0f7a-132">如果您輸入任何不會出現在任何說明文章標題中的文字，則會 `Get-Help` 顯示其內容中包含該文字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-132">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="d0f7a-133">`Get-Help` 可以取得所有支援的語言和地區設定的說明文章。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-133">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="d0f7a-134">`Get-Help` 先在 Windows 的地區設定中尋找說明檔，然後在父地區設定中尋找說明檔， **例如 pt** **-BR** ，然後在回溯地區設定中。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-134">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="d0f7a-135">從 PowerShell 3.0 開始，如果在回溯 `Get-Help` 地區設定中找不到說明，則會在傳回錯誤訊息或顯示自動產生的說明之前，先尋找英文（ **en-us** ）的說明文章。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-135">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="d0f7a-136">如需 `Get-Help` 在命令語法圖表中顯示之符號的詳細資訊，請參閱 [about_Command_Syntax](./About/about_Command_Syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-136">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="d0f7a-137">如需參數屬性的相關資訊，例如 [ **必要** ] 和 [ **位置** ]，請參閱 [about_Parameters](./About/about_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-137">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="d0f7a-138">在 PowerShell 3.0 和 PowerShell 4.0 中， `Get-Help` 除非將模組匯入目前的會話，否則找不到模組中的 **相關** 文章。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-138">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="d0f7a-139">這是已知的問題。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-139">This is a known issue.</span></span> <span data-ttu-id="d0f7a-140">若要取得模組中的 **相關** 文章，請使用 `Import-Module` Cmdlet 或執行模組中包含的 Cmdlet 來匯入模組。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-140">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="d0f7a-141">範例</span><span class="sxs-lookup"><span data-stu-id="d0f7a-141">EXAMPLES</span></span>

### <span data-ttu-id="d0f7a-142">範例1：顯示有關 Cmdlet 的基本說明資訊</span><span class="sxs-lookup"><span data-stu-id="d0f7a-142">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="d0f7a-143">這些範例會顯示 Cmdlet 的基本說明資訊 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-143">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="d0f7a-144">`Get-Help <cmdlet-name>` 是 Cmdlet 的最簡單和預設語法 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-144">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="d0f7a-145">您可以省略 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-145">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="d0f7a-146">語法 `<cmdlet-name> -?` 只適用于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-146">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="d0f7a-147">範例2：一次顯示一個頁面的基本資訊</span><span class="sxs-lookup"><span data-stu-id="d0f7a-147">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="d0f7a-148">這些範例會 `Format-Table` 一次顯示一頁 Cmdlet 的基本說明資訊。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-148">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="d0f7a-149">`help` 是一種函式，會在 `Get-Help` 內部執行 Cmdlet，並一次顯示一個頁面的結果。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-149">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="d0f7a-150">`man` 這是函數的別名 `help` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-150">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="d0f7a-151">`Get-Help Format-Table` 將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-151">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="d0f7a-152">`Out-Host -Paging` 接收管線的輸出，並一次顯示一個頁面。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-152">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="d0f7a-153">如需詳細資訊，請參閱 [Out-Host](Out-Host.md)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-153">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="d0f7a-154">範例3：顯示 Cmdlet 的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d0f7a-154">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="d0f7a-155">這些範例會顯示更詳細的 Cmdlet 說明資訊 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-155">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="d0f7a-156">**詳細** 的參數會顯示說明文章的詳細資訊，其中包含參數說明和範例。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-156">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="d0f7a-157">**Full** 參數會顯示說明文章的完整視圖，其中包含參數描述、範例、輸入和輸出物件類型，以及其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-157">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="d0f7a-158">**詳細** 的和 **完整** 參數只適用于電腦上已安裝說明檔的命令。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-158">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="d0f7a-159">這些參數對概念 ( **about_** ) 說明文章而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-159">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="d0f7a-160">範例4：使用參數顯示 Cmdlet 的選取部分</span><span class="sxs-lookup"><span data-stu-id="d0f7a-160">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="d0f7a-161">這些範例會顯示 Cmdlet 說明的選取部分 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-161">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="d0f7a-162">**範例** 參數會顯示說明檔的 **名稱** 和 **概要** 區段，以及所有範例。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-162">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="d0f7a-163">您無法指定範例編號，因為 **範例** 參數是切換參數。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-163">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="d0f7a-164">**參數** 參數只會顯示指定參數的描述。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-164">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="d0f7a-165">如果您只指定星號 (`*`) 萬用字元，則會顯示所有參數的描述。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-165">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="d0f7a-166">當 **參數** 指定參數名稱（例如 **GroupBy** ）時，就會顯示該參數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-166">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="d0f7a-167">這些參數對概念 ( **about_** ) 說明文章而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-167">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="d0f7a-168">範例5：顯示線上版本的說明</span><span class="sxs-lookup"><span data-stu-id="d0f7a-168">Example 5: Display online version of help</span></span>

<span data-ttu-id="d0f7a-169">此範例會 `Format-Table` 在您的預設網頁瀏覽器中顯示此 Cmdlet 的說明文章的線上版本。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-169">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="d0f7a-170">範例6：顯示 help 系統的說明</span><span class="sxs-lookup"><span data-stu-id="d0f7a-170">Example 6: Display help about the help system</span></span>

<span data-ttu-id="d0f7a-171">`Get-Help`沒有參數的 Cmdlet 會顯示 PowerShell 說明系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-171">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="d0f7a-172">範例7：顯示可用的說明文章</span><span class="sxs-lookup"><span data-stu-id="d0f7a-172">Example 7: Display available help articles</span></span>

<span data-ttu-id="d0f7a-173">此範例會顯示電腦上可用的所有說明文章清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-173">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="d0f7a-174">範例8：顯示概念性文章清單</span><span class="sxs-lookup"><span data-stu-id="d0f7a-174">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="d0f7a-175">此範例會顯示 PowerShell 說明中包含的概念性文章清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-175">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="d0f7a-176">這些文章都是以 **about_** 的字元開頭。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-176">All these articles begin with the characters **about_** .</span></span> <span data-ttu-id="d0f7a-177">若要顯示特定的說明檔，請輸入 `Get-Help \<about_article-name\>` ，例如 `Get-Help about_Signing` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-177">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="d0f7a-178">只會顯示在您的電腦上安裝說明檔的概念性文章。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-178">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="d0f7a-179">如需有關在 PowerShell 3.0 中下載和安裝說明檔的詳細資訊，請參閱 [update-help](Update-Help.md)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-179">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="d0f7a-180">範例9：在 Cmdlet 說明中搜尋單字</span><span class="sxs-lookup"><span data-stu-id="d0f7a-180">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="d0f7a-181">此範例示範如何在 Cmdlet 說明文章中搜尋單字。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-181">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="d0f7a-182">`Get-Help` 使用 **Full** 參數來取得的說明資訊 `Add-Member` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-182">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="d0f7a-183">**MamlCommandHelpInfo** 物件會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-183">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="d0f7a-184">`Out-String` 使用 **資料流程** 參數將物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-184">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="d0f7a-185">`Select-String` 使用 **Pattern** 參數來搜尋字串以進行 **Clixml** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-185">`Select-String` uses the **Pattern** parameter to search the string for **Clixml** .</span></span>

### <span data-ttu-id="d0f7a-186">範例10：顯示包含單字的文章清單</span><span class="sxs-lookup"><span data-stu-id="d0f7a-186">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="d0f7a-187">此範例會顯示包含「 **遠端處理** 」一字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-187">This example displays a list of articles that include the word **remoting** .</span></span>

<span data-ttu-id="d0f7a-188">當您輸入未出現在任何文章標題中的單字時，會 `Get-Help` 顯示包含該單字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-188">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

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

### <span data-ttu-id="d0f7a-189">範例11：顯示提供者特定說明</span><span class="sxs-lookup"><span data-stu-id="d0f7a-189">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="d0f7a-190">這個範例示範兩種取得提供者特定說明的方式 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-190">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="d0f7a-191">這些命令會取得說明如何 `Get-Item` 在 PowerShell SQL Server 提供者的 **DataCollection** 節點中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-191">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="d0f7a-192">第一個範例會使用 `Get-Help` **Path** 參數來指定 SQL Server 提供者的路徑。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-192">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="d0f7a-193">由於已指定提供者的路徑，因此您可以從任何路徑位置執行此命令。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-193">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="d0f7a-194">第二個範例會使用 `Set-Location` 來流覽至 SQL Server 提供者的路徑。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-194">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="d0f7a-195">從該位置中，不需要 **Path** 參數 `Get-Help` 來取得提供者特定的說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-195">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

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

### <span data-ttu-id="d0f7a-196">範例12：顯示腳本的說明</span><span class="sxs-lookup"><span data-stu-id="d0f7a-196">Example 12: Display help for a script</span></span>

<span data-ttu-id="d0f7a-197">這個範例會取得的說明 `MyScript.ps1 script` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-197">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="d0f7a-198">如需如何撰寫函數和腳本說明的相關資訊，請參閱 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-198">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="d0f7a-199">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d0f7a-199">PARAMETERS</span></span>

### <span data-ttu-id="d0f7a-200">-Category</span><span class="sxs-lookup"><span data-stu-id="d0f7a-200">-Category</span></span>

<span data-ttu-id="d0f7a-201">僅針對指定類別中的項目顯示說明及其別名。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-201">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="d0f7a-202">概念文章位於 [功能 **説明** ] 分類中。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-202">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="d0f7a-203">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="d0f7a-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="d0f7a-204">Alias</span><span class="sxs-lookup"><span data-stu-id="d0f7a-204">Alias</span></span>
- <span data-ttu-id="d0f7a-205">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d0f7a-205">Cmdlet</span></span>
- <span data-ttu-id="d0f7a-206">提供者</span><span class="sxs-lookup"><span data-stu-id="d0f7a-206">Provider</span></span>
- <span data-ttu-id="d0f7a-207">一般</span><span class="sxs-lookup"><span data-stu-id="d0f7a-207">General</span></span>
- <span data-ttu-id="d0f7a-208">常見問題集</span><span class="sxs-lookup"><span data-stu-id="d0f7a-208">FAQ</span></span>
- <span data-ttu-id="d0f7a-209">詞彙</span><span class="sxs-lookup"><span data-stu-id="d0f7a-209">Glossary</span></span>
- <span data-ttu-id="d0f7a-210">HelpFile</span><span class="sxs-lookup"><span data-stu-id="d0f7a-210">HelpFile</span></span>
- <span data-ttu-id="d0f7a-211">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="d0f7a-211">ScriptCommand</span></span>
- <span data-ttu-id="d0f7a-212">函式</span><span class="sxs-lookup"><span data-stu-id="d0f7a-212">Function</span></span>
- <span data-ttu-id="d0f7a-213">Filter</span><span class="sxs-lookup"><span data-stu-id="d0f7a-213">Filter</span></span>
- <span data-ttu-id="d0f7a-214">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="d0f7a-214">ExternalScript</span></span>
- <span data-ttu-id="d0f7a-215">全部</span><span class="sxs-lookup"><span data-stu-id="d0f7a-215">All</span></span>
- <span data-ttu-id="d0f7a-216">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="d0f7a-216">DefaultHelp</span></span>
- <span data-ttu-id="d0f7a-217">工作流程</span><span class="sxs-lookup"><span data-stu-id="d0f7a-217">Workflow</span></span>
- <span data-ttu-id="d0f7a-218">DscResource</span><span class="sxs-lookup"><span data-stu-id="d0f7a-218">DscResource</span></span>
- <span data-ttu-id="d0f7a-219">類別</span><span class="sxs-lookup"><span data-stu-id="d0f7a-219">Class</span></span>
- <span data-ttu-id="d0f7a-220">組態</span><span class="sxs-lookup"><span data-stu-id="d0f7a-220">Configuration</span></span>

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

### <span data-ttu-id="d0f7a-221">-元件</span><span class="sxs-lookup"><span data-stu-id="d0f7a-221">-Component</span></span>

<span data-ttu-id="d0f7a-222">顯示具有指定元件值的命令，例如 **Exchange** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-222">Displays commands with the specified component value, such as **Exchange** .</span></span> <span data-ttu-id="d0f7a-223">輸入元件名稱。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-223">Enter a component name.</span></span>
<span data-ttu-id="d0f7a-224">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-224">Wildcard characters are permitted.</span></span> <span data-ttu-id="d0f7a-225">此參數不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-225">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="d0f7a-226">-Detailed</span><span class="sxs-lookup"><span data-stu-id="d0f7a-226">-Detailed</span></span>

<span data-ttu-id="d0f7a-227">將參數說明和範例新增到基本的說明顯示中。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-227">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="d0f7a-228">只有當電腦上已安裝說明檔時，此參數才會生效。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-228">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="d0f7a-229">它不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-229">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="d0f7a-230">-Examples</span><span class="sxs-lookup"><span data-stu-id="d0f7a-230">-Examples</span></span>

<span data-ttu-id="d0f7a-231">只顯示名稱、概要和範例。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-231">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="d0f7a-232">若只要顯示範例，請輸入 `(Get-Help \<cmdlet-name\>).Examples` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-232">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="d0f7a-233">只有當電腦上已安裝說明檔時，此參數才會生效。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-233">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="d0f7a-234">它不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-234">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="d0f7a-235">-Full</span><span class="sxs-lookup"><span data-stu-id="d0f7a-235">-Full</span></span>

<span data-ttu-id="d0f7a-236">顯示 Cmdlet 的整個說明文章。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-236">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="d0f7a-237">**Full** 包含參數說明和屬性、範例、輸入和輸出物件類型，以及其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-237">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="d0f7a-238">只有當電腦上已安裝說明檔時，此參數才會生效。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-238">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="d0f7a-239">它不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-239">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="d0f7a-240">-功能</span><span class="sxs-lookup"><span data-stu-id="d0f7a-240">-Functionality</span></span>

<span data-ttu-id="d0f7a-241">顯示具有指定功能的項目說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-241">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="d0f7a-242">輸入功能。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-242">Enter the functionality.</span></span> <span data-ttu-id="d0f7a-243">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-243">Wildcard characters are permitted.</span></span> <span data-ttu-id="d0f7a-244">此參數不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-244">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="d0f7a-245">-Name</span><span class="sxs-lookup"><span data-stu-id="d0f7a-245">-Name</span></span>

<span data-ttu-id="d0f7a-246">取得指定命令或概念的相關說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-246">Gets help about the specified command or concept.</span></span> <span data-ttu-id="d0f7a-247">輸入 Cmdlet、函式、提供者、腳本或工作流程的名稱，例如概念發行項 `Get-Member` 名稱（例如 `about_Objects` ）或別名（例如） `ls` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-247">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="d0f7a-248">Cmdlet 和提供者名稱中允許使用萬用字元，但是您不能使用萬用字元來尋找函式說明和腳本說明文章的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-248">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="d0f7a-249">若要取得不是位於環境變數所列路徑中的腳本說明 `$env:Path` ，請輸入腳本的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-249">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="d0f7a-250">如果您輸入說明文章的完整名稱，則會 `Get-Help` 顯示文章內容。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-250">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="d0f7a-251">如果您輸入在數個說明文章標題中出現的單字或單字模式，則會 `Get-Help` 顯示相符標題的清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-251">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="d0f7a-252">如果您輸入任何不符合任何說明文章標題的文字，則會 `Get-Help` 在其內容中顯示包含該文字的文章清單。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-252">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="d0f7a-253">概念文章的名稱（例如 `about_Objects` ）必須以英文輸入，即使是在非英文版的 PowerShell 中也一樣。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-253">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

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

### <span data-ttu-id="d0f7a-254">-Online</span><span class="sxs-lookup"><span data-stu-id="d0f7a-254">-Online</span></span>

<span data-ttu-id="d0f7a-255">在預設瀏覽器中顯示說明文章的線上版本。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-255">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="d0f7a-256">此參數僅適用于 Cmdlet、函式、工作流程和腳本說明文章。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-256">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="d0f7a-257">您無法 **Online** `Get-Help` 在遠端會話中使用 Online 參數。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-257">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="d0f7a-258">如需有關在您撰寫的說明文章中支援這項功能的詳細資訊，請參閱 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)和 [支援線上說明](/powershell/scripting/developer/module/supporting-online-help)，以及 [撰寫 PowerShell Cmdlet 的](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-258">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

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

### <span data-ttu-id="d0f7a-259">-Parameter</span><span class="sxs-lookup"><span data-stu-id="d0f7a-259">-Parameter</span></span>

<span data-ttu-id="d0f7a-260">只顯示指定參數的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-260">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="d0f7a-261">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-261">Wildcards are permitted.</span></span> <span data-ttu-id="d0f7a-262">此參數不會影響概念性 ( **About_** ) 說明的顯示。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-262">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

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

### <span data-ttu-id="d0f7a-263">-Path</span><span class="sxs-lookup"><span data-stu-id="d0f7a-263">-Path</span></span>

<span data-ttu-id="d0f7a-264">取得說明 Cmdlet 如何在指定的提供者路徑中運作的說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-264">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="d0f7a-265">輸入 PowerShell 提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-265">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="d0f7a-266">此參數會取得 Cmdlet 說明文章的自訂版本，說明該 Cmdlet 如何在指定的 PowerShell 提供者路徑中運作。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-266">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="d0f7a-267">此參數僅適用于提供者 Cmdlet 的說明，而且只有在提供者于其說明檔中包含自訂版本的提供者 Cmdlet 說明文章時才會生效。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-267">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="d0f7a-268">若要使用這個參數，請針對包含提供者的模組安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-268">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="d0f7a-269">若要查看提供者路徑的自訂 Cmdlet 說明，請移至提供者路徑位置並輸入 `Get-Help` 命令，或從任何路徑位置，使用的 **path** 參數 `Get-Help` 指定提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-269">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="d0f7a-270">您也可以在 [說明] 文章的 [提供者說明] 區段中，線上找到自訂的 Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-270">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="d0f7a-271">如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](./About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-271">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

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

### <span data-ttu-id="d0f7a-272">-Role</span><span class="sxs-lookup"><span data-stu-id="d0f7a-272">-Role</span></span>

<span data-ttu-id="d0f7a-273">顯示針對指定使用者角色自訂的說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-273">Displays help customized for the specified user role.</span></span> <span data-ttu-id="d0f7a-274">輸入角色。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-274">Enter a role.</span></span> <span data-ttu-id="d0f7a-275">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="d0f7a-276">輸入使用者在組織中扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-276">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="d0f7a-277">某些 Cmdlet 會根據這個參數值，在說明檔中顯示不同的文字。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-277">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="d0f7a-278">這個參數不會對核心 Cmdlet 的說明產生任何影響。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-278">This parameter has no effect on help for the core cmdlets.</span></span>

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

### <span data-ttu-id="d0f7a-279">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d0f7a-279">CommonParameters</span></span>

<span data-ttu-id="d0f7a-280">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-280">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d0f7a-281">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-281">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d0f7a-282">輸入</span><span class="sxs-lookup"><span data-stu-id="d0f7a-282">INPUTS</span></span>

### <span data-ttu-id="d0f7a-283">無</span><span class="sxs-lookup"><span data-stu-id="d0f7a-283">None</span></span>

<span data-ttu-id="d0f7a-284">您無法將物件沿著管線向下傳送至 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-284">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="d0f7a-285">輸出</span><span class="sxs-lookup"><span data-stu-id="d0f7a-285">OUTPUTS</span></span>

### <span data-ttu-id="d0f7a-286">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f7a-286">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="d0f7a-287">如果您在沒有說明檔的 `Get-Help` 命令上執行，則會傳回代表自動產生說明的 `Get-Help` **ExtendedCmdletHelpInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-287">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="d0f7a-288">System.String</span><span class="sxs-lookup"><span data-stu-id="d0f7a-288">System.String</span></span>

<span data-ttu-id="d0f7a-289">如果您取得概念性說明文章，則 `Get-Help` 會以字串形式傳回。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-289">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="d0f7a-290">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f7a-290">MamlCommandHelpInfo</span></span>

<span data-ttu-id="d0f7a-291">如果您收到具有說明檔的命令，則會傳回 `Get-Help` **MamlCommandHelpInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-291">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="d0f7a-292">注意</span><span class="sxs-lookup"><span data-stu-id="d0f7a-292">NOTES</span></span>

<span data-ttu-id="d0f7a-293">PowerShell 3.0 不包含說明檔。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-293">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="d0f7a-294">若要下載並安裝讀取的說明檔 `Get-Help` ，請使用 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-294">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="d0f7a-295">您可以使用指令程式 `Update-Help` 來下載並安裝 PowerShell 隨附的核心命令的說明檔，以及您安裝的任何模組。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-295">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="d0f7a-296">您也可以使用它來更新說明檔，讓電腦上的說明永遠都不會過期。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-296">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="d0f7a-297">您也可以閱讀有關 PowerShell online 命令的說明文章，從 [消費者入門與 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)開始。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-297">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="d0f7a-298">`Get-Help` 在針對 Windows 作業系統設定的地區設定中，或在該地區設定的備用語言中顯示說明。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-298">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="d0f7a-299">如果您沒有主要或備用地區設定的說明檔，其 `Get-Help` 行為就如同電腦上沒有說明檔一樣。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-299">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="d0f7a-300">若要取得不同地區設定的說明，請使用主控台中的 **地區** 和 **語言** 來變更設定。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-300">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="d0f7a-301">在 Windows 10、 **設定** 、 **時間 & 語言** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-301">On Windows 10, **Settings** , **Time & Language** .</span></span>

<span data-ttu-id="d0f7a-302">[說明] 的完整觀點包括參數的相關資訊表。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-302">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="d0f7a-303">該表格包含下列欄位：</span><span class="sxs-lookup"><span data-stu-id="d0f7a-303">The table includes the following fields:</span></span>

- <span data-ttu-id="d0f7a-304">**必要** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-304">**Required** .</span></span> <span data-ttu-id="d0f7a-305">指出參數是否為必要 (true) 或選擇性 (false)。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-305">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="d0f7a-306">**位置** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-306">**Position** .</span></span> <span data-ttu-id="d0f7a-307">指出參數的名稱是否為或 (數值) 的位置。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-307">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="d0f7a-308">位置參數必須出現在命令中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-308">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="d0f7a-309">**指名** 的表示參數名稱是必要的，但參數可以出現在命令中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-309">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="d0f7a-310">**數值** 表示參數名稱是選擇性的，但若省略名稱，參數必須位於數位所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-310">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="d0f7a-311">例如， `2` 指出當省略參數名稱時，參數必須是命令中的第二個或唯一未命名的參數。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-311">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="d0f7a-312">使用參數名稱時，參數可以出現在命令中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-312">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="d0f7a-313">**預設值** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-313">**Default value** .</span></span> <span data-ttu-id="d0f7a-314">如果您未在命令中包含參數，則 PowerShell 會使用的參數值或預設行為。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-314">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="d0f7a-315">接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-315">Accepts pipeline input.</span></span> <span data-ttu-id="d0f7a-316">指出您是否可以 (true) 或無法 (false) 透過管線將物件傳送至參數。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-316">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="d0f7a-317">**根據屬性名稱** ，表示管線物件必須具有與參數名稱相同名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-317">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="d0f7a-318">**接受萬用字元** 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-318">**Accepts wildcard characters** .</span></span> <span data-ttu-id="d0f7a-319">指出參數值是否可以包含萬用字元，例如星號 (`*`) 或 () 的問號 `?` 。</span><span class="sxs-lookup"><span data-stu-id="d0f7a-319">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="d0f7a-320">相關連結</span><span class="sxs-lookup"><span data-stu-id="d0f7a-320">RELATED LINKS</span></span>

[<span data-ttu-id="d0f7a-321">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="d0f7a-321">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="d0f7a-322">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="d0f7a-322">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="d0f7a-323">Get-Command</span><span class="sxs-lookup"><span data-stu-id="d0f7a-323">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="d0f7a-324">支援可更新的說明</span><span class="sxs-lookup"><span data-stu-id="d0f7a-324">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="d0f7a-325">Update-Help</span><span class="sxs-lookup"><span data-stu-id="d0f7a-325">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="d0f7a-326">撰寫註解型說明主題</span><span class="sxs-lookup"><span data-stu-id="d0f7a-326">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="d0f7a-327">撰寫 PowerShell Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="d0f7a-327">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)
