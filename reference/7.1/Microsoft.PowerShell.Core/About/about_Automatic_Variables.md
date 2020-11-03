---
description: 描述儲存 PowerShell 狀態資訊的變數。 PowerShell 會建立和維護這些變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 5ce9e61113da2c781f5774866e827663a7c7ced4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208367"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="09343-105">關於自動變數</span><span class="sxs-lookup"><span data-stu-id="09343-105">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="09343-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="09343-106">Short description</span></span>

<span data-ttu-id="09343-107">描述儲存 PowerShell 狀態資訊的變數。</span><span class="sxs-lookup"><span data-stu-id="09343-107">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="09343-108">PowerShell 會建立和維護這些變數。</span><span class="sxs-lookup"><span data-stu-id="09343-108">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="09343-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="09343-109">Long description</span></span>

<span data-ttu-id="09343-110">在概念上，這些變數會被視為唯讀。</span><span class="sxs-lookup"><span data-stu-id="09343-110">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="09343-111">雖然它們 **可** 寫入至，但為了回溯相容性， **不應** 將其寫入。</span><span class="sxs-lookup"><span data-stu-id="09343-111">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="09343-112">以下是 PowerShell 中的自動變數清單：</span><span class="sxs-lookup"><span data-stu-id="09343-112">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="09343-113">包含會話收到的最後一行中的最後一個 token。</span><span class="sxs-lookup"><span data-stu-id="09343-113">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="09343-114">$?</span><span class="sxs-lookup"><span data-stu-id="09343-114">$?</span></span>

<span data-ttu-id="09343-115">包含最後一個命令的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="09343-115">Contains the execution status of the last command.</span></span> <span data-ttu-id="09343-116">如果最後一個命令成功，則會包含 **True** ，如果失敗，則為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="09343-116">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="09343-117">對於在管線中多個階段執行的 Cmdlet 和 advanced 函式（例如在 `process` 和區塊中 `end` ），在 `this.WriteError()` `$PSCmdlet.WriteError()` 任何時間點呼叫或分別會將設定 `$?` 為 **False** ，如同 `this.ThrowTerminatingError()` 和 `$PSCmdlet.ThrowTerminatingError()` 。</span><span class="sxs-lookup"><span data-stu-id="09343-117">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False** , as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="09343-118">Cmdlet 會在 `Write-Error` `$?` 執行之後立即將設定為 **false** ，但在呼叫它的函式中，不會將設定 `$?` 為 **false** ：</span><span class="sxs-lookup"><span data-stu-id="09343-118">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="09343-119">針對第二個用途， `$PSCmdlet.WriteError()` 應該改為使用。</span><span class="sxs-lookup"><span data-stu-id="09343-119">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="09343-120">若為原生命令 (可執行檔) ， `$?` 當是0時，會設定為 **True** `$LASTEXITCODE` ，當為任何其他值時，則設定為 **False** `$LASTEXITCODE` 。</span><span class="sxs-lookup"><span data-stu-id="09343-120">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="09343-121">除非 PowerShell 7 包含括弧內的語句，否則 `(...)` 子運算式語法 `$(...)` 或陣列運算式 `@(...)` 一律會重設 `$?` 為 **true** ，因此會 `(Write-Error)` 顯示 `$?` 為 **true** 。</span><span class="sxs-lookup"><span data-stu-id="09343-121">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True** , so that `(Write-Error)` shows `$?` as **True** .</span></span>
> <span data-ttu-id="09343-122">這已在 PowerShell 7 中變更，因此 `$?` 一律會反映在這些運算式中，最後一個命令執行的實際成功與否。</span><span class="sxs-lookup"><span data-stu-id="09343-122">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="09343-123">包含會話收到的最後一行中的第一個 token。</span><span class="sxs-lookup"><span data-stu-id="09343-123">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="09343-124">$_</span><span class="sxs-lookup"><span data-stu-id="09343-124">$_</span></span>

<span data-ttu-id="09343-125">與 `$PSItem` 相同。</span><span class="sxs-lookup"><span data-stu-id="09343-125">Same as `$PSItem`.</span></span> <span data-ttu-id="09343-126">包含管線物件中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="09343-126">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="09343-127">您可以在命令中使用這個變數，這些命令會在管線中的每個物件或選取的物件上執行動作。</span><span class="sxs-lookup"><span data-stu-id="09343-127">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="09343-128">$args</span><span class="sxs-lookup"><span data-stu-id="09343-128">$args</span></span>

<span data-ttu-id="09343-129">包含未宣告參數的值陣列，這些參數會傳遞至函式、腳本或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09343-129">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="09343-130">當您建立函式時，您可以使用關鍵字來宣告參數，或在函 `param` 式名稱後面的括弧中新增以逗號分隔的參數清單。</span><span class="sxs-lookup"><span data-stu-id="09343-130">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="09343-131">在事件動作中， `$Args` 變數包含物件，這些物件代表正在處理之事件的事件引數。</span><span class="sxs-lookup"><span data-stu-id="09343-131">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="09343-132">此變數只會填入 `Action` 事件註冊命令的區塊內。</span><span class="sxs-lookup"><span data-stu-id="09343-132">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="09343-133">您也可以在傳回的 **PSEventArgs** 物件的 **SourceArgs** 屬性中找到這個變數的值 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="09343-133">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="09343-134">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="09343-134">$ConsoleFileName</span></span>

<span data-ttu-id="09343-135">包含在 `.psc1` 會話中最近使用的主控台檔案 () 的路徑。</span><span class="sxs-lookup"><span data-stu-id="09343-135">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="09343-136">當您使用 **PSConsoleFile** 參數啟動 PowerShell，或使用指令程式將嵌入式 `Export-Console` 管理單元名稱匯出到主控台檔案時，就會填入此變數。</span><span class="sxs-lookup"><span data-stu-id="09343-136">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="09343-137">當您使用 `Export-Console` 不含參數的 Cmdlet 時，它會自動更新會話中最近使用的主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="09343-137">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="09343-138">您可以使用此自動變數來判斷將更新的檔案。</span><span class="sxs-lookup"><span data-stu-id="09343-138">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="09343-139">$Error</span><span class="sxs-lookup"><span data-stu-id="09343-139">$Error</span></span>

<span data-ttu-id="09343-140">包含錯誤物件的陣列，這些物件表示最新的錯誤。</span><span class="sxs-lookup"><span data-stu-id="09343-140">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="09343-141">最新的錯誤是陣列中的第一個錯誤物件 `$Error[0]` 。</span><span class="sxs-lookup"><span data-stu-id="09343-141">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="09343-142">若要避免將錯誤新增至 `$Error` 陣列，請使用 **ErrorAction** 一般參數搭配 [ **略** 過] 的值。</span><span class="sxs-lookup"><span data-stu-id="09343-142">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore** .</span></span> <span data-ttu-id="09343-143">如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="09343-143">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="09343-144">$Event</span><span class="sxs-lookup"><span data-stu-id="09343-144">$Event</span></span>

<span data-ttu-id="09343-145">包含 **PSEventArgs** 物件，表示正在處理的事件。</span><span class="sxs-lookup"><span data-stu-id="09343-145">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="09343-146">此變數只會填入 `Action` 事件註冊命令的區塊中，例如 `Register-ObjectEvent` 。</span><span class="sxs-lookup"><span data-stu-id="09343-146">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="09343-147">此變數的值與 Cmdlet 所傳回的物件相同 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="09343-147">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="09343-148">因此，您可以 `Event` `$Event.TimeGenerated` 在腳本區塊中使用變數的屬性，例如 `Action` 。</span><span class="sxs-lookup"><span data-stu-id="09343-148">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="09343-149">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="09343-149">$EventArgs</span></span>

<span data-ttu-id="09343-150">包含物件，該物件表示衍生自所處理事件之 **EventArgs** 的第一個事件引數。</span><span class="sxs-lookup"><span data-stu-id="09343-150">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="09343-151">此變數只會填入 `Action` 事件註冊命令的區塊內。</span><span class="sxs-lookup"><span data-stu-id="09343-151">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="09343-152">您也可以在傳回的 **PSEventArgs** 物件的 **SourceEventArgs** 屬性中找到這個變數的值 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="09343-152">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="09343-153">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="09343-153">$EventSubscriber</span></span>

<span data-ttu-id="09343-154">包含 **PSEventSubscriber** 物件，這個物件表示正在處理之事件的事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="09343-154">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="09343-155">此變數只會填入 `Action` 事件註冊命令的區塊內。</span><span class="sxs-lookup"><span data-stu-id="09343-155">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="09343-156">此變數的值與 Cmdlet 所傳回的物件相同 `Get-EventSubscriber` 。</span><span class="sxs-lookup"><span data-stu-id="09343-156">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="09343-157">$ExecutionCoNtext</span><span class="sxs-lookup"><span data-stu-id="09343-157">$ExecutionContext</span></span>

<span data-ttu-id="09343-158">包含 **EngineIntrinsics** 物件，該物件代表 PowerShell 主機的執行內容。</span><span class="sxs-lookup"><span data-stu-id="09343-158">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="09343-159">您可以使用此變數來尋找可供 Cmdlet 使用的執行物件。</span><span class="sxs-lookup"><span data-stu-id="09343-159">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="09343-160">$false</span><span class="sxs-lookup"><span data-stu-id="09343-160">$false</span></span>

<span data-ttu-id="09343-161">包含 **False** 。</span><span class="sxs-lookup"><span data-stu-id="09343-161">Contains **False** .</span></span> <span data-ttu-id="09343-162">您可以使用此變數來表示命令和腳本中的 **False** ，而不是使用字串 "False"。</span><span class="sxs-lookup"><span data-stu-id="09343-162">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="09343-163">如果字串轉換成非空白字串或非零整數，則可以將該字串解釋為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="09343-163">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="09343-164">$foreach</span><span class="sxs-lookup"><span data-stu-id="09343-164">$foreach</span></span>

<span data-ttu-id="09343-165">包含 (非 [ForEach](about_ForEach.md) 迴圈的結果值) 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="09343-165">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="09343-166">`$ForEach`只有在迴圈執行時，變數才存在，在 `ForEach` 迴圈完成之後就會刪除。</span><span class="sxs-lookup"><span data-stu-id="09343-166">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="09343-167">列舉值包含屬性和方法，您可以使用這些屬性和方法來取得迴圈值並變更目前的迴圈反覆運算。</span><span class="sxs-lookup"><span data-stu-id="09343-167">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="09343-168">如需詳細資訊，請參閱 [使用枚舉](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="09343-168">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="09343-169">$HOME</span><span class="sxs-lookup"><span data-stu-id="09343-169">$HOME</span></span>

<span data-ttu-id="09343-170">包含使用者主目錄的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="09343-170">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="09343-171">此變數相當於 `"$env:homedrive$env:homepath"` Windows 環境變數，通常是 `C:\Users\<UserName>` 。</span><span class="sxs-lookup"><span data-stu-id="09343-171">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="09343-172">$Host</span><span class="sxs-lookup"><span data-stu-id="09343-172">$Host</span></span>

<span data-ttu-id="09343-173">包含物件，該物件表示 PowerShell 的目前主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="09343-173">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="09343-174">您可以使用此變數來代表命令中的目前主機，或顯示或變更主機的屬性，例如 `$Host.version` 或或 `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` 。</span><span class="sxs-lookup"><span data-stu-id="09343-174">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="09343-175">$input</span><span class="sxs-lookup"><span data-stu-id="09343-175">$input</span></span>

<span data-ttu-id="09343-176">包含列舉傳遞給函式之所有輸入的列舉值。</span><span class="sxs-lookup"><span data-stu-id="09343-176">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="09343-177">`$input`變數僅適用于) 未命名函式 (的函式和腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09343-177">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="09343-178">在不含、或區塊的函式中 `Begin` `Process` ，變數會列舉函式 `End` `$input` 所有輸入的集合。</span><span class="sxs-lookup"><span data-stu-id="09343-178">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="09343-179">在 `Begin` 區塊中， `$input` 變數不包含任何資料。</span><span class="sxs-lookup"><span data-stu-id="09343-179">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="09343-180">在 `Process` 區塊中， `$input` 變數包含目前在管線中的物件。</span><span class="sxs-lookup"><span data-stu-id="09343-180">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="09343-181">在 `End` 區塊中， `$input` 變數會列舉函數的所有輸入集合。</span><span class="sxs-lookup"><span data-stu-id="09343-181">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="09343-182">您無法 `$input` 在相同函式或腳本區塊中的進程區塊和 End 區塊內部使用變數。</span><span class="sxs-lookup"><span data-stu-id="09343-182">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="09343-183">因為 `$input` 是列舉值，所以存取它的任何屬性都會導致無法 `$input` 再使用。</span><span class="sxs-lookup"><span data-stu-id="09343-183">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="09343-184">您可以儲存 `$input` 在另一個變數中，以重複使用這些 `$input` 屬性。</span><span class="sxs-lookup"><span data-stu-id="09343-184">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="09343-185">列舉值包含屬性和方法，您可以使用這些屬性和方法來取得迴圈值並變更目前的迴圈反覆運算。</span><span class="sxs-lookup"><span data-stu-id="09343-185">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="09343-186">如需詳細資訊，請參閱 [使用枚舉](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="09343-186">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="iscoreclr"></a><span data-ttu-id="09343-187">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="09343-187">$IsCoreCLR</span></span>

<span data-ttu-id="09343-188">`$True`如果目前的會話是在 .Net Core 執行時間上執行 (CoreCLR) ，則為 [包含]。</span><span class="sxs-lookup"><span data-stu-id="09343-188">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="09343-189">否則會包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="09343-189">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="09343-190">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="09343-190">$IsLinux</span></span>

<span data-ttu-id="09343-191">包含 `$True` 目前的會話是否正在 Linux 作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="09343-191">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="09343-192">否則會包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="09343-192">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="09343-193">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="09343-193">$IsMacOS</span></span>

<span data-ttu-id="09343-194">包含 `$True` 目前的會話是否正在 MacOS 作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="09343-194">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="09343-195">否則會包含 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="09343-195">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="09343-196">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="09343-196">$IsWindows</span></span>

<span data-ttu-id="09343-197">包含 `$TRUE` 目前的會話是否正在 Windows 作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="09343-197">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="09343-198">否則會包含 `$FALSE` 。</span><span class="sxs-lookup"><span data-stu-id="09343-198">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="09343-199">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="09343-199">$LastExitCode</span></span>

<span data-ttu-id="09343-200">包含上次執行之 Windows 程式的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="09343-200">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="09343-201">$Matches</span><span class="sxs-lookup"><span data-stu-id="09343-201">$Matches</span></span>

<span data-ttu-id="09343-202">`Matches`變數適用于 `-match` 和 `-notmatch` 運算子。</span><span class="sxs-lookup"><span data-stu-id="09343-202">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="09343-203">當您將純量輸入提交給 `-match` 或 `-notmatch` 運算子，且其中一個偵測到相符項時，它們會傳回布林值，並 `$Matches` 以符合的任何字串值的雜湊表填入自動變數。</span><span class="sxs-lookup"><span data-stu-id="09343-203">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="09343-204">`$Matches`當您使用正則運算式搭配運算子時，雜湊表也可以填入捕捉 `-match` 。</span><span class="sxs-lookup"><span data-stu-id="09343-204">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="09343-205">如需有關運算子的詳細資訊 `-match` ，請參閱 [about_Comparison_Operators](about_comparison_operators.md)。</span><span class="sxs-lookup"><span data-stu-id="09343-205">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="09343-206">如需正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](about_Regular_Expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="09343-206">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="09343-207">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="09343-207">$MyInvocation</span></span>

<span data-ttu-id="09343-208">包含目前命令的相關資訊，例如名稱、參數、參數值，以及如何啟動、呼叫或叫用命令的相關資訊，例如呼叫目前命令的腳本名稱。</span><span class="sxs-lookup"><span data-stu-id="09343-208">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="09343-209">`$MyInvocation` 只會填入腳本、函式和腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09343-209">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="09343-210">您可以使用在目前的腳本中傳回的 **InvocationInfo** 物件中的資訊 `$MyInvocation` ，例如腳本的路徑和檔案名 (`$MyInvocation.MyCommand.Path`) 或 () 的函式名稱， `$MyInvocation.MyCommand.Name` 以識別目前的命令。</span><span class="sxs-lookup"><span data-stu-id="09343-210">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="09343-211">這特別適合用來尋找目前腳本的名稱。</span><span class="sxs-lookup"><span data-stu-id="09343-211">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="09343-212">從 PowerShell 3.0 開始， `MyInvocation` 有下列新屬性。</span><span class="sxs-lookup"><span data-stu-id="09343-212">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="09343-213">屬性</span><span class="sxs-lookup"><span data-stu-id="09343-213">Property</span></span>      | <span data-ttu-id="09343-214">描述</span><span class="sxs-lookup"><span data-stu-id="09343-214">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="09343-215">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="09343-215">**PSScriptRoot**</span></span>  | <span data-ttu-id="09343-216">包含已叫用之腳本的完整路徑</span><span class="sxs-lookup"><span data-stu-id="09343-216">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="09343-217">目前的命令。</span><span class="sxs-lookup"><span data-stu-id="09343-217">the current command.</span></span> <span data-ttu-id="09343-218">這個屬性的值為</span><span class="sxs-lookup"><span data-stu-id="09343-218">The value of this property is</span></span>  |
|               | <span data-ttu-id="09343-219">只有在呼叫端為腳本時才會填入。</span><span class="sxs-lookup"><span data-stu-id="09343-219">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="09343-220">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="09343-220">**PSCommandPath**</span></span> | <span data-ttu-id="09343-221">包含腳本的完整路徑和檔案名</span><span class="sxs-lookup"><span data-stu-id="09343-221">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="09343-222">，叫用目前的命令。</span><span class="sxs-lookup"><span data-stu-id="09343-222">that invoked the current command.</span></span> <span data-ttu-id="09343-223">這個的值</span><span class="sxs-lookup"><span data-stu-id="09343-223">The value of this</span></span> |
|               | <span data-ttu-id="09343-224">只有當呼叫端為時，才會填入屬性</span><span class="sxs-lookup"><span data-stu-id="09343-224">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="09343-225">指令碼。</span><span class="sxs-lookup"><span data-stu-id="09343-225">script.</span></span>                                             |

<span data-ttu-id="09343-226">不同于 `$PSScriptRoot` 和 `$PSCommandPath` 自動變數，自動變數的 **PSScriptRoot** 和 **PSCommandPath** 屬性 `$MyInvocation` 會包含啟動程式或呼叫腳本的相關資訊，而不是目前的腳本。</span><span class="sxs-lookup"><span data-stu-id="09343-226">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="09343-227">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="09343-227">$NestedPromptLevel</span></span>

<span data-ttu-id="09343-228">包含目前的提示層級。</span><span class="sxs-lookup"><span data-stu-id="09343-228">Contains the current prompt level.</span></span> <span data-ttu-id="09343-229">0值表示原始提示層級。</span><span class="sxs-lookup"><span data-stu-id="09343-229">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="09343-230">當您輸入嵌套層級時，值會遞增，而當您結束時，該值會遞減。</span><span class="sxs-lookup"><span data-stu-id="09343-230">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="09343-231">例如，當您使用方法時，PowerShell 會顯示一個嵌套的命令提示字元 `$Host.EnterNestedPrompt` 。</span><span class="sxs-lookup"><span data-stu-id="09343-231">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="09343-232">當您進入 PowerShell 偵錯工具中的中斷點時，PowerShell 也會顯示一個嵌套的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="09343-232">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="09343-233">當您輸入嵌套提示字元時，PowerShell 會暫停目前的命令、儲存執行內容，並遞增變數的值 `$NestedPromptLevel` 。</span><span class="sxs-lookup"><span data-stu-id="09343-233">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="09343-234">若要建立額外的嵌套命令提示字元 (最多128層級) 或返回原始命令提示字元，請完成命令或輸入 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="09343-234">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="09343-235">此 `$NestedPromptLevel` 變數可協助您追蹤提示層級。</span><span class="sxs-lookup"><span data-stu-id="09343-235">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="09343-236">您可以建立包含此值的替代 PowerShell 命令提示字元，讓它一律可見。</span><span class="sxs-lookup"><span data-stu-id="09343-236">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="09343-237">$null</span><span class="sxs-lookup"><span data-stu-id="09343-237">$null</span></span>

<span data-ttu-id="09343-238">`$null` 這是包含 **null** 或空白值的自動變數。</span><span class="sxs-lookup"><span data-stu-id="09343-238">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="09343-239">您可以使用此變數來代表命令和腳本中不存在或未定義的值。</span><span class="sxs-lookup"><span data-stu-id="09343-239">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="09343-240">PowerShell 會將 `$null` 值視為具有值的物件，也就是明確的預留位置，因此您可以使用在 `$null` 一系列的值中表示空的值。</span><span class="sxs-lookup"><span data-stu-id="09343-240">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="09343-241">例如，當 `$null` 集合中包含時，會計算為其中一個物件。</span><span class="sxs-lookup"><span data-stu-id="09343-241">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="09343-242">如果您使用管線將 `$null` 變數傳送至 `ForEach-Object` Cmdlet，它會產生的值 `$null` ，就像是對其他物件所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="09343-242">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="09343-243">因此，您無法使用 `$null` 來表示 **沒有參數值** 。</span><span class="sxs-lookup"><span data-stu-id="09343-243">As a result, you can't use `$null` to mean **no parameter value** .</span></span> <span data-ttu-id="09343-244">的參數值會 `$null` 覆寫預設參數值。</span><span class="sxs-lookup"><span data-stu-id="09343-244">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="09343-245">不過，因為 PowerShell 會將 `$null` 變數視為預留位置，所以您可以在如下的腳本中使用它，如果被忽略，就不會有作用 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="09343-245">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a><span data-ttu-id="09343-246">$PID</span><span class="sxs-lookup"><span data-stu-id="09343-246">$PID</span></span>

<span data-ttu-id="09343-247">包含裝載目前 PowerShell 會話之進程 (PID) 的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="09343-247">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="09343-248">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="09343-248">$PROFILE</span></span>

<span data-ttu-id="09343-249">包含目前使用者和目前主機應用程式之 PowerShell 設定檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="09343-249">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="09343-250">您可以使用此變數來代表命令中的設定檔。</span><span class="sxs-lookup"><span data-stu-id="09343-250">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="09343-251">例如，您可以在命令中使用它來判斷是否已建立設定檔：</span><span class="sxs-lookup"><span data-stu-id="09343-251">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="09343-252">或者，您可以在命令中使用它來建立設定檔：</span><span class="sxs-lookup"><span data-stu-id="09343-252">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="09343-253">您可以在命令中使用它，在 **notepad.exe** 中開啟設定檔：</span><span class="sxs-lookup"><span data-stu-id="09343-253">You can use it in a command to open the profile in **notepad.exe** :</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="09343-254">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="09343-254">$PSBoundParameters</span></span>

<span data-ttu-id="09343-255">包含傳遞至腳本或函式之參數的字典，以及其目前的值。</span><span class="sxs-lookup"><span data-stu-id="09343-255">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="09343-256">此變數只有在宣告參數的範圍中具有值，例如腳本或函式。</span><span class="sxs-lookup"><span data-stu-id="09343-256">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="09343-257">您可以使用它來顯示或變更目前的參數值，或將參數值傳遞至另一個腳本或函式。</span><span class="sxs-lookup"><span data-stu-id="09343-257">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="09343-258">在此範例中， **Test2** 函式會將傳遞 `$PSBoundParameters` 至 **Test1** 函數。</span><span class="sxs-lookup"><span data-stu-id="09343-258">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="09343-259">`$PSBoundParameters`會以索引 **鍵** 和 **值** 的格式顯示。</span><span class="sxs-lookup"><span data-stu-id="09343-259">The `$PSBoundParameters` are displayed in the format of **Key** and **Value** .</span></span>

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a><span data-ttu-id="09343-260">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="09343-260">$PSCmdlet</span></span>

<span data-ttu-id="09343-261">包含物件，該物件表示正在執行的 Cmdlet 或 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="09343-261">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="09343-262">您可以在 Cmdlet 或函式程式碼中使用物件的屬性和方法，以回應使用的條件。</span><span class="sxs-lookup"><span data-stu-id="09343-262">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="09343-263">例如， **ParameterSetName** 屬性包含所使用之參數集的名稱，而 **ShouldProcess** 方法會動態地將 **WhatIf** 和 **Confirm** 參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09343-263">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="09343-264">如需自動變數的詳細資訊 `$PSCmdlet` ，請參閱 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="09343-264">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="09343-265">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="09343-265">$PSCommandPath</span></span>

<span data-ttu-id="09343-266">包含正在執行之腳本的完整路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="09343-266">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="09343-267">此變數在所有腳本中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="09343-267">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="09343-268">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="09343-268">$PSCulture</span></span>

<span data-ttu-id="09343-269">從 PowerShell 7 開始，會 `$PSCulture` 反映目前 PowerShell 運行時 (會話) 的文化特性。</span><span class="sxs-lookup"><span data-stu-id="09343-269">Beginning in PowerShell 7, `$PSCulture` reflects the culture of the current PowerShell runspace (session).</span></span> <span data-ttu-id="09343-270">如果 PowerShell 執行時間中的文化特性有所變更，則 `$PSCulture` 會更新該執行時間的值。</span><span class="sxs-lookup"><span data-stu-id="09343-270">If the culture is changed in a PowerShell runspace, the `$PSCulture` value for that runspace is updated.</span></span>

<span data-ttu-id="09343-271">文化特性會決定專案（例如數位、貨幣及日期）的顯示格式，並且儲存在 **system.string 物件中。**</span><span class="sxs-lookup"><span data-stu-id="09343-271">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="09343-272">用 `Get-Culture` 來顯示電腦的文化特性。</span><span class="sxs-lookup"><span data-stu-id="09343-272">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="09343-273">`$PSCulture` 包含 **Name** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="09343-273">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="09343-274">$PSDebugCoNtext</span><span class="sxs-lookup"><span data-stu-id="09343-274">$PSDebugContext</span></span>

<span data-ttu-id="09343-275">在進行調試時，此變數包含有關調試環境的資訊。</span><span class="sxs-lookup"><span data-stu-id="09343-275">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="09343-276">否則，它會包含 **null** 值。</span><span class="sxs-lookup"><span data-stu-id="09343-276">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="09343-277">因此，您可以使用它來指出偵錯工具是否有控制權。</span><span class="sxs-lookup"><span data-stu-id="09343-277">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="09343-278">填入時，它會包含具有 **中斷點** 和 **InvocationInfo** 屬性的 **PsDebugCoNtext** 物件。</span><span class="sxs-lookup"><span data-stu-id="09343-278">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="09343-279">**InvocationInfo** 屬性有數個有用的屬性，包括 **Location** 屬性。</span><span class="sxs-lookup"><span data-stu-id="09343-279">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="09343-280">**Location** 屬性指出正在進行調試的腳本路徑。</span><span class="sxs-lookup"><span data-stu-id="09343-280">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="09343-281">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="09343-281">$PSHOME</span></span>

<span data-ttu-id="09343-282">包含 PowerShell 安裝目錄的完整路徑（通常是 `$env:windir\System32\PowerShell\v1.0` 在 Windows 系統中）。</span><span class="sxs-lookup"><span data-stu-id="09343-282">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="09343-283">您可以在 PowerShell 檔案的路徑中使用此變數。</span><span class="sxs-lookup"><span data-stu-id="09343-283">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="09343-284">例如，下列命令會在概念說明主題中搜尋單字 **變數** ：</span><span class="sxs-lookup"><span data-stu-id="09343-284">For example, the following command searches the conceptual Help topics for the word **variable** :</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="09343-285">$PSItem</span><span class="sxs-lookup"><span data-stu-id="09343-285">$PSItem</span></span>

<span data-ttu-id="09343-286">與 `$_` 相同。</span><span class="sxs-lookup"><span data-stu-id="09343-286">Same as `$_`.</span></span> <span data-ttu-id="09343-287">包含管線物件中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="09343-287">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="09343-288">您可以在命令中使用這個變數，這些命令會在管線中的每個物件或選取的物件上執行動作。</span><span class="sxs-lookup"><span data-stu-id="09343-288">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="09343-289">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="09343-289">$PSScriptRoot</span></span>

<span data-ttu-id="09343-290">包含正在執行腳本的目錄。</span><span class="sxs-lookup"><span data-stu-id="09343-290">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="09343-291">在 PowerShell 2.0 中，此變數僅適用于腳本模組 (`.psm1`) 。</span><span class="sxs-lookup"><span data-stu-id="09343-291">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="09343-292">從 PowerShell 3.0 開始，它在所有腳本中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="09343-292">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="09343-293">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="09343-293">$PSSenderInfo</span></span>

<span data-ttu-id="09343-294">包含啟動 PSSession 之使用者的相關資訊，包括原始電腦的使用者身分識別和時區。</span><span class="sxs-lookup"><span data-stu-id="09343-294">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="09343-295">此變數僅適用于 Pssession。</span><span class="sxs-lookup"><span data-stu-id="09343-295">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="09343-296">`$PSSenderInfo`變數包含使用者可設定的屬性 **ApplicationArguments** ，預設只會包含 `$PSVersionTable` 來自原始會話的。</span><span class="sxs-lookup"><span data-stu-id="09343-296">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments** , that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="09343-297">若要將資料新增至 **ApplicationArguments** 屬性，請使用 Cmdlet 的 **ApplicationArguments** 參數 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="09343-297">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="09343-298">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="09343-298">$PSUICulture</span></span>

<span data-ttu-id="09343-299">包含目前正在作業系統中使用的使用者介面 (UI) 文化特性的名稱。</span><span class="sxs-lookup"><span data-stu-id="09343-299">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="09343-300">UI 文化特性會決定要將哪些文字字串用於使用者介面元素，例如功能表和訊息。</span><span class="sxs-lookup"><span data-stu-id="09343-300">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="09343-301">這是系統 **System.Globalization.CultureInfo.CurrentUICulture.Name** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="09343-301">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="09343-302">若要取得系統的 **system.object** 物件，請使用 `Get-UICulture` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09343-302">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="09343-303">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="09343-303">$PSVersionTable</span></span>

<span data-ttu-id="09343-304">包含唯讀的雜湊表，顯示目前會話中執行的 PowerShell 版本的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09343-304">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="09343-305">資料表包含下列專案：</span><span class="sxs-lookup"><span data-stu-id="09343-305">The table includes the following items:</span></span>

| <span data-ttu-id="09343-306">屬性</span><span class="sxs-lookup"><span data-stu-id="09343-306">Property</span></span>                  | <span data-ttu-id="09343-307">描述</span><span class="sxs-lookup"><span data-stu-id="09343-307">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="09343-308">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="09343-308">**PSVersion**</span></span>             | <span data-ttu-id="09343-309">PowerShell 版本號碼</span><span class="sxs-lookup"><span data-stu-id="09343-309">The PowerShell version number</span></span>                 |
| <span data-ttu-id="09343-310">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="09343-310">**PSEdition**</span></span>             | <span data-ttu-id="09343-311">這個屬性的值為</span><span class="sxs-lookup"><span data-stu-id="09343-311">This property has the value of 'Desktop' for</span></span>  |
|                           | <span data-ttu-id="09343-312">PowerShell 4 和更低的 powershell，以及 PowerShell</span><span class="sxs-lookup"><span data-stu-id="09343-312">PowerShell 4 and below as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="09343-313">5.1 在功能完整的 Windows 版本上。</span><span class="sxs-lookup"><span data-stu-id="09343-313">5.1 on full-featured Windows editions.</span></span>        |
|                           | <span data-ttu-id="09343-314">這個屬性的值為 < Core</span><span class="sxs-lookup"><span data-stu-id="09343-314">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="09343-315">PowerShell 6 和更新版本，以及 PowerShell</span><span class="sxs-lookup"><span data-stu-id="09343-315">PowerShell 6 and above as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="09343-316">低使用量版本上的 PowerShell 5。1</span><span class="sxs-lookup"><span data-stu-id="09343-316">PowerShell 5.1 on reduced-footprint editions</span></span>  |
|                           | <span data-ttu-id="09343-317">就像 Windows Nano Server 或 Windows IoT 一樣。</span><span class="sxs-lookup"><span data-stu-id="09343-317">like Windows Nano Server or Windows IoT.</span></span>      |
| <span data-ttu-id="09343-318">**GitCommitId**</span><span class="sxs-lookup"><span data-stu-id="09343-318">**GitCommitId**</span></span>           | <span data-ttu-id="09343-319">來源檔案在 GitHub 中的認可識別碼</span><span class="sxs-lookup"><span data-stu-id="09343-319">The commit Id of the source files, in GitHub,</span></span> |
| <span data-ttu-id="09343-320">**作業系統**</span><span class="sxs-lookup"><span data-stu-id="09343-320">**OS**</span></span>                    | <span data-ttu-id="09343-321">作業系統的描述</span><span class="sxs-lookup"><span data-stu-id="09343-321">Description of the operating system that</span></span>      |
|                           | <span data-ttu-id="09343-322">PowerShell 正在執行。</span><span class="sxs-lookup"><span data-stu-id="09343-322">PowerShell is running on.</span></span>                     |
| <span data-ttu-id="09343-323">**平台**</span><span class="sxs-lookup"><span data-stu-id="09343-323">**Platform**</span></span>              | <span data-ttu-id="09343-324">作業系統正在執行的平臺</span><span class="sxs-lookup"><span data-stu-id="09343-324">Platform that the operating system is running</span></span> |
|                           | <span data-ttu-id="09343-325">開啟。</span><span class="sxs-lookup"><span data-stu-id="09343-325">on.</span></span> <span data-ttu-id="09343-326">Linux 和 macOS 上的值為 **Unix** 。</span><span class="sxs-lookup"><span data-stu-id="09343-326">The value on Linux and macOS is **Unix** .</span></span> |
|                           | <span data-ttu-id="09343-327">請參閱 `$IsMacOs` 和 `$IsLinux`。</span><span class="sxs-lookup"><span data-stu-id="09343-327">See `$IsMacOs` and `$IsLinux`.</span></span>                |
| <span data-ttu-id="09343-328">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="09343-328">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="09343-329">相容的 PowerShell 版本</span><span class="sxs-lookup"><span data-stu-id="09343-329">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="09343-330">使用目前的版本</span><span class="sxs-lookup"><span data-stu-id="09343-330">with the current version</span></span>                      |
| <span data-ttu-id="09343-331">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="09343-331">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="09343-332">PowerShell 遠端版本</span><span class="sxs-lookup"><span data-stu-id="09343-332">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="09343-333">管理通訊協定。</span><span class="sxs-lookup"><span data-stu-id="09343-333">management protocol.</span></span>                          |
| <span data-ttu-id="09343-334">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="09343-334">**SerializationVersion**</span></span>  | <span data-ttu-id="09343-335">序列化方法的版本</span><span class="sxs-lookup"><span data-stu-id="09343-335">The version of the serialization method</span></span>       |
| <span data-ttu-id="09343-336">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="09343-336">**WSManStackVersion**</span></span>     | <span data-ttu-id="09343-337">WS-Management 堆疊的版本號碼</span><span class="sxs-lookup"><span data-stu-id="09343-337">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="09343-338">$PWD</span><span class="sxs-lookup"><span data-stu-id="09343-338">$PWD</span></span>

<span data-ttu-id="09343-339">包含代表目前的目錄完整路徑的路徑物件。</span><span class="sxs-lookup"><span data-stu-id="09343-339">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="09343-340">$Sender</span><span class="sxs-lookup"><span data-stu-id="09343-340">$Sender</span></span>

<span data-ttu-id="09343-341">包含產生這個事件的物件。</span><span class="sxs-lookup"><span data-stu-id="09343-341">Contains the object that generated this event.</span></span> <span data-ttu-id="09343-342">此變數只會填入事件註冊命令的動作區塊內。</span><span class="sxs-lookup"><span data-stu-id="09343-342">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="09343-343">這個變數的值也可以在傳回之 **PSEventArgs** 物件的寄件者屬性中找到 `Get-Event` 。</span><span class="sxs-lookup"><span data-stu-id="09343-343">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="09343-344">$ShellId</span><span class="sxs-lookup"><span data-stu-id="09343-344">$ShellId</span></span>

<span data-ttu-id="09343-345">包含目前 shell 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="09343-345">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="09343-346">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="09343-346">$StackTrace</span></span>

<span data-ttu-id="09343-347">包含最近錯誤的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="09343-347">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="09343-348">$switch</span><span class="sxs-lookup"><span data-stu-id="09343-348">$switch</span></span>

<span data-ttu-id="09343-349">包含列舉值，而不是語句的結果值 `Switch` 。</span><span class="sxs-lookup"><span data-stu-id="09343-349">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="09343-350">`$switch`只有當語句正在執行時，變數才存在 `Switch` ; 當語句完成執行時，就會刪除此變數 `switch` 。</span><span class="sxs-lookup"><span data-stu-id="09343-350">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="09343-351">如需詳細資訊，請參閱 [about_Switch](about_Switch.md)。</span><span class="sxs-lookup"><span data-stu-id="09343-351">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="09343-352">列舉值包含屬性和方法，您可以使用這些屬性和方法來取得迴圈值並變更目前的迴圈反覆運算。</span><span class="sxs-lookup"><span data-stu-id="09343-352">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="09343-353">如需詳細資訊，請參閱 [使用枚舉](#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="09343-353">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="09343-354">$this</span><span class="sxs-lookup"><span data-stu-id="09343-354">$this</span></span>

<span data-ttu-id="09343-355">在定義腳本屬性或腳本方法的腳本區塊中， `$this` 變數會參考正在擴充的物件。</span><span class="sxs-lookup"><span data-stu-id="09343-355">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="09343-356">在自訂類別中， `$this` 變數會參考類別物件本身，以允許存取類別中定義的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="09343-356">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="09343-357">$true</span><span class="sxs-lookup"><span data-stu-id="09343-357">$true</span></span>

<span data-ttu-id="09343-358">包含 **True** 。</span><span class="sxs-lookup"><span data-stu-id="09343-358">Contains **True** .</span></span> <span data-ttu-id="09343-359">您可以使用此變數來表示命令和腳本中的 **True** 。</span><span class="sxs-lookup"><span data-stu-id="09343-359">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="09343-360">使用枚舉器</span><span class="sxs-lookup"><span data-stu-id="09343-360">Using Enumerators</span></span>

<span data-ttu-id="09343-361">`$input`、 `$foreach` 和變數全都 `$switch` 是用來逐一查看其包含程式碼區塊所處理之值的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="09343-361">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="09343-362">列舉值包含屬性和方法，您可以使用這些屬性和方法來向前或重設反復專案，或取得反復專案值。</span><span class="sxs-lookup"><span data-stu-id="09343-362">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="09343-363">直接操作列舉值不會被視為最佳做法。</span><span class="sxs-lookup"><span data-stu-id="09343-363">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="09343-364">在迴圈中，應偏好流量控制關鍵字 [break](about_Break.md) 和 [continue](about_Continue.md) 。</span><span class="sxs-lookup"><span data-stu-id="09343-364">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="09343-365">在接受管線輸入的函式中，最佳做法是使用參數搭配 **ValueFromPipeline** 或 **ValueFromPipelineByPropertyName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="09343-365">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="09343-366">如需詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="09343-366">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="09343-367">MoveNext</span><span class="sxs-lookup"><span data-stu-id="09343-367">MoveNext</span></span>

<span data-ttu-id="09343-368">[MoveNext](/dotnet/api/system.collections.ienumerator.movenext)方法會將列舉值前移至集合中的下一個元素。</span><span class="sxs-lookup"><span data-stu-id="09343-368">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="09343-369">如果列舉 **值** 成功地前移， **MoveNext** 會傳回 True，如果列舉值已超過集合的結尾，則 **為 False** 。</span><span class="sxs-lookup"><span data-stu-id="09343-369">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="09343-370">傳回 my **MoveNext** 的 **布林** 值會傳送到輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="09343-370">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="09343-371">您可以 typecasting 輸出， `[void]` 或將其輸送至 [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null)，以隱藏輸出。</span><span class="sxs-lookup"><span data-stu-id="09343-371">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="09343-372">重設</span><span class="sxs-lookup"><span data-stu-id="09343-372">Reset</span></span>

<span data-ttu-id="09343-373">[Reset](/dotnet/api/system.collections.ienumerator.reset)方法會將列舉值設定為其初始位置，這是在集合中的第一個元素 **之前** 。</span><span class="sxs-lookup"><span data-stu-id="09343-373">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="09343-374">目前</span><span class="sxs-lookup"><span data-stu-id="09343-374">Current</span></span>

<span data-ttu-id="09343-375">[目前](/dotnet/api/system.collections.ienumerator.current)的屬性會取得集合中的元素，或在目前列舉值的位置中的管線。</span><span class="sxs-lookup"><span data-stu-id="09343-375">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="09343-376">**目前** 的屬性會繼續傳回相同的屬性，直到呼叫 **MoveNext** 為止。</span><span class="sxs-lookup"><span data-stu-id="09343-376">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="09343-377">範例</span><span class="sxs-lookup"><span data-stu-id="09343-377">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="09343-378">範例1：使用 $input 變數</span><span class="sxs-lookup"><span data-stu-id="09343-378">Example 1: Using the $input variable</span></span>

<span data-ttu-id="09343-379">在下列範例中，存取 `$input` 變數會清除變數，直到下一次進程區塊執行為止。</span><span class="sxs-lookup"><span data-stu-id="09343-379">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="09343-380">使用 **Reset** 方法會將變數重設 `$input` 為目前的管線值。</span><span class="sxs-lookup"><span data-stu-id="09343-380">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

<span data-ttu-id="09343-381">即使您未存取，進程區塊也會自動將變數往前移 `$input` 。</span><span class="sxs-lookup"><span data-stu-id="09343-381">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="09343-382">範例2：在進程區塊之外使用 $input</span><span class="sxs-lookup"><span data-stu-id="09343-382">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="09343-383">在進程區塊外部， `$input` 變數代表所有輸送至函式的值。</span><span class="sxs-lookup"><span data-stu-id="09343-383">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="09343-384">存取 `$input` 變數會清除所有值。</span><span class="sxs-lookup"><span data-stu-id="09343-384">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="09343-385">**Reset** 方法會重設整個集合。</span><span class="sxs-lookup"><span data-stu-id="09343-385">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="09343-386">永遠不會填入 **目前** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="09343-386">The **Current** property is never populated.</span></span>
- <span data-ttu-id="09343-387">**MoveNext** 方法會傳回 false，因為集合無法是先進的。</span><span class="sxs-lookup"><span data-stu-id="09343-387">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="09343-388">呼叫 **MoveNext** 會清除 `$input` 變數。</span><span class="sxs-lookup"><span data-stu-id="09343-388">Calling **MoveNext** clears out the `$input` variable.</span></span>

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="09343-389">範例3：使用 $input。Current 屬性</span><span class="sxs-lookup"><span data-stu-id="09343-389">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="09343-390">藉由使用 **current** 屬性，可以在不使用 **Reset** 方法的情況下多次存取目前的管線值。</span><span class="sxs-lookup"><span data-stu-id="09343-390">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="09343-391">進程區塊不會自動呼叫 **MoveNext** 方法。</span><span class="sxs-lookup"><span data-stu-id="09343-391">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="09343-392">除非您明確呼叫 **MoveNext** ，否則永遠不會填入 **目前** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="09343-392">The **Current** property will never be populated unless you explicitly call **MoveNext** .</span></span> <span data-ttu-id="09343-393">您可以在進程區塊內多次存取 **目前** 的屬性，而不需要清除其值。</span><span class="sxs-lookup"><span data-stu-id="09343-393">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="09343-394">範例4：使用 $foreach 變數</span><span class="sxs-lookup"><span data-stu-id="09343-394">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="09343-395">與變數不同的 `$input` 是， `$foreach` 當直接存取時，變數一律會代表集合中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="09343-395">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="09343-396">使用 **current** 屬性來存取目前的 collection 元素，以及使用 **Reset** 和 **MoveNext** 方法來變更其值。</span><span class="sxs-lookup"><span data-stu-id="09343-396">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="09343-397">迴圈的每個反復專案 `foreach` 都會自動呼叫 **MoveNext** 方法。</span><span class="sxs-lookup"><span data-stu-id="09343-397">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="09343-398">下列迴圈只會執行兩次。</span><span class="sxs-lookup"><span data-stu-id="09343-398">The following loop only executes twice.</span></span> <span data-ttu-id="09343-399">在第二個反復專案中，集合會在反覆運算完成之前移至第三個元素。</span><span class="sxs-lookup"><span data-stu-id="09343-399">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="09343-400">在第二個反復專案之後，現在沒有可逐一查看的值，而且迴圈會結束。</span><span class="sxs-lookup"><span data-stu-id="09343-400">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="09343-401">**MoveNext** 屬性不會影響已選擇逐一查看集合 () 的變數 `$Num` 。</span><span class="sxs-lookup"><span data-stu-id="09343-401">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

<span data-ttu-id="09343-402">使用 **Reset** 方法會重設集合中目前的元素。</span><span class="sxs-lookup"><span data-stu-id="09343-402">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="09343-403">下列範例會迴圈執行前兩個元素 **兩次** ，因為會呼叫 **Reset** 方法。</span><span class="sxs-lookup"><span data-stu-id="09343-403">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="09343-404">在前兩個迴圈之後， `if` 語句會失敗，而且迴圈會正常地逐一查看所有三個元素。</span><span class="sxs-lookup"><span data-stu-id="09343-404">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09343-405">這可能會導致無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="09343-405">This could result in an infinite loop.</span></span>

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="09343-406">範例5：使用 $switch 變數</span><span class="sxs-lookup"><span data-stu-id="09343-406">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="09343-407">`$switch`變數與變數具有完全相同的規則 `$foreach` 。</span><span class="sxs-lookup"><span data-stu-id="09343-407">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="09343-408">下列範例示範所有列舉值概念。</span><span class="sxs-lookup"><span data-stu-id="09343-408">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="09343-409">請注意， **NotEvaluated** 即使 `break` **MoveNext** 方法之後沒有語句，NotEvaluated 案例也不會執行。</span><span class="sxs-lookup"><span data-stu-id="09343-409">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a><span data-ttu-id="09343-410">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09343-410">See also</span></span>

[<span data-ttu-id="09343-411">about_Functions</span><span class="sxs-lookup"><span data-stu-id="09343-411">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="09343-412">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="09343-412">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="09343-413">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="09343-413">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="09343-414">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="09343-414">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="09343-415">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="09343-415">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="09343-416">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="09343-416">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="09343-417">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="09343-417">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="09343-418">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="09343-418">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="09343-419">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="09343-419">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="09343-420">about_Variables</span><span class="sxs-lookup"><span data-stu-id="09343-420">about_Variables</span></span>](about_Variables.md)

