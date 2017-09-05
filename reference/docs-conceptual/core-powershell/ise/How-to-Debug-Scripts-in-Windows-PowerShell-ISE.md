---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "如何在 Windows PowerShell ISE 中偵錯指令碼"
ms.assetid: 6dc6d8f9-8978-46e9-a92f-169af37e2817
ms.openlocfilehash: 2b8313c3f2ae1a8fb670099baa8950db49722330
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2017
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a><span data-ttu-id="3428f-103">如何在 Windows PowerShell ISE 中偵錯指令碼</span><span class="sxs-lookup"><span data-stu-id="3428f-103">How to Debug Scripts in Windows PowerShell ISE</span></span>
<span data-ttu-id="3428f-104">本主題說明如何使用 Windows PowerShell® 整合式指令碼環境 (ISE) 視覺化偵錯功能，對本機電腦上的指令碼執行偵錯。</span><span class="sxs-lookup"><span data-stu-id="3428f-104">This topic describes how to debug scripts on a local computer by using the Windows PowerShell® Integrated Scripting Environment (ISE) visual debugging features.</span></span>

<span data-ttu-id="3428f-105">[如何管理中斷點]()
[如何管理偵錯工作階段]()
[如何在偵錯時逐程序、逐步執行及跳出]()
[如何在偵錯時顯示變數的值]()</span><span class="sxs-lookup"><span data-stu-id="3428f-105">[How to manage breakpoints]()
[How to manage a debugging session]()
[How to step over, step into, and step out while debugging]()
[How to display the values of variables while debugging]()</span></span>

## <span data-ttu-id="3428f-106"><a name="bkmk_1"></a>如何管理中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-106"><a name="bkmk_1"></a>How to manage breakpoints</span></span>
<span data-ttu-id="3428f-107">中斷點是您要在指令碼中暫停作業的指定位置，以便您可以檢查變數及指令碼執行所在之環境的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="3428f-107">A breakpoint is a designated spot in a script where you would like operation to pause so that you can examine the current state of the variables and the environment in which your script is running.</span></span> <span data-ttu-id="3428f-108">在中斷點暫停指令碼之後，您可以在主控台窗格中執行命令，以檢查指令碼的狀態。</span><span class="sxs-lookup"><span data-stu-id="3428f-108">Once your script is paused by a breakpoint, you can run commands in the Console Pane to examine the state of your script.</span></span>  <span data-ttu-id="3428f-109">您可以輸出變數或執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="3428f-109">You can output variables or run other commands.</span></span> <span data-ttu-id="3428f-110">您甚至可以修改目前執行中指令碼內容所顯示的任何變數值。</span><span class="sxs-lookup"><span data-stu-id="3428f-110">You can even modify the value of any variables that are visible to the context of the currently running script.</span></span> <span data-ttu-id="3428f-111">檢查您要查看的項目之後，您可以繼續指令碼作業。</span><span class="sxs-lookup"><span data-stu-id="3428f-111">After you have examined what you want to see, you can resume operation of the script.</span></span>

<span data-ttu-id="3428f-112">您可以在 Windows PowerShell 偵錯環境中，設定三種中斷點類型︰</span><span class="sxs-lookup"><span data-stu-id="3428f-112">You can set three types of breakpoints in the Windows PowerShell debugging environment:</span></span>

1.  <span data-ttu-id="3428f-113">**行中斷點**：</span><span class="sxs-lookup"><span data-stu-id="3428f-113">**Line breakpoint**.</span></span> <span data-ttu-id="3428f-114">在指令碼作業期間，當到達指定的行時，就會暫停指令碼</span><span class="sxs-lookup"><span data-stu-id="3428f-114">The script pauses when the designated line is reached during the operation of the script</span></span>

2.  <span data-ttu-id="3428f-115">**變數中斷點。**</span><span class="sxs-lookup"><span data-stu-id="3428f-115">**Variable breakpoint.**</span></span> <span data-ttu-id="3428f-116">當指定的變數值變更時，就會暫停指令碼。</span><span class="sxs-lookup"><span data-stu-id="3428f-116">The script pauses whenever the designated variable’s value changes.</span></span>

3.  <span data-ttu-id="3428f-117">**命令中斷點。**</span><span class="sxs-lookup"><span data-stu-id="3428f-117">**Command breakpoint.**</span></span> <span data-ttu-id="3428f-118">在指令碼作業期間，當指定的命令即將執行時，就會暫停指令碼。</span><span class="sxs-lookup"><span data-stu-id="3428f-118">The script pauses whenever the designated command is about to be run during the operation of the script.</span></span> <span data-ttu-id="3428f-119">它可以包含參數，以進一步將中斷點篩選到您需要的唯一作業。</span><span class="sxs-lookup"><span data-stu-id="3428f-119">It can include parameters to further filter the breakpoint to only the operation you want.</span></span> <span data-ttu-id="3428f-120">此命令也可以是您已建立的函式。</span><span class="sxs-lookup"><span data-stu-id="3428f-120">The command can also be a function you created.</span></span>

<span data-ttu-id="3428f-121">在 Windows PowerShell ISE 偵錯環境中，只有行中斷點可以使用功能表或鍵盤快速鍵來設定。</span><span class="sxs-lookup"><span data-stu-id="3428f-121">Of these, in the Windows PowerShell ISE debugging environment, only line breakpoints can be set by using the menu or the keyboard shortcuts.</span></span> <span data-ttu-id="3428f-122">另有其他兩種中斷點類型可供設定，但必須使用 [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) Cmdlet 從 [主控台] 設定。</span><span class="sxs-lookup"><span data-stu-id="3428f-122">The other two types of breakpoints can be set, but they are set from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet.</span></span> <span data-ttu-id="3428f-123">本節說明如何使用功能表 (可用時) 在 Windows PowerShell ISE 中執行偵錯工作，並從主控台窗格中使用指令碼執行更廣泛的命令。</span><span class="sxs-lookup"><span data-stu-id="3428f-123">This section describes how you can perform debugging tasks in Windows PowerShell ISE by using the menus where available, and perform a wider range of commands from the Console Pane by using scripting.</span></span>

### <a name="to-set-a-breakpoint"></a><span data-ttu-id="3428f-124">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-124">To set a breakpoint</span></span>
<span data-ttu-id="3428f-125">只有在儲存指令碼之後，才能在其中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-125">A breakpoint can be set in a script only after it has been saved.</span></span> <span data-ttu-id="3428f-126">以滑鼠右鍵按一下您要設定行中斷點的行，然後按一下 [切換中斷點]。</span><span class="sxs-lookup"><span data-stu-id="3428f-126">Right-click the line where you want to set a line breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="3428f-127">或者，按一下您要設定行中斷點的行，然後按 **F9** 鍵，或在 **[偵錯]** 功能表上，按一下 **[切換中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-127">Or, click the line where you want to set a line breakpoint, and press **F9** or, on the **Debug** menu, click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="3428f-128">下列指令碼示範如何從主控台窗格使用 [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) Cmdlet 設定變數中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-128">The following script is an example of how you can set a variable breakpoint from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.</span></span>

``` PowerShell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a><span data-ttu-id="3428f-129">列出所有中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-129">List all breakpoints</span></span>
<span data-ttu-id="3428f-130">顯示目前 Windows PowerShell® 工作階段中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-130">Displays all breakpoints in the current Windows PowerShell® session.</span></span>

<span data-ttu-id="3428f-131">在 **[偵錯]** 功能表上，按一下 **[列出中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-131">On the **Debug** menu, click **List Breakpoints**.</span></span> <span data-ttu-id="3428f-132">下列指令碼示範如何從主控台窗格使用 [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) Cmdlet 列出所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-132">The following script is an example of how you can list all breakpoints from the Console Pane by using the [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.</span></span>

``` PowerShell
# This command lists all breakpoints in the current session. 
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a><span data-ttu-id="3428f-133">移除中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-133">Remove a breakpoint</span></span>
<span data-ttu-id="3428f-134">移除中斷點會將它刪除。</span><span class="sxs-lookup"><span data-stu-id="3428f-134">Removing a breakpoint deletes it.</span></span>  <span data-ttu-id="3428f-135">如果您認為稍後可能需要重複使用，請考慮改為將它[停用]()。</span><span class="sxs-lookup"><span data-stu-id="3428f-135">If you think you might want to use it again later, consider [disabling]() it instead.</span></span>  <span data-ttu-id="3428f-136">以滑鼠右鍵按一下您要移除中斷點的行，然後按一下 [切換中斷點]。</span><span class="sxs-lookup"><span data-stu-id="3428f-136">Right-click the line where you want to remove a breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="3428f-137">或者，按一下您要移除中斷點的行，然後在 **[偵錯]** 功能表上，按一下 **[切換中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-137">Or, click the line where you want to remove a breakpoint, and on the **Debug** menu, click **Toggle Breakpoint**.</span></span> <span data-ttu-id="3428f-138">下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) Cmdlet 移除具有指定識別碼的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-138">The following script is an example of how to remove a breakpoint with a specified ID from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

``` PowerShell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a><span data-ttu-id="3428f-139">移除所有中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-139">Remove All Breakpoints</span></span>
<span data-ttu-id="3428f-140">若要移除目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[移除所有中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-140">To remove all breakpoints defined in the current session, on the **Debug** menu, click **Remove All Breakpoints**.</span></span>

<span data-ttu-id="3428f-141">下列指令碼示範如何從主控台窗格使用 [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) Cmdlet 移除所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-141">The following script is an example of how to remove all breakpoints from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

``` PowerShell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <span data-ttu-id="3428f-142"><a name="bkmk_disable"></a>停用中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-142"><a name="bkmk_disable"></a>Disable a Breakpoint</span></span>
<span data-ttu-id="3428f-143">停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。</span><span class="sxs-lookup"><span data-stu-id="3428f-143">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="3428f-144">若要停用特定行中斷點，請以滑鼠右鍵按一下您要停用中斷點的行，然後按一下 [停用中斷點]。</span><span class="sxs-lookup"><span data-stu-id="3428f-144">To disable a specific line breakpoint, right-click the line where you want to disable a breakpoint, and then click **Disable Breakpoint**.</span></span> <span data-ttu-id="3428f-145">或者，按一下您要停用中斷點的行，然後按 **F9** 鍵，或在 **[偵錯]** 功能表上，按一下 **[停用中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-145">Or, click the line where you want to disable a breakpoint, and press **F9** or, on the **Debug** menu, click **Disable Breakpoint**.</span></span> <span data-ttu-id="3428f-146">下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) Cmdlet 移除具有指定識別碼的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-146">The following script is an example of how you can remove a breakpoint with a specified ID from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

``` PowerShell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a><span data-ttu-id="3428f-147">停用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-147">Disable All Breakpoints</span></span>
<span data-ttu-id="3428f-148">停用中斷點不會將它移除，而是將它關閉直到再次啟用為止。</span><span class="sxs-lookup"><span data-stu-id="3428f-148">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="3428f-149">若要停用目前工作階段中的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-149">To disable all breakpoints in the current session, on the **Debug** menu, click **Disable all Breakpoints**.</span></span> <span data-ttu-id="3428f-150">下列指令碼示範如何從主控台窗格使用 [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) Cmdlet 來停用所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-150">The following script is an example of how you can disable all breakpoints from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

``` PowerShell
# This command disables all breakpoints in the current session. 
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a><span data-ttu-id="3428f-151">啟用中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-151">Enable a Breakpoint</span></span>
<span data-ttu-id="3428f-152">若要啟用特定中斷點，請以滑鼠右鍵按一下您要啟用中斷點的行，然後按一下 [啟用中斷點]。</span><span class="sxs-lookup"><span data-stu-id="3428f-152">To enable a specific breakpoint, right-click the line where you want to enable a breakpoint, and then click **Enable Breakpoint**.</span></span> <span data-ttu-id="3428f-153">或者，按一下您要啟用中斷點的行，然後按 **F9** 鍵，或在 **[偵錯]** 功能表上，按一下 **[啟用中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-153">Or, click the line where you want to enable a breakpoint, and then press **F9** or, on the **Debug** menu, click **Enable Breakpoint**.</span></span> <span data-ttu-id="3428f-154">下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) Cmdlet 來啟用特定中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-154">The following script is an example of how you can enable specific breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

``` PowerShell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a><span data-ttu-id="3428f-155">啟用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="3428f-155">Enable All Breakpoints</span></span>
<span data-ttu-id="3428f-156">若要啟用目前工作階段中定義的所有中斷點，請在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="3428f-156">To enable all breakpoints defined in the current session, on the **Debug** menu, click **Enable all Breakpoints**.</span></span> <span data-ttu-id="3428f-157">下列指令碼示範如何從主控台窗格使用 [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) Cmdlet 啟用所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-157">The following script is an example of how you can enable all breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

``` PowerShell
# This command enables all breakpoints in the current session. 
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <span data-ttu-id="3428f-158"><a name="bkmk_2"></a>如何管理偵錯工作階段</span><span class="sxs-lookup"><span data-stu-id="3428f-158"><a name="bkmk_2"></a>How to manage a debugging session</span></span>
<span data-ttu-id="3428f-159">開始偵錯之前，您必須設定一或多個中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-159">Before you start debugging, you must set one or more breakpoints.</span></span> <span data-ttu-id="3428f-160">您必須儲存要偵錯的指令碼，才能設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-160">You cannot set a breakpoint unless the script that you want to debug is saved.</span></span> <span data-ttu-id="3428f-161">如需如何設定中斷點的指示，請參閱[如何管理中斷點]()或 [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420)。</span><span class="sxs-lookup"><span data-stu-id="3428f-161">For directions on of how to set a breakpoint, see [How to manage breakpoints]() or [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420).</span></span> <span data-ttu-id="3428f-162">開始偵錯之後，直到停止偵錯為止，都無法編輯指令碼。</span><span class="sxs-lookup"><span data-stu-id="3428f-162">After you start debugging, you cannot edit a script until you stop debugging.</span></span> <span data-ttu-id="3428f-163">已設定一或多個中斷點的指令碼會自動儲存後再執行。</span><span class="sxs-lookup"><span data-stu-id="3428f-163">A script that has one or more breakpoints set is automatically saved before it is run.</span></span>

### <a name="to-start-debugging"></a><span data-ttu-id="3428f-164">開始偵錯</span><span class="sxs-lookup"><span data-stu-id="3428f-164">To start debugging</span></span>
<span data-ttu-id="3428f-165">按 **F5** 鍵；按一下工具列中的**執行指令碼**圖示；或在 [偵錯] 功能表上，按一下 [執行/繼續]。</span><span class="sxs-lookup"><span data-stu-id="3428f-165">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu click **Run/Continue**.</span></span> <span data-ttu-id="3428f-166">指令碼會執行，直到它遇到第一個中斷點為止。</span><span class="sxs-lookup"><span data-stu-id="3428f-166">The script runs until it encounters the first breakpoint.</span></span> <span data-ttu-id="3428f-167">然後它會在此暫停作業，並反白暫停的行。</span><span class="sxs-lookup"><span data-stu-id="3428f-167">It pauses operation there and highlights the line on which it paused.</span></span>

### <a name="to-continue-debugging"></a><span data-ttu-id="3428f-168">繼續偵錯</span><span class="sxs-lookup"><span data-stu-id="3428f-168">To continue debugging</span></span>
<span data-ttu-id="3428f-169">請執行下列其中一個動作：按 **F5** 鍵、按一下工具列中的**執行指令碼**圖示、在 [偵錯] 功能表上，按一下 [執行/繼續]、在主控台窗格中輸入 **C**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-169">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu, click **Run/Continue** or, in the Console Pane, type **C** and then press **ENTER**.</span></span> <span data-ttu-id="3428f-170">這會使指令碼繼續執行到下一個中斷點，或到指令碼結尾 (如果未遇到任何其他中斷點)。</span><span class="sxs-lookup"><span data-stu-id="3428f-170">This causes the script to continue running to the next breakpoint or to the end of the script if no further breakpoints are encountered.</span></span>

### <a name="to-view-the-call-stack"></a><span data-ttu-id="3428f-171">檢視呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="3428f-171">To view the call stack</span></span>
<span data-ttu-id="3428f-172">呼叫堆疊會顯示指令碼中的目前執行位置。</span><span class="sxs-lookup"><span data-stu-id="3428f-172">The call stack displays the current run location in the script.</span></span> <span data-ttu-id="3428f-173">如果指令碼在由其他函式呼叫的函式中執行，則會在顯示中以輸出的其他資料列來表示其他函式。</span><span class="sxs-lookup"><span data-stu-id="3428f-173">If the script is running in a function that was called by a different function, then that is represented in the display by additional rows in the output.</span></span> <span data-ttu-id="3428f-174">最底端的資料列顯示原始指令碼及其中用來呼叫函式的行。</span><span class="sxs-lookup"><span data-stu-id="3428f-174">The bottom-most row displays the original script and the line in it in which a function was called.</span></span> <span data-ttu-id="3428f-175">上一行顯示該函式及其中可能用來呼叫其他函式的行。</span><span class="sxs-lookup"><span data-stu-id="3428f-175">The next line up shows that function and the line in it in which another function might have been called.</span></span>  <span data-ttu-id="3428f-176">最頂端的資料列顯示設定中斷點之目前行的目前內容。</span><span class="sxs-lookup"><span data-stu-id="3428f-176">The top-most row shows the current context of the current line on which the breakpoint is set.</span></span>

<span data-ttu-id="3428f-177">若要在暫停期間查看目前的呼叫堆疊，請執行下列其中一個動作：按 **CTRL+SHIFT+D**、在 [偵錯] 功能表上，按一下 [顯示呼叫堆疊]、在主控台窗格中輸入 **K**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-177">While paused, to see the current call stack, press **CTRL+SHIFT+D** or, on the **Debug** menu, click **Display Call Stack** or, in the Console Pane, type **K** and then press **ENTER**.</span></span>

### <a name="to-stop-debugging"></a><span data-ttu-id="3428f-178">停止偵錯</span><span class="sxs-lookup"><span data-stu-id="3428f-178">To stop debugging</span></span>
<span data-ttu-id="3428f-179">按 **SHIFT-F5**；在 [偵錯] 功能表上，按一下 [停止偵錯工具]；或者，在主控台窗格中輸入 **Q**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-179">Press **SHIFT-F5** or, on the **Debug** menu, click **Stop Debugger**, or, in the Console Pane, type **Q** and then press **ENTER**.</span></span>

## <span data-ttu-id="3428f-180"><a name="bkmk_3"></a>如何在偵錯時逐程序、逐步執行及跳出</span><span class="sxs-lookup"><span data-stu-id="3428f-180"><a name="bkmk_3"></a>How to step over, step into, and step out while debugging</span></span>
<span data-ttu-id="3428f-181">逐步執行是一次執行一個陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="3428f-181">Stepping is the process of running one statement at a time.</span></span> <span data-ttu-id="3428f-182">您可以在某行程式碼停止，然後檢查變數值和系統狀態。</span><span class="sxs-lookup"><span data-stu-id="3428f-182">You can stop on a line of code, and examine the values of variables and the state of the system.</span></span> <span data-ttu-id="3428f-183">下表說明常見的偵錯工作，例如逐程序、逐步執行及跳出。</span><span class="sxs-lookup"><span data-stu-id="3428f-183">The following table describes common debugging tasks such as stepping over, stepping into, and stepping out.</span></span>

| <span data-ttu-id="3428f-184">偵錯工作</span><span class="sxs-lookup"><span data-stu-id="3428f-184">Debugging Task</span></span> | <span data-ttu-id="3428f-185">描述</span><span class="sxs-lookup"><span data-stu-id="3428f-185">Description</span></span> | <span data-ttu-id="3428f-186">如何在 PowerShell ISE 中完成</span><span class="sxs-lookup"><span data-stu-id="3428f-186">How to accomplish it in PowerShell ISE</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3428f-187">**逐步執行**</span><span class="sxs-lookup"><span data-stu-id="3428f-187">**Step Into**</span></span> | <span data-ttu-id="3428f-188">執行目前的陳述式，然後在下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="3428f-188">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="3428f-189">如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會逐步執行該函式或指令碼，否則會在下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="3428f-189">If the current statement is a function or script call, then the debugger steps into that function or script, otherwise it stops at the next statement.</span></span> | <span data-ttu-id="3428f-190">請執行下列其中一個動作：按 **F11**、在 **[偵錯]** 功能表上，按一下 **[逐步執行]**、在主控台窗格中輸入 **S**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-190">Press **F11** or, on the **Debug** menu, click **Step Into**, or in the Console Pane, type **S** and press **ENTER**.</span></span> |
| <span data-ttu-id="3428f-191">**逐程序**</span><span class="sxs-lookup"><span data-stu-id="3428f-191">**Step Over**</span></span> | <span data-ttu-id="3428f-192">執行目前的陳述式，然後在下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="3428f-192">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="3428f-193">如果目前的陳述式是函式或指令碼呼叫，則偵錯工具會執行整個函式或指令碼，並在函式呼叫後於下一個陳述式停止。</span><span class="sxs-lookup"><span data-stu-id="3428f-193">If the current statement is a function or script call then the debugger executes the whole function or script, and it stops at the next statement after the function call.</span></span> | <span data-ttu-id="3428f-194">請執行下列其中一個動作：按 **F10**、在 **[偵錯]** 功能表上，按一下 **[逐程序]**、在主控台窗格中輸入 **V**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-194">Press **F10** or, on the **Debug** menu, click **Step Over**, or in the Console Pane, type **V** and press **ENTER**.</span></span> |
| <span data-ttu-id="3428f-195">**跳出**</span><span class="sxs-lookup"><span data-stu-id="3428f-195">**Step Out**</span></span> | <span data-ttu-id="3428f-196">移離目前的函式，並在函式為巢狀時移到上一層。</span><span class="sxs-lookup"><span data-stu-id="3428f-196">Steps out of the current function and up one level if the function is nested.</span></span> <span data-ttu-id="3428f-197">如果在主體中，指令碼會執行到結尾，或到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-197">If in the main body, the script is executed to the end, or to the next breakpoint.</span></span> <span data-ttu-id="3428f-198">這會執行已跳過的陳述式，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="3428f-198">The skipped statements are executed, but not stepped through.</span></span> | <span data-ttu-id="3428f-199">請執行下列其中一個動作：按 **SHIFT+F11**、在 [偵錯] 功能表上，按一下 [跳出]、在主控台窗格中輸入 **O**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-199">Press **SHIFT+F11**, or on the **Debug** menu, click **Step Out**, or in the Console Pane, type **O** and press **ENTER**.</span></span> |
| <span data-ttu-id="3428f-200">**繼續**</span><span class="sxs-lookup"><span data-stu-id="3428f-200">**Continue**</span></span> | <span data-ttu-id="3428f-201">繼續執行到結尾，或到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="3428f-201">Continues execution to the end, or to the next breakpoint.</span></span> <span data-ttu-id="3428f-202">這會執行已跳過的函式和引動過程，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="3428f-202">The skipped functions and invocations are executed, but not stepped through.</span></span> | <span data-ttu-id="3428f-203">請執行下列其中一個動作：按 **F5**、在 [偵錯] 功能表上，按一下 [執行/繼續]、在主控台窗格中輸入 **C**，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-203">Press **F5** or, on the **Debug** menu, click **Run/Continue**, or in the Console Pane, type **C** and press **ENTER**.</span></span> |

## <span data-ttu-id="3428f-204"><a name="bkmk_4"></a>如何在偵錯時顯示變數的值</span><span class="sxs-lookup"><span data-stu-id="3428f-204"><a name="bkmk_4"></a>How to display the values of variables while debugging</span></span>
<span data-ttu-id="3428f-205">當您逐步執行程式碼時，您可以顯示指令碼中變數的目前值。</span><span class="sxs-lookup"><span data-stu-id="3428f-205">You can display the current values of variables in the script as you step through the code.</span></span>

### <a name="to-display-the-values-of-standard-variables"></a><span data-ttu-id="3428f-206">顯示標準變數的值</span><span class="sxs-lookup"><span data-stu-id="3428f-206">To display the values of standard variables</span></span>
<span data-ttu-id="3428f-207">使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="3428f-207">Use one of the following methods:</span></span>

-   <span data-ttu-id="3428f-208">在指令碼窗格中，將游標移到變數上，以工具提示顯示其值。</span><span class="sxs-lookup"><span data-stu-id="3428f-208">In the Script Pane, hover over the variable to display its value as a tool tip.</span></span>

-   <span data-ttu-id="3428f-209">在主控台窗格中輸入變數名稱，然後按 **ENTER** 鍵。</span><span class="sxs-lookup"><span data-stu-id="3428f-209">In the Console Pane, type the variable name and press **ENTER**.</span></span>

<span data-ttu-id="3428f-210">ISE 中的所有窗格一律會在相同範圍內。</span><span class="sxs-lookup"><span data-stu-id="3428f-210">All panes in ISE are always in the same scope.</span></span> <span data-ttu-id="3428f-211">因此，當您對指令碼進行偵錯時，您在主控台窗格中輸入的命令會在指令碼範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="3428f-211">Therefore, while you are debugging a script, the commands that you type in the Console Pane run in script scope.</span></span> <span data-ttu-id="3428f-212">這可讓您使用主控台窗格尋找變數的值，然後只呼叫指令碼中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="3428f-212">This allows you to use the Console Pane to find the values of variables and call functions that are defined only in the script.</span></span>

### <a name="to-display-the-values-of-automatic-variables"></a><span data-ttu-id="3428f-213">顯示自動變數的值</span><span class="sxs-lookup"><span data-stu-id="3428f-213">To display the values of automatic variables</span></span>
<span data-ttu-id="3428f-214">您可以使用上述方法，在對指令碼進行偵錯時顯示幾乎所有變數的值。</span><span class="sxs-lookup"><span data-stu-id="3428f-214">You can use the preceding method to display the value of almost all variables while you are debugging a script.</span></span> <span data-ttu-id="3428f-215">不過，這些方法不適用於下列自動變數。</span><span class="sxs-lookup"><span data-stu-id="3428f-215">However, these methods do not work for the following automatic variables.</span></span>

-   <span data-ttu-id="3428f-216">$_</span><span class="sxs-lookup"><span data-stu-id="3428f-216">$_</span></span>

-   <span data-ttu-id="3428f-217">$Input</span><span class="sxs-lookup"><span data-stu-id="3428f-217">$Input</span></span>

-   <span data-ttu-id="3428f-218">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="3428f-218">$MyInvocation</span></span>

-   <span data-ttu-id="3428f-219">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="3428f-219">$PSBoundParameters</span></span>

-   <span data-ttu-id="3428f-220">$Args</span><span class="sxs-lookup"><span data-stu-id="3428f-220">$Args</span></span>

<span data-ttu-id="3428f-221">如果您嘗試顯示上述任何變數的值，您會取得偵錯工具所使用之內部管線中的變數值，而不是指令碼中的變數值。</span><span class="sxs-lookup"><span data-stu-id="3428f-221">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span> <span data-ttu-id="3428f-222">您可以對一些變數 ($_、$Input、$MyInvocation、$PSBoundParameters 和 $Args) 使用下列方法，來解決此問題：</span><span class="sxs-lookup"><span data-stu-id="3428f-222">You can work around this for a few variables ($_, $Input, $MyInvocation, $PSBoundParameters, and $Args) by using the following method:</span></span>

1.  <span data-ttu-id="3428f-223">在指令碼中，將自動變數的值指派給新變數。</span><span class="sxs-lookup"><span data-stu-id="3428f-223">In the script, assign the value of the automatic variable to a new variable.</span></span>

2.  <span data-ttu-id="3428f-224">將游標移到指令碼窗格中的新變數上，或在主控台窗格中輸入新變數，以顯示新變數的值。</span><span class="sxs-lookup"><span data-stu-id="3428f-224">Display the value of the new variable, either by hovering over the new variable in the Script Pane, or by typing the new variable in the Console Pane.</span></span>

<span data-ttu-id="3428f-225">例如，若要顯示指令碼中的 $MyInvocation 變數值，請將該值指派給新變數 (例如 $scriptname)，然後將游標移到 $scriptname 變數上或輸入 $scriptname 變數，以顯示其值。</span><span class="sxs-lookup"><span data-stu-id="3428f-225">For example, to display the value of the $MyInvocation variable, in the script, assign the value to a new variable, such as $scriptname, and then hover over or type the $scriptname variable to display its value.</span></span>

``` PowerShell
#In MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path

#In the Console Pane:
C:\ps-test> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a><span data-ttu-id="3428f-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3428f-226">See Also</span></span>
- [<span data-ttu-id="3428f-227">使用 Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3428f-227">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

