---
title: 使用 Visual Studio Code 來進行遠端編輯與偵錯
description: 使用 Visual Studio Code 來進行遠端編輯與偵錯
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086660"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="3b70d-103">使用 Visual Studio Code 來進行遠端編輯與偵錯</span><span class="sxs-lookup"><span data-stu-id="3b70d-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="3b70d-104">對於已經熟悉使用 ISE 的人，可能還記得可以從整合式主控台執行 `psedit file.ps1` 以直接在 ISE 中開啟檔案 (本機或遠端)。</span><span class="sxs-lookup"><span data-stu-id="3b70d-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="3b70d-105">其實適用於 VSCode 的 PowerShell 延伸模組中也提供此功能。</span><span class="sxs-lookup"><span data-stu-id="3b70d-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="3b70d-106">此指南將示範如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="3b70d-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b70d-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="3b70d-107">Prerequisites</span></span>

<span data-ttu-id="3b70d-108">此指南假設您有：</span><span class="sxs-lookup"><span data-stu-id="3b70d-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="3b70d-109">您擁有存取權的遠端資源 (例如：VM、容器)</span><span class="sxs-lookup"><span data-stu-id="3b70d-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="3b70d-110">在遠端資源和主機電腦中執行的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b70d-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="3b70d-111">VSCode 和適用於 VSCode 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="3b70d-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="3b70d-112">此功能可在 Windows PowerShell 和 PowerShell Core 上運作。</span><span class="sxs-lookup"><span data-stu-id="3b70d-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="3b70d-113">透過 WinRM、PowerShell Direct 或 SSH 連線至遠端電腦時，也可以使用此功能。</span><span class="sxs-lookup"><span data-stu-id="3b70d-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="3b70d-114">如果想要使用 SSH，但現在使用 Windows，請參閱 [SSH 的 Win32 版本](https://github.com/PowerShell/Win32-OpenSSH) \(英文\)！</span><span class="sxs-lookup"><span data-stu-id="3b70d-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="3b70d-115">開始</span><span class="sxs-lookup"><span data-stu-id="3b70d-115">Let's go</span></span>

<span data-ttu-id="3b70d-116">在此節中，我將透過 MacBook Pro 逐步示範並說明對 Azure 中執行的 Ubuntu VM 進行遠端編輯和偵錯。</span><span class="sxs-lookup"><span data-stu-id="3b70d-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="3b70d-117">我可能不會再使用 Windows 示範一次，不過**程序完全相同**。</span><span class="sxs-lookup"><span data-stu-id="3b70d-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="3b70d-118">使用 Open-EditorFile 編輯本機檔案</span><span class="sxs-lookup"><span data-stu-id="3b70d-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="3b70d-119">當適用於 VSCode 的 PowerShell 延伸模組已啟動且 PowerShell 整合式主控台已開啟之後，我們可以輸入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1`，以直接在編輯器中開啟本機 foo.ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="3b70d-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 可在本機運作](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="3b70d-121">foo.ps1 必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="3b70d-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="3b70d-122">我們可以從那裡：</span><span class="sxs-lookup"><span data-stu-id="3b70d-122">From there, we can:</span></span>

<span data-ttu-id="3b70d-123">將中斷點新增至巡覽邊![將中斷點新增至巡覽邊](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png) \(英文\)，</span><span class="sxs-lookup"><span data-stu-id="3b70d-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="3b70d-124">然後按 F5 以針對 PowerShell 指令碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="3b70d-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="3b70d-125">![針對 PowerShell 本機指令碼進行偵錯](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="3b70d-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="3b70d-126">偵錯時，可以與偵錯主控台互動，查看左側範圍中和所有其他標準偵錯工具中的變數。</span><span class="sxs-lookup"><span data-stu-id="3b70d-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="3b70d-127">使用 Open-EditorFile 編輯遠端檔案</span><span class="sxs-lookup"><span data-stu-id="3b70d-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="3b70d-128">現在讓我們進入遠端檔案編輯和偵錯。</span><span class="sxs-lookup"><span data-stu-id="3b70d-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="3b70d-129">步驟幾乎完全相同，只是要先做一件事，那就是在遠端伺服器中啟動我們的 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="3b70d-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="3b70d-130">有一個 Cmdlet 可執行此動作。</span><span class="sxs-lookup"><span data-stu-id="3b70d-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="3b70d-131">它稱為 `Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="3b70d-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="3b70d-132">下面提供該 Cmdlet 的說明：</span><span class="sxs-lookup"><span data-stu-id="3b70d-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="3b70d-133">`Enter-PSSession -ComputerName foo` 會透過 WinRM 啟動一個工作階段</span><span class="sxs-lookup"><span data-stu-id="3b70d-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="3b70d-134">`Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 會透過 PowerShell Direct 啟動一個工作階段</span><span class="sxs-lookup"><span data-stu-id="3b70d-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="3b70d-135">`Enter-PSSession -HostName foo` 會透過 SSH 啟動一個工作階段</span><span class="sxs-lookup"><span data-stu-id="3b70d-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="3b70d-136">如需 `Enter-PSSession` 的詳細資訊，請參閱[這裡](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6) \(英文\) 的文件。</span><span class="sxs-lookup"><span data-stu-id="3b70d-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="3b70d-137">我將使用 SSH 進行遠端處理，因為我要從 macOS 前往 Azure 中的 Ubuntu VM。</span><span class="sxs-lookup"><span data-stu-id="3b70d-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="3b70d-138">首先，在整合式主控台中執行我們的 Enter-PSSession。</span><span class="sxs-lookup"><span data-stu-id="3b70d-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="3b70d-139">您將會知道您正在工作階段中，因為 `[something]` 會顯示在您系統提示的左邊。</span><span class="sxs-lookup"><span data-stu-id="3b70d-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![呼叫 Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="3b70d-141">我們可以從這裡依據之前編輯好的本機指令碼，確切地執行每個步驟。</span><span class="sxs-lookup"><span data-stu-id="3b70d-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="3b70d-142">執行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 以開啟遠端 `test.ps1` 檔案 ![Open-EditorFile the test.ps1 檔案](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="3b70d-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="3b70d-143">編輯檔案/設定中斷點</span><span class="sxs-lookup"><span data-stu-id="3b70d-143">Edit the file/set breakpoints</span></span> ![編輯並設定中斷點](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="3b70d-145">開始針對遠端檔案進行偵錯 (F5)</span><span class="sxs-lookup"><span data-stu-id="3b70d-145">Start debugging (F5) the remote file</span></span>

![針對遠端檔案進行偵錯](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="3b70d-147">這樣就完成了！</span><span class="sxs-lookup"><span data-stu-id="3b70d-147">That's all there's to it!</span></span> <span data-ttu-id="3b70d-148">我們希望此指南能協助您解決和在 VSCode 中進行遠端偵錯和編輯 PowerShell 有關的問題。</span><span class="sxs-lookup"><span data-stu-id="3b70d-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="3b70d-149">如果您有任何問題，歡迎前往 [GitHub 存放庫](http://github.com/powershell/vscode-powershell) \(英文\) 提出問題。</span><span class="sxs-lookup"><span data-stu-id="3b70d-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
