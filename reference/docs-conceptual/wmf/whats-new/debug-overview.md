---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: PowerShell 指令碼偵錯的增強功能
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147808"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="ed20c-103">PowerShell 指令碼偵錯的增強功能</span><span class="sxs-lookup"><span data-stu-id="ed20c-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="ed20c-104">PowerShell 5.0 包含數個可增強偵錯體驗的改進。</span><span class="sxs-lookup"><span data-stu-id="ed20c-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="ed20c-105">全部中斷</span><span class="sxs-lookup"><span data-stu-id="ed20c-105">Break All</span></span>

<span data-ttu-id="ed20c-106">PowerShell 主控台和 PowerShell ISE 現在可讓您針對執行中的指令碼切換到偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ed20c-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="ed20c-107">這在本機和遠端工作階段皆適用。</span><span class="sxs-lookup"><span data-stu-id="ed20c-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="ed20c-108">在主控台中，按下 <kbd>Ctrl</kbd>+<kbd>Break</kbd>。</span><span class="sxs-lookup"><span data-stu-id="ed20c-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="ed20c-109">在 ISE 中，按下 <kbd>Ctrl</kbd>+<kbd>B</kbd>，或使用 [偵錯] -> [全部中斷]  功能表命令。</span><span class="sxs-lookup"><span data-stu-id="ed20c-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="ed20c-110">PowerShell ISE 中的遠端偵錯和遠端檔案編輯</span><span class="sxs-lookup"><span data-stu-id="ed20c-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="ed20c-111">PowerShell ISE 現在可讓您藉由執行 PSEdit 命令，在遠端工作階段中開啟及編輯檔案。</span><span class="sxs-lookup"><span data-stu-id="ed20c-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="ed20c-112">例如，您可以開啟檔案從遠端工作階段的命令列中進行編輯，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="ed20c-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="ed20c-113">此外，您現在可以編輯並儲存遠端檔案中的變更，當您點擊中斷點時，該遠端檔案就會在 PowerShell ISE 中自動開啟。</span><span class="sxs-lookup"><span data-stu-id="ed20c-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="ed20c-114">現在，您可以偵錯在遠端電腦上執行的指令碼檔案、編輯檔案以修正錯誤，然後重新執行修改過的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ed20c-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="ed20c-115">進階指令碼偵錯</span><span class="sxs-lookup"><span data-stu-id="ed20c-115">Advanced Script Debugging</span></span>

<span data-ttu-id="ed20c-116">有新的進階偵錯功能，可讓您附加至任何已載入 PowerShell 的本機電腦處理序，並對該處理序中的任意 Runspace 進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="ed20c-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="ed20c-117">Runspace 偵錯</span><span class="sxs-lookup"><span data-stu-id="ed20c-117">Runspace Debugging</span></span>

<span data-ttu-id="ed20c-118">已新增新的 Cmdlet，可讓您列出處理序中目前的 Runspace，並將 PowerShell 主控台或 PowerShell ISE 偵錯工具附加至該 Runspace，以進行指令碼偵錯：</span><span class="sxs-lookup"><span data-stu-id="ed20c-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="ed20c-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="ed20c-119">Get-Runspace</span></span>
- <span data-ttu-id="ed20c-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="ed20c-120">Debug-Runspace</span></span>
- <span data-ttu-id="ed20c-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="ed20c-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="ed20c-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="ed20c-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="ed20c-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="ed20c-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="ed20c-124">附加至裝載 PowerShell 的處理程序</span><span class="sxs-lookup"><span data-stu-id="ed20c-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="ed20c-125">您現在可以附加至任何已載入 PowerShell 的電腦處理序。</span><span class="sxs-lookup"><span data-stu-id="ed20c-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="ed20c-126">您可以進入與主機處理序的互動式工作階段，來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="ed20c-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="ed20c-127">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="ed20c-127">For more information, see:</span></span>

- [<span data-ttu-id="ed20c-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="ed20c-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="ed20c-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="ed20c-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
