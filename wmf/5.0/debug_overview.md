---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: dee5e8206c61d79faadf8573a82c74d4ac0fb8e0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="3626c-102">PowerShell 指令碼偵錯的增強功能</span><span class="sxs-lookup"><span data-stu-id="3626c-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="3626c-103">PowerShell 5.0 已改善數項功能，以增強偵錯經驗︰</span><span class="sxs-lookup"><span data-stu-id="3626c-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="3626c-104">全部中斷</span><span class="sxs-lookup"><span data-stu-id="3626c-104">Break All</span></span>

<span data-ttu-id="3626c-105">PowerShell 主控台和 Windows PowerShell ISE 現在可讓您開始偵錯工具執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="3626c-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="3626c-106">這在本機和遠端工作階段皆適用。</span><span class="sxs-lookup"><span data-stu-id="3626c-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="3626c-107">在主控台中，按 **Ctrl+Break**。</span><span class="sxs-lookup"><span data-stu-id="3626c-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="3626c-108">在 ISE 中，按 **Ctrl+B**，或使用 **[偵錯] -> [全部中斷]** 功能表命令。</span><span class="sxs-lookup"><span data-stu-id="3626c-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="3626c-109">Windows PowerShell ISE 的遠端偵錯和遠端檔案編輯</span><span class="sxs-lookup"><span data-stu-id="3626c-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="3626c-110">Windows PowerShell ISE 現在可讓您執行 PSEdit 命令，在遠端工作階段中開啟及編輯檔案。</span><span class="sxs-lookup"><span data-stu-id="3626c-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="3626c-111">例如，您可以開啟檔案從遠端工作階段的命令列中進行編輯，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="3626c-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="3626c-112">此外，您現在可以編輯並儲存遠端檔案的變更，當您點擊中斷點時遠端檔案就會自動在 Windows PowerShell ISE 中開啟。</span><span class="sxs-lookup"><span data-stu-id="3626c-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="3626c-113">現在，您可以偵錯在遠端電腦上執行的指令碼檔案、編輯檔案以修正錯誤，然後重新執行修改過的指令碼。</span><span class="sxs-lookup"><span data-stu-id="3626c-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="3626c-114">進階指令碼偵錯</span><span class="sxs-lookup"><span data-stu-id="3626c-114">Advanced Script Debugging</span></span>

<span data-ttu-id="3626c-115">有新的進階偵錯功能，可讓您附加至任何已載入 Windows PowerShell 的本機電腦處理程序，並偵錯該處理程序的任意 Runspace。</span><span class="sxs-lookup"><span data-stu-id="3626c-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="3626c-116">Runspace 偵錯</span><span class="sxs-lookup"><span data-stu-id="3626c-116">Runspace Debugging</span></span>

<span data-ttu-id="3626c-117">已加入新的 Cmdlet，可讓您列出處理程序目前的 Runspace，並將 Windows PowerShell 主控台或 ISE 偵錯工具附加至指令碼偵錯的 Runspace：</span><span class="sxs-lookup"><span data-stu-id="3626c-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="3626c-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="3626c-118">Get-Runspace</span></span>
-   <span data-ttu-id="3626c-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="3626c-119">Debug-Runspace</span></span>
-   <span data-ttu-id="3626c-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3626c-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="3626c-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3626c-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="3626c-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="3626c-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="3626c-123">附加至裝載 PowerShell 的處理程序</span><span class="sxs-lookup"><span data-stu-id="3626c-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="3626c-124">您現在可以附加至已載入 Windows PowerShell 的任何電腦處理程序。</span><span class="sxs-lookup"><span data-stu-id="3626c-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="3626c-125">方法是：進入有此處理程序的互動式工作階段，類似執行 Enter-PSSession Cmdlet 進入互動遠端工作階段的方式：</span><span class="sxs-lookup"><span data-stu-id="3626c-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="3626c-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3626c-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="3626c-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="3626c-127">Exit-PSHostProcess</span></span>