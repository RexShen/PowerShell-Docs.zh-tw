---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell 指令碼
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058483"
---
# <a name="powershell"></a><span data-ttu-id="8e128-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e128-103">PowerShell</span></span>

<span data-ttu-id="8e128-104">PowerShell 是工作型命令列殼層與指令碼語言，並建置在 .NET 之上。</span><span class="sxs-lookup"><span data-stu-id="8e128-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="8e128-105">PowerShell 可協助系統管理員與進階使用者快速地將管理作業系統 (Linux、macOS 與 Windows) 與處理序的工作自動化。</span><span class="sxs-lookup"><span data-stu-id="8e128-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="8e128-106">PowerShell 命令可讓您從命令列管理電腦。</span><span class="sxs-lookup"><span data-stu-id="8e128-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="8e128-107">PowerShell 提供者可讓您如同存取檔案系統般輕易地存取資料存放區 (例如登錄與憑證存放區)。</span><span class="sxs-lookup"><span data-stu-id="8e128-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="8e128-108">PowerShell 包含豐富的運算式剖析器與完整開發的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="8e128-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="8e128-109">PowerShell 是開放原始碼</span><span class="sxs-lookup"><span data-stu-id="8e128-109">PowerShell is open-source</span></span>

<span data-ttu-id="8e128-110">PowerShell 基本原始程式碼現在可在 GitHub 中取得並開放進行社群參與。</span><span class="sxs-lookup"><span data-stu-id="8e128-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="8e128-111">請參閱 [GitHub 上的 PowerShell 原始碼](https://github.com/powershell/powershell)。</span><span class="sxs-lookup"><span data-stu-id="8e128-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="8e128-112">您可以在[取得 PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 中，找到入門所需的事項。</span><span class="sxs-lookup"><span data-stu-id="8e128-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="8e128-113">或者，從[開始使用](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell) \(英文\) 的快速入門開始。</span><span class="sxs-lookup"><span data-stu-id="8e128-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="8e128-114">PowerShell 設計目標</span><span class="sxs-lookup"><span data-stu-id="8e128-114">PowerShell design goals</span></span>

<span data-ttu-id="8e128-115">PowerShell 消除了長久以來的問題並加入新功能，藉以改善命令列和指令碼環境。</span><span class="sxs-lookup"><span data-stu-id="8e128-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="8e128-116">可搜尋性</span><span class="sxs-lookup"><span data-stu-id="8e128-116">Discoverability</span></span>

<span data-ttu-id="8e128-117">PowerShell 可讓您輕鬆搜尋它的功能。</span><span class="sxs-lookup"><span data-stu-id="8e128-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="8e128-118">例如，若要尋找可檢視和變更 Windows 服務的 Cmdlet 清單，請輸入：</span><span class="sxs-lookup"><span data-stu-id="8e128-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="8e128-119">搜尋到可完成工作的 Cmdlet 之後，即可使用 `Get-Help` Cmdlet 來進一步了解此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e128-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="8e128-120">例如，若要顯示 `Get-Service` Cmdlet 的說明，請輸入：</span><span class="sxs-lookup"><span data-stu-id="8e128-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="8e128-121">大部分的 Cmdlet 都會傳回物件，這些物件可均操作然後轉譯為可供顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="8e128-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="8e128-122">若要完全了解 Cmdlet 的輸出，請透過管道將輸出傳送到 `Get-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e128-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="8e128-123">例如，下列命令會顯示 `Get-Service` Cmdlet 所輸出物件的成員相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8e128-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="8e128-124">一致性</span><span class="sxs-lookup"><span data-stu-id="8e128-124">Consistency</span></span>

<span data-ttu-id="8e128-125">管理系統是一個複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="8e128-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="8e128-126">擁有一致介面的工具有助於控制其中的複雜性。</span><span class="sxs-lookup"><span data-stu-id="8e128-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="8e128-127">可惜的是，命令列工具與可編寫指令碼的元件物件模型 (COM) 物件都不具有一致性。</span><span class="sxs-lookup"><span data-stu-id="8e128-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="8e128-128">因此，PowerShell 的一致性是非常寶貴的資產。</span><span class="sxs-lookup"><span data-stu-id="8e128-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="8e128-129">例如，如果您知道如何使用 `Sort-Object` Cmdlet，即可利用該知識來排序任何 Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="8e128-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="8e128-130">您不必了解每個 Cmdlet 的不同排序常式。</span><span class="sxs-lookup"><span data-stu-id="8e128-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="8e128-131">此外，Cmdlet 開發人員也不需要設計其 Cmdlet 的排序功能。</span><span class="sxs-lookup"><span data-stu-id="8e128-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="8e128-132">PowerShell 提供具有基本功能的架構，以強制執行一致性。</span><span class="sxs-lookup"><span data-stu-id="8e128-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="8e128-133">此架構會消除一些留給開發人員的選項。</span><span class="sxs-lookup"><span data-stu-id="8e128-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="8e128-134">但結果會讓 Cmdlet 的開發作業變得更簡單。</span><span class="sxs-lookup"><span data-stu-id="8e128-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="8e128-135">互動式與指令碼環境</span><span class="sxs-lookup"><span data-stu-id="8e128-135">Interactive and scripting environments</span></span>

<span data-ttu-id="8e128-136">Windows 命令提示字元提供互動式殼層，其中具備命令列工具與基本指令碼的存取權。</span><span class="sxs-lookup"><span data-stu-id="8e128-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="8e128-137">Windows Script Host (WSH) 具有可編寫指令碼的命令列工具與 COM 自動化物件，但不提供互動式殼層。</span><span class="sxs-lookup"><span data-stu-id="8e128-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="8e128-138">PowerShell 結合了互動式殼層與指令碼環境。</span><span class="sxs-lookup"><span data-stu-id="8e128-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="8e128-139">PowerShell 可以存取命令列工具、COM 物件與 .NET 類別庫。</span><span class="sxs-lookup"><span data-stu-id="8e128-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="8e128-140">這個功能組合會擴充互動式使用者、指令碼寫入器與系統管理員的能力。</span><span class="sxs-lookup"><span data-stu-id="8e128-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="8e128-141">物件導向</span><span class="sxs-lookup"><span data-stu-id="8e128-141">Object orientation</span></span>

<span data-ttu-id="8e128-142">PowerShell 以物件而非文字為基礎。</span><span class="sxs-lookup"><span data-stu-id="8e128-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="8e128-143">命令的輸出即為物件。</span><span class="sxs-lookup"><span data-stu-id="8e128-143">The output of a command is an object.</span></span> <span data-ttu-id="8e128-144">您可以透過管線將輸出物件傳送到另一個命令以作為它的輸入。</span><span class="sxs-lookup"><span data-stu-id="8e128-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="8e128-145">此管線為具有其他殼層使用體驗的人提供熟悉的介面。</span><span class="sxs-lookup"><span data-stu-id="8e128-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="8e128-146">PowerShell 透過傳送物件而非文字來延伸此概念。</span><span class="sxs-lookup"><span data-stu-id="8e128-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="8e128-147">輕鬆轉換為指令碼</span><span class="sxs-lookup"><span data-stu-id="8e128-147">Easy transition to scripting</span></span>

<span data-ttu-id="8e128-148">PowerShell 的命令可探索性可將以互動方式輸入命令的作業，輕鬆轉換為建立及執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="8e128-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="8e128-149">PowerShell 文字記錄與歷程記錄可讓您輕鬆地將命令複製到檔案，以用來作為指令碼。</span><span class="sxs-lookup"><span data-stu-id="8e128-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
