---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShell 指令碼
ms.openlocfilehash: 7de5a3f3149d8d464b34101d94a5f9430d9b0f23
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="powershell"></a><span data-ttu-id="3ab7b-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ab7b-103">PowerShell</span></span>

<span data-ttu-id="3ab7b-104">PowerShell 建基於 .NET Framework，是以工作為基礎的命令列殼層與指令碼語言；專為系統管理員和進階使用者而設計，可快速將多個作業系統 (Linux、macOS、Unix 及 Windows) 的管理，以及這些作業系統上執行的應用程式相關處理序自動化。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="3ab7b-105">PowerShell 是開放原始碼</span><span class="sxs-lookup"><span data-stu-id="3ab7b-105">PowerShell is open source</span></span>

<span data-ttu-id="3ab7b-106">PowerShell 基本原始程式碼現在可在 GitHub 中取得並開放進行社群參與。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span> <span data-ttu-id="3ab7b-107">請參閱 [GitHub 上的 PowerShell 原始碼](https://github.com/powershell/powershell)。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="3ab7b-108">您可以從 [get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 所需的位元開始。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-108">You can start with the bits you need at [get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="3ab7b-109">或者，可能是從[開始使用](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)的快速入門開始</span><span class="sxs-lookup"><span data-stu-id="3ab7b-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="3ab7b-110">PowerShell 設計目標</span><span class="sxs-lookup"><span data-stu-id="3ab7b-110">PowerShell design goals</span></span>
<span data-ttu-id="3ab7b-111">Windows PowerShell 的設計目的是消除長久以來的問題並加入新功能，以改善命令列和指令碼環境。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-111">Windows PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="3ab7b-112">可搜尋性</span><span class="sxs-lookup"><span data-stu-id="3ab7b-112">Discoverability</span></span>
<span data-ttu-id="3ab7b-113">Windows PowerShell 可讓您輕鬆搜尋它的功能。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-113">Windows PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="3ab7b-114">例如，若要尋找可檢視和變更 Windows 服務的 Cmdlet 清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="3ab7b-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="3ab7b-115">搜尋到可完成工作的 Cmdlet 之後，即可使用 Get-Help Cmdlet 進一步了解此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the Get-Help cmdlet.</span></span> <span data-ttu-id="3ab7b-116">例如，若要顯示 Get-Service Cmdlet 的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="3ab7b-116">For example, to display help about the Get-Service cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="3ab7b-117">多數 Cmdlet 皆會發出物件，此類物件可操作並轉譯成供顯示用的文字。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span> <span data-ttu-id="3ab7b-118">若要完全了解該 Cmdlet 的輸出，可將其輸出輸送至 Get-Member Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-118">To fully understand the output of that cmdlet, pipe its output to the Get-Member cmdlet.</span></span> <span data-ttu-id="3ab7b-119">例如，下列命令會顯示 Get-Service Cmdlet 之物件輸出成員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-119">For example, the following command displays information about the members of the object output by the Get-Service cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="3ab7b-120">一致性</span><span class="sxs-lookup"><span data-stu-id="3ab7b-120">Consistency</span></span>
<span data-ttu-id="3ab7b-121">管理系統是一項複雜的工作，因此擁有一致介面的工具有助控制其中的複雜性。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="3ab7b-122">可惜的是，不論命令列工具或可編寫指令碼的 COM 物件都不具有一致性。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="3ab7b-123">因此，Windows PowerShell 的一致性是非常寶貴的資產。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-123">The consistency of Windows PowerShell is one of its primary assets.</span></span> <span data-ttu-id="3ab7b-124">例如，如果您知道如何使用 Sort-Object Cmdlet，即可利用該知識來排序任何 Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-124">For example, if you learn how to use the Sort-Object cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="3ab7b-125">而不必去了解每個 Cmdlet 的不同排序常式。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="3ab7b-126">此外，Cmdlet 開發人員也不需要設計其 Cmdlet 的排序功能。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="3ab7b-127">Windows PowerShell 提供具有基本功能的架構，可強制讓介面的許多方面保持一致。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-127">Windows PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span> <span data-ttu-id="3ab7b-128">雖然開發人員針對此架構少了一些選擇權，但是這個架構可讓他們更輕鬆開發出強固和易於使用的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="3ab7b-129">互動式和指令碼環境</span><span class="sxs-lookup"><span data-stu-id="3ab7b-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="3ab7b-130">Windows PowerShell 是一種結合的互動式和指令碼環境，可讓您存取命令列工具和 COM 物件，並讓您使用 .NET Framework Class Library (FCL) 的功能。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-130">Windows PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="3ab7b-131">Windows 命令提示字元提供互動式環境及多種命令列工具，而這個環境則更加強化。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span> <span data-ttu-id="3ab7b-132">Windows Script Host (WSH) 指令碼可讓您使用多種命令列工具和 COM Automation 物件，但不提供互動式環境；基於此，這個環境也做了改善。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="3ab7b-133">Windows PowerShell 將上述所有功能的存取結合，擴充互動式使用者和指令碼寫入器的功能，並使系統管理更容易進行。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-133">By combining access to all of these features, Windows PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="3ab7b-134">物件導向</span><span class="sxs-lookup"><span data-stu-id="3ab7b-134">Object Orientation</span></span>
<span data-ttu-id="3ab7b-135">雖然您可以輸入文字命令來與 Windows PowerShell 互動，但 Windows PowerShell 是以物件為基礎，而非文字。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-135">Although you interact with Windows PowerShell by typing commands in text, Windows PowerShell is based on objects, not text.</span></span> <span data-ttu-id="3ab7b-136">命令的輸出即為物件。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-136">The output of a command is an object.</span></span> <span data-ttu-id="3ab7b-137">您可以將輸出物件傳送到另一個命令以作為輸入。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-137">You can send the output object to another command as its input.</span></span> <span data-ttu-id="3ab7b-138">因此，Windows PowerShell 提供熟悉的介面給慣用其他介面的使用者，同時還引入功能強大的全新命令列範例。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-138">As a result, Windows PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span> <span data-ttu-id="3ab7b-139">它可讓您傳送物件，而不是文字，藉此延伸在命令之間傳送資料的概念。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="3ab7b-140">輕鬆轉換指令碼</span><span class="sxs-lookup"><span data-stu-id="3ab7b-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="3ab7b-141">Windows PowerShell 可將以互動方式輸入命令的作業，輕鬆轉換為建立和執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-141">Windows PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="3ab7b-142">您可以在 Windows PowerShell 命令提示字元中輸入命令，以探索執行工作的命令。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-142">You can type commands at the Windows PowerShell command prompt to discover the commands that perform a task.</span></span> <span data-ttu-id="3ab7b-143">然後，您可以將這些命令儲存在文字記錄或歷程記錄中，再複製到檔案，以作為指令碼使用。</span><span class="sxs-lookup"><span data-stu-id="3ab7b-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
