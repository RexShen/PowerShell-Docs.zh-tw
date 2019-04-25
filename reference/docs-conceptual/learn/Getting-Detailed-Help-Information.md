---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 取得詳細的說明資訊
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086522"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="42a14-103">取得詳細的說明資訊</span><span class="sxs-lookup"><span data-stu-id="42a14-103">Getting detailed help information</span></span>

<span data-ttu-id="42a14-104">PowerShell 包含詳細的說明文章，可說明 PowerShell 概念與 PowerShell 語言。</span><span class="sxs-lookup"><span data-stu-id="42a14-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="42a14-105">此外，還有針對每個 Cmdlet 和提供者，以及許多函式與指令碼的說明文章。</span><span class="sxs-lookup"><span data-stu-id="42a14-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="42a14-106">您可以在命令提示字元中顯示這些說明文章，或在 [PowerShell](/powershell/scripting/overview) 文件中線上檢視這些文章的最近更新版本。</span><span class="sxs-lookup"><span data-stu-id="42a14-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="42a14-107">取得 Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="42a14-107">Getting help for cmdlets</span></span>

<span data-ttu-id="42a14-108">若要取得 PowerShell Cmdlet 的相關說明，請使用 [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="42a14-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="42a14-109">例如，若要取得 `Get-ChildItem` Cmdlet 的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="42a14-110">或</span><span class="sxs-lookup"><span data-stu-id="42a14-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="42a14-111">您甚至可以取得 Get-Help Cmdlet 的相關說明。</span><span class="sxs-lookup"><span data-stu-id="42a14-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="42a14-112">例如：</span><span class="sxs-lookup"><span data-stu-id="42a14-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="42a14-113">若要取得工作階段中的所有 Cmdlet 說明文章清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="42a14-114">若要一次顯示一頁說明文章，請使用 `help` 函式或其別名 `man`。</span><span class="sxs-lookup"><span data-stu-id="42a14-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="42a14-115">例如，若要顯示 `Get-ChildItem` Cmdlet 的說明，請輸入</span><span class="sxs-lookup"><span data-stu-id="42a14-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="42a14-116">或</span><span class="sxs-lookup"><span data-stu-id="42a14-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="42a14-117">若要顯示詳細資訊，請使用 `Get-Help` Cmdlet 的 **Detailed** 參數。</span><span class="sxs-lookup"><span data-stu-id="42a14-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="42a14-118">例如，若要取得 `Get-ChildItem` Cmdlet 的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="42a14-119">若要顯示說明文章中的所有內容，請使用 `Get-Help` Cmdlet 的 **Full** 參數。</span><span class="sxs-lookup"><span data-stu-id="42a14-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="42a14-120">例如，若要顯示 `Get-ChildItem` Cmdlet 之說明文章中的所有內容，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="42a14-121">若要取得 Cmdlet 之參數的詳細說明，請使用 `Get-Help` Cmdlet 的 **Parameter** 參數。</span><span class="sxs-lookup"><span data-stu-id="42a14-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="42a14-122">例如，若要取得 `Get-ChildItem` Cmdlet 之所有參數的詳細說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="42a14-123">若只要顯示說明文章中的範例，請使用 `Get-Help` 的 **Example** 參數。</span><span class="sxs-lookup"><span data-stu-id="42a14-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="42a14-124">例如，若只要顯示說明文章中的 `Get-ChildItem` Cmdlet 範例，請鍵入：</span><span class="sxs-lookup"><span data-stu-id="42a14-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="42a14-125">如需如何為您撰寫的 Cmdlet 撰寫說明文章的相關資訊，請參閱[如何撰寫 Cmdlet 說明](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="42a14-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="42a14-126">取得概念性說明</span><span class="sxs-lookup"><span data-stu-id="42a14-126">Getting conceptual help</span></span>

<span data-ttu-id="42a14-127">`Get-Help` Cmdlet 也會顯示 PowerShell 中概念性文章的相關資訊，包括 PowerShell 語言的相關文章。</span><span class="sxs-lookup"><span data-stu-id="42a14-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="42a14-128">概念性說明文章是以 "about_" 前置詞為開頭，例如 about_line_editing</span><span class="sxs-lookup"><span data-stu-id="42a14-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="42a14-129">(概念性文章的名稱必須以英文輸入，即使是在非英文版的 PowerShell 中也一樣)。</span><span class="sxs-lookup"><span data-stu-id="42a14-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="42a14-130">若要顯示概念性文章清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="42a14-131">若要顯示特定說明文章，請輸入文章名稱，例如：</span><span class="sxs-lookup"><span data-stu-id="42a14-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="42a14-132">`Get-Help` 的參數 (例如 **Detailed**、**Parameter** 與 **Examples**) 不會影響概念性說明文章的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="42a14-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="42a14-133">取得提供者的相關說明</span><span class="sxs-lookup"><span data-stu-id="42a14-133">Getting help about providers</span></span>

<span data-ttu-id="42a14-134">`Get-Help` Cmdlet 會顯示 PowerShell 提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="42a14-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="42a14-135">若要取得提供者的說明，請輸入 `Get-Help`，後面接著提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="42a14-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="42a14-136">例如，若要取得登錄提供者的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="42a14-137">若要取得工作階段中的所有提供者說明文章清單，請輸入</span><span class="sxs-lookup"><span data-stu-id="42a14-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="42a14-138">`Get-Help` 的參數 (例如 **Detailed**、**Parameter** 與 **Examples**) 不會影響提供者說明文章的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="42a14-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="42a14-139">取得指令碼與函式的相關說明</span><span class="sxs-lookup"><span data-stu-id="42a14-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="42a14-140">PowerShell 中的許多指令碼與函式都有說明文章。</span><span class="sxs-lookup"><span data-stu-id="42a14-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="42a14-141">使用 `Get-Help` Cmdlet 可顯示指令碼與函式的說明文章。</span><span class="sxs-lookup"><span data-stu-id="42a14-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="42a14-142">若要顯示函式的說明，請輸入 `Get-Help`，後面接著函式名稱。</span><span class="sxs-lookup"><span data-stu-id="42a14-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="42a14-143">例如，若要取得 `Disable-PSRemoting` 函式的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="42a14-144">若要顯示指令碼的說明，請輸入指令碼檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="42a14-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="42a14-145">如果指令碼不在 Path 環境變數所列的路徑中，您必須使用完整路徑。</span><span class="sxs-lookup"><span data-stu-id="42a14-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="42a14-146">例如，如果您的 C:\\PS-Test 目錄中有稱為 "TestScript.ps1" 的指令碼，若要顯示該指令碼的說明文章，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="42a14-147">設計來顯示 Cmdlet 說明的參數也適用於指令碼與函式說明。</span><span class="sxs-lookup"><span data-stu-id="42a14-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="42a14-148">不過，函式與指令碼的說明不會在您執行 `Get-Help *` 時顯示。</span><span class="sxs-lookup"><span data-stu-id="42a14-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="42a14-149">如需撰寫函式與指令碼之說明文章的相關資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="42a14-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="42a14-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="42a14-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="42a14-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="42a14-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="42a14-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="42a14-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="42a14-153">線上取得說明</span><span class="sxs-lookup"><span data-stu-id="42a14-153">Getting help online</span></span>

<span data-ttu-id="42a14-154">線上檢視說明文章是取得協助的最佳方式之一。</span><span class="sxs-lookup"><span data-stu-id="42a14-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="42a14-155">線上文章可以更輕鬆地更新，並提供最新的內容。</span><span class="sxs-lookup"><span data-stu-id="42a14-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="42a14-156">若要線上取得說明，請使用 `Get-Help` Cmdlet 的 **Online** 參數。</span><span class="sxs-lookup"><span data-stu-id="42a14-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="42a14-157">PowerShell 隨附的所有說明文章 (包括提供者說明與概念性 (關於) 說明文章) 都可以在 [PowerShell](/powershell/scripting/powershell-scripting) 文件中線上取得。</span><span class="sxs-lookup"><span data-stu-id="42a14-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="42a14-158">您無法對概念性 (about_\*) 或提供者說明文章使用 **Online** 參數。</span><span class="sxs-lookup"><span data-stu-id="42a14-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="42a14-159">線上說明是選擇性的，因此並非每一個 Cmdlet、函式或指令碼都適用。</span><span class="sxs-lookup"><span data-stu-id="42a14-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="42a14-160">例如，若要取得 `Get-ChildItem` Cmdlet 相關說明文章的線上版本，請輸入：</span><span class="sxs-lookup"><span data-stu-id="42a14-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="42a14-161">PowerShell 會在預設瀏覽器中開啟文章。</span><span class="sxs-lookup"><span data-stu-id="42a14-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="42a14-162">如果某篇說明文章支援線上說明，您也可以檢視該說明文章的 URL。</span><span class="sxs-lookup"><span data-stu-id="42a14-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="42a14-163">URL 會出現在說明文章的 [相關連結] 區段中。</span><span class="sxs-lookup"><span data-stu-id="42a14-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="42a14-164">例如，若要查看 Add-Computer Cmdlet 的線上版本 URL，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="42a14-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="42a14-165">該文章之 [相關連結] 區段中的第一行如下所示。</span><span class="sxs-lookup"><span data-stu-id="42a14-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="42a14-166">如需如何提供說明文章線上支援的相關資訊，請參閱 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="42a14-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="42a14-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42a14-167">See also</span></span>

- [<span data-ttu-id="42a14-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="42a14-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="42a14-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="42a14-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="42a14-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="42a14-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="42a14-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="42a14-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
