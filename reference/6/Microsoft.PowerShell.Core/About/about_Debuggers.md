---
description: 描述 PowerShell 偵錯工具。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: a200d5612c29cfad63100e0db5686996032f96fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207140"
---
# <a name="about-debuggers"></a><span data-ttu-id="bf871-104">關於偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bf871-104">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="bf871-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="bf871-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bf871-106">描述 PowerShell 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-106">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf871-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="bf871-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bf871-108">偵錯工具是指在腳本執行時檢查腳本，以識別並更正腳本指令中錯誤的流程。</span><span class="sxs-lookup"><span data-stu-id="bf871-108">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="bf871-109">PowerShell 偵錯工具可協助您檢查和識別腳本、函式、命令、PowerShell Desired State Configuration (DSC) 設定或運算式中的錯誤和效率不佳。</span><span class="sxs-lookup"><span data-stu-id="bf871-109">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="bf871-110">從 PowerShell 5.0 開始，已更新 PowerShell 偵錯工具，以在主控台或 Windows PowerShell ISE 遠端電腦上執行的腳本、函式、命令、設定或運算式。</span><span class="sxs-lookup"><span data-stu-id="bf871-110">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="bf871-111">您可以執行 `Enter-PSSession` 以啟動互動式遠端 PowerShell 會話，以便在遠端電腦上設定中斷點和偵錯工具腳本檔案和命令。</span><span class="sxs-lookup"><span data-stu-id="bf871-111">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="bf871-112">`Enter-PSSession` 功能已更新為可讓您重新連線，並輸入在遠端電腦上執行腳本或命令的中斷連線會話。</span><span class="sxs-lookup"><span data-stu-id="bf871-112">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="bf871-113">如果執行中的腳本叫用中斷點，您的用戶端會話就會自動啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-113">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="bf871-114">如果執行腳本的已中斷連線會話已到達中斷點，並在中斷點停止， `Enter-PSSession` 則在您重新連線到會話之後，會自動啟動命令列偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-114">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="bf871-115">您可以使用 PowerShell 偵錯工具的功能來檢查 PowerShell 腳本、函式、命令或運算式是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-115">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, or expression while it is running.</span></span> <span data-ttu-id="bf871-116">PowerShell 偵錯工具包含一組 Cmdlet，可讓您設定中斷點、管理中斷點，以及查看呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="bf871-116">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="bf871-117">偵錯工具 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bf871-117">Debugger Cmdlets</span></span>

<span data-ttu-id="bf871-118">PowerShell 偵錯工具包含下列一組 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="bf871-118">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="bf871-119">`Set-PSBreakpoint`：在行、變數和命令上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-119">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="bf871-120">`Get-PSBreakpoint`：取得目前會話中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-120">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="bf871-121">`Disable-PSBreakpoint`：關閉目前會話中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-121">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="bf871-122">`Enable-PSBreakpoint`：重新啟用目前會話中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-122">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="bf871-123">`Remove-PSBreakpoint`：刪除目前會話中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-123">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="bf871-124">`Get-PSCallStack`：顯示目前的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="bf871-124">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="bf871-125">啟動和停止偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bf871-125">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="bf871-126">若要啟動偵錯工具，請設定一或多個中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-126">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="bf871-127">然後，執行您要進行偵錯工具的腳本、命令或函數。</span><span class="sxs-lookup"><span data-stu-id="bf871-127">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="bf871-128">當您到達中斷點時，執行會停止，並將控制權轉換至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-128">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="bf871-129">若要停止偵錯工具，請執行腳本、命令或函數，直到完成為止。</span><span class="sxs-lookup"><span data-stu-id="bf871-129">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="bf871-130">或者，輸入 `stop` 或 `t` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-130">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="bf871-131">偵錯工具命令</span><span class="sxs-lookup"><span data-stu-id="bf871-131">Debugger Commands</span></span>

<span data-ttu-id="bf871-132">當您在 PowerShell 主控台中使用偵錯工具時，請使用下列命令來控制執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-132">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="bf871-133">在 Windows PowerShell ISE 中，使用 [調試] 功能表上的命令。</span><span class="sxs-lookup"><span data-stu-id="bf871-133">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="bf871-134">注意：如需有關如何在其他主應用程式中使用偵錯工具的詳細資訊，請參閱主機應用程式檔集。</span><span class="sxs-lookup"><span data-stu-id="bf871-134">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="bf871-135">`s`， `StepInto` ：執行下一個語句，然後停止。</span><span class="sxs-lookup"><span data-stu-id="bf871-135">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="bf871-136">`v``StepOver`：執行下一個語句，但略過函數和調用。</span><span class="sxs-lookup"><span data-stu-id="bf871-136">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="bf871-137">這會執行已跳過的陳述式，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-137">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="bf871-138">`Ctrl+Break`： (在 ISE 中中斷所有) 會中斷到 PowerShell 主控台或 Windows PowerShell ISE 內的執行中腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-138">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="bf871-139">請注意<kbd>Ctrl</kbd>， + Windows PowerShell 2.0、3.0 和4.0 中的 Ctrl<kbd>Break</kbd>會關閉程式。</span><span class="sxs-lookup"><span data-stu-id="bf871-139">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="bf871-140">Break 全都適用于本機和遠端互動執行的腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-140">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="bf871-141">`o`：從目前的函式中 `StepOut` 移出; 如果是 nested，則向上移一層。</span><span class="sxs-lookup"><span data-stu-id="bf871-141">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="bf871-142">如果在主體中，它會繼續到結束或下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-142">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="bf871-143">這會執行已跳過的陳述式，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-143">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="bf871-144">`c``Continue`：會繼續執行，直到腳本完成或到達下一個中斷點為止。</span><span class="sxs-lookup"><span data-stu-id="bf871-144">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="bf871-145">這會執行已跳過的陳述式，但不會逐步執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-145">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="bf871-146">`l``List`：顯示正在執行之腳本的一部分。</span><span class="sxs-lookup"><span data-stu-id="bf871-146">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="bf871-147">依預設，它會顯示目前的行、前五行，以及10個後續的行。</span><span class="sxs-lookup"><span data-stu-id="bf871-147">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="bf871-148">若要繼續列出腳本，請按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="bf871-148">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="bf871-149">`l <m>``List`：顯示以指定的行號開頭之腳本的16行 `<m>` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-149">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="bf871-150">`l <m> <n>``List`：顯示 `<n>` 腳本的行，以指定的行號為開頭 `<m>` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-150">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="bf871-151">`q`、 `Stop` 、 `Exit` ：停止執行腳本，並結束偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-151">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="bf871-152">如果您要藉由執行指令程式來進行工作的偵錯工具，命令會中斷偵錯工具的連結 `Debug-Job` `Exit` ，並允許工作繼續執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-152">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="bf871-153">`k``Get-PsCallStack`：顯示目前的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="bf871-153">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="bf871-154">`<Enter>`：如果步驟 (s) 、跨距 (v) 或清單 (l) ，則重複最後一個命令。</span><span class="sxs-lookup"><span data-stu-id="bf871-154">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="bf871-155">否則，代表提交動作。</span><span class="sxs-lookup"><span data-stu-id="bf871-155">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="bf871-156">`?``h`：顯示偵錯工具命令說明。</span><span class="sxs-lookup"><span data-stu-id="bf871-156">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="bf871-157">若要結束偵錯工具，您可以使用 Stop (q) 。</span><span class="sxs-lookup"><span data-stu-id="bf871-157">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="bf871-158">從 PowerShell 5.0 開始，您可以執行 [結束] 命令來結束您藉由執行或來啟動的嵌套式偵錯工具 `Debug-Job` `Debug-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-158">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="bf871-159">藉由使用這些偵錯工具命令，您可以執行腳本、停止關注點、檢查變數值和系統狀態，然後繼續執行腳本，直到找出問題為止。</span><span class="sxs-lookup"><span data-stu-id="bf871-159">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="bf871-160">注意：如果您逐步執行具有重新導向運算子的語句，例如 ">"，則 PowerShell 偵錯工具會逐步執行腳本中所有其餘的語句。</span><span class="sxs-lookup"><span data-stu-id="bf871-160">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="bf871-161">顯示腳本變數的值</span><span class="sxs-lookup"><span data-stu-id="bf871-161">Displaying the Values of script Variables</span></span>

<span data-ttu-id="bf871-162">當您在偵錯工具中時，您也可以輸入命令、顯示變數的值、使用指令程式，以及在命令列執行腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-162">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="bf871-163">除了下列自動變數之外，您可以在正在進行調試的腳本中顯示所有變數的目前值：</span><span class="sxs-lookup"><span data-stu-id="bf871-163">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="bf871-164">如果您嘗試顯示上述任何變數的值，您會取得偵錯工具所使用之內部管線中的變數值，而不是指令碼中的變數值。</span><span class="sxs-lookup"><span data-stu-id="bf871-164">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="bf871-165">若要針對正在進行調試的腳本顯示這些變數的值，請在腳本中，將自動變數的值指派給新的變數。</span><span class="sxs-lookup"><span data-stu-id="bf871-165">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="bf871-166">然後，您可以顯示新變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf871-166">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="bf871-167">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="bf871-167">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="bf871-168">在本主題的範例中， `$MyInvocation` 會重新指派變數的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bf871-168">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="bf871-169">偵錯工具環境</span><span class="sxs-lookup"><span data-stu-id="bf871-169">The Debugger Environment</span></span>

<span data-ttu-id="bf871-170">當您到達中斷點時，您會進入偵錯工具環境。</span><span class="sxs-lookup"><span data-stu-id="bf871-170">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="bf871-171">命令提示字元會變更，使其開頭為 "[DBG]："。</span><span class="sxs-lookup"><span data-stu-id="bf871-171">The command prompt changes so that it begins with "[DBG]:".</span></span>

<span data-ttu-id="bf871-172">如需自訂提示的詳細資訊，請參閱 [about_Prompts](about_prompts.md)。</span><span class="sxs-lookup"><span data-stu-id="bf871-172">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="bf871-173">此外，在某些主機應用程式（例如 PowerShell 主控台）中 (但不是在 Windows PowerShell 整合式腳本環境 [ISE] ) 中，會開啟內嵌的提示以進行調試。</span><span class="sxs-lookup"><span data-stu-id="bf871-173">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="bf871-174">您可以在命令提示字元中出現重複的大於字元 (ASCII 62) 來偵測嵌套提示。</span><span class="sxs-lookup"><span data-stu-id="bf871-174">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="bf871-175">例如，以下是 PowerShell 主控台中的預設偵錯工具提示：</span><span class="sxs-lookup"><span data-stu-id="bf871-175">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="bf871-176">您可以使用自動變數來尋找嵌套層級 `$NestedPromptLevel` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-176">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="bf871-177">此外，自動變數 `$PSDebugContext` 是在區域範圍中定義的。</span><span class="sxs-lookup"><span data-stu-id="bf871-177">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="bf871-178">您可以使用變數的存在， `$PsDebugContext` 判斷您是否在偵錯工具中。</span><span class="sxs-lookup"><span data-stu-id="bf871-178">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="bf871-179">例如：</span><span class="sxs-lookup"><span data-stu-id="bf871-179">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="bf871-180">您可以 `$PSDebugContext` 在偵錯工具中使用變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf871-180">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="bf871-181">調試和範圍</span><span class="sxs-lookup"><span data-stu-id="bf871-181">Debugging and Scope</span></span>

<span data-ttu-id="bf871-182">中斷偵錯工具並不會變更您正在操作的範圍，但當您到達腳本中的中斷點時，您會移至腳本範圍中。</span><span class="sxs-lookup"><span data-stu-id="bf871-182">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="bf871-183">腳本範圍是您執行偵錯工具之範圍的子系。</span><span class="sxs-lookup"><span data-stu-id="bf871-183">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="bf871-184">若要尋找腳本範圍中定義的變數和別名，請使用或 Cmdlet 的 Scope 參數 `Get-Alias` `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-184">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="bf871-185">例如，下列命令會取得本機 (腳本) 範圍中的變數：</span><span class="sxs-lookup"><span data-stu-id="bf871-185">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="bf871-186">您可以將命令縮寫為：</span><span class="sxs-lookup"><span data-stu-id="bf871-186">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="bf871-187">這是只查看您在腳本中定義且在偵錯工具中定義之變數的實用方式。</span><span class="sxs-lookup"><span data-stu-id="bf871-187">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="bf871-188">在命令列進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bf871-188">Debugging at the Command Line</span></span>

<span data-ttu-id="bf871-189">當您設定變數中斷點或命令中斷點時，您只能在腳本檔案中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-189">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="bf871-190">不過，根據預設，中斷點會設定在目前會話中執行的任何作業。</span><span class="sxs-lookup"><span data-stu-id="bf871-190">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="bf871-191">例如，如果您在變數上設定中斷點 `$name` ，偵錯工具會在您 `$name` 執行的任何腳本、命令、函數、腳本 Cmdlet 或運算式中的任何變數上中斷，直到您停用或移除中斷點為止。</span><span class="sxs-lookup"><span data-stu-id="bf871-191">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="bf871-192">這可讓您在更實際的內容中進行腳本的偵測，這些內容可能會受到會話和使用者設定檔中的函式、變數和其他腳本影響。</span><span class="sxs-lookup"><span data-stu-id="bf871-192">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="bf871-193">行中斷點是腳本檔專用的，因此只會在腳本檔案中設定。</span><span class="sxs-lookup"><span data-stu-id="bf871-193">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-functions"></a><span data-ttu-id="bf871-194">調試函數</span><span class="sxs-lookup"><span data-stu-id="bf871-194">Debugging Functions</span></span>

<span data-ttu-id="bf871-195">當您在具有、和區段的函式上設定中斷點時 `Begin` `Process` `End` ，偵錯工具會在每個區段的第一行中斷。</span><span class="sxs-lookup"><span data-stu-id="bf871-195">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="bf871-196">例如：</span><span class="sxs-lookup"><span data-stu-id="bf871-196">For example:</span></span>

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a><span data-ttu-id="bf871-197">對遠端腳本進行調試</span><span class="sxs-lookup"><span data-stu-id="bf871-197">Debugging Remote Scripts</span></span>

<span data-ttu-id="bf871-198">從 PowerShell 5.0 開始，您可以在遠端會話、主控台或 Windows PowerShell ISE 中執行 PowerShell 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-198">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="bf871-199">`Enter-PSSession` 功能已更新為可讓您重新連接並輸入在遠端電腦上執行的已中斷連線會話，以及目前正在執行的腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-199">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="bf871-200">如果執行中的腳本叫用中斷點，您的用戶端會話就會自動啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-200">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="bf871-201">以下範例會示範其運作方式，並在第6、11、22和25行的腳本中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-201">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="bf871-202">請注意，在此範例中，當偵錯工具啟動時，有兩個識別提示：會話執行所在的電腦名稱稱，以及可讓您知道您處於偵錯工具模式的 DBG 提示。</span><span class="sxs-lookup"><span data-stu-id="bf871-202">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a><span data-ttu-id="bf871-203">範例</span><span class="sxs-lookup"><span data-stu-id="bf871-203">Examples</span></span>

<span data-ttu-id="bf871-204">此測試腳本會偵測作業系統的版本，並顯示系統適當的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf871-204">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="bf871-205">它包含函式、函式呼叫和變數。</span><span class="sxs-lookup"><span data-stu-id="bf871-205">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="bf871-206">下列命令會顯示測試腳本檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="bf871-206">The following command displays the contents of the test script file:</span></span>

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

<span data-ttu-id="bf871-207">若要開始，請在腳本中的相關點設定中斷點，例如行、命令、變數或函數。</span><span class="sxs-lookup"><span data-stu-id="bf871-207">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="bf871-208">首先，在目前目錄中 Test.ps1 腳本的第一行建立行中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-208">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="bf871-209">您可以將此命令縮寫為：</span><span class="sxs-lookup"><span data-stu-id="bf871-209">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="bf871-210">此命令會傳回 ( **system.management.automation.linebreakpoint** ) 的行中斷點物件。</span><span class="sxs-lookup"><span data-stu-id="bf871-210">The command returns a line-breakpoint object ( **System.Management.Automation.LineBreakpoint** ).</span></span>

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

<span data-ttu-id="bf871-211">現在，啟動腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-211">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="bf871-212">當腳本到達第一個中斷點時，中斷點訊息會指出偵錯工具為作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="bf871-212">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="bf871-213">它描述中斷點，並預覽腳本的第一行，也就是函式宣告。</span><span class="sxs-lookup"><span data-stu-id="bf871-213">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="bf871-214">命令提示字元也會變更，以指出偵錯工具有控制權。</span><span class="sxs-lookup"><span data-stu-id="bf871-214">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="bf871-215">預覽行包含預覽命令的腳本名稱和行號。</span><span class="sxs-lookup"><span data-stu-id="bf871-215">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="bf871-216">使用 (s 的步驟命令) 執行腳本中的第一個語句，以及預覽下一個語句。</span><span class="sxs-lookup"><span data-stu-id="bf871-216">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="bf871-217">下一個語句會使用 `$MyInvocation` 自動變數，將變數的值設定 `$scriptName` 為腳本檔案的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="bf871-217">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="bf871-218">此時 `$scriptName` 不會填入變數，但您可以藉由顯示變數的值來確認變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf871-218">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="bf871-219">此處的值為 `$null`。</span><span class="sxs-lookup"><span data-stu-id="bf871-219">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="bf871-220">使用 (s 的其他步驟命令) 執行目前的語句，並預覽腳本中的下一個語句。</span><span class="sxs-lookup"><span data-stu-id="bf871-220">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="bf871-221">下一個語句會呼叫 PsVersion 函數。</span><span class="sxs-lookup"><span data-stu-id="bf871-221">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="bf871-222">此時 `$scriptName` 會填入變數，但您可以藉由顯示變數的值來確認變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf871-222">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="bf871-223">在此情況下，此值會設定為腳本路徑。</span><span class="sxs-lookup"><span data-stu-id="bf871-223">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="bf871-224">使用其他步驟命令來執行函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="bf871-224">Use another Step command to execute the function call.</span></span> <span data-ttu-id="bf871-225">按 ENTER 鍵，或輸入 "s" 進行步驟。</span><span class="sxs-lookup"><span data-stu-id="bf871-225">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="bf871-226">偵錯工具訊息包含函式中之語句的預覽。</span><span class="sxs-lookup"><span data-stu-id="bf871-226">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="bf871-227">若要執行這個語句並預覽函式中的下一個語句，您可以使用 `Step` 命令。</span><span class="sxs-lookup"><span data-stu-id="bf871-227">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="bf871-228">但在此情況下，請使用 StepOut 命令 (o) 。</span><span class="sxs-lookup"><span data-stu-id="bf871-228">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="bf871-229">它會完成函式 (的執行，除非它到達中斷點) ，並逐步執行至腳本中的下一個語句。</span><span class="sxs-lookup"><span data-stu-id="bf871-229">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="bf871-230">因為我們是在腳本中的最後一個語句，所以 Step、StepOut 和 Continue 命令都有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="bf871-230">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="bf871-231">在此情況下，請使用 StepOut (o) 。</span><span class="sxs-lookup"><span data-stu-id="bf871-231">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="bf871-232">StepOut 命令會執行最後一個命令。</span><span class="sxs-lookup"><span data-stu-id="bf871-232">The StepOut command executes the last command.</span></span> <span data-ttu-id="bf871-233">標準命令提示字元指出偵錯工具已結束，並將控制權傳回給命令處理器。</span><span class="sxs-lookup"><span data-stu-id="bf871-233">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="bf871-234">現在，再次執行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-234">Now, run the debugger again.</span></span> <span data-ttu-id="bf871-235">首先，若要刪除目前的中斷點，請使用 `Get-PsBreakpoint` 和 `Remove-PsBreakpoint` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf871-235">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="bf871-236"> (如果您認為您可能會重複使用中斷點，請使用 `Disable-PsBreakpoint` Cmdlet 而不是 `Remove-PsBreakpoint` 。 ) </span><span class="sxs-lookup"><span data-stu-id="bf871-236">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="bf871-237">您可以將此命令縮寫為：</span><span class="sxs-lookup"><span data-stu-id="bf871-237">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="bf871-238">或者，藉由撰寫函數來執行命令，例如下列函式：</span><span class="sxs-lookup"><span data-stu-id="bf871-238">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="bf871-239">現在，在變數上建立中斷點 `$scriptname` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-239">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="bf871-240">您可以將命令縮寫為：</span><span class="sxs-lookup"><span data-stu-id="bf871-240">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="bf871-241">現在，啟動腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-241">Now, start the script.</span></span> <span data-ttu-id="bf871-242">腳本到達變數中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-242">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="bf871-243">預設模式為 [寫入]，因此會在變更變數值的語句之前停止執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-243">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="bf871-244">顯示變數目前的值 `$scriptName` ，也就是 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-244">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="bf871-245">使用步驟命令 (s) 執行填入變數的語句。</span><span class="sxs-lookup"><span data-stu-id="bf871-245">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="bf871-246">然後，顯示變數的新值 `$scriptName` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-246">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="bf871-247">下一個語句是 PsVersion 函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="bf871-247">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="bf871-248">若要略過函式但仍執行它，請使用跨距命令 (v) 。</span><span class="sxs-lookup"><span data-stu-id="bf871-248">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="bf871-249">如果您在使用跨距時已在函式中，則不會有效。</span><span class="sxs-lookup"><span data-stu-id="bf871-249">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="bf871-250">會顯示函式呼叫，但不會執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-250">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="bf871-251">跨距命令會執行函式，並預覽腳本中的下一個語句，以列印最後一行。</span><span class="sxs-lookup"><span data-stu-id="bf871-251">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="bf871-252">使用 Stop 命令 (t) 結束偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-252">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="bf871-253">命令提示字元會還原為標準的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="bf871-253">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="bf871-254">若要刪除中斷點，請使用 `Get-PsBreakpoint` 和 `Remove-PsBreakpoint` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf871-254">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="bf871-255">在 PsVersion 函式上建立新的命令中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-255">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="bf871-256">您可以將此命令縮寫為：</span><span class="sxs-lookup"><span data-stu-id="bf871-256">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="bf871-257">現在，執行腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-257">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="bf871-258">腳本會在函式呼叫中到達中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-258">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="bf871-259">至此，尚未呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="bf871-259">At this point, the function has not yet been called.</span></span> <span data-ttu-id="bf871-260">這讓您有機會使用的 Action 參數 `Set-PSBreakpoint` 來設定執行中斷點的條件，或是執行準備或診斷工作，例如開機記錄或叫用診斷或安全性腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-260">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="bf871-261">若要設定動作，請使用 Continue 命令 (c) 結束腳本，並使用 `Remove-PsBreakpoint` 命令來刪除目前的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-261">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="bf871-262"> (中斷點是唯讀的，因此您無法將動作加入至目前的中斷點。 ) </span><span class="sxs-lookup"><span data-stu-id="bf871-262">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="bf871-263">現在，使用動作建立新的命令中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-263">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="bf871-264">下列命令會使用動作來設定命令中斷點， `$scriptName` 此動作會在呼叫函式時記錄變數的值。</span><span class="sxs-lookup"><span data-stu-id="bf871-264">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="bf871-265">因為不會在動作中使用 Break 關鍵字，所以不會停止執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-265">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="bf871-266"> (倒引號 (') 是行接續字元。 ) </span><span class="sxs-lookup"><span data-stu-id="bf871-266">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="bf871-267">您也可以新增動作來設定中斷點的條件。</span><span class="sxs-lookup"><span data-stu-id="bf871-267">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="bf871-268">在下列命令中，只有當執行原則設定為 RemoteSigned 時，才會執行命令中斷點，這是限制最嚴格的原則，仍允許您執行腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-268">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="bf871-269"> (倒引號 (') 是接續字元。 ) </span><span class="sxs-lookup"><span data-stu-id="bf871-269">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="bf871-270">動作中的 Break 關鍵字會指示偵錯工具執行中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf871-270">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="bf871-271">您也可以使用 Continue 關鍵字，指示偵錯工具在不中斷的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-271">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="bf871-272">因為 default 關鍵字是 Continue，所以您必須指定 Break 來停止執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-272">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="bf871-273">現在，執行腳本。</span><span class="sxs-lookup"><span data-stu-id="bf871-273">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="bf871-274">因為執行原則設定為 **RemoteSigned** ，所以會在函式呼叫時停止執行。</span><span class="sxs-lookup"><span data-stu-id="bf871-274">Because the execution policy is set to **RemoteSigned** , execution stops at the function call.</span></span>

<span data-ttu-id="bf871-275">至此，您可能會想要檢查呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="bf871-275">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="bf871-276">使用 `Get-PsCallStack` Cmdlet 或 `Get-PsCallStack` 偵錯工具命令 (k) 。</span><span class="sxs-lookup"><span data-stu-id="bf871-276">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="bf871-277">下列命令會取得目前的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="bf871-277">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="bf871-278">此範例只會示範使用 PowerShell 偵錯工具的許多方式。</span><span class="sxs-lookup"><span data-stu-id="bf871-278">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="bf871-279">如需偵錯工具 Cmdlet 的詳細資訊，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="bf871-279">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="bf871-280">例如，輸入：</span><span class="sxs-lookup"><span data-stu-id="bf871-280">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="bf871-281">PowerShell 中的其他調試功能</span><span class="sxs-lookup"><span data-stu-id="bf871-281">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="bf871-282">除了 PowerShell 偵錯工具之外，PowerShell 還包含數個可供您用來偵測腳本和函式的其他功能。</span><span class="sxs-lookup"><span data-stu-id="bf871-282">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="bf871-283">Windows PowerShell ISE 包含互動式圖形偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="bf871-283">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="bf871-284">如需詳細資訊，請啟動 Windows PowerShell ISE，然後按下 F1。</span><span class="sxs-lookup"><span data-stu-id="bf871-284">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="bf871-285">此 `Set-PSDebug` Cmdlet 提供非常基本的腳本調試功能，包括逐步執行和追蹤。</span><span class="sxs-lookup"><span data-stu-id="bf871-285">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="bf871-286">使用指令 `Set-StrictMode` 程式可偵測未初始化變數的參考、參考不存在之物件的屬性，以及函式不正確語法。</span><span class="sxs-lookup"><span data-stu-id="bf871-286">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="bf871-287">將診斷語句新增至腳本，例如顯示變數值的語句、從命令列讀取輸入的語句，或報告目前指令的語句。</span><span class="sxs-lookup"><span data-stu-id="bf871-287">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="bf871-288">使用包含此工作之寫入動詞的 Cmdlet，例如 `Write-Host` 、 `Write-Debug` 、 `Write-Warning` 和 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="bf871-288">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf871-289">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf871-289">SEE ALSO</span></span>

- [<span data-ttu-id="bf871-290">停用->disable-psbreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf871-290">Disable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="bf871-291">啟用->disable-psbreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf871-291">Enable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="bf871-292">>disable-psbreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf871-292">Get-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="bf871-293">Get-pscallstack</span><span class="sxs-lookup"><span data-stu-id="bf871-293">Get-PsCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="bf871-294">移除->disable-psbreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf871-294">Remove-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="bf871-295">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf871-295">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="bf871-296">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="bf871-296">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="bf871-297">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="bf871-297">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
