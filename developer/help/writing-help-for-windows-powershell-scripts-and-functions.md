---
title: 撰寫 PowerShell 指令碼和函式的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083105"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a><span data-ttu-id="15965-102">撰寫 PowerShell 指令碼和函式的說明</span><span class="sxs-lookup"><span data-stu-id="15965-102">Writing Help for PowerShell Scripts and Functions</span></span>

<span data-ttu-id="15965-103">PowerShell 指令碼和函式都應該詳細記錄時它們會與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="15965-103">PowerShell scripts and functions should be fully documented whenever they are shared with others.</span></span>
<span data-ttu-id="15965-104">`Get-Help` Cmdlet 會顯示指令碼和函式的 [說明] 主題相同的格式與顯示的 cmdlet 和所有說明`Get-Help`參數作用於指令碼和函式的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="15965-104">The `Get-Help` cmdlet displays the script and function help topics in the same format as it displays help for cmdlets, and all of the `Get-Help` parameters work on script and function help topics.</span></span>

<span data-ttu-id="15965-105">PowerShell 指令碼可以包括有關指令碼的說明主題以及有關每個函式的說明主題，指令碼中。</span><span class="sxs-lookup"><span data-stu-id="15965-105">PowerShell scripts can include a help topic about the script and help topics about each functions in the script.</span></span>
<span data-ttu-id="15965-106">共用獨立指令碼的函式可以包含它們自己的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="15965-106">Functions that are shared independently of scripts can include their own help topics.</span></span>

<span data-ttu-id="15965-107">本文件說明的格式和的 [說明] 主題的正確位置，並建議讓內容的指導方針。</span><span class="sxs-lookup"><span data-stu-id="15965-107">This document explains the format and correct placement of the help topics, and it suggests guidelines for the content.</span></span>

## <a name="types-of-script-and-function-help"></a><span data-ttu-id="15965-108">類型的指令碼和函式的說明</span><span class="sxs-lookup"><span data-stu-id="15965-108">Types of Script and Function Help</span></span>

### <a name="comment-based-help"></a><span data-ttu-id="15965-109">註解型說明</span><span class="sxs-lookup"><span data-stu-id="15965-109">Comment-Based Help</span></span>
<span data-ttu-id="15965-110">「 說明 」 主題所描述的指令碼或函式可以實作為一組內的指令碼或函式的註解。</span><span class="sxs-lookup"><span data-stu-id="15965-110">The help topic that describes a script or function can be implemented as a set of comments within the script or function.</span></span>
<span data-ttu-id="15965-111">在指令碼中撰寫註解型說明的指令碼和函式，請特別注意規則放置註解型說明。</span><span class="sxs-lookup"><span data-stu-id="15965-111">When writing comment-based help for a script and for functions in a script, pay careful attention to the rules for placing the comment-based help.</span></span>
<span data-ttu-id="15965-112">位置會決定是否`Get-Help`cmdlet 說明主題將與相關聯的指令碼或函式。</span><span class="sxs-lookup"><span data-stu-id="15965-112">The placement determines whether the `Get-Help` cmdlet associates the help topic with the script or a function.</span></span>
<span data-ttu-id="15965-113">如需有關如何撰寫註解式說明主題的詳細資訊，請參閱[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="15965-113">For more information about writing comment-based help topics, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

### <a name="xml-based-command-help"></a><span data-ttu-id="15965-114">以 XML 為基礎的命令說明</span><span class="sxs-lookup"><span data-stu-id="15965-114">XML-Based Command Help</span></span>
<span data-ttu-id="15965-115">描述指令碼或函式的 [說明] 主題可以實作中使用的命令說明結構描述的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="15965-115">The help topic that describes a script or function can be implemented in an XML file that uses the command help schema.</span></span>
<span data-ttu-id="15965-116">若要關聯的 XML 檔案中的指令碼或函式，使用`ExternalHelp`註解關鍵字後面的路徑和名稱的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="15965-116">To associate the script or function with the XML file, use the `ExternalHelp` comment keyword followed by the path and name of the XML file.</span></span>

<span data-ttu-id="15965-117">當`ExternalHelp`關鍵字，則其優先順序高於註解型說明註解，即使`Get-Help`找不到符合的值的說明檔`ExternalHelp`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="15965-117">When the `ExternalHelp` comment keyword is present, it takes precedence over comment-based help, even when `Get-Help` cannot find a help file that matches the value of the `ExternalHelp` keyword.</span></span>

### <a name="online-help"></a><span data-ttu-id="15965-118">線上說明</span><span class="sxs-lookup"><span data-stu-id="15965-118">Online Help</span></span>
<span data-ttu-id="15965-119">您可以在網際網路上張貼您的說明主題，並再直接`Get-Help`開啟主題。</span><span class="sxs-lookup"><span data-stu-id="15965-119">You can post your help topics on the Internet and then direct `Get-Help` to open the topics.</span></span>
<span data-ttu-id="15965-120">如需有關如何撰寫註解式說明主題的詳細資訊，請參閱[支援線上說明](../module/supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="15965-120">For more information about writing comment-based help topics, see [Supporting Online Help](../module/supporting-online-help.md).</span></span>

<span data-ttu-id="15965-121">沒有概念性 （「 關於 」） 主題中的指令碼和函式的建立的方法進行寫入。</span><span class="sxs-lookup"><span data-stu-id="15965-121">There is no established method for writing conceptual ("About") topics for scripts and functions.</span></span>
<span data-ttu-id="15965-122">不過，您可以張貼網際網路清單上的概念性主題的主題，以及其 Url 命令的說明主題的相關連結 區段中。</span><span class="sxs-lookup"><span data-stu-id="15965-122">However, you can post conceptual topics on the Internet list the topics and their URLs in the Related Links section of a command help topic.</span></span>

## <a name="content-considerations-for-script-and-function-help"></a><span data-ttu-id="15965-123">說明內容的指令碼和函式的考量</span><span class="sxs-lookup"><span data-stu-id="15965-123">Content Considerations for Script and Function Help</span></span>

- <span data-ttu-id="15965-124">如果您正在撰寫非常簡短的 [說明] 主題，使用只有幾個可用的命令說明部分，請務必包含指令碼或函式參數的清楚描述。</span><span class="sxs-lookup"><span data-stu-id="15965-124">If you are writing a very brief help topic with only a few of the available command help sections, be sure to include clear descriptions of the script or function parameters.</span></span> <span data-ttu-id="15965-125">也包含一或兩個範例命令範例 > 一節中，即使您決定省略範例的描述。</span><span class="sxs-lookup"><span data-stu-id="15965-125">Also include one or two sample commands in the examples section, even if you decide to omit example descriptions.</span></span>

- <span data-ttu-id="15965-126">在所有的描述，請參閱命令的指令碼或函式。</span><span class="sxs-lookup"><span data-stu-id="15965-126">In all descriptions, refer to the command as a script or function.</span></span> <span data-ttu-id="15965-127">這項資訊可協助使用者了解並管理命令。</span><span class="sxs-lookup"><span data-stu-id="15965-127">This information helps the user to understand and manage the command.</span></span>

  <span data-ttu-id="15965-128">比方說，下列的詳細的描述狀態的新主題的命令是指令碼。</span><span class="sxs-lookup"><span data-stu-id="15965-128">For example, the following detailed description states that the New-Topic command is a script.</span></span> <span data-ttu-id="15965-129">這會提醒使用者他們需要執行它時指定的路徑和完整名稱。</span><span class="sxs-lookup"><span data-stu-id="15965-129">This reminds users that they need to specify the path and full name when they run it.</span></span>

  > <span data-ttu-id="15965-130">「 新增主題指令碼會建立在輸入檔...空白的觀念性主題，每個主題名稱 」</span><span class="sxs-lookup"><span data-stu-id="15965-130">"The New-Topic script creates a blank conceptual topic for each topic name in the input file..."</span></span>

  <span data-ttu-id="15965-131">下列的詳細的描述指出`Disable-PSRemoting`是函式。</span><span class="sxs-lookup"><span data-stu-id="15965-131">The following detailed description states that `Disable-PSRemoting` is a function.</span></span> <span data-ttu-id="15965-132">當工作階段包含多個具有相同的名稱，其中有些可能會被隱藏命令具有較高優先順序的命令，這項資訊是使用者特別有用。</span><span class="sxs-lookup"><span data-stu-id="15965-132">This information is particularly useful to users when the session includes multiple commands with the same name, some of which might be hidden by a command with higher precedence.</span></span>

  > <span data-ttu-id="15965-133">`Disable-PSRemoting`函式會停用本機電腦上的所有工作階段設定...</span><span class="sxs-lookup"><span data-stu-id="15965-133">The `Disable-PSRemoting` function disables all session configurations on the local computer...</span></span>

- <span data-ttu-id="15965-134">在指令碼說明主題，說明如何使用指令碼整體。</span><span class="sxs-lookup"><span data-stu-id="15965-134">In a script help topic, explain how to use the script as a whole.</span></span> <span data-ttu-id="15965-135">如果您也在指令碼中撰寫函式的說明主題，提及您的指令碼說明主題中的函式，並包含在指令碼的 說明 主題的相關連結 區段中的函式的 說明 主題的參考。</span><span class="sxs-lookup"><span data-stu-id="15965-135">If you are also writing help topics for functions in the script, mention the functions in your script help topic and include references to the function help topics in the Related Links section of the script help topic.</span></span> <span data-ttu-id="15965-136">相反地，在指令碼函式時，說明函式的 [說明] 主題中的函式中的指令碼，並可能會用它獨立所扮演的角色。</span><span class="sxs-lookup"><span data-stu-id="15965-136">Conversely, when a function is part of a script, explain in the function help topic the role that the function plays in the script and how it might be used independently.</span></span> <span data-ttu-id="15965-137">然後列出指令碼說明主題中的函式的 說明 主題的相關連結 區段。</span><span class="sxs-lookup"><span data-stu-id="15965-137">Then list the script help topic in the Related Links section of the function help topic.</span></span>

- <span data-ttu-id="15965-138">在撰寫指令碼說明主題的範例，請務必範例命令中包含的指令碼檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="15965-138">When writing examples for a script help topic, be sure to include the path to the script file in the example command.</span></span> <span data-ttu-id="15965-139">這會提醒使用者，他們必須指定路徑明確，即使指令碼是在目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="15965-139">This reminds users that they must specify the path explicitly, even when the script is in the current directory.</span></span>

- <span data-ttu-id="15965-140">在函式說明主題中，提醒函式只存在於目前工作階段的使用者，而若要使用它在其他工作階段，它們需要加入它，或將它加入 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="15965-140">In a function help topic, remind users that the function exists only in the current session and, to use it in other sessions, they need to add it, or add it a PowerShell profile.</span></span>

- <span data-ttu-id="15965-141">`Get-Help` 顯示說明主題的指令碼或函式的指令碼檔案和說明主題檔會儲存在正確的位置時，才。</span><span class="sxs-lookup"><span data-stu-id="15965-141">`Get-Help` displays the help topic for a script or function only when the script file and help topic files are saved in the correct locations.</span></span> <span data-ttu-id="15965-142">因此，最好不包含安裝 PowerShell，或儲存安裝指令碼或函式的說明主題中的指令碼或函式的相關指示。</span><span class="sxs-lookup"><span data-stu-id="15965-142">Therefore, it is not useful to include instructions for installing PowerShell, or saving or installing the script or function in a script or function help topic.</span></span> <span data-ttu-id="15965-143">相反地，您使用發佈的指令碼或函式的文件中包含的任何安裝指示。</span><span class="sxs-lookup"><span data-stu-id="15965-143">Instead, include any installation instructions in the document that you use to distribute the script or function.</span></span>

## <a name="see-also"></a><span data-ttu-id="15965-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15965-144">See Also</span></span>

 [<span data-ttu-id="15965-145">指令碼和函式撰寫 XML 為基礎的說明主題</span><span class="sxs-lookup"><span data-stu-id="15965-145">Writing XML-Based Help Topics for Scripts and Functions</span></span>](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [<span data-ttu-id="15965-146">撰寫 XML 為基礎的說明主題的命令</span><span class="sxs-lookup"><span data-stu-id="15965-146">Writing XML-Based Help Topics for Commands</span></span>](./writing-xml-based-help-topics-for-commands.md)

 [<span data-ttu-id="15965-147">撰寫註解式說明主題</span><span class="sxs-lookup"><span data-stu-id="15965-147">Writing Comment-Based Help Topics</span></span>](./writing-comment-based-help-topics.md)
