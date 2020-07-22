---
title: 撰寫 PowerShell 腳本和功能的說明
ms.date: 09/13/2016
ms.openlocfilehash: 381c501d87b7381075f89412f654c6121493856e
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892909"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="33740-102">撰寫 PowerShell 腳本和功能的說明</span><span class="sxs-lookup"><span data-stu-id="33740-102">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="33740-103">當 PowerShell 腳本和函式與其他人共用時，應該完整記載。</span><span class="sxs-lookup"><span data-stu-id="33740-103">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="33740-104">此 `Get-Help` Cmdlet 會顯示腳本和函式說明主題，其格式與顯示 Cmdlet 的說明相同，而且所有參數都 `Get-Help` 適用于腳本和函式說明主題。</span><span class="sxs-lookup"><span data-stu-id="33740-104">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="33740-105">PowerShell 腳本可以包含有關腳本中每個函式之腳本和說明主題的說明主題。</span><span class="sxs-lookup"><span data-stu-id="33740-105">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span> <span data-ttu-id="33740-106">獨立于腳本共用的函式可以包含自己的說明主題。</span><span class="sxs-lookup"><span data-stu-id="33740-106">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="33740-107">本檔說明說明主題的格式和正確位置，並建議內容的指導方針。</span><span class="sxs-lookup"><span data-stu-id="33740-107">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="33740-108">腳本和函數說明的類型</span><span class="sxs-lookup"><span data-stu-id="33740-108">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="33740-109">註解型說明</span><span class="sxs-lookup"><span data-stu-id="33740-109">Comment-Based Help</span></span>

<span data-ttu-id="33740-110">描述腳本或函式的說明主題，可以實作為腳本或函式中的一組批註。</span><span class="sxs-lookup"><span data-stu-id="33740-110">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span> <span data-ttu-id="33740-111">針對腳本撰寫以批註為基礎的說明，並針對腳本中的函式，請特別注意放置以批註為基礎之說明的規則。</span><span class="sxs-lookup"><span data-stu-id="33740-111">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span> <span data-ttu-id="33740-112">此位置會決定 Cmdlet 是否要將 `Get-Help` 說明主題與腳本或函式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="33740-112">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span> <span data-ttu-id="33740-113">如需撰寫以批註為基礎之說明主題的詳細資訊，請參閱[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="33740-113">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="33740-114">以 XML 為基礎的命令說明</span><span class="sxs-lookup"><span data-stu-id="33740-114">XML-Based Command Help</span></span>

<span data-ttu-id="33740-115">描述腳本或函數的說明主題，可以在使用命令說明架構的 XML 檔案中執行。</span><span class="sxs-lookup"><span data-stu-id="33740-115">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span> <span data-ttu-id="33740-116">若要將腳本或函數與 XML 檔案產生關聯，請使用 `ExternalHelp` comment 關鍵字，後面接著 xml 檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="33740-116">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="33740-117">當 `ExternalHelp` comment 關鍵字出現時，它的優先順序高於以批註為基礎的說明，即使找 `Get-Help` 不到符合關鍵字值的說明檔也一樣 `ExternalHelp` 。</span><span class="sxs-lookup"><span data-stu-id="33740-117">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="33740-118">線上說明</span><span class="sxs-lookup"><span data-stu-id="33740-118">Online Help</span></span>

<span data-ttu-id="33740-119">您可以在網際網路上張貼說明主題，然後直接 `Get-Help` 開啟主題。</span><span class="sxs-lookup"><span data-stu-id="33740-119">You can post your help topics on the internet and then direct `Get-Help` to open the topics.</span></span> <span data-ttu-id="33740-120">如需撰寫以批註為基礎之說明主題的詳細資訊，請參閱[支援線上說明](../module/supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="33740-120">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="33740-121">沒有已建立的方法可撰寫腳本和函式的概念性（「關於」）主題。</span><span class="sxs-lookup"><span data-stu-id="33740-121">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="33740-122">不過，您可以在網際網路清單上張貼概念性主題的主題，以及命令說明主題的 [相關連結] 區段中的 Url。</span><span class="sxs-lookup"><span data-stu-id="33740-122">However, you can post conceptual topics on the internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="33740-123">腳本和函數說明的內容考慮</span><span class="sxs-lookup"><span data-stu-id="33740-123">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="33740-124">如果您要撰寫一個非常簡短的說明主題，其中只有幾個可用的命令說明區段，請務必包含腳本或函數參數的清楚描述。</span><span class="sxs-lookup"><span data-stu-id="33740-124">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="33740-125">也請在 [範例] 區段中包含一或兩個範例命令，即使您決定省略範例描述也一樣。</span><span class="sxs-lookup"><span data-stu-id="33740-125">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="33740-126">在所有描述中，請將命令稱為腳本或函式。</span><span class="sxs-lookup"><span data-stu-id="33740-126">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="33740-127">此資訊可協助使用者瞭解和管理命令。</span><span class="sxs-lookup"><span data-stu-id="33740-127">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="33740-128">例如，下列詳細描述說明新主題的命令是腳本。</span><span class="sxs-lookup"><span data-stu-id="33740-128">For example, the following detailed description states that the New-Topic command is a script.</span></span>
  <span data-ttu-id="33740-129">這會提醒使用者他們在執行時必須指定路徑和完整名稱。</span><span class="sxs-lookup"><span data-stu-id="33740-129">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="33740-130">「新主題腳本會針對輸入檔中的每個主題名稱建立空白的概念主題 ...」</span><span class="sxs-lookup"><span data-stu-id="33740-130">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="33740-131">下列詳細描述說明為函式 `Disable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="33740-131">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="33740-132">當會話包含多個具有相同名稱的命令時，這項資訊特別有用，其中某些命令可能會被較高優先順序的命令隱藏。</span><span class="sxs-lookup"><span data-stu-id="33740-132">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="33740-133">此函式會 `Disable-PSRemoting` 停用本機電腦上的所有會話設定 .。。</span><span class="sxs-lookup"><span data-stu-id="33740-133">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="33740-134">在腳本說明主題中，說明如何使用整個腳本。</span><span class="sxs-lookup"><span data-stu-id="33740-134">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="33740-135">如果您也在腳本中撰寫函式的說明主題，請在腳本說明主題中提及函數，並在腳本說明主題的 [相關連結] 區段中包含函數說明主題的參考。</span><span class="sxs-lookup"><span data-stu-id="33740-135">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span>
  <span data-ttu-id="33740-136">相反地，當函式是腳本的一部分時，請在函式說明主題中說明函式在腳本中所扮演的角色，以及如何獨立使用該功能。</span><span class="sxs-lookup"><span data-stu-id="33740-136">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="33740-137">然後在函式說明主題的 [相關連結] 區段中列出腳本說明主題。</span><span class="sxs-lookup"><span data-stu-id="33740-137">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="33740-138">撰寫腳本說明主題的範例時，請務必在範例命令中包含腳本檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="33740-138">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="33740-139">這會提醒使用者必須明確指定路徑，即使腳本位於目前目錄中也一樣。</span><span class="sxs-lookup"><span data-stu-id="33740-139">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="33740-140">在函式說明主題中，提醒使用者該函式只存在於目前的會話中，若要在其他會話中使用，他們必須加以新增，或將它新增至 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="33740-140">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="33740-141">`Get-Help`只有在腳本檔案和說明主題檔案儲存在正確的位置時，才會顯示腳本或函數的說明主題。</span><span class="sxs-lookup"><span data-stu-id="33740-141">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="33740-142">因此，包含安裝 PowerShell 的指示，或儲存或安裝腳本或函式說明主題中的腳本或函式，並不會很有用。</span><span class="sxs-lookup"><span data-stu-id="33740-142">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="33740-143">相反地，請在您用來散發腳本或函式的檔中包含任何安裝指示。</span><span class="sxs-lookup"><span data-stu-id="33740-143">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="33740-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33740-144">See Also</span></span>

[<span data-ttu-id="33740-145">撰寫註解型說明主題</span><span class="sxs-lookup"><span data-stu-id="33740-145">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
