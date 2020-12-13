---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 PowerShell 腳本和函式的說明
description: 撰寫 PowerShell 腳本和函式的說明
ms.openlocfilehash: f72742e2a131f41ba8ffdcec4901c7c3ea1da1ad
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654633"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="cb2ba-103">撰寫 PowerShell 腳本和函式的說明</span><span class="sxs-lookup"><span data-stu-id="cb2ba-103">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="cb2ba-104">只要與其他人共用 PowerShell 腳本和函式，就應該完整記載。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-104">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="cb2ba-105">此 `Get-Help` Cmdlet 會以顯示 Cmdlet 說明的相同格式顯示腳本和函式說明主題，而且所有參數都可 `Get-Help` 在腳本和函式說明主題中運作。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-105">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="cb2ba-106">PowerShell 腳本可包含有關腳本的說明主題，以及腳本中每個函式的說明主題。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-106">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span> <span data-ttu-id="cb2ba-107">與腳本分開共用的函式可以包含自己的說明主題。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-107">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="cb2ba-108">本檔說明說明主題的格式和正確位置，並建議內容的指導方針。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-108">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="cb2ba-109">腳本和函式說明的類型</span><span class="sxs-lookup"><span data-stu-id="cb2ba-109">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="cb2ba-110">註解型說明</span><span class="sxs-lookup"><span data-stu-id="cb2ba-110">Comment-Based Help</span></span>

<span data-ttu-id="cb2ba-111">描述腳本或函式的說明主題可以實作為腳本或函數內的一組批註。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-111">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span> <span data-ttu-id="cb2ba-112">撰寫腳本的批註式說明和腳本中的函式時，請特別注意放置以批註為基礎的說明的規則。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-112">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span> <span data-ttu-id="cb2ba-113">放置會決定 Cmdlet 是否將 `Get-Help` 說明主題與腳本或函式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-113">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span> <span data-ttu-id="cb2ba-114">如需撰寫以批註為基礎的說明主題的詳細資訊，請參閱 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-114">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="cb2ba-115">XML-Based 命令說明</span><span class="sxs-lookup"><span data-stu-id="cb2ba-115">XML-Based Command Help</span></span>

<span data-ttu-id="cb2ba-116">描述腳本或函式的說明主題可以在使用命令說明架構的 XML 檔案中執行。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-116">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span> <span data-ttu-id="cb2ba-117">若要將腳本或函式與 XML 檔案產生關聯，請使用 `ExternalHelp` comment 關鍵字，後面接著 xml 檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-117">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="cb2ba-118">當 `ExternalHelp` comment 關鍵字存在時，其優先于批註式說明，即使 `Get-Help` 找不到符合關鍵字值的說明檔 `ExternalHelp` 。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-118">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="cb2ba-119">線上說明</span><span class="sxs-lookup"><span data-stu-id="cb2ba-119">Online Help</span></span>

<span data-ttu-id="cb2ba-120">您可以在網際網路上張貼說明主題，然後直接 `Get-Help` 開啟主題。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-120">You can post your help topics on the internet and then direct `Get-Help` to open the topics.</span></span> <span data-ttu-id="cb2ba-121">如需撰寫以批註為基礎的說明主題的詳細資訊，請參閱 [支援線上說明](../module/supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-121">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="cb2ba-122">沒有針對腳本和函式撰寫概念 ( "About" ) 主題的已建立方法。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-122">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="cb2ba-123">不過，您可以在網際網路上張貼概念性主題，在命令說明主題的 [相關連結] 區段中，列出主題及其 Url。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-123">However, you can post conceptual topics on the internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="cb2ba-124">腳本和函數說明的內容考慮</span><span class="sxs-lookup"><span data-stu-id="cb2ba-124">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="cb2ba-125">如果您要撰寫一個非常簡短的說明主題，其中只包含幾個可用的命令説明區段，請務必包含腳本或函式參數的清楚描述。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-125">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="cb2ba-126">也請在 [範例] 區段中包含一或兩個範例命令，即使您決定省略範例描述。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-126">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="cb2ba-127">在 [所有描述] 中，以腳本或函式的形式來參考命令。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-127">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="cb2ba-128">此資訊可協助使用者瞭解和管理命令。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-128">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="cb2ba-129">例如，下列詳細描述指出 New-Topic 命令是腳本。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-129">For example, the following detailed description states that the New-Topic command is a script.</span></span>
  <span data-ttu-id="cb2ba-130">這會提醒使用者他們在執行時必須指定路徑和完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-130">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="cb2ba-131">「New-Topic 腳本會為輸入檔中的每個主題名稱建立空白的概念主題 ...」</span><span class="sxs-lookup"><span data-stu-id="cb2ba-131">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="cb2ba-132">以下是函式的詳細說明 `Disable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-132">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="cb2ba-133">當會話包含多個具有相同名稱的命令時，這項資訊特別有用，其中有些命令可能會由優先順序較高的命令隱藏。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-133">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="cb2ba-134">此 `Disable-PSRemoting` 函數會停用本機電腦上的所有會話設定 .。。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-134">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="cb2ba-135">在腳本說明主題中，說明如何使用整個腳本。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-135">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="cb2ba-136">如果您也要撰寫腳本中函式的說明主題，請提及腳本說明主題中的函式，並在腳本說明主題的 [相關連結] 區段中包含函數說明主題的參考。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-136">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span>
  <span data-ttu-id="cb2ba-137">相反地，當函式是腳本的一部分時，會在函式說明主題中說明函式在腳本中扮演的角色，以及如何獨立使用它。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-137">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="cb2ba-138">然後，列出函數說明主題之 [相關連結] 區段中的腳本說明主題。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-138">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="cb2ba-139">撰寫腳本說明主題的範例時，請務必在範例命令中包含指令檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-139">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="cb2ba-140">這會提醒使用者必須明確指定路徑，即使腳本是在目前的目錄中也一樣。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-140">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="cb2ba-141">在函式說明主題中，提醒使用者函式只存在於目前的會話中，若要在其他會話中使用它，他們需要新增它，或將它新增至 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-141">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="cb2ba-142">`Get-Help` 只有當腳本檔案和說明主題檔案儲存在正確的位置時，才會顯示腳本或函式的說明主題。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-142">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="cb2ba-143">因此，在腳本或函式說明主題中包含安裝 PowerShell 或儲存或安裝腳本或函式的指示並不實用。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-143">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="cb2ba-144">相反地，請在您用來散發腳本或功能的檔中包含任何安裝指示。</span><span class="sxs-lookup"><span data-stu-id="cb2ba-144">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb2ba-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb2ba-145">See Also</span></span>

[<span data-ttu-id="cb2ba-146">撰寫註解型說明主題</span><span class="sxs-lookup"><span data-stu-id="cb2ba-146">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
