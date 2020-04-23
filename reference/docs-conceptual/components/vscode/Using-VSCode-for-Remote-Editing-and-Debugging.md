---
title: 使用 Visual Studio Code 來進行遠端編輯與偵錯
description: 使用 Visual Studio Code 來進行遠端編輯與偵錯
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78279104"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="55975-103">使用 Visual Studio Code 來進行遠端編輯與偵錯</span><span class="sxs-lookup"><span data-stu-id="55975-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="55975-104">對於熟悉使用 ISE 的人，可能還記得可以從整合式主控台執行 `psedit file.ps1`，以直接在 ISE 中開啟檔案 (本機或遠端)。</span><span class="sxs-lookup"><span data-stu-id="55975-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="55975-105">適用於 VSCode 的 PowerShell 延伸模組中也提供此功能。</span><span class="sxs-lookup"><span data-stu-id="55975-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="55975-106">此指南將示範如何執行此動作。</span><span class="sxs-lookup"><span data-stu-id="55975-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55975-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="55975-107">Prerequisites</span></span>

<span data-ttu-id="55975-108">此指南假設您有：</span><span class="sxs-lookup"><span data-stu-id="55975-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="55975-109">您有權存取的遠端資源 (例如：VM、容器)</span><span class="sxs-lookup"><span data-stu-id="55975-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="55975-110">在遠端資源和主機電腦中執行的 PowerShell</span><span class="sxs-lookup"><span data-stu-id="55975-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="55975-111">VSCode 和適用於 VSCode 的 PowerShell 延伸模組</span><span class="sxs-lookup"><span data-stu-id="55975-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="55975-112">此功能可在 Windows PowerShell 和 PowerShell Core 上運作。</span><span class="sxs-lookup"><span data-stu-id="55975-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="55975-113">透過 WinRM、PowerShell Direct 或 SSH 連線至遠端電腦時，也可以使用此功能。</span><span class="sxs-lookup"><span data-stu-id="55975-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="55975-114">如果想要使用 SSH，但現在使用 Windows，請參閱 [SSH 的 Win32 版本](https://github.com/PowerShell/Win32-OpenSSH) \(英文\)！</span><span class="sxs-lookup"><span data-stu-id="55975-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55975-115">`Open-EditorFile` 和 `psedit` 命令只能在適用於 VSCode 的 PowerShell 延伸模組所建立的 **PowerShell 整合式主控台**中運作。</span><span class="sxs-lookup"><span data-stu-id="55975-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="55975-116">使用範例</span><span class="sxs-lookup"><span data-stu-id="55975-116">Usage examples</span></span>

<span data-ttu-id="55975-117">這些範例將示範如何從 MacBook Pro，對在 Azure 中執行的 Ubuntu VM 進行遠端編輯和偵錯。</span><span class="sxs-lookup"><span data-stu-id="55975-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="55975-118">此程序在 Windows 上完全相同。</span><span class="sxs-lookup"><span data-stu-id="55975-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="55975-119">使用 Open-EditorFile 編輯本機檔案</span><span class="sxs-lookup"><span data-stu-id="55975-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="55975-120">當適用於 VSCode 的 PowerShell 延伸模組已啟動且 PowerShell 整合式主控台已開啟之後，我們可以輸入 `Open-EditorFile foo.ps1` 或 `psedit foo.ps1`，以直接在編輯器中開啟本機 foo.ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="55975-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 可在本機運作](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="55975-122">`foo.ps1` 檔案必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="55975-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="55975-123">我們可以從那裡：</span><span class="sxs-lookup"><span data-stu-id="55975-123">From there, we can:</span></span>

- <span data-ttu-id="55975-124">在巡覽邊新增中斷點</span><span class="sxs-lookup"><span data-stu-id="55975-124">Add breakpoints to the gutter</span></span>

  ![在巡覽邊新增中斷點](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="55975-126">按 F5 以針對 PowerShell 指令碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="55975-126">Hit F5 to debug the PowerShell script.</span></span>

  ![針對 PowerShell 本機指令碼進行偵錯](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="55975-128">偵錯時，可以與偵錯主控台互動，查看左側範圍中和所有其他標準偵錯工具中的變數。</span><span class="sxs-lookup"><span data-stu-id="55975-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="55975-129">使用 Open-EditorFile 編輯遠端檔案</span><span class="sxs-lookup"><span data-stu-id="55975-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="55975-130">現在讓我們進入遠端檔案編輯和偵錯。</span><span class="sxs-lookup"><span data-stu-id="55975-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="55975-131">步驟幾乎完全相同，只是要先做一件事，那就是在遠端伺服器中啟動我們的 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="55975-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="55975-132">有一個 Cmdlet 可執行此動作。</span><span class="sxs-lookup"><span data-stu-id="55975-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="55975-133">它稱為 `Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="55975-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="55975-134">下面提供該 Cmdlet 的說明：</span><span class="sxs-lookup"><span data-stu-id="55975-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="55975-135">`Enter-PSSession -ComputerName foo` 會透過 WinRM 啟動一個工作階段</span><span class="sxs-lookup"><span data-stu-id="55975-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="55975-136">`Enter-PSSession -ContainerId foo` 和 `Enter-PSSession -VmId foo` 會透過 PowerShell Direct 啟動一個工作階段</span><span class="sxs-lookup"><span data-stu-id="55975-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="55975-137">`Enter-PSSession -HostName foo` 會透過 SSH 啟動一個工作階段</span><span class="sxs-lookup"><span data-stu-id="55975-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="55975-138">如需詳細資訊，請參閱適用於 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) 的文件。</span><span class="sxs-lookup"><span data-stu-id="55975-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="55975-139">由於我們要從 macOS 前往 Azure 中的 Ubuntu VM，因此會使用 SSH 進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="55975-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="55975-140">首先，在整合式主控台中，執行 `Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="55975-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="55975-141">當 `[<hostname>]` 顯示於您提示字元的最左邊時，表示您已連線到遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="55975-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![呼叫 Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="55975-143">現在，我們可以執行與編輯本機指令碼相同的步驟。</span><span class="sxs-lookup"><span data-stu-id="55975-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="55975-144">執行 `Open-EditorFile test.ps1` 或 `psedit test.ps1` 以開啟遠端 `test.ps1` 檔案</span><span class="sxs-lookup"><span data-stu-id="55975-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Open-EditorFile test.ps1 檔案](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="55975-146">編輯檔案/設定中斷點</span><span class="sxs-lookup"><span data-stu-id="55975-146">Edit the file/set breakpoints</span></span>

   ![編輯並設定中斷點](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="55975-148">開始針對遠端檔案進行偵錯 (F5)</span><span class="sxs-lookup"><span data-stu-id="55975-148">Start debugging (F5) the remote file</span></span>

   ![針對遠端檔案進行偵錯](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="55975-150">如果您有任何問題，您可以在 [GitHub 存放庫](https://github.com/powershell/vscode-powershell) \(英文\) 中提出問題。</span><span class="sxs-lookup"><span data-stu-id="55975-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
