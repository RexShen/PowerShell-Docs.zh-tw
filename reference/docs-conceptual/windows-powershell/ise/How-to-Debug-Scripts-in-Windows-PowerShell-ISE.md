---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中偵錯指令碼
ms.openlocfilehash: 6fbe340cbff832b5d0e2a5515ef432cec574a3c1
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809344"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a><span data-ttu-id="f78e0-103">如何在 Windows PowerShell ISE 中偵錯指令碼</span><span class="sxs-lookup"><span data-stu-id="f78e0-103">How to Debug Scripts in Windows PowerShell ISE</span></span>

<span data-ttu-id="f78e0-104">本文章說明如何使用 Windows PowerShell 整合式指令碼環境 (ISE) 視覺化偵錯功能，對本機電腦上的指令碼執行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f78e0-104">This article describes how to debug scripts on a local computer by using the Windows PowerShell Integrated Scripting Environment (ISE) visual debugging features.</span></span>

## <a name="how-to-manage-breakpoints"></a><span data-ttu-id="f78e0-105">如何管理中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-105">How to manage breakpoints</span></span>

<span data-ttu-id="f78e0-106">中斷點是您要在指令碼中暫停作業的指定位置，以便您可以檢查變數及指令碼執行所在之環境的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="f78e0-106">A breakpoint is a designated spot in a script where you would like operation to pause so that you can examine the current state of the variables and the environment in which your script is running.</span></span>
<span data-ttu-id="f78e0-107">在中斷點暫停指令碼之後，您可以在主控台窗格中執行命令，以檢查指令碼的狀態。</span><span class="sxs-lookup"><span data-stu-id="f78e0-107">Once your script is paused by a breakpoint, you can run commands in the Console Pane to examine the state of your script.</span></span> <span data-ttu-id="f78e0-108">您可以輸出變數或執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="f78e0-108">You can output variables or run other commands.</span></span> <span data-ttu-id="f78e0-109">您甚至可以修改目前執行中指令碼內容所顯示的任何變數值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-109">You can even modify the value of any variables that are visible to the context of the currently running script.</span></span> <span data-ttu-id="f78e0-110">檢查您要查看的項目之後，您可以繼續指令碼作業。</span><span class="sxs-lookup"><span data-stu-id="f78e0-110">After you have examined what you want to see, you can resume operation of the script.</span></span>

<span data-ttu-id="f78e0-111">您可以在 Windows PowerShell 偵錯環境中，設定三種中斷點類型︰</span><span class="sxs-lookup"><span data-stu-id="f78e0-111">You can set three types of breakpoints in the Windows PowerShell debugging environment:</span></span>

1. <span data-ttu-id="f78e0-112">**行中斷點**：</span><span class="sxs-lookup"><span data-stu-id="f78e0-112">**Line breakpoint**.</span></span> <span data-ttu-id="f78e0-113">在指令碼作業期間，當到達指定的行時，就會暫停指令碼</span><span class="sxs-lookup"><span data-stu-id="f78e0-113">The script pauses when the designated line is reached during the operation of the script</span></span>

1. <span data-ttu-id="f78e0-114">**變數中斷點。**</span><span class="sxs-lookup"><span data-stu-id="f78e0-114">**Variable breakpoint.**</span></span> <span data-ttu-id="f78e0-115">當指定的變數值變更時，指令碼就會暫停。</span><span class="sxs-lookup"><span data-stu-id="f78e0-115">The script pauses whenever the designated variable's value changes.</span></span>

1. <span data-ttu-id="f78e0-116">**命令中斷點。**</span><span class="sxs-lookup"><span data-stu-id="f78e0-116">**Command breakpoint.**</span></span> <span data-ttu-id="f78e0-117">在指令碼作業期間，當指定的命令即將執行時，就會暫停指令碼。</span><span class="sxs-lookup"><span data-stu-id="f78e0-117">The script pauses whenever the designated command is about to be run during the operation of the script.</span></span> <span data-ttu-id="f78e0-118">它可以包含參數，以進一步將中斷點篩選到您需要的唯一作業。</span><span class="sxs-lookup"><span data-stu-id="f78e0-118">It can include parameters to further filter the breakpoint to only the operation you want.</span></span> <span data-ttu-id="f78e0-119">此命令也可以是您已建立的函式。</span><span class="sxs-lookup"><span data-stu-id="f78e0-119">The command can also be a function you created.</span></span>

<span data-ttu-id="f78e0-120">在 Windows PowerShell ISE 偵錯環境中，只有行中斷點可以使用功能表或鍵盤快速鍵來設定。</span><span class="sxs-lookup"><span data-stu-id="f78e0-120">Of these, in the Windows PowerShell ISE debugging environment, only line breakpoints can be set by using the menu or the keyboard shortcuts.</span></span> <span data-ttu-id="f78e0-121">另有其他兩種中斷點類型可供設定，但必須使用 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) Cmdlet 從 [主控台] 設定。</span><span class="sxs-lookup"><span data-stu-id="f78e0-121">The other two types of breakpoints can be set, but they are set from the Console Pane by using the [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) cmdlet.</span></span> <span data-ttu-id="f78e0-122">本節說明如何使用功能表 (可用時) 在 Windows PowerShell ISE 中執行偵錯工作，並從主控台窗格中使用指令碼執行更廣泛的命令。</span><span class="sxs-lookup"><span data-stu-id="f78e0-122">This section describes how you can perform debugging tasks in Windows PowerShell ISE by using the menus where available, and perform a wider range of commands from the Console Pane by using scripting.</span></span>

### <a name="to-set-a-breakpoint"></a><span data-ttu-id="f78e0-123">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-123">To set a breakpoint</span></span>

<span data-ttu-id="f78e0-124">只有在儲存指令碼之後，才能在其中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-124">A breakpoint can be set in a script only after it has been saved.</span></span> <span data-ttu-id="f78e0-125">以滑鼠右鍵按一下您要設定行中斷點的行，然後按一下 [切換中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="f78e0-125">Right-click the line where you want to set a line breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="f78e0-126">或者，按一下您要設定行中斷點的行，然後按 <kbd>F9</kbd> 鍵，或在 **[偵錯]** 功能表上，按一下 **[切換中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-126">Or, click the line where you want to set a line breakpoint, and press <kbd>F9</kbd> or, on the **Debug** menu, click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="f78e0-127">下列指令碼示範如何從主控台窗格使用 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) Cmdlet 設定變數中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-127">The following script is an example of how you can set a variable breakpoint from the Console Pane by using the [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a><span data-ttu-id="f78e0-128">列出所有中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-128">List all breakpoints</span></span>

<span data-ttu-id="f78e0-129">顯示目前 Windows PowerShell 工作階段中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-129">Displays all breakpoints in the current Windows PowerShell session.</span></span>

<span data-ttu-id="f78e0-130">在 **[偵錯]** 功能表上，按一下 **[列出中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-130">On the **Debug** menu, click **List Breakpoints**.</span></span> <span data-ttu-id="f78e0-131">下列指令碼示範如何從主控台窗格使用 [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) Cmdlet 列出所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-131">The following script is an example of how you can list all breakpoints from the Console Pane by using the [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a><span data-ttu-id="f78e0-132">移除中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-132">Remove a breakpoint</span></span>

<span data-ttu-id="f78e0-133">移除中斷點會將它刪除。</span><span class="sxs-lookup"><span data-stu-id="f78e0-133">Removing a breakpoint deletes it.</span></span>

<span data-ttu-id="f78e0-134">如果您認為稍後可能需要再度使用，請考慮改為[停用中斷點](#disable-a-breakpoint)。</span><span class="sxs-lookup"><span data-stu-id="f78e0-134">If you think you might want to use it again later, consider [Disable a Breakpoint](#disable-a-breakpoint) it instead.</span></span> <span data-ttu-id="f78e0-135">以滑鼠右鍵按一下您要移除中斷點的行，然後按一下 [切換中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="f78e0-135">Right-click the line where you want to remove a breakpoint, and then click **ToggleBreakpoint**.</span></span>
<span data-ttu-id="f78e0-136">或者，按一下您要移除中斷點的行，然後在 **[偵錯]** 功能表上，按一下 **[切換中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-136">Or, click the line where you want to remove a breakpoint, and on the **Debug** menu, click **Toggle Breakpoint**.</span></span> <span data-ttu-id="f78e0-137">下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) Cmdlet 移除具有指定識別碼的中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-137">The following script is an example of how to remove a breakpoint with a specified ID from the Console Pane by using the [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a><span data-ttu-id="f78e0-138">移除所有中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-138">Remove All Breakpoints</span></span>

<span data-ttu-id="f78e0-139">若要移除目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[移除所有中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-139">To remove all breakpoints defined in the current session, on the **Debug** menu, click **Remove All Breakpoints**.</span></span>

<span data-ttu-id="f78e0-140">下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) Cmdlet 移除所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-140">The following script is an example of how to remove all breakpoints from the Console Pane by using the [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a><span data-ttu-id="f78e0-141">停用中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-141">Disable a Breakpoint</span></span>

<span data-ttu-id="f78e0-142">停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-142">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span> <span data-ttu-id="f78e0-143">若要停用特定行中斷點，請以滑鼠右鍵按一下您要停用中斷點的行，然後按一下 [停用中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="f78e0-143">To disable a specific line breakpoint, right-click the line where you want to disable a breakpoint, and then click **Disable Breakpoint**.</span></span> <span data-ttu-id="f78e0-144">或者，按一下您要停用中斷點的行，然後按 <kbd>F9</kbd> 鍵，或在 **[偵錯]** 功能表上，按一下 **[停用中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-144">Or, click the line where you want to disable a breakpoint, and press <kbd>F9</kbd> or, on the **Debug** menu, click **Disable Breakpoint**.</span></span> <span data-ttu-id="f78e0-145">下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) Cmdlet 移除具有指定識別碼的中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-145">The following script is an example of how you can remove a breakpoint with a specified ID from the Console Pane by using the [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a><span data-ttu-id="f78e0-146">停用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-146">Disable All Breakpoints</span></span>

<span data-ttu-id="f78e0-147">停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-147">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span> <span data-ttu-id="f78e0-148">若要停用目前工作階段中的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-148">To disable all breakpoints in the current session, on the **Debug** menu, click **Disable all Breakpoints**.</span></span> <span data-ttu-id="f78e0-149">下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) Cmdlet 來停用所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-149">The following script is an example of how you can disable all breakpoints from the Console Pane by using the [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a><span data-ttu-id="f78e0-150">啟用中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-150">Enable a Breakpoint</span></span>

<span data-ttu-id="f78e0-151">若要啟用特定中斷點，請以滑鼠右鍵按一下您要啟用中斷點的行，然後按一下 [啟用中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="f78e0-151">To enable a specific breakpoint, right-click the line where you want to enable a breakpoint, and then click **Enable Breakpoint**.</span></span> <span data-ttu-id="f78e0-152">或者，按一下您要啟用中斷點的行，然後按 <kbd>F9</kbd> 鍵，或在 **[偵錯]** 功能表上，按一下 **[啟用中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-152">Or, click the line where you want to enable a breakpoint, and then press <kbd>F9</kbd> or, on the **Debug** menu, click **Enable Breakpoint**.</span></span> <span data-ttu-id="f78e0-153">下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) Cmdlet 來啟用特定中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-153">The following script is an example of how you can enable specific breakpoints from the Console Pane by using the [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a><span data-ttu-id="f78e0-154">啟用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="f78e0-154">Enable All Breakpoints</span></span>

<span data-ttu-id="f78e0-155">若要啟用目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]** 。</span><span class="sxs-lookup"><span data-stu-id="f78e0-155">To enable all breakpoints defined in the current session, on the **Debug** menu, click **Enable all Breakpoints**.</span></span> <span data-ttu-id="f78e0-156">下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) Cmdlet 啟用所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-156">The following script is an example of how you can enable all breakpoints from the Console Pane by using the [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a><span data-ttu-id="f78e0-157">如何管理偵錯工作階段</span><span class="sxs-lookup"><span data-stu-id="f78e0-157">How to manage a debugging session</span></span>

<span data-ttu-id="f78e0-158">開始偵錯之前，您必須設定一或多個中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-158">Before you start debugging, you must set one or more breakpoints.</span></span> <span data-ttu-id="f78e0-159">您必須儲存要偵錯的指令碼，才能設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-159">You cannot set a breakpoint unless the script that you want to debug is saved.</span></span> <span data-ttu-id="f78e0-160">如需如何設定中斷點的指示，請參閱[如何管理中斷點](#how-to-manage-breakpoints)或 [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint)。</span><span class="sxs-lookup"><span data-stu-id="f78e0-160">For directions on of how to set a breakpoint, see [How to manage breakpoints](#how-to-manage-breakpoints) or [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint).</span></span>
<span data-ttu-id="f78e0-161">開始偵錯之後，直到停止偵錯為止，都無法編輯指令碼。</span><span class="sxs-lookup"><span data-stu-id="f78e0-161">After you start debugging, you cannot edit a script until you stop debugging.</span></span> <span data-ttu-id="f78e0-162">已設定一或多個中斷點的指令碼會自動儲存後再執行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-162">A script that has one or more breakpoints set is automatically saved before it is run.</span></span>

### <a name="to-start-debugging"></a><span data-ttu-id="f78e0-163">開始偵錯</span><span class="sxs-lookup"><span data-stu-id="f78e0-163">To start debugging</span></span>

<span data-ttu-id="f78e0-164">按 <kbd>F5</kbd> 鍵；按一下工具列中的**執行指令碼**圖示；或在 [偵錯]  功能表上，按一下 [執行/繼續]  。</span><span class="sxs-lookup"><span data-stu-id="f78e0-164">Press <kbd>F5</kbd> or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu click **Run/Continue**.</span></span> <span data-ttu-id="f78e0-165">指令碼會執行，直到它遇到第一個中斷點為止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-165">The script runs until it encounters the first breakpoint.</span></span> <span data-ttu-id="f78e0-166">然後它會在此暫停作業，並反白暫停的行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-166">It pauses operation there and highlights the line on which it paused.</span></span>

### <a name="to-continue-debugging"></a><span data-ttu-id="f78e0-167">繼續偵錯</span><span class="sxs-lookup"><span data-stu-id="f78e0-167">To continue debugging</span></span>

<span data-ttu-id="f78e0-168">請執行下列其中一個動作：按 <kbd>F5</kbd> 鍵、按一下工具列中的**執行指令碼**圖示、在 [偵錯]  功能表上，按一下 [執行/繼續]  、在主控台窗格中輸入 `C`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-168">Press <kbd>F5</kbd> or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu, click **Run/Continue** or, in the Console Pane, type `C` and then press <kbd>ENTER</kbd>.</span></span> <span data-ttu-id="f78e0-169">這會使指令碼繼續執行到下一個中斷點，或到指令碼結尾 (如果未遇到任何其他中斷點)。</span><span class="sxs-lookup"><span data-stu-id="f78e0-169">This causes the script to continue running to the next breakpoint or to the end of the script if no further breakpoints are encountered.</span></span>

### <a name="to-view-the-call-stack"></a><span data-ttu-id="f78e0-170">檢視呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="f78e0-170">To view the call stack</span></span>

<span data-ttu-id="f78e0-171">呼叫堆疊會顯示指令碼中的目前執行位置。</span><span class="sxs-lookup"><span data-stu-id="f78e0-171">The call stack displays the current run location in the script.</span></span> <span data-ttu-id="f78e0-172">如果指令碼在由其他函式呼叫的函式中執行，則會在顯示中以輸出的其他資料列來表示其他函式。</span><span class="sxs-lookup"><span data-stu-id="f78e0-172">If the script is running in a function that was called by a different function, then that is represented in the display by additional rows in the output.</span></span> <span data-ttu-id="f78e0-173">最底端的資料列顯示原始指令碼及其中用來呼叫函式的行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-173">The bottom-most row displays the original script and the line in it in which a function was called.</span></span> <span data-ttu-id="f78e0-174">上一行顯示該函式及其中可能用來呼叫其他函式的行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-174">The next line up shows that function and the line in it in which another function might have been called.</span></span> <span data-ttu-id="f78e0-175">最頂端的資料列顯示設定中斷點之目前行的目前內容。</span><span class="sxs-lookup"><span data-stu-id="f78e0-175">The top-most row shows the current context of the current line on which the breakpoint is set.</span></span>

<span data-ttu-id="f78e0-176">若要在暫停期間查看目前的呼叫堆疊，請執行下列其中一個動作：按 <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>、在 [偵錯]  功能表上，按一下 [顯示呼叫堆疊]  、在主控台窗格中輸入 `K`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-176">While paused, to see the current call stack, press <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd> or, on the **Debug** menu, click **Display Call Stack** or, in the Console Pane, type `K` and then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-stop-debugging"></a><span data-ttu-id="f78e0-177">停止偵錯</span><span class="sxs-lookup"><span data-stu-id="f78e0-177">To stop debugging</span></span>

<span data-ttu-id="f78e0-178">請執行下列其中一個動作：按 <kbd>SHIFT</kbd>+<kbd>F5</kbd>、在 [偵錯]  功能表上，按一下 [停止偵錯工具]  、在主控台窗格中輸入 `Q`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-178">Press <kbd>SHIFT</kbd>+<kbd>F5</kbd> or, on the **Debug** menu, click **Stop Debugger**, or, in the Console Pane, type `Q` and then press <kbd>ENTER</kbd>.</span></span>

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a><span data-ttu-id="f78e0-179">如何在偵錯時逐程序、逐步執行及跳出</span><span class="sxs-lookup"><span data-stu-id="f78e0-179">How to step over, step into, and step out while debugging</span></span>

<span data-ttu-id="f78e0-180">逐步執行是一次執行一個陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="f78e0-180">Stepping is the process of running one statement at a time.</span></span> <span data-ttu-id="f78e0-181">您可以在某行程式碼停止，然後檢查變數值和系統狀態。</span><span class="sxs-lookup"><span data-stu-id="f78e0-181">You can stop on a line of code, and examine the values of variables and the state of the system.</span></span> <span data-ttu-id="f78e0-182">下表說明常見的偵錯工作，例如逐程序、逐步執行及跳出。</span><span class="sxs-lookup"><span data-stu-id="f78e0-182">The following table describes common debugging tasks such as stepping over, stepping into, and stepping out.</span></span>

| <span data-ttu-id="f78e0-183">偵錯工作</span><span class="sxs-lookup"><span data-stu-id="f78e0-183">Debugging Task</span></span> |                                                                                                                   <span data-ttu-id="f78e0-184">描述</span><span class="sxs-lookup"><span data-stu-id="f78e0-184">Description</span></span>                                                                                                                    |                                                      <span data-ttu-id="f78e0-185">如何在 PowerShell ISE 中完成</span><span class="sxs-lookup"><span data-stu-id="f78e0-185">How to accomplish it in PowerShell ISE</span></span>                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f78e0-186">**逐步執行**</span><span class="sxs-lookup"><span data-stu-id="f78e0-186">**Step Into**</span></span>  | <span data-ttu-id="f78e0-187">執行目前的陳述式，然後在下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-187">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="f78e0-188">如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會逐步執行該函式或指令碼，否則會在下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-188">If the current statement is a function or script call, then the debugger steps into that function or script, otherwise it stops at the next statement.</span></span>                      | <span data-ttu-id="f78e0-189">請執行下列其中一個動作：按 <kbd>F11</kbd>、在 [偵錯]  功能表上，按一下 [逐步執行]  、在主控台窗格中輸入 `S`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-189">Press <kbd>F11</kbd> or, on the **Debug** menu, click **Step Into**, or in the Console Pane, type `S` and press <kbd>ENTER</kbd>.</span></span>                 |
| <span data-ttu-id="f78e0-190">**逐程序**</span><span class="sxs-lookup"><span data-stu-id="f78e0-190">**Step Over**</span></span>  | <span data-ttu-id="f78e0-191">執行目前的陳述式，然後在下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-191">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="f78e0-192">如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會執行整個函式或指令碼，並在函式呼叫後於下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="f78e0-192">If the current statement is a function or script call, then the debugger executes the whole function or script, and it stops at the next statement after the function call.</span></span> | <span data-ttu-id="f78e0-193">請執行下列其中一個動作：按 <kbd>F10</kbd>、在 [偵錯]  功能表上，按一下 [不進入函數]  、在主控台窗格中輸入 `V`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-193">Press <kbd>F10</kbd> or, on the **Debug** menu, click **Step Over**, or in the Console Pane, type `V` and press <kbd>ENTER</kbd>.</span></span>                 |
| <span data-ttu-id="f78e0-194">**跳出**</span><span class="sxs-lookup"><span data-stu-id="f78e0-194">**Step Out**</span></span>   | <span data-ttu-id="f78e0-195">移離目前的函式，並在函式為巢狀時移到上一層。</span><span class="sxs-lookup"><span data-stu-id="f78e0-195">Steps out of the current function and up one level if the function is nested.</span></span> <span data-ttu-id="f78e0-196">如果在主體中，指令碼會執行到結尾，或到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-196">If in the main body, the script is executed to the end, or to the next breakpoint.</span></span> <span data-ttu-id="f78e0-197">這會執行已跳過的陳述式，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-197">The skipped statements are executed, but not stepped through.</span></span>                   | <span data-ttu-id="f78e0-198">請執行下列其中一個動作：<kbd>SHIFT</kbd>+<kbd>F11</kbd>、在 [偵錯]  功能表上，按一下 [跳離]  、在主控台窗格中輸入 `O`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-198">Press <kbd>SHIFT</kbd>+<kbd>F11</kbd>, or on the **Debug** menu, click **Step Out**, or in the Console Pane, type `O` and press <kbd>ENTER</kbd>.</span></span> |
| <span data-ttu-id="f78e0-199">**繼續**</span><span class="sxs-lookup"><span data-stu-id="f78e0-199">**Continue**</span></span>   | <span data-ttu-id="f78e0-200">繼續執行到結尾，或到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="f78e0-200">Continues execution to the end, or to the next breakpoint.</span></span> <span data-ttu-id="f78e0-201">這會執行已跳過的函式和引動過程，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-201">The skipped functions and invocations are executed, but not stepped through.</span></span>                                                                                                          | <span data-ttu-id="f78e0-202">請執行下列其中一個動作：按 <kbd>F5</kbd>、在 [偵錯]  功能表上，按一下 [執行/繼續]  、在主控台窗格中輸入 `C`，然後按 <kbd>ENTER</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f78e0-202">Press <kbd>F5</kbd> or, on the **Debug** menu, click **Run/Continue**, or in the Console Pane, type `C` and press <kbd>ENTER</kbd>.</span></span>               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a><span data-ttu-id="f78e0-203">如何在偵錯時顯示變數的值</span><span class="sxs-lookup"><span data-stu-id="f78e0-203">How to display the values of variables while debugging</span></span>

<span data-ttu-id="f78e0-204">當您逐步執行程式碼時，您可以顯示指令碼中變數的目前值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-204">You can display the current values of variables in the script as you step through the code.</span></span>

### <a name="to-display-the-values-of-standard-variables"></a><span data-ttu-id="f78e0-205">顯示標準變數的值</span><span class="sxs-lookup"><span data-stu-id="f78e0-205">To display the values of standard variables</span></span>

<span data-ttu-id="f78e0-206">請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="f78e0-206">Use one of the following methods:</span></span>

- <span data-ttu-id="f78e0-207">在指令碼窗格中，將游標移到變數上，以工具提示顯示其值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-207">In the Script Pane, hover over the variable to display its value as a tool tip.</span></span>

- <span data-ttu-id="f78e0-208">在主控台窗格中輸入變數名稱，然後按 <kbd>ENTER</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="f78e0-208">In the Console Pane, type the variable name and press <kbd>ENTER</kbd>.</span></span>

<span data-ttu-id="f78e0-209">ISE 中的所有窗格一律會在相同範圍內。</span><span class="sxs-lookup"><span data-stu-id="f78e0-209">All panes in ISE are always in the same scope.</span></span> <span data-ttu-id="f78e0-210">因此，當您對指令碼進行偵錯時，您在主控台窗格中輸入的命令會在指令碼範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="f78e0-210">Therefore, while you are debugging a script, the commands that you type in the Console Pane run in script scope.</span></span> <span data-ttu-id="f78e0-211">這可讓您使用主控台窗格尋找變數的值，然後只呼叫指令碼中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="f78e0-211">This allows you to use the Console Pane to find the values of variables and call functions that are defined only in the script.</span></span>

### <a name="to-display-the-values-of-automatic-variables"></a><span data-ttu-id="f78e0-212">顯示自動變數的值</span><span class="sxs-lookup"><span data-stu-id="f78e0-212">To display the values of automatic variables</span></span>

<span data-ttu-id="f78e0-213">您可以使用上述方法，在對指令碼進行偵錯時顯示幾乎所有變數的值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-213">You can use the preceding method to display the value of almost all variables while you are debugging a script.</span></span> <span data-ttu-id="f78e0-214">不過，這些方法不適用於下列自動變數。</span><span class="sxs-lookup"><span data-stu-id="f78e0-214">However, these methods do not work for the following automatic variables.</span></span>

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

<span data-ttu-id="f78e0-215">如果您嘗試顯示上述任何變數的值，您會取得偵錯工具所使用之內部管線中的變數值，而不是指令碼中的變數值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-215">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span> <span data-ttu-id="f78e0-216">您可以對一些變數 (`$_`、`$Input`、`$MyInvocation`、`$PSBoundParameters` 和 `$Args`) 使用下列方法，來解決此問題：</span><span class="sxs-lookup"><span data-stu-id="f78e0-216">You can work around this for a few variables (`$_`, `$Input`, `$MyInvocation`, `$PSBoundParameters`, and `$Args`) by using the following method:</span></span>

1. <span data-ttu-id="f78e0-217">在指令碼中，將自動變數的值指派給新變數。</span><span class="sxs-lookup"><span data-stu-id="f78e0-217">In the script, assign the value of the automatic variable to a new variable.</span></span>

1. <span data-ttu-id="f78e0-218">將游標移到指令碼窗格中的新變數上，或在主控台窗格中輸入新變數，以顯示新變數的值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-218">Display the value of the new variable, either by hovering over the new variable in the Script Pane, or by typing the new variable in the Console Pane.</span></span>

<span data-ttu-id="f78e0-219">例如，若要顯示指令碼中的 `$MyInvocation` 變數值，請將該值指派給新變數 (例如 `$scriptName`)，然後將游標移到 `$scriptName` 變數上或輸入該變數，以顯示其值。</span><span class="sxs-lookup"><span data-stu-id="f78e0-219">For example, to display the value of the `$MyInvocation` variable, in the script, assign the value to a new variable, such as `$scriptName`, and then hover over or type the `$scriptName` variable to display its value.</span></span>

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a><span data-ttu-id="f78e0-220">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f78e0-220">See Also</span></span>

[<span data-ttu-id="f78e0-221">探索 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f78e0-221">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
