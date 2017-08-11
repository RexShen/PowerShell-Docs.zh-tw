---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "取得詳細的說明資訊"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 3260b5ec0a91749d3b7b126412137aa9d603ef0e
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="d0087-103">取得詳細的說明資訊</span><span class="sxs-lookup"><span data-stu-id="d0087-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="d0087-104">Windows PowerShell 包含詳細的說明主題，說明 Windows PowerShell 概念和 Windows PowerShell 語言。</span><span class="sxs-lookup"><span data-stu-id="d0087-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="d0087-105">此外，還有針對每個 Cmdlet 和提供者，以及許多函式和指令碼的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="d0087-106">您可以在命令提示字元中顯示這些說明主題，或在 Microsoft TechNet Library 中檢視這些主題的最近更新版本。</span><span class="sxs-lookup"><span data-stu-id="d0087-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="d0087-107">許多裝載 Windows PowerShell 的程式 (例如 Windows PowerShell 整合式指令碼環境) 都提供額外的說明功能，例如即時線上說明和編譯的說明檔案 (.chm)。</span><span class="sxs-lookup"><span data-stu-id="d0087-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="d0087-108">取得 Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="d0087-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="d0087-109">若要取得 Windows PowerShell Cmdlet 的相關說明，請使用 [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d0087-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="d0087-110">例如，若要取得 [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) Cmdlet 的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="d0087-111">或</span><span class="sxs-lookup"><span data-stu-id="d0087-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="d0087-112">您甚至可以取得 Get-Help Cmdlet 的相關說明。</span><span class="sxs-lookup"><span data-stu-id="d0087-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="d0087-113">例如：</span><span class="sxs-lookup"><span data-stu-id="d0087-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="d0087-114">若要取得工作階段中的所有 Cmdlet 說明主題清單，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="d0087-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="d0087-115">若要一次顯示一頁說明主題，請使用 **help** 函式或其別名 **man**。</span><span class="sxs-lookup"><span data-stu-id="d0087-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="d0087-116">例如，若要顯示 Get-ChildItem Cmdlet 的說明，請輸入</span><span class="sxs-lookup"><span data-stu-id="d0087-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="d0087-117">或</span><span class="sxs-lookup"><span data-stu-id="d0087-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="d0087-118">若要顯示 Cmdlet、函式或指令碼的詳細資訊，包括其參數的描述及其使用範例，請使用 Get-Help Cmdlet 的 *Detailed* 參數。</span><span class="sxs-lookup"><span data-stu-id="d0087-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="d0087-119">例如，若要取得 Get-ChildItem Cmdlet 的詳細資訊，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="d0087-120">若要顯示說明主題中的所有內容，請使用 Get-Help Cmdlet 的 *Full* 參數。</span><span class="sxs-lookup"><span data-stu-id="d0087-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="d0087-121">例如，若要顯示 Get-ChildItem Cmdlet 之說明主題中的所有內容，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="d0087-122">若要取得 Cmdlet 之參數的詳細說明，請使用 Get-Help Cmdlet 的 *Parameter* 參數。</span><span class="sxs-lookup"><span data-stu-id="d0087-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="d0087-123">例如，若要取得 Get-ChildItem Cmdlet 之所有參數的詳細說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="d0087-124">若只要顯示說明主題中的範例，請使用 Get-Help 的 *Example* 參數。</span><span class="sxs-lookup"><span data-stu-id="d0087-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="d0087-125">例如，若只要顯示 Get-ChildItem Cmdlet 之說明主題中的範例，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="d0087-126">如需如何為您撰寫的 Cmdlet 撰寫說明主題的資訊，請參閱 MSDN 中的＜How to Write Cmdlet Help＞(如何撰寫 Cmdlet 說明) 主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-126">For information about how to write Help topics for the cmdlets that you write, see the "How to Write Cmdlet Help" topic in MSDN.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="d0087-127">取得概念性說明</span><span class="sxs-lookup"><span data-stu-id="d0087-127">Getting Conceptual Help</span></span>
<span data-ttu-id="d0087-128">Get-Help Cmdlet 也會顯示有關 Windows PowerShell 中概念性主題的相關資訊，包括 Windows PowerShell 語言的相關主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="d0087-129">概念性說明主題是以 "about_" 前置詞為開頭，例如 about_line_editing。</span><span class="sxs-lookup"><span data-stu-id="d0087-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="d0087-130">(概念性主題的名稱必須以英文輸入，即使是在非英文版的 Windows PowerShell 中也一樣)。</span><span class="sxs-lookup"><span data-stu-id="d0087-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="d0087-131">若要顯示概念性主題清單，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="d0087-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="d0087-132">若要顯示特定說明主題，請輸入主題名稱，例如︰</span><span class="sxs-lookup"><span data-stu-id="d0087-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="d0087-133">Get-Help 的參數 (例如 *Detailed*、*Parameter* 和 *Examples*) 不會影響概念性說明主題的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="d0087-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="d0087-134">取得提供者的相關說明</span><span class="sxs-lookup"><span data-stu-id="d0087-134">Getting Help About Providers</span></span>
<span data-ttu-id="d0087-135">Get-Help Cmdlet 會顯示 Windows PowerShell 提供者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d0087-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="d0087-136">若要取得提供者的說明，請輸入 "Get-Help"，後面接著提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="d0087-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="d0087-137">例如，若要取得登錄提供者的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="d0087-138">若要取得工作階段中的所有提供者說明主題清單，請輸入</span><span class="sxs-lookup"><span data-stu-id="d0087-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="d0087-139">Get-Help 的參數 (例如 *Detailed*、*Parameter* 和 *Examples*) 不會影響提供者說明主題的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="d0087-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="d0087-140">取得指令碼和函式的相關說明</span><span class="sxs-lookup"><span data-stu-id="d0087-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="d0087-141">Windows PowerShell 中的許多指令碼和函式都有說明主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="d0087-142">使用 Get-Help Cmdlet 可顯示指令碼和函式的說明主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="d0087-143">若要顯示函式的說明，請輸入"get-help"，後面接著函式名稱。</span><span class="sxs-lookup"><span data-stu-id="d0087-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="d0087-144">例如，若要取得 Disable-PSRemoting 函式的說明，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="d0087-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="d0087-145">若要顯示指令碼的說明，請輸入指令碼檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="d0087-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="d0087-146">如果指令碼位於 Path 環境變數中所列的路徑，您可以省略命令中的路徑。</span><span class="sxs-lookup"><span data-stu-id="d0087-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="d0087-147">例如，如果您的 C:\\PS-Test 目錄中有稱為 "TestScript.ps1" 的指令碼，若要顯示該指令碼的說明主題，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="d0087-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="d0087-148">為顯示 Cmdlet 說明所設計的參數 (例如 *Detailed*、*Full*、*Examples* 和 *Parameter*) 也適用於指令碼說明和函式說明。</span><span class="sxs-lookup"><span data-stu-id="d0087-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="d0087-149">不過，當您顯示所有說明時，若輸入"get-help \*"，則不會顯示函式和指令碼的說明。</span><span class="sxs-lookup"><span data-stu-id="d0087-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="d0087-150">如需撰寫函式和指令碼說明主題的資訊，請參閱 [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)、[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) 和 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)。</span><span class="sxs-lookup"><span data-stu-id="d0087-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="d0087-151">線上取得說明</span><span class="sxs-lookup"><span data-stu-id="d0087-151">Getting Help Online</span></span>
<span data-ttu-id="d0087-152">如果您連線到網際網路，取得說明的最佳方式之一是線上檢視說明主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="d0087-153">由於線上主題很容易更新，因此可能會提供最新的內容。</span><span class="sxs-lookup"><span data-stu-id="d0087-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="d0087-154">若要線上取得說明，請嘗試 Get-Help Cmdlet 的 *Online* 參數。</span><span class="sxs-lookup"><span data-stu-id="d0087-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="d0087-155">Get-Help Cmdlet 的 *Online* 參數只適用於 Cmdlet 說明、函式說明和指令碼說明。</span><span class="sxs-lookup"><span data-stu-id="d0087-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="d0087-156">您無法對概念性 (關於) 主題或提供者說明主題使用 *Online* 參數。</span><span class="sxs-lookup"><span data-stu-id="d0087-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="d0087-157">此外，由於這是選擇性功能，因此並非每一個 Cmdlet、函式或指令碼說明主題都適用。</span><span class="sxs-lookup"><span data-stu-id="d0087-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="d0087-158">不過，您可以在 Microsoft TechNet Library 的 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) 區段中，線上取得 Windows PowerShell 隨附的所有說明主題，包括提供者說明和概念性 (關於) 說明主題。</span><span class="sxs-lookup"><span data-stu-id="d0087-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="d0087-159">若要使用 Get-Help Cmdlet 的 *Online*e 參數，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="d0087-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="d0087-160">例如，若要取得 Get-ChildItem Cmdlet 相關說明主題的線上版本，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d0087-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="d0087-161">如果此說明主題有線上版本可用，就會在您的預設瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="d0087-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="d0087-162">如果某個說明主題支援線上說明，您也可以檢視該說明主題的網際網路位址 (URL)。</span><span class="sxs-lookup"><span data-stu-id="d0087-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="d0087-163">網際網路位址會出現在說明主題的 [相關連結] 區段中。</span><span class="sxs-lookup"><span data-stu-id="d0087-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="d0087-164">例如，若要查看 Add-Computer Cmdlet 的線上版本 URL，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="d0087-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="d0087-165">該主題之 [相關連結] 區段中的第一行會如下所示。</span><span class="sxs-lookup"><span data-stu-id="d0087-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="d0087-166">如需如何提供說明主題之線上支援的資訊，請參閱 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)，並請參閱 MSDN (Microsoft Developer Network) Library 中的＜How to Write Cmdlet Help＞(如何撰寫 Cmdlet 說明) ([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415))。</span><span class="sxs-lookup"><span data-stu-id="d0087-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see "How to Write Cmdlet Help" ([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415)) in the MSDN (Microsoft Developer Network) library.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0087-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0087-167">See Also</span></span>
- [<span data-ttu-id="d0087-168">about_Functions [m2]</span><span class="sxs-lookup"><span data-stu-id="d0087-168">about_Functions [m2]</span></span>](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [<span data-ttu-id="d0087-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="d0087-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="d0087-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="d0087-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [<span data-ttu-id="d0087-171">Get-Help [m2]</span><span class="sxs-lookup"><span data-stu-id="d0087-171">Get-Help [m2]</span></span>](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

