---
title: 使用 Visual Studio Code 來進行遠端編輯與偵錯
description: 使用 Visual Studio Code 來進行遠端編輯與偵錯
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655584"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="1e683-103">使用 Visual Studio Code 來進行遠端編輯與偵錯</span><span class="sxs-lookup"><span data-stu-id="1e683-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="1e683-104">對於您已熟悉使用 ISE，您可能還記得，您可以執行`psedit file.ps1`從整合式主控台來開啟檔案-本機或遠端-以滑鼠右鍵在 ISE 中。</span><span class="sxs-lookup"><span data-stu-id="1e683-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="1e683-105">其實，這項功能也是用於 VSCode 的 PowerShell 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1e683-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="1e683-106">本指南將示範如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="1e683-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e683-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="1e683-107">Prerequisites</span></span>

<span data-ttu-id="1e683-108">本指南假設您有：</span><span class="sxs-lookup"><span data-stu-id="1e683-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="1e683-109">遠端資源 (例如： VM 時，容器)，您必須擁有存取權</span><span class="sxs-lookup"><span data-stu-id="1e683-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="1e683-110">它與主機電腦上執行的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e683-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="1e683-111">VSCode，VSCode 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="1e683-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="1e683-112">這項功能適用於 Windows PowerShell 和 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="1e683-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="1e683-113">連接到遠端電腦透過 WinRM、 PowerShell Direct 或 SSH 時，也適用於這項功能。</span><span class="sxs-lookup"><span data-stu-id="1e683-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="1e683-114">如果您想要使用 SSH，但使用 Windows，請參閱[SSH Win32 版本](https://github.com/PowerShell/Win32-OpenSSH)！</span><span class="sxs-lookup"><span data-stu-id="1e683-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="1e683-115">開始</span><span class="sxs-lookup"><span data-stu-id="1e683-115">Let's go</span></span>

<span data-ttu-id="1e683-116">在本節中，我將逐步遠端編輯和偵錯從我的 Iphone，以在 Azure 中執行的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="1e683-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="1e683-117">我可能不會使用 Windows，但**程序是相同**。</span><span class="sxs-lookup"><span data-stu-id="1e683-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="1e683-118">使用開放 EditorFile 編輯本機檔案</span><span class="sxs-lookup"><span data-stu-id="1e683-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="1e683-119">使用 PowerShell 延伸模組啟動 VSCode，並開啟 PowerShell 整合式主控台中，我們可以輸入`Open-EditorFile foo.ps1`或`psedit foo.ps1`在編輯器中開啟本機 foo.ps1 檔案權限。</span><span class="sxs-lookup"><span data-stu-id="1e683-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![在本機開啟 EditorFile foo.ps1 運作方式](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="1e683-121">foo.ps1 必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="1e683-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="1e683-122">在這裡，我們可以：</span><span class="sxs-lookup"><span data-stu-id="1e683-122">From there, we can:</span></span>

<span data-ttu-id="1e683-123">將中斷點加入至巡覽邊![加入到邊的中斷點](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="1e683-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="1e683-124">然後按 F5 以偵錯 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e683-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="1e683-125">![PowerShell 的本機指令碼偵錯](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="1e683-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="1e683-126">偵錯時，您可以與偵錯主控台互動，查看在左側，而所有其他標準偵錯工具的範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="1e683-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="1e683-127">使用開放 EditorFile 編輯遠端檔案</span><span class="sxs-lookup"><span data-stu-id="1e683-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="1e683-128">現在讓我們進入遠端檔案編輯和偵錯。</span><span class="sxs-lookup"><span data-stu-id="1e683-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="1e683-129">步驟幾乎完全相同，我們需要先進行-我們的 PowerShell 工作階段輸入到遠端伺服器的只是一件事。</span><span class="sxs-lookup"><span data-stu-id="1e683-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="1e683-130">若要這樣做沒有一個 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1e683-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="1e683-131">它會呼叫`Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="1e683-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="1e683-132">灌了水，向下的說明內容是 cmdlet 的：</span><span class="sxs-lookup"><span data-stu-id="1e683-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="1e683-133">`Enter-PSSession -ComputerName foo` 啟動工作階段透過 WinRM</span><span class="sxs-lookup"><span data-stu-id="1e683-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="1e683-134">`Enter-PSSession -ContainerId foo` 和`Enter-PSSession -VmId foo`開始透過 PowerShell Direct 工作階段</span><span class="sxs-lookup"><span data-stu-id="1e683-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="1e683-135">`Enter-PSSession -HostName foo` 啟動透過 SSH 工作階段</span><span class="sxs-lookup"><span data-stu-id="1e683-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="1e683-136">如需詳細資訊`Enter-PSSession`，查看文件[這裡](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6)。</span><span class="sxs-lookup"><span data-stu-id="1e683-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="1e683-137">我將使用 SSH 進行遠端處理因為我從 macOS 要在 Azure 中的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="1e683-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="1e683-138">首先，在整合式主控台中，讓我們執行我們 Enter-pssession。</span><span class="sxs-lookup"><span data-stu-id="1e683-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="1e683-139">您知道您正在工作階段中，因為`[something]`會顯示您的提示字元的左邊。</span><span class="sxs-lookup"><span data-stu-id="1e683-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Enter-pssession 呼叫](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="1e683-141">在這裡，我們可以處理的確切步驟，如同我們先前所編輯的本機指令碼。</span><span class="sxs-lookup"><span data-stu-id="1e683-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="1e683-142">執行`Open-EditorFile test.ps1`或是`psedit test.ps1`以開啟遠端`test.ps1`檔案![開放 EditorFile test.ps1 檔案](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="1e683-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="1e683-143">編輯檔案/設定中斷點</span><span class="sxs-lookup"><span data-stu-id="1e683-143">Edit the file/set breakpoints</span></span> ![編輯，並設定中斷點](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="1e683-145">開始偵錯 (F5) 的遠端檔案</span><span class="sxs-lookup"><span data-stu-id="1e683-145">Start debugging (F5) the remote file</span></span>

![偵錯遠端檔案](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="1e683-147">這樣就完成了 ！</span><span class="sxs-lookup"><span data-stu-id="1e683-147">That's all there's to it!</span></span> <span data-ttu-id="1e683-148">我們希望本指南協助清除任何關於遠端偵錯和編輯在 VSCode 中的 PowerShell 的問題。</span><span class="sxs-lookup"><span data-stu-id="1e683-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="1e683-149">如果您有任何問題，歡迎提出問題[GitHub 儲存機制](http://github.com/powershell/vscode-powershell)。</span><span class="sxs-lookup"><span data-stu-id="1e683-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
