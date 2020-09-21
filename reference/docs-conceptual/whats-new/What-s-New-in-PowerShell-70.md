---
title: PowerShell 7.0 的新功能
description: PowerShell 7.0 中發行的新功能與變更
ms.date: 03/04/2020
ms.openlocfilehash: d52b536efd9d7a1f8e6b01a58952f08ca49016b1
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162455"
---
# <a name="whats-new-in-powershell-70"></a><span data-ttu-id="eb895-103">PowerShell 7.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="eb895-103">What's New in PowerShell 7.0</span></span>

<span data-ttu-id="eb895-104">PowerShell 7.0 為開放原始碼、跨平台 (Windows、macOS 和 Linux) 的 PowerShell 版本，建置來管理異質環境和混合式雲端。</span><span class="sxs-lookup"><span data-stu-id="eb895-104">PowerShell 7.0 is an open-source, cross-platform (Windows, macOS, and Linux) edition of PowerShell, built to manage heterogeneous environments and hybrid cloud.</span></span>

<span data-ttu-id="eb895-105">在此版本中，我們引進了許多新功能，包括：</span><span class="sxs-lookup"><span data-stu-id="eb895-105">In this release, we're introducing a number of new features, including:</span></span>

- <span data-ttu-id="eb895-106">使用 `ForEach-Object -Parallel` 進行管線平行處理</span><span class="sxs-lookup"><span data-stu-id="eb895-106">Pipeline parallelization with `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="eb895-107">新增運算子：</span><span class="sxs-lookup"><span data-stu-id="eb895-107">New operators:</span></span>
  - <span data-ttu-id="eb895-108">三元運算子：`a ? b : c`</span><span class="sxs-lookup"><span data-stu-id="eb895-108">Ternary operator: `a ? b : c`</span></span>
  - <span data-ttu-id="eb895-109">管線鏈結運算子：`||` 和 `&&`</span><span class="sxs-lookup"><span data-stu-id="eb895-109">Pipeline chain operators: `||` and `&&`</span></span>
  - <span data-ttu-id="eb895-110">Null 條件運算子：`??` 和 `??=`</span><span class="sxs-lookup"><span data-stu-id="eb895-110">Null conditional operators: `??` and `??=`</span></span>
- <span data-ttu-id="eb895-111">簡化的動態錯誤檢視和 `Get-Error` Cmdlet，可讓您更輕鬆地調查錯誤</span><span class="sxs-lookup"><span data-stu-id="eb895-111">A simplified and dynamic error view and `Get-Error` cmdlet for easier investigation of errors</span></span>
- <span data-ttu-id="eb895-112">相容性階層，可讓使用者在隱含的 Windows PowerShell 工作階段中匯入模組</span><span class="sxs-lookup"><span data-stu-id="eb895-112">A compatibility layer that enables users to import modules in an implicit Windows PowerShell session</span></span>
- <span data-ttu-id="eb895-113">自動新版本通知</span><span class="sxs-lookup"><span data-stu-id="eb895-113">Automatic new version notifications</span></span>
- <span data-ttu-id="eb895-114">能夠直接從 PowerShell 7 叫用 DSC 資源 (實驗性)</span><span class="sxs-lookup"><span data-stu-id="eb895-114">The ability to invoke DSC resources directly from PowerShell 7 (experimental)</span></span>

<span data-ttu-id="eb895-115">若要查看完整的功能和修正清單，請參閱[變更記錄](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="eb895-115">To see a full list of features and fixes, see the [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).</span></span>

## <a name="where-can-i-install-powershell"></a><span data-ttu-id="eb895-116">我可以在哪裡安裝 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="eb895-116">Where can I install PowerShell?</span></span>

<span data-ttu-id="eb895-117">PowerShell 7 在 x64 上目前支援下列作業系統，包括：</span><span class="sxs-lookup"><span data-stu-id="eb895-117">PowerShell 7 currently supports the following operating systems on x64, including:</span></span>

- <span data-ttu-id="eb895-118">Windows 8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="eb895-118">Windows 8.1, and 10</span></span>
- <span data-ttu-id="eb895-119">Windows Server 2012、2012 R2、2016 及 2019</span><span class="sxs-lookup"><span data-stu-id="eb895-119">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>
- <span data-ttu-id="eb895-120">macOS 10.13+</span><span class="sxs-lookup"><span data-stu-id="eb895-120">macOS 10.13+</span></span>
- <span data-ttu-id="eb895-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span><span class="sxs-lookup"><span data-stu-id="eb895-121">Red Hat Enterprise Linux (RHEL) / CentOS 7</span></span>
- <span data-ttu-id="eb895-122">Fedora 30+</span><span class="sxs-lookup"><span data-stu-id="eb895-122">Fedora 30+</span></span>
- <span data-ttu-id="eb895-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="eb895-123">Debian 9</span></span>
- <span data-ttu-id="eb895-124">Ubuntu LTS 16.04+</span><span class="sxs-lookup"><span data-stu-id="eb895-124">Ubuntu LTS 16.04+</span></span>
- <span data-ttu-id="eb895-125">Alpine Linux 3.8+</span><span class="sxs-lookup"><span data-stu-id="eb895-125">Alpine Linux 3.8+</span></span>

<span data-ttu-id="eb895-126">此外，PowerShell 7.0 支援 Debian、Ubuntu 和 ARM64 Alpine Linux 的 ARM32 和 ARM64 變體。</span><span class="sxs-lookup"><span data-stu-id="eb895-126">Additionally, PowerShell 7.0 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="eb895-127">請查看適用於您慣用作業系統 [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7)、[macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) 或 [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) 的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="eb895-127">Check the installation instructions for your preferred operating system [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7), or [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).</span></span>

<span data-ttu-id="eb895-128">雖然尚未正式支援，但該社群也會提供適用於 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的套件。</span><span class="sxs-lookup"><span data-stu-id="eb895-128">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-129">Debian 10 和 CentOS 8 目前不支援 WinRM 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="eb895-129">Debian 10 and CentOS 8 currently do not support WinRM remoting.</span></span> <span data-ttu-id="eb895-130">如需設定 SSH 型遠端處理的詳細資訊，請參閱[透過 SSH 的 PowerShell 遠端處理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-130">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).</span></span>

<span data-ttu-id="eb895-131">如需更多有關支援的作業系統和支援週期的最新資訊，請參閱 [PowerShell 支援週期](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-131">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).</span></span>

## <a name="running-powershell-7"></a><span data-ttu-id="eb895-132">執行中的 PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="eb895-132">Running PowerShell 7</span></span>

<span data-ttu-id="eb895-133">PowerShell 7 會分別從 Windows PowerShell 安裝到目錄。</span><span class="sxs-lookup"><span data-stu-id="eb895-133">PowerShell 7 installs to a directory seperately from Windows PowerShell.</span></span>
<span data-ttu-id="eb895-134">如此一來，您就能同時安裝 PowerShell 7 與 Windows PowerShell 5.1。</span><span class="sxs-lookup"><span data-stu-id="eb895-134">This enables you to run PowerShell 7 side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="eb895-135">針對 PowerShell Core 6.x，PowerShell 7 會就地升級並移除 PowerShell Core 6.x。</span><span class="sxs-lookup"><span data-stu-id="eb895-135">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>

- <span data-ttu-id="eb895-136">PowerShell 7 會安裝到 `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="eb895-136">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="eb895-137">系統會在 `$env:PATH` 中新增 `%programfiles%\PowerShell\7` 資料夾</span><span class="sxs-lookup"><span data-stu-id="eb895-137">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>

<span data-ttu-id="eb895-138">PowerShell 7 安裝程式套件會升級舊版的 PowerShell Core 6.x：</span><span class="sxs-lookup"><span data-stu-id="eb895-138">The PowerShell 7 installer package upgrades previous versions of PowerShell Core 6.x:</span></span>

- <span data-ttu-id="eb895-139">Windows 上的 PowerShell Core 6.x：`%programfiles%\PowerShell\6` 已由 `%programfiles%\PowerShell\7` 取代</span><span class="sxs-lookup"><span data-stu-id="eb895-139">PowerShell Core 6.x on Windows: `%programfiles%\PowerShell\6` is replaced by `%programfiles%\PowerShell\7`</span></span>
- <span data-ttu-id="eb895-140">Linux：`/opt/microsoft/powershell/6` 已由 `/opt/microsoft/powershell/7` 取代</span><span class="sxs-lookup"><span data-stu-id="eb895-140">Linux: `/opt/microsoft/powershell/6` is replaced by `/opt/microsoft/powershell/7`</span></span>
- <span data-ttu-id="eb895-141">macOS：`/usr/local/microsoft/powershell/6` 已由 `/usr/local/microsoft/powershell/7` 取代</span><span class="sxs-lookup"><span data-stu-id="eb895-141">macOS: `/usr/local/microsoft/powershell/6` is replaced by `/usr/local/microsoft/powershell/7`</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-142">在 Windows PowerShell 中，啟動 PowerShell 的可執行檔名稱為 `powershell.exe`。</span><span class="sxs-lookup"><span data-stu-id="eb895-142">In Windows PowerShell, the executable to launch PowerShell is named `powershell.exe`.</span></span> <span data-ttu-id="eb895-143">在第 6 版與更新版本中，此可執行檔名稱已變更，以支援並存執行。</span><span class="sxs-lookup"><span data-stu-id="eb895-143">In version 6 and above, the executable name is changed to support side-by-side execution.</span></span> <span data-ttu-id="eb895-144">用以啟動 PowerShell 7 的新可執行檔名稱為 `pwsh.exe`。</span><span class="sxs-lookup"><span data-stu-id="eb895-144">The new executable name to launch PowerShell 7 is `pwsh.exe`.</span></span> <span data-ttu-id="eb895-145">預覽版組建仍繼續保留在 `pwsh-preview` 原地，而不會在 7-preview 目錄卜的 `pwsh`。</span><span class="sxs-lookup"><span data-stu-id="eb895-145">Preview builds remain in-place as `pwsh-preview` instead of `pwsh` under the 7-preview directory.</span></span>

## <a name="improved-backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="eb895-146">已改善與 Windows PowerShell 的回溯相容性</span><span class="sxs-lookup"><span data-stu-id="eb895-146">Improved backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="eb895-147">PowerShell 7.0 會標記要移轉到 .NET Core 3.1，大幅提高與現有的 Windows PowerShell 模組的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="eb895-147">PowerShell 7.0 marks a move a to .NET Core 3.1, enabling significantly more backwards compatibility with existing Windows PowerShell modules.</span></span> <span data-ttu-id="eb895-148">這在 Windows 上包含許多模組，其需要 `Out-GridView` 和 `Show-Command` 之類的 GUI 功能，以及 Windows 隨附的許多角色管理模組。</span><span class="sxs-lookup"><span data-stu-id="eb895-148">This includes many modules on Windows that require GUI functionality like `Out-GridView` and `Show-Command`, as well as many role management modules that ship as part of Windows.</span></span>

<span data-ttu-id="eb895-149">針對 Windows，已將新的切換參數 **UseWindowsPowerShell** 新增至 `Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="eb895-149">For Windows, a new switch parameter **UseWindowsPowerShell** is added to `Import-Module`.</span></span> <span data-ttu-id="eb895-150">此參數會在 PowerShell 7 中建立 Proxy 模組，以使用本機 Windows PowerShell 處理序，隱含地執行該模組中包含的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb895-150">This switch creates a proxy module in PowerShell 7 that uses a local Windows PowerShell process to implicitly run any cmdlets contained in that module.</span></span> <span data-ttu-id="eb895-151">如需詳細資訊，請參閱 [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-151">For more information on [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).</span></span>

<span data-ttu-id="eb895-152">如需哪些 Microsoft 模組使用 PowerShell 7.0 的詳細資訊，請參閱[模組相容性表格](https://aka.ms/PSModuleCompat) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="eb895-152">For more information on which Microsoft modules work with PowerShell 7.0, see the [Module Compatibility Table](https://aka.ms/PSModuleCompat).</span></span>

## <a name="parallel-execution-added-to-foreach-object"></a><span data-ttu-id="eb895-153">已在 ForEach-Object 中新增平行執行</span><span class="sxs-lookup"><span data-stu-id="eb895-153">Parallel execution added to ForEach-Object</span></span>

<span data-ttu-id="eb895-154">`ForEach-Object` Cmdlet (會逐一查看集合中的項目) 現在具備含有新 **Parallel** 參數的內建平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="eb895-154">The `ForEach-Object` cmdlet, which iterates items in a collection, now has built-in parallelism with the new **Parallel** parameter.</span></span>

<span data-ttu-id="eb895-155">根據預設，平行指令碼區塊會使用已啟動平行工作之呼叫者的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="eb895-155">By default, parallel script blocks use the current working directory of the caller that started the parallel tasks.</span></span>

<span data-ttu-id="eb895-156">此範例會從本機 Windows 電腦上的 5 個系統記錄中擷取 50,000 個記錄項目：</span><span class="sxs-lookup"><span data-stu-id="eb895-156">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine:</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

<span data-ttu-id="eb895-157">**Parallel** 參數會針對每個輸入記錄名稱指定平行執行的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="eb895-157">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span>

<span data-ttu-id="eb895-158">新的 **ThrottleLimit** 參數會限制在指定時間平行執行的指令碼區塊數目。</span><span class="sxs-lookup"><span data-stu-id="eb895-158">The new **ThrottleLimit** parameter limits the number of script blocks running in parallel at a given time.</span></span> <span data-ttu-id="eb895-159">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="eb895-159">The default is 5.</span></span>

<span data-ttu-id="eb895-160">在指令碼區塊中，使用 `$_` 變數來代表目前的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="eb895-160">Use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="eb895-161">使用 `$using:` 範圍，將變數參考傳遞至執行中的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="eb895-161">Use the `$using:` scope to pass variable references to the running script block.</span></span>

<span data-ttu-id="eb895-162">如需詳細資訊，請參閱 [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-162">For more information about [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).</span></span>

## <a name="ternary-operator"></a><span data-ttu-id="eb895-163">三元運算子</span><span class="sxs-lookup"><span data-stu-id="eb895-163">Ternary operator</span></span>

<span data-ttu-id="eb895-164">PowerShell 7.0 引進了三元運算子，其行為類似簡化的 `if-else` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb895-164">PowerShell 7.0 introduces a ternary operator which behaves like a simplified `if-else` statement.</span></span>
<span data-ttu-id="eb895-165">PowerShell 的三元運算子會根據 C# 三元運算子語法嚴密地進行模型化：</span><span class="sxs-lookup"><span data-stu-id="eb895-165">PowerShell's ternary operator is closely modeled from the C# ternary operator syntax:</span></span>

```
<condition> ? <if-true> : <if-false>
```

<span data-ttu-id="eb895-166">條件運算式一律會進行評估，並將結果轉換成**布林值**，以判斷下一個要評估的分支：</span><span class="sxs-lookup"><span data-stu-id="eb895-166">The condition-expression is always evaluated and its result converted to a **Boolean** to determine which branch is evaluated next:</span></span>

- <span data-ttu-id="eb895-167">如果 `<condition>` 運算式為 True，就會執行 `<if-true>` 運算式</span><span class="sxs-lookup"><span data-stu-id="eb895-167">The `<if-true>` expression is executed if the `<condition>` expression is true</span></span>
- <span data-ttu-id="eb895-168">如果 `<condition>` 運算式為 False，就會執行 `<if-false>` 運算式</span><span class="sxs-lookup"><span data-stu-id="eb895-168">The `<if-false>` expression is executed if the `<condition>` expression is false</span></span>

<span data-ttu-id="eb895-169">例如：</span><span class="sxs-lookup"><span data-stu-id="eb895-169">For example:</span></span>

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

<span data-ttu-id="eb895-170">在此範例中，如果路徑存在，就會顯示 **Path exists**。</span><span class="sxs-lookup"><span data-stu-id="eb895-170">In this example, if the path exists, then **Path exists** is displayed.</span></span> <span data-ttu-id="eb895-171">如果路徑不存在，則會顯示 **Path not found**。</span><span class="sxs-lookup"><span data-stu-id="eb895-171">If the path does not exist, then **Path not found** is displayed.</span></span>

<span data-ttu-id="eb895-172">如需詳細資訊，請參閱[關於 If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-172">For more information [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).</span></span>

## <a name="pipeline-chain-operators"></a><span data-ttu-id="eb895-173">管線鏈結運算子</span><span class="sxs-lookup"><span data-stu-id="eb895-173">Pipeline chain operators</span></span>

<span data-ttu-id="eb895-174">PowerShell 7 會實作 `&&` 和 `||` 運算子，有條件地鏈結管線。</span><span class="sxs-lookup"><span data-stu-id="eb895-174">PowerShell 7 implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="eb895-175">這些運算子在 PowerShell 中稱為「管線鏈結運算子」，類似於 **Bash** 和 **Zsh** 等殼層中的 AND 和 OR 清單，以及 Windows 命令殼層 (**cmd.exe**) 中的條件式處理符號。</span><span class="sxs-lookup"><span data-stu-id="eb895-175">These operators are known in PowerShell as "pipeline chain operators", and are similar to AND and OR lists in shells like **Bash** and **Zsh**, as well as conditional processing symbols in the Windows Command Shell (**cmd.exe**).</span></span>

<span data-ttu-id="eb895-176">如果左側管線成功，`&&` 運算子就會執行右側管線。</span><span class="sxs-lookup"><span data-stu-id="eb895-176">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="eb895-177">反過來說，如果左側管線失敗，`||` 運算子就會執行右側管線。</span><span class="sxs-lookup"><span data-stu-id="eb895-177">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-178">這些運算子會使用 `$?` 和 `$LASTEXITCODE` 變數來判斷管線是否失敗。</span><span class="sxs-lookup"><span data-stu-id="eb895-178">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="eb895-179">這可讓您將其與原生命令搭配使用，而不只是與 Cmdlet 或函式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="eb895-179">This allows you to use them with native commands and not just with cmdlets or functions.</span></span>

<span data-ttu-id="eb895-180">在這裡，第一個命令成功，且會執行第二個命令：</span><span class="sxs-lookup"><span data-stu-id="eb895-180">Here, the first command succeeds and the second command is executed:</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

<span data-ttu-id="eb895-181">在這裡，第一個命令失敗，且不會執行第二個命令：</span><span class="sxs-lookup"><span data-stu-id="eb895-181">Here, the first command fails, the second is not executed:</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

<span data-ttu-id="eb895-182">在這裡，第一個命令成功，且不會執行第二個命令：</span><span class="sxs-lookup"><span data-stu-id="eb895-182">Here, the first command succeeds, the second command is not executed:</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

<span data-ttu-id="eb895-183">在這裡，第一個命令失敗，因此會執行第二個命令：</span><span class="sxs-lookup"><span data-stu-id="eb895-183">Here, the first command fails, so the second command is executed:</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

<span data-ttu-id="eb895-184">如需詳細資訊，請參閱[關於管線鏈結運算子](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-184">For more information [About Pipeline Chain Operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).</span></span>

## <a name="null-coalescing-assignment-and-conditional-operators"></a><span data-ttu-id="eb895-185">Null 聯合、指派和條件運算子</span><span class="sxs-lookup"><span data-stu-id="eb895-185">Null-coalescing, assignment, and conditional operators</span></span>

<span data-ttu-id="eb895-186">PowerShell 7 包含 Null 聯合運算子 `??`、Null 條件式指派 `??=`，以及 Null 條件式成員存取運算子 `?.` 和 `?[]`。</span><span class="sxs-lookup"><span data-stu-id="eb895-186">PowerShell 7 includes Null coalescing operator `??`, Null conditional assignment `??=`, and Null conditional member access operators `?.` and `?[]`.</span></span>

### <a name="null-coalescing-operator-"></a><span data-ttu-id="eb895-187">Null 聯合運算子 ??</span><span class="sxs-lookup"><span data-stu-id="eb895-187">Null-coalescing Operator ??</span></span>

<span data-ttu-id="eb895-188">Null 聯合運算子 `??` 會傳回其左側運算元的值 (如果不是 Null)。</span><span class="sxs-lookup"><span data-stu-id="eb895-188">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't null.</span></span>
<span data-ttu-id="eb895-189">否則會評估右側運算元，並傳回其結果。</span><span class="sxs-lookup"><span data-stu-id="eb895-189">Otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="eb895-190">如果左側運算元評估為非 Null，則 `??` 運算子不會評估右側運算元。</span><span class="sxs-lookup"><span data-stu-id="eb895-190">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ?? 100
100
```

<span data-ttu-id="eb895-191">在下列範例中，將不會評估右側運算元：</span><span class="sxs-lookup"><span data-stu-id="eb895-191">In the following example, the right-hand operand won't be evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a><span data-ttu-id="eb895-192">Null 條件式指派運算子 ??=</span><span class="sxs-lookup"><span data-stu-id="eb895-192">Null conditional assignment operator ??=</span></span>

<span data-ttu-id="eb895-193">Null 條件式指派運算子 `??=` 只有當左側運算元評估為 Null 時，才會將右側運算元的值指派給左側運算元。</span><span class="sxs-lookup"><span data-stu-id="eb895-193">The null conditional assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to null.</span></span> <span data-ttu-id="eb895-194">如果左側運算元評估為非 Null，則 `??=` 運算子不會評估右側運算元。</span><span class="sxs-lookup"><span data-stu-id="eb895-194">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

```powershell
$x = $null
$x ??= 100
$x
100
```

<span data-ttu-id="eb895-195">下列範例不會評估右側的運算元：</span><span class="sxs-lookup"><span data-stu-id="eb895-195">In the following example, the right-hand operand is not evaluated:</span></span>

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a><span data-ttu-id="eb895-196">Null 條件式成員存取運算子 ?.</span><span class="sxs-lookup"><span data-stu-id="eb895-196">Null conditional member access operators ?.</span></span> <span data-ttu-id="eb895-197">和 ?[] (實驗性)</span><span class="sxs-lookup"><span data-stu-id="eb895-197">and ?[] (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-198">這是名為 **PSNullConditionalOperators** 的實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="eb895-198">This is an experimental feature named **PSNullConditionalOperators**.</span></span> <span data-ttu-id="eb895-199">深入了解[關於實驗性功能](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-199">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="eb895-200">Null 條件運算子只有在其運算元評估為非 Null 時，才會允許對該運算元進行成員存取 `?.` 或元素存取 `?[]`；否則就會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="eb895-200">A null conditional operator permits member access, `?.`, or element access, `?[]`, to its operand only if that operand evaluates to non-null; otherwise, it returns null.</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-201">由於 PowerShell 允許 `?` 作為變數名稱的一部分，因此，使用這些運算子時需要變數名稱的型式規格。</span><span class="sxs-lookup"><span data-stu-id="eb895-201">Since PowerShell allows `?` to be part of the variable name, formal specification of the variable name is required for using these operators.</span></span> <span data-ttu-id="eb895-202">因此，必須在 `${a}` 之類的變數名稱前後，或是當 `?` 為變數名稱 `${a?}` 的一部分時，使用 `{}`。</span><span class="sxs-lookup"><span data-stu-id="eb895-202">So it is required to use `{}` around the variable names like `${a}` or when `?` is part of the variable name `${a?}`.</span></span>

<span data-ttu-id="eb895-203">在下列範例中，會傳回成員屬性 **Status** 的值：</span><span class="sxs-lookup"><span data-stu-id="eb895-203">In the following example, the value of the member property **Status** is returned:</span></span>

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

<span data-ttu-id="eb895-204">下列範例會傳回 Null，而不會嘗試存取成員名稱 **Status**：</span><span class="sxs-lookup"><span data-stu-id="eb895-204">The following example returns null, without trying to access the member name **Status**:</span></span>

```powershell
$service = $Null
${Service}?.status
```

<span data-ttu-id="eb895-205">同樣地，使用 `?[]` 將會傳回元素的值：</span><span class="sxs-lookup"><span data-stu-id="eb895-205">Similarly, using `?[]`, the value of the element is returned:</span></span>

```powershell
$a = 1..10
${a}?[0]
1
```

<span data-ttu-id="eb895-206">此外，當運算元為 Null 時，就不會存取元素，且會傳回 Null：</span><span class="sxs-lookup"><span data-stu-id="eb895-206">And when the operand is null, the element isn't accessed and null is returned:</span></span>

```powershell
$a = $null
${a}?[0]
```

<span data-ttu-id="eb895-207">如需詳細資訊，請參閱[關於運算元](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-207">For more information [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).</span></span>

## <a name="new-view-conciseview-and-cmdlet-get-error"></a><span data-ttu-id="eb895-208">新增 ConciseView 檢視和 Get-Error Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb895-208">New view ConciseView and cmdlet Get-Error</span></span>

<span data-ttu-id="eb895-209">PowerShell 7.0 增強了錯誤訊息的顯示方式，以新的預設檢視 **ConciseView**，改進互動式與指令碼錯誤的可讀性。</span><span class="sxs-lookup"><span data-stu-id="eb895-209">PowerShell 7.0 enhances the display of error messages to improve the readability of interactive and script errors with a new default view **ConciseView**.</span></span> <span data-ttu-id="eb895-210">使用者可以透過喜好設定變數 `$ErrorView` 來選取這些檢視。</span><span class="sxs-lookup"><span data-stu-id="eb895-210">The views are user-selectable through the preference variable `$ErrorView`.</span></span>

<span data-ttu-id="eb895-211">使用 **ConciseView**，如果錯誤不是來自指令碼或剖析器錯誤，則會是單行錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="eb895-211">With **ConciseView**, if an error is not from a script or parser error, then it's a single line error message:</span></span>

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

<span data-ttu-id="eb895-212">如果錯誤發生於指令碼執行期間或是剖析錯誤，PowerShell 就會傳回包含該錯誤的多行錯誤訊息，以及顯示錯誤在該行中所在位置的指標和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="eb895-212">If the error occurs during script execution or is a parsing error, PowerShell returns a multiline error message that contains the error, a pointer and error message showing where the error is in that line.</span></span> <span data-ttu-id="eb895-213">如果終端機不支援 ANSI 色彩逸出序列 (VT100)，則不會顯示色彩。</span><span class="sxs-lookup"><span data-stu-id="eb895-213">If the terminal doesn't support ANSI color escape sequences (VT100), then colors are not displayed.</span></span>

![指令碼的錯誤顯示](./media/What-s-New-in-PowerShell-70/myscript-error.png)

<span data-ttu-id="eb895-215">PowerShell 7 中的預設檢視為 **ConciseView**。</span><span class="sxs-lookup"><span data-stu-id="eb895-215">The default view in PowerShell 7 is **ConciseView**.</span></span> <span data-ttu-id="eb895-216">先前的預設檢視為 **NormalView**。您可以設定喜好設定變數 `$ErrorView` 來選取此檢視。</span><span class="sxs-lookup"><span data-stu-id="eb895-216">The previous default view was **NormalView** and you can select thisby setting the preference variable `$ErrorView`.</span></span>

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> <span data-ttu-id="eb895-217">已將新的屬性 **ErrorAccentColor** 新增至 `$Host.PrivateData`，以支援變更錯誤訊息的輔色。</span><span class="sxs-lookup"><span data-stu-id="eb895-217">A new property **ErrorAccentColor** is added to `$Host.PrivateData` to support changing the accent color of the error message.</span></span>

<span data-ttu-id="eb895-218">當需要時，新的 Cmdlet `Get-Error` 會提供完整錯誤的完整詳細檢視。</span><span class="sxs-lookup"><span data-stu-id="eb895-218">A new cmdlet `Get-Error` provides a complete detailed view of the fully qualified error when desired.</span></span>
<span data-ttu-id="eb895-219">根據預設，此 Cmdlet 會顯示最後發生之錯誤的完整詳細資料，包括內部例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eb895-219">By default the cmdlet displays the full details, including inner exceptions, of the last error that occurred.</span></span>

![顯示自 Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

<span data-ttu-id="eb895-221">`Get-Error` Cmdlet 支援使用內建變數 `$Error` 來從管線輸入。</span><span class="sxs-lookup"><span data-stu-id="eb895-221">The `Get-Error` cmdlet supports input from the pipeline using the built-in variable `$Error`.</span></span>
<span data-ttu-id="eb895-222">`Get-Error` 顯示所有透過管道傳送的錯誤。</span><span class="sxs-lookup"><span data-stu-id="eb895-222">`Get-Error` displays all piped errors.</span></span>

```powershell
$Error | Get-Error
```

<span data-ttu-id="eb895-223">`Get-Error` Cmdlet 支援 **Newest** 參數，可讓您指定希望顯示目前工作階段中的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="eb895-223">The `Get-Error` cmdlet supports the **Newest** parameter, allowing you to specify how many errors from the current session you wish displayed.</span></span>

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

<span data-ttu-id="eb895-224">如需詳細資訊，請參閱 [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-224">For more information about [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).</span></span>

## <a name="new-version-notification"></a><span data-ttu-id="eb895-225">新版本通知</span><span class="sxs-lookup"><span data-stu-id="eb895-225">New version notification</span></span>

<span data-ttu-id="eb895-226">PowerShell 7 會使用更新通知來警示使用者是否有 PowerShell 的更新存在。</span><span class="sxs-lookup"><span data-stu-id="eb895-226">PowerShell 7 uses update notifications to alert users to the existence of updates to PowerShell.</span></span>
<span data-ttu-id="eb895-227">PowerShell 會以每天一次的頻率來查詢線上服務，以判斷是否有較新版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="eb895-227">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-228">更新檢查會在指定的 24 小時期間內的第一個工作階段中發生。</span><span class="sxs-lookup"><span data-stu-id="eb895-228">The update check happens during the first session in a given 24-hour period.</span></span> <span data-ttu-id="eb895-229">基於效能考量，更新檢查會在工作階段開始後的 3 秒開始。</span><span class="sxs-lookup"><span data-stu-id="eb895-229">For performance reasons, the update check starts 3 seconds after the session begins.</span></span> <span data-ttu-id="eb895-230">只有在後續的工作階段開始時，才會顯示通知。</span><span class="sxs-lookup"><span data-stu-id="eb895-230">The notification is shown only on the start of subsequent sessions.</span></span>

<span data-ttu-id="eb895-231">根據預設，PowerShell 會依據其版本/分支，訂閱兩個不同通知通道的其中一個。</span><span class="sxs-lookup"><span data-stu-id="eb895-231">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="eb895-232">支援、正式推出 (GA) 的 PowerShell 版本只會傳回已更新 GA 版本的通知。</span><span class="sxs-lookup"><span data-stu-id="eb895-232">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="eb895-233">預覽和候選版 (RC) 版本會通知預覽、RC 和 GA 版本的更新。</span><span class="sxs-lookup"><span data-stu-id="eb895-233">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="eb895-234">更新通知行為可以使用 `$Env:POWERSHELL_UPDATECHECK` 環境變數來變更。</span><span class="sxs-lookup"><span data-stu-id="eb895-234">The update notification behavior can be changed using the `$Env:POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="eb895-235">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="eb895-235">The following values are supported:</span></span>

- <span data-ttu-id="eb895-236">**Default** 與未定義 `$Env:POWERSHELL_UPDATECHECK` 相同</span><span class="sxs-lookup"><span data-stu-id="eb895-236">**Default** is the same as not defining `$Env:POWERSHELL_UPDATECHECK`</span></span>
  - <span data-ttu-id="eb895-237">GA 版本會通知 GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="eb895-237">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="eb895-238">預覽/RC 版本會通知 GA 和預覽版本的更新</span><span class="sxs-lookup"><span data-stu-id="eb895-238">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="eb895-239">**Off** 會關閉更新通知功能</span><span class="sxs-lookup"><span data-stu-id="eb895-239">**Off** turns off the update notification feature</span></span>
- <span data-ttu-id="eb895-240">**LTS** 只會通知長期維護 (LTS) GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="eb895-240">**LTS** only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-241">環境變數 `$Env:POWERSHELL_UPDATECHECK` 在第一次設定之後才會存在。</span><span class="sxs-lookup"><span data-stu-id="eb895-241">The environment variable `$Env:POWERSHELL_UPDATECHECK` does not exist until it is set for the first time.</span></span>

<span data-ttu-id="eb895-242">僅針對 `LTS` 版本設定版本通知：</span><span class="sxs-lookup"><span data-stu-id="eb895-242">To set the version notification for `LTS` releases only:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

<span data-ttu-id="eb895-243">將版本通知設定為 `Default` 行為：</span><span class="sxs-lookup"><span data-stu-id="eb895-243">To set the version notification to the `Default` behavior:</span></span>

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

<span data-ttu-id="eb895-244">如需詳細資訊，請參閱[關於更新通知](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-244">For more information [About Update Notifications](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).</span></span>

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a><span data-ttu-id="eb895-245">使用 Invoke-DSCResource 新增 DSC 資源支援 (實驗性)</span><span class="sxs-lookup"><span data-stu-id="eb895-245">New DSC Resource support with Invoke-DSCResource (Experimental)</span></span>

> [!NOTE]
> <span data-ttu-id="eb895-246">這是名為 **PSDesiredStateConfiguration.InvokeDscResource** 的實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="eb895-246">This is an experimental feature named **PSDesiredStateConfiguration.InvokeDscResource**.</span></span> <span data-ttu-id="eb895-247">深入了解[關於實驗性功能](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-247">Learn more [About Experimental Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).</span></span>

<span data-ttu-id="eb895-248">`Invoke-DscResource` Cmdlet 會執行指定之 PowerShell Desired State Configuration (DSC) 資源的方法。</span><span class="sxs-lookup"><span data-stu-id="eb895-248">The `Invoke-DscResource` cmdlet runs a method of a specified PowerShell Desired State Configuration (DSC) resource.</span></span>

<span data-ttu-id="eb895-249">此 Cmdlet 會直接叫用 DSC 資源，而不需建立設定文件。</span><span class="sxs-lookup"><span data-stu-id="eb895-249">This cmdlet invokes a DSC resource directly, without creating a configuration document.</span></span> <span data-ttu-id="eb895-250">使用此 Cmdlet，設定管理產品就能使用 DSC 資源來管理 Windows 或 Linux。</span><span class="sxs-lookup"><span data-stu-id="eb895-250">Using this cmdlet, configuration management products can manage Windows or Linux by using DSC resources.</span></span> <span data-ttu-id="eb895-251">當 DSC 引擎在啟用了偵錯的情況下執行時，此 Cmdlet 也會啟用資源的偵錯。</span><span class="sxs-lookup"><span data-stu-id="eb895-251">This cmdlet also enables debugging of resources when the DSC engine is running with debugging enabled.</span></span>

<span data-ttu-id="eb895-252">此命令會叫用名為 **WindowProcess** 資源的 **Set** 方法，並提供強制的 **Path** 和 **Arguments** 屬性來啟動所指定 Windows 處理序。</span><span class="sxs-lookup"><span data-stu-id="eb895-252">This command invokes the **Set** method of a resource named **WindowsProcess** and provides the mandatory **Path** and **Arguments** properties to start the specified Windows process.</span></span>

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

<span data-ttu-id="eb895-253">如需詳細資訊，請參閱 [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7)。</span><span class="sxs-lookup"><span data-stu-id="eb895-253">For more information about [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="eb895-254">中斷性變更和改進</span><span class="sxs-lookup"><span data-stu-id="eb895-254">Breaking Changes and Improvements</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="eb895-255">重大變更</span><span class="sxs-lookup"><span data-stu-id="eb895-255">Breaking Changes</span></span>

- <span data-ttu-id="eb895-256">讓更新通知支援 LTS 和預設通道 (#11132)</span><span class="sxs-lookup"><span data-stu-id="eb895-256">Make update notification support LTS and default channels (#11132)</span></span>
- <span data-ttu-id="eb895-257">更新 Test-Connection，使其運作方式與 Windows PowerShell 中的更相似 (#10697) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-257">Update Test-Connection to work more like the one in Windows PowerShell (#10697) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-258">針對</span><span class="sxs-lookup"><span data-stu-id="eb895-258">Preserve $?</span></span> <span data-ttu-id="eb895-259">ParenExpression、SubExpression 及 ArrayExpression 保留 $? (#11040)</span><span class="sxs-lookup"><span data-stu-id="eb895-259">for ParenExpression, SubExpression and ArrayExpression (#11040)</span></span>
- <span data-ttu-id="eb895-260">將工作目錄設定為 Start-Job 中目前的目錄 (#10920) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-260">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-261">讓 $PSCulture 一律能夠反映工作階段內的文化特性變更 (#10138) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-261">Make $PSCulture consistently reflect in-session culture changes (#10138) (Thanks @iSazonov!)</span></span>

### <a name="engine-updates-and-fixes"></a><span data-ttu-id="eb895-262">引擎更新與修正</span><span class="sxs-lookup"><span data-stu-id="eb895-262">Engine Updates and Fixes</span></span>

- <span data-ttu-id="eb895-263">針對遠端案例之中斷點 API 的改進 (#11312)</span><span class="sxs-lookup"><span data-stu-id="eb895-263">Improvements in breakpoint APIs for remote scenarios (#11312)</span></span>
- <span data-ttu-id="eb895-264">修正會流失到另一個 Runspace 的 PowerShell 類別定義 (#11273)</span><span class="sxs-lookup"><span data-stu-id="eb895-264">Fix PowerShell class definition leaking into another Runspace (#11273)</span></span>
- <span data-ttu-id="eb895-265">修正 7.0.0-Preview1 中新增之 FirstOrDefault 基本類型所導致的格式迴歸 (#11258)</span><span class="sxs-lookup"><span data-stu-id="eb895-265">Fix a regression in formatting caused by the FirstOrDefault primitive added in 7.0.0-Preview1 (#11258)</span></span>
- <span data-ttu-id="eb895-266">要在 PS7 遙測中追蹤的其他 Microsoft 模組 (#10751)</span><span class="sxs-lookup"><span data-stu-id="eb895-266">Additional Microsoft Modules to track in PS7 Telemetry (#10751)</span></span>
- <span data-ttu-id="eb895-267">讓核准的功能成為非實驗性的 (#11303)</span><span class="sxs-lookup"><span data-stu-id="eb895-267">Make approved features non-experimental (#11303)</span></span>
- <span data-ttu-id="eb895-268">更新 ConciseView 以使用 TargetObject (如果適用) (#11075)</span><span class="sxs-lookup"><span data-stu-id="eb895-268">Update ConciseView to use TargetObject if applicable (#11075)</span></span>
- <span data-ttu-id="eb895-269">修正 CompletionCompleters 公用方法中的 NullReferenceException (#11274)</span><span class="sxs-lookup"><span data-stu-id="eb895-269">Fix NullReferenceException in CompletionCompleters public methods (#11274)</span></span>
- <span data-ttu-id="eb895-270">修正非 Windows 平台上的 Apartment 執行緒狀態檢查 (#11301)</span><span class="sxs-lookup"><span data-stu-id="eb895-270">Fix apartment thread state check on non-Windows platforms (#11301)</span></span>
- <span data-ttu-id="eb895-271">更新設定 PSModulePath 以串連處理序和電腦環境變數 (#11276)</span><span class="sxs-lookup"><span data-stu-id="eb895-271">Update setting PSModulePath to concatenate the process and machine environment variables (#11276)</span></span>
- <span data-ttu-id="eb895-272">將 .NET Core 改為 3.1.0 (#11260)</span><span class="sxs-lookup"><span data-stu-id="eb895-272">Bump .NET Core to 3.1.0 (#11260)</span></span>
- <span data-ttu-id="eb895-273">修正 $env:PATH 前面的 $PSHOME 偵測 (#11141)</span><span class="sxs-lookup"><span data-stu-id="eb895-273">Fix detection of $PSHOME in front of $env:PATH (#11141)</span></span>
- <span data-ttu-id="eb895-274">允許 pwsh 繼承 $env:PSModulePath，讓 powershell.exe 能夠正確啟動 (#11057)</span><span class="sxs-lookup"><span data-stu-id="eb895-274">Allow pwsh to inherit $env:PSModulePath and enable powershell.exe to start correctly (#11057)</span></span>
- <span data-ttu-id="eb895-275">移至 .NET Core 3.1 Preview 1 (#10798)</span><span class="sxs-lookup"><span data-stu-id="eb895-275">Move to .NET Core 3.1 preview 1 (#10798)</span></span>
- <span data-ttu-id="eb895-276">在檔案系統提供者中重構重新剖析標記檢查 (#10431) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-276">Refactor reparse tag checks in file system provider (#10431) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-277">在指令碼記錄中使用 0x23CE 字元取代 CR 和新行 (#10616)</span><span class="sxs-lookup"><span data-stu-id="eb895-277">Replace CR and new line with a 0x23CE character in script logging (#10616)</span></span>
- <span data-ttu-id="eb895-278">從 AppDomain.CurrentDomain.ProcessExit 取消註冊事件處理常式，以修正資源流失 (#10626)</span><span class="sxs-lookup"><span data-stu-id="eb895-278">Fix a resource leak by unregistering the event handler from AppDomain.CurrentDomain.ProcessExit (#10626)</span></span>
- <span data-ttu-id="eb895-279">新增對 ActionPreference.Break 的支援，以便在產生偵錯、錯誤、資訊、進度、詳細資訊或警告訊息時中斷偵錯工具 (#8205) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-279">Add support to ActionPreference.Break to break into debugger when Debug, Error, Information, Progress, Verbose or Warning messages are generated (#8205) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-280">能夠在不指定 .CPL 擴充功能的情況下，於 PowerShell Core 內啟動控制台增益集。</span><span class="sxs-lookup"><span data-stu-id="eb895-280">Enable starting control panel add-ins within PowerShell Core without specifying .CPL extension.</span></span> <span data-ttu-id="eb895-281">(#9828)</span><span class="sxs-lookup"><span data-stu-id="eb895-281">(#9828)</span></span>
- <span data-ttu-id="eb895-282">支援 -split 運算子 (#8960) 中有負數 (感謝 @ece-jacob-scott！)</span><span class="sxs-lookup"><span data-stu-id="eb895-282">Support negative numbers in -split operator (#8960) (Thanks @ece-jacob-scott!)</span></span>

### <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="eb895-283">一般 Cmdlet 更新與修正</span><span class="sxs-lookup"><span data-stu-id="eb895-283">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="eb895-284">修正在 UnixStat 實驗性功能中設定檔案變更日期的 Raspbian 問題 (#11313)</span><span class="sxs-lookup"><span data-stu-id="eb895-284">Fix for issue on Raspbian for setting date of file changes in UnixStat Experimental Feature (#11313)</span></span>
- <span data-ttu-id="eb895-285">將 -AsPlainText 新增至 ConvertFrom-SecureString (#11142)</span><span class="sxs-lookup"><span data-stu-id="eb895-285">Add -AsPlainText to ConvertFrom-SecureString (#11142)</span></span>
- <span data-ttu-id="eb895-286">已新增 WinCompat 的 WindowsPS 版本檢查 (#11148)</span><span class="sxs-lookup"><span data-stu-id="eb895-286">Added WindowsPS version check for WinCompat (#11148)</span></span>
- <span data-ttu-id="eb895-287">修正某些 WinCompat 案例中的錯誤報告 (#11259)</span><span class="sxs-lookup"><span data-stu-id="eb895-287">Fix error-reporting in some WinCompat scenarios (#11259)</span></span>
- <span data-ttu-id="eb895-288">新增原生的二進位解析程式 (#11032) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-288">Add native binary resolver (#11032) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-289">更新字元寬度的計算，以正確遵循 CJK 字元 (#11262)</span><span class="sxs-lookup"><span data-stu-id="eb895-289">Update calculation of char width to respect CJK chars correctly (#11262)</span></span>
- <span data-ttu-id="eb895-290">針對 macOS 新增 Unblock-File (#11137)</span><span class="sxs-lookup"><span data-stu-id="eb895-290">Add Unblock-File for macOS (#11137)</span></span>
- <span data-ttu-id="eb895-291">修正 Get-PSCallStack 中的迴歸 (#11210) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-291">Fix regression in Get-PSCallStack (#11210) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-292">移除使用 Job Cmdlet 時自動載入 ScheduledJob 模組的功能 (#11194)</span><span class="sxs-lookup"><span data-stu-id="eb895-292">Remove autoloading of the ScheduledJob module when using Job cmdlets (#11194)</span></span>
- <span data-ttu-id="eb895-293">將 OutputType 新增至 Get-Error Cmdlet，並保留原始類型名稱 (#10856)</span><span class="sxs-lookup"><span data-stu-id="eb895-293">Add OutputType to Get-Error cmdlet and preserve original typenames (#10856)</span></span>
- <span data-ttu-id="eb895-294">修正 SupportsVirtualTerminal 屬性中的 Null 參考 (#11105)</span><span class="sxs-lookup"><span data-stu-id="eb895-294">Fix null reference in SupportsVirtualTerminal property (#11105)</span></span>
- <span data-ttu-id="eb895-295">在 Get-WinEvent 中新增限制檢查 (#10648) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-295">Add limit check in Get-WinEvent (#10648) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-296">修正命令執行階段，如此就不會在 -ErrorVariable 中填入 StopUpstreamCommandsException (#10840)</span><span class="sxs-lookup"><span data-stu-id="eb895-296">Fix command runtime so StopUpstreamCommandsException doesn't get populated in -ErrorVariable (#10840)</span></span>
- <span data-ttu-id="eb895-297">針對原生命令，將輸出編碼設定為 [Console]::OutputEncoding (#10824)</span><span class="sxs-lookup"><span data-stu-id="eb895-297">Set the output encoding to [Console]::OutputEncoding for native commands (#10824)</span></span>
- <span data-ttu-id="eb895-298">支援範例中的多行程式碼區塊 (#10776) (感謝 @Greg-Smulko！)</span><span class="sxs-lookup"><span data-stu-id="eb895-298">Support multi-line code blocks in examples (#10776) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="eb895-299">將 Culture 參數新增至 Select-String Cmdlet (#10943) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-299">Add Culture parameter to Select-String cmdlet (#10943) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-300">以後置反斜線修正 Start-Job 工作目錄路徑 (#11041)</span><span class="sxs-lookup"><span data-stu-id="eb895-300">Fix Start-Job working directory path with trailing backslash (#11041)</span></span>
- <span data-ttu-id="eb895-301">ConvertFrom-Json：預設會將集合解除包裝 (#10861) (感謝 @danstur！)</span><span class="sxs-lookup"><span data-stu-id="eb895-301">ConvertFrom-Json: Unwrap collections by default (#10861) (Thanks @danstur!)</span></span>
- <span data-ttu-id="eb895-302">針對含有 -CaseSensitive 和 -AsHashtable 參數的 Group-Object Cmdlet 使用區分大小寫的雜湊表 (#11030) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-302">Use case-sensitive Hashtable for Group-Object cmdlet with -CaseSensitive and -AsHashtable switches (#11030) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-303">在重建路徑以具備正確的大小寫時，如果列舉檔案失敗，就會處理例外狀況 (#11014)</span><span class="sxs-lookup"><span data-stu-id="eb895-303">Handle exception if enumerating files fails when rebuilding path to have correct casing (#11014)</span></span>
- <span data-ttu-id="eb895-304">修正 ConciseView 以顯示 Activity，而不是 myCommand (#11007)</span><span class="sxs-lookup"><span data-stu-id="eb895-304">Fix ConciseView to show Activity instead of myCommand (#11007)</span></span>
- <span data-ttu-id="eb895-305">允許 Web Cmdlet 忽略 HTTP 錯誤狀態 (#10466) (感謝 @vdamewood！)</span><span class="sxs-lookup"><span data-stu-id="eb895-305">Allow web cmdlets to ignore HTTP error statuses (#10466) (Thanks @vdamewood!)</span></span>
- <span data-ttu-id="eb895-306">修正將多個 CommandInfo 透過管道傳送到 Get-Command (#10929)</span><span class="sxs-lookup"><span data-stu-id="eb895-306">Fix piping of more than one CommandInfo to Get-Command (#10929)</span></span>
- <span data-ttu-id="eb895-307">針對 Windows 重新新增 Get-Counter Cmdlet (#10933)</span><span class="sxs-lookup"><span data-stu-id="eb895-307">Add back Get-Counter cmdlet for Windows (#10933)</span></span>
- <span data-ttu-id="eb895-308">讓 ConvertTo-Json 將 [AutomationNull]::Value 和 [NullString]::Value 視為 $null (#10957)</span><span class="sxs-lookup"><span data-stu-id="eb895-308">Make ConvertTo-Json treat [AutomationNull]::Value and [NullString]::Value as $null (#10957)</span></span>
- <span data-ttu-id="eb895-309">從 ipv6 位址移除括弧以進行 SSH 遠端處理 (#10968)</span><span class="sxs-lookup"><span data-stu-id="eb895-309">Remove brackets from ipv6 address for SSH remoting (#10968)</span></span>
- <span data-ttu-id="eb895-310">修正當傳送至 pwsh 的命令只是空白時所造成的損毀 (#10977)</span><span class="sxs-lookup"><span data-stu-id="eb895-310">Fix crash if command sent to pwsh is just whitespace (#10977)</span></span>
- <span data-ttu-id="eb895-311">已新增跨平台的 Get-Clipboard 和 Set-Clipboard (#10340)</span><span class="sxs-lookup"><span data-stu-id="eb895-311">Added cross-platform Get-Clipboard and Set-Clipboard (#10340)</span></span>
- <span data-ttu-id="eb895-312">修正將系統檔案物件的原始路徑設定為不具額外的後置斜線 (#10959)</span><span class="sxs-lookup"><span data-stu-id="eb895-312">Fix setting original path of filesystem object to not have extra trailing slash (#10959)</span></span>
- <span data-ttu-id="eb895-313">針對 ConvertTo-Json 支援 $null (#10947)</span><span class="sxs-lookup"><span data-stu-id="eb895-313">Support $null for ConvertTo-Json (#10947)</span></span>
- <span data-ttu-id="eb895-314">在 Windows 上重新新增 Out-Printer 命令 (#10906)</span><span class="sxs-lookup"><span data-stu-id="eb895-314">Add back Out-Printer command on Windows (#10906)</span></span>
- <span data-ttu-id="eb895-315">修正含有空格的 Start-Job -WorkingDirectory (#10951)</span><span class="sxs-lookup"><span data-stu-id="eb895-315">Fix Start-Job -WorkingDirectory with whitespace (#10951)</span></span>
- <span data-ttu-id="eb895-316">當 PSConfiguration.cs 中的設定為 Null 時，會傳回預設值 (#10963) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-316">Return default value when getting null for a setting in PSConfiguration.cs (#10963) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-317">將 IO 例外狀況處理為非終止 (#10950)</span><span class="sxs-lookup"><span data-stu-id="eb895-317">Handle IO exception as non-terminating (#10950)</span></span>
- <span data-ttu-id="eb895-318">新增 GraphicalHost 組件，以啟用 Out-GridView、Show-Command 及 Get-Help -ShowWindow (#10899)</span><span class="sxs-lookup"><span data-stu-id="eb895-318">Add GraphicalHost assembly to enable Out-GridView, Show-Command, and Get-Help -ShowWindow (#10899)</span></span>
- <span data-ttu-id="eb895-319">在 Get-HotFix 中透過管線取得 ComputerName (#10852) (感謝 @kvprasoon！)</span><span class="sxs-lookup"><span data-stu-id="eb895-319">Take ComputerName via pipeline in Get-HotFix (#10852) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="eb895-320">修正參數的 Tab 鍵自動完成功能，如此便能顯示可用的一般參數 (#10850)</span><span class="sxs-lookup"><span data-stu-id="eb895-320">Fix tab completion for parameters so that it shows common parameters as available (#10850)</span></span>
- <span data-ttu-id="eb895-321">修正 GetCorrectCasedPath()，以便先檢查是否傳回任何系統檔案項目，然後再呼叫 First() (#10930)</span><span class="sxs-lookup"><span data-stu-id="eb895-321">Fix GetCorrectCasedPath() to first check if any system file entries is returned before calling First() (#10930)</span></span>
- <span data-ttu-id="eb895-322">將工作目錄設定為 Start-Job 中目前的目錄 (#10920) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-322">Set working directory to current directory in Start-Job (#10920) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-323">將 TabExpansion2 變更為不需要 -CursorColumn，並視為 $InputScript.Length (#10849)</span><span class="sxs-lookup"><span data-stu-id="eb895-323">Change TabExpansion2 to not require -CursorColumn and treat as $InputScript.Length (#10849)</span></span>
- <span data-ttu-id="eb895-324">處理主機可能無法傳回螢幕之資料列或資料行的情況 (#10938)</span><span class="sxs-lookup"><span data-stu-id="eb895-324">Handle case where Host may not return Rows or Columns of screen (#10938)</span></span>
- <span data-ttu-id="eb895-325">修正針對不支援之主機的輔色使用方式 (#10937)</span><span class="sxs-lookup"><span data-stu-id="eb895-325">Fix use of accent colors for hosts that don't support them (#10937)</span></span>
- <span data-ttu-id="eb895-326">重新新增 Update-List 命令 (#10922)</span><span class="sxs-lookup"><span data-stu-id="eb895-326">Add back Update-List command (#10922)</span></span>
- <span data-ttu-id="eb895-327">更新適用於 Clear-RecycleBin 的 FWLink (#10925)</span><span class="sxs-lookup"><span data-stu-id="eb895-327">Update FWLink Id for Clear-RecycleBin (#10925)</span></span>
- <span data-ttu-id="eb895-328">在 Tab 鍵自動完成期間，如果無法讀取檔案屬性，即會略過檔案 (#10910)</span><span class="sxs-lookup"><span data-stu-id="eb895-328">During tab completion, skip file if can't read file attributes (#10910)</span></span>
- <span data-ttu-id="eb895-329">針對 Windows 重新新增 Clear-RecycleBin (#10909)</span><span class="sxs-lookup"><span data-stu-id="eb895-329">Add back Clear-RecycleBin for Windows (#10909)</span></span>
- <span data-ttu-id="eb895-330">新增 `$env:__SuppressAnsiEscapeSequences`，以控制是否要在輸出中使用 VT 逸出序列 (#10814)</span><span class="sxs-lookup"><span data-stu-id="eb895-330">Add `$env:__SuppressAnsiEscapeSequences` to control whether to have VT escape sequence in output (#10814)</span></span>
- <span data-ttu-id="eb895-331">新增 -NoEmphasize 參數，以便為 Select-String 輸出上色 (#8963) (感謝 @derek-xia！)</span><span class="sxs-lookup"><span data-stu-id="eb895-331">Add -NoEmphasize parameter to colorize Select-String output (#8963) (Thanks @derek-xia!)</span></span>
- <span data-ttu-id="eb895-332">重新新增 Get-HotFix Cmdlet (#10740)</span><span class="sxs-lookup"><span data-stu-id="eb895-332">Add back Get-HotFix cmdlet (#10740)</span></span>
- <span data-ttu-id="eb895-333">讓 Add-Type 可用於裝載 PowerShell 的應用程式中 (#10587)</span><span class="sxs-lookup"><span data-stu-id="eb895-333">Make Add-Type usable in applications that host PowerShell (#10587)</span></span>
- <span data-ttu-id="eb895-334">在 LanguagePrimitives.IsNullLike() 中使用更有效率的評估順序 (#10781) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-334">Use more effective evaluation order in LanguagePrimitives.IsNullLike() (#10781) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-335">以 Format-Hex 改善混合式集合透過管道傳送的輸入，以及透過管道傳送之輸入串流的處理方式 (#8674) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-335">Improve handling of mixed-collection piped input and piped streams of input in Format-Hex (#8674) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-336">當值不符合預期的類型時，在 SSHConnection 雜湊表中使用類型轉換 (#10720) (感謝 @SeeminglyScience！)</span><span class="sxs-lookup"><span data-stu-id="eb895-336">Use type conversion in SSHConnection hashtables when value doesn't match expected type (#10720) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="eb895-337">修正設定 -TotalCount 時 Get-Content -ReadCount 0 的行為 (#10749) (感謝 @eugenesmlv！)</span><span class="sxs-lookup"><span data-stu-id="eb895-337">Fix Get-Content -ReadCount 0 behavior when -TotalCount is set (#10749) (Thanks @eugenesmlv!)</span></span>
- <span data-ttu-id="eb895-338">重寫 Get-WinEvent 中的拒絕存取錯誤訊息 (#10639) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-338">Reword access denied error message in Get-WinEvent (#10639) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-339">針對列舉或類型條件約束的變數指派啟用 Tab 鍵自動完成 (#10646)</span><span class="sxs-lookup"><span data-stu-id="eb895-339">Enable tab completion for variable assignment that is enum or type constrained (#10646)</span></span>
- <span data-ttu-id="eb895-340">移除未使用且會導致格式問題的 SourceLength 遠端屬性 (#10765)</span><span class="sxs-lookup"><span data-stu-id="eb895-340">Remove unused SourceLength remoting property causing formatting issues (#10765)</span></span>
- <span data-ttu-id="eb895-341">將 -Delimiter 參數新增至 ConvertFrom-StringData (#10665) (感謝 @steviecoaster！)</span><span class="sxs-lookup"><span data-stu-id="eb895-341">Add -Delimiter parameter to ConvertFrom-StringData (#10665) (Thanks @steviecoaster!)</span></span>
- <span data-ttu-id="eb895-342">搭配 SSH 使用 Invoke-Command 時，為 ScriptBlock 新增位置參數 (#10721) (感謝 @machgo！)</span><span class="sxs-lookup"><span data-stu-id="eb895-342">Add positional parameter for ScriptBlock when using Invoke-Command with SSH (#10721) (Thanks @machgo!)</span></span>
- <span data-ttu-id="eb895-343">如果有多行，但沒有 ConciseView 的指令碼名稱，則會顯示行內容資訊 (#10746)</span><span class="sxs-lookup"><span data-stu-id="eb895-343">Show line context information if multiple lines but no script name for ConciseView (#10746)</span></span>
- <span data-ttu-id="eb895-344">將對 \\wsl$\ 路徑的支援新增至檔案系統提供者 (#10674)</span><span class="sxs-lookup"><span data-stu-id="eb895-344">Add support for \\wsl$\ paths to file system provider (#10674)</span></span>
- <span data-ttu-id="eb895-345">在剖析器中針對 TokenKind.QuestionMark 新增遺漏的權杖文字 (#10706)</span><span class="sxs-lookup"><span data-stu-id="eb895-345">Add the missing token text for TokenKind.QuestionMark in parser (#10706)</span></span>
- <span data-ttu-id="eb895-346">將每個 ForEach-Object -Parallel 執行中指令碼的目前工作目錄設定為與呼叫指令碼相同的位置。</span><span class="sxs-lookup"><span data-stu-id="eb895-346">Set current working directory of each ForEach-Object -Parallel running script to the same location as the calling script.</span></span> <span data-ttu-id="eb895-347">(#10672)</span><span class="sxs-lookup"><span data-stu-id="eb895-347">(#10672)</span></span>
- <span data-ttu-id="eb895-348">針對 FindFirstStreamW 和 FindNextStreamW API，使用 Kernell32.dll 取代 api-ms-win-core-file-l1-2-2.dll (#10680) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-348">Replace api-ms-win-core-file-l1-2-2.dll with Kernell32.dll for FindFirstStreamW and FindNextStreamW APIs (#10680) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-349">調整協助將指令碼格式化，以使其更能容忍 StrictMode (#10563)</span><span class="sxs-lookup"><span data-stu-id="eb895-349">Tweak help formatting script to be more StrictMode tolerant (#10563)</span></span>
- <span data-ttu-id="eb895-350">將 -SecurityDescriptorSDDL 參數新增至 New-Service (#10483) (感謝 @kvprasoon！)</span><span class="sxs-lookup"><span data-stu-id="eb895-350">Add -SecurityDescriptorSDDL parameter to New-Service (#10483) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="eb895-351">移除資訊輸出，合併 Test-Connection 中 Ping 的使用方式 (#10478) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-351">Remove informational output, consolidate ping usage in Test-Connection (#10478) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-352">不需存取，即可讀取特定的重新剖析點 (#10662) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-352">Read special reparse points without accessing them (#10662) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-353">將 Clear-Host 輸出指向終端機 (#10681) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-353">Direct Clear-Host output to terminal (#10681) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-354">使用 Format-Table 和 -Property 重新新增新行以利分組 (#10653)</span><span class="sxs-lookup"><span data-stu-id="eb895-354">Add back newline for grouping with Format-Table and -Property (#10653)</span></span>
- <span data-ttu-id="eb895-355">在 Get-Random 上，從 -InputObject 中移除 [ValidateNotNullOrEmpty]，以允許空字串 (#10644)</span><span class="sxs-lookup"><span data-stu-id="eb895-355">Remove [ValidateNotNullOrEmpty] from -InputObject on Get-Random to allow empty string (#10644)</span></span>
- <span data-ttu-id="eb895-356">將建議系統字串距離演算法設定為不區分大小寫 (#10549) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-356">Make suggestion system string distance algorithm case-insensitive (#10549) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-357">修正 ForEach-Object -Parallel 輸入處理中的 Null 參考例外狀況 (#10577)</span><span class="sxs-lookup"><span data-stu-id="eb895-357">Fix null reference exception in ForEach-Object -Parallel input processing (#10577)</span></span>
- <span data-ttu-id="eb895-358">新增 PowerShell Core 群組原則定義 (#10468)</span><span class="sxs-lookup"><span data-stu-id="eb895-358">Add PowerShell Core group policy definitions (#10468)</span></span>
- <span data-ttu-id="eb895-359">更新主控台主機，以支援可組合性案例中所使用的 XTPUSHSGR/XTPOPSGR VT 控制順序。</span><span class="sxs-lookup"><span data-stu-id="eb895-359">Update console host to support XTPUSHSGR/XTPOPSGR VT control sequences that are used in composability scenarios.</span></span> <span data-ttu-id="eb895-360">(#10208)</span><span class="sxs-lookup"><span data-stu-id="eb895-360">(#10208)</span></span>
- <span data-ttu-id="eb895-361">將 WorkingDirectory 參數新增至 Start-Job (#10324) (感謝 @davinci26！)</span><span class="sxs-lookup"><span data-stu-id="eb895-361">Add WorkingDirectory parameter to Start-Job (#10324) (Thanks @davinci26!)</span></span>
- <span data-ttu-id="eb895-362">移除導致中斷點變更錯誤複寫到主機 Runspace 偵錯工具的事件處理常式 (#10503) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-362">Remove the event handler that was causing breakpoint changes to be erroneously replicated to the host runspace debugger (#10503) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-363">在 Microsoft.PowerShell.Commands.NativeMethods P/Invoke API 中，使用 Kernell32.dll 取代 api-ms-win-core-job-12-1-0.dll (#10417) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-363">Replace api-ms-win-core-job-12-1-0.dll with Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-364">修正變數指派的 New-Service 和 -OutVariable 中的錯誤輸出 (#10444) (感謝 @kvprasoon！)</span><span class="sxs-lookup"><span data-stu-id="eb895-364">Fix wrong output for New-Service in variable assignment and -OutVariable (#10444) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="eb895-365">修正結束代碼、命令列參數和含有空格之路徑的全域工具問題 (#10461)</span><span class="sxs-lookup"><span data-stu-id="eb895-365">Fix global tool issues around exit code, command line parameters and path with spaces (#10461)</span></span>
- <span data-ttu-id="eb895-366">將遞迴修正到 OneDrive - 變更 FindFirstFileEx() 以使用 SafeFindHandle 類型 (#10405)</span><span class="sxs-lookup"><span data-stu-id="eb895-366">Fix recursion into OneDrive - change FindFirstFileEx() to use SafeFindHandle type (#10405)</span></span>
- <span data-ttu-id="eb895-367">如果 NVDA 螢幕助讀程式為作用中，即會略過在 Windows 上自動載入 PSReadLine (#10385)</span><span class="sxs-lookup"><span data-stu-id="eb895-367">Skip auto-loading PSReadLine on Windows if the NVDA screen reader is active (#10385)</span></span>
- <span data-ttu-id="eb895-368">將使用 PowerShell 建置的模組版本增加至 7.0.0.0 (#10356)</span><span class="sxs-lookup"><span data-stu-id="eb895-368">Increase built-with-PowerShell module versions to 7.0.0.0 (#10356)</span></span>
- <span data-ttu-id="eb895-369">新增如果已經存在相同名稱的類型，即會在 Add-Type 中擲回錯誤 (#9609) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-369">Add throwing an error in Add-Type if a type with the same name already exists (#9609) (Thanks @iSazonov!)</span></span>

### <a name="performance"></a><span data-ttu-id="eb895-370">效能</span><span class="sxs-lookup"><span data-stu-id="eb895-370">Performance</span></span>

- <span data-ttu-id="eb895-371">避免在 Parser.SaveError 中使用 Closure (#11006)</span><span class="sxs-lookup"><span data-stu-id="eb895-371">Avoid using closure in Parser.SaveError (#11006)</span></span>
- <span data-ttu-id="eb895-372">改善在建立新 Regex 執行個體時的快取 (#10657) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-372">Improve the caching when creating new Regex instances (#10657) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-373">改善從 types.ps1xml、typesV3.ps1xml 及 GetEvent.types.ps1xml 處理 PowerShell 內建類型資料 (#10898)</span><span class="sxs-lookup"><span data-stu-id="eb895-373">Improve processing of the PowerShell built-in type data from types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml (#10898)</span></span>
- <span data-ttu-id="eb895-374">更新 PSConfiguration.ReadValueFromFile，使其變得更快速且記憶體更有效率 (#10839)</span><span class="sxs-lookup"><span data-stu-id="eb895-374">Update PSConfiguration.ReadValueFromFile to make it faster and more memory efficient (#10839)</span></span>
- <span data-ttu-id="eb895-375">新增適用於 Runspace 初始化的次要效能改善 (#10569) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-375">Add minor performance improvements for runspace initialization (#10569) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-376">讓 ForEach-Object 能夠更快速地適用於其常用案例 (#10454)，並使用多個 Runspace 來修正 ForEach-Object -Parallel 效能問題 (#10455)</span><span class="sxs-lookup"><span data-stu-id="eb895-376">Make ForEach-Object faster for its commonly used scenarios (#10454) and fix ForEach-Object -Parallel performance problem with many runspaces (#10455)</span></span>

### <a name="code-cleanup"></a><span data-ttu-id="eb895-377">程式碼清除</span><span class="sxs-lookup"><span data-stu-id="eb895-377">Code Cleanup</span></span>

- <span data-ttu-id="eb895-378">變更註解和元素文字以符合 Microsoft 標準 (#11304)</span><span class="sxs-lookup"><span data-stu-id="eb895-378">Change comment and element text to meet Microsoft standards (#11304)</span></span>
- <span data-ttu-id="eb895-379">清除 Compiler.cs 中的樣式問題 (#10368) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-379">Cleanup style issues in Compiler.cs (#10368) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-380">針對 CommaDelimitedStringCollection 移除未使用的類型轉換器 (#11000) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-380">Remove the unused type converter for CommaDelimitedStringCollection (#11000) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-381">清除 InitialSessionState.cs 中的樣式 (#10865) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-381">Cleanup style in InitialSessionState.cs (#10865) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-382">針對 PSSession 類別進行程式碼清除 (#11001)</span><span class="sxs-lookup"><span data-stu-id="eb895-382">Code clean up for PSSession class (#11001)</span></span>
- <span data-ttu-id="eb895-383">移除無法運作的「當 Get-Help 第一次執行時，從 Get-Help 中執行 Update-Help」功能 (#10974)</span><span class="sxs-lookup"><span data-stu-id="eb895-383">Remove the not-working 'run Update-Help from Get-Help when Get-Help runs for the first time' feature (#10974)</span></span>
- <span data-ttu-id="eb895-384">修正樣式問題 (#10998) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-384">Fix style issues (#10998) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-385">清除：使用內建類型別名 (#10882) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-385">Cleanup: use the built-in type alias (#10882) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-386">移除未使用的設定索引鍵 ConsolePrompting，並避免在查詢 ExecutionPolicy 設定時建立不必要的字串 (#10985)</span><span class="sxs-lookup"><span data-stu-id="eb895-386">Remove the unused setting key ConsolePrompting and avoid unnecessary string creation when querying ExecutionPolicy setting (#10985)</span></span>
- <span data-ttu-id="eb895-387">停用每日組建的更新通知檢查 (#10903) (感謝 @bergmeister！)</span><span class="sxs-lookup"><span data-stu-id="eb895-387">Disable update notification check for daily builds (#10903) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="eb895-388">恢復 #10338 中遺失的偵錯 API (#10808)</span><span class="sxs-lookup"><span data-stu-id="eb895-388">Reinstate debugging API lost in #10338 (#10808)</span></span>
- <span data-ttu-id="eb895-389">移除不再使用的 WorkflowJobSourceAdapter 參考 (#10326) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-389">Remove WorkflowJobSourceAdapter reference that is no longer used (#10326) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-390">藉由修正 PreserveSig 屬性來清除捷徑清單程式碼中的 COM 介面 (#9899) (感謝 @weltkante！)</span><span class="sxs-lookup"><span data-stu-id="eb895-390">Cleanup COM interfaces in jump list code by fixing PreserveSig attributes (#9899) (Thanks @weltkante!)</span></span>
- <span data-ttu-id="eb895-391">新增註解，以描述為什麼 -ia 不是 -InformationAction 一般參數的別名 (#10703) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-391">Add a comment describing why -ia is not the alias for -InformationAction common parameter (#10703) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-392">將 InvokeCommandCmdlet.cs 重新命名為 InvokeExpressionCommand.cs (#10659) (感謝 @kilasuit！)</span><span class="sxs-lookup"><span data-stu-id="eb895-392">Rename InvokeCommandCmdlet.cs to InvokeExpressionCommand.cs (#10659) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="eb895-393">新增與更新通知相關的次要程式碼清除 (#10698)</span><span class="sxs-lookup"><span data-stu-id="eb895-393">Add minor code cleanups related to update notifications (#10698)</span></span>
- <span data-ttu-id="eb895-394">從遠端安裝指令碼移除即將淘汰的工作流程邏輯 (#10320) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-394">Remove deprecated workflow logic from the remoting setup scripts (#10320) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-395">更新說明格式以使用適當的大小寫 (#10678) (感謝 @tnieto88！)</span><span class="sxs-lookup"><span data-stu-id="eb895-395">Update help format to use proper case (#10678) (Thanks @tnieto88!)</span></span>
- <span data-ttu-id="eb895-396">清除認可中過去一個月發生的 CodeFactor 樣式問題 (#10591) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-396">Clean up CodeFactor style issues coming in commits for the last month (#10591) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-397">修正 PSTernaryOperator 實驗性功能描述中的打字錯誤 (#10586) (感謝 @bergmeister！)</span><span class="sxs-lookup"><span data-stu-id="eb895-397">Fix typo in description of PSTernaryOperator experimental feature (#10586) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="eb895-398">將 ActionPreference.Suspend 列舉值轉換為不支援的保留狀態，並在喜好設定變數中移除使用 ActionPreference.Ignore 的限制 (#10317) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-398">Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-399">使用 List\<T> 取代 ArrayList，以取得更容易閱讀且可靠的程式碼，而不需變更功能 (#10333) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-399">Replace ArrayList with List\<T> to get more readable and reliable code without changing functionality (#10333) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-400">對 TestConnectionCommand 進行程式碼樣式修正 (#10439) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-400">Make code style fixes to TestConnectionCommand (#10439) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-401">清除 AutomationEngine，並移除額外的 SetSessionStateDrive 方法呼叫 (#10416) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-401">Cleanup AutomationEngine and remove extra SetSessionStateDrive method call (#10416) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-402">針對 ConvertTo-Csv 和 ConvertFrom-Csv，將預設的 ParameterSetName 再次重新命名為 Delimiter (#10425)</span><span class="sxs-lookup"><span data-stu-id="eb895-402">Rename default ParameterSetName back to Delimiter for ConvertTo-Csv and ConvertFrom-Csv (#10425)</span></span>

### <a name="tools"></a><span data-ttu-id="eb895-403">工具</span><span class="sxs-lookup"><span data-stu-id="eb895-403">Tools</span></span>

- <span data-ttu-id="eb895-404">新增 SDKToUse 屬性的預設設定，使其建置於 VS 中 (#11085)</span><span class="sxs-lookup"><span data-stu-id="eb895-404">Add default setting for the SDKToUse property so that it builds in VS (#11085)</span></span>
- <span data-ttu-id="eb895-405">Install-Powershell.ps1：新增參數以使用 MSI 安裝 (#10921) (感謝 @MJECloud！)</span><span class="sxs-lookup"><span data-stu-id="eb895-405">Install-Powershell.ps1: Add parameter to use MSI installation (#10921) (Thanks @MJECloud!)</span></span>
- <span data-ttu-id="eb895-406">新增 install-powershell.ps1 的基本範例 (#10914) (感謝 @kilasuit！)</span><span class="sxs-lookup"><span data-stu-id="eb895-406">Add basic examples for install-powershell.ps1 (#10914) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="eb895-407">讓 Install-PowerShellRemoting.ps1 處理 PowerShellHome 參數中的空字串 (#10526) (感謝 @Orca88！)</span><span class="sxs-lookup"><span data-stu-id="eb895-407">Make Install-PowerShellRemoting.ps1 handle empty string in PowerShellHome parameter (#10526) (Thanks @Orca88!)</span></span>
- <span data-ttu-id="eb895-408">在 install-powershell.sh 中，從 /etc/lsb-release 切換到 /etc/os-release (#10773) (感謝 @Himura2la！)</span><span class="sxs-lookup"><span data-stu-id="eb895-408">Switch from /etc/lsb-release to /etc/os-release in install-powershell.sh (#10773) (Thanks @Himura2la!)</span></span>
- <span data-ttu-id="eb895-409">在 Windows 上的每日版本中檢查 pwsh.exe 和 pwsh (#10738) (感謝 @centreboard！)</span><span class="sxs-lookup"><span data-stu-id="eb895-409">Check pwsh.exe and pwsh in daily version on Windows (#10738) (Thanks @centreboard!)</span></span>
- <span data-ttu-id="eb895-410">移除 installpsh-osx.sh 中不必要的點選 (#10752)</span><span class="sxs-lookup"><span data-stu-id="eb895-410">Remove unneeded tap in installpsh-osx.sh (#10752)</span></span>
- <span data-ttu-id="eb895-411">更新 install-powershell.ps1，以檢查已經安裝的每日組建 (#10489)</span><span class="sxs-lookup"><span data-stu-id="eb895-411">Update install-powershell.ps1 to check for already installed daily build (#10489)</span></span>

### <a name="tests"></a><span data-ttu-id="eb895-412">測試</span><span class="sxs-lookup"><span data-stu-id="eb895-412">Tests</span></span>

- <span data-ttu-id="eb895-413">讓不可靠的 DSC 測試暫止 (#11131)</span><span class="sxs-lookup"><span data-stu-id="eb895-413">Make unreliable DSC test pending (#11131)</span></span>
- <span data-ttu-id="eb895-414">修正字串資料測試，以正確驗證雜湊表的索引鍵 (#10810)</span><span class="sxs-lookup"><span data-stu-id="eb895-414">Fix stringdata test to correctly validate keys of hashtables (#10810)</span></span>
- <span data-ttu-id="eb895-415">卸載測試模組 (#11061) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-415">Unload test modules (#11061) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-416">增加測試 URL 的重試間隔時間 (#11015)</span><span class="sxs-lookup"><span data-stu-id="eb895-416">Increase time between retries of testing URL (#11015)</span></span>
- <span data-ttu-id="eb895-417">更新測試以正確描述測試動作。</span><span class="sxs-lookup"><span data-stu-id="eb895-417">Update tests to accurately describe test actions.</span></span> <span data-ttu-id="eb895-418">(#10928) (感謝 @romero126！)</span><span class="sxs-lookup"><span data-stu-id="eb895-418">(#10928) (Thanks @romero126!)</span></span>
- <span data-ttu-id="eb895-419">暫時略過不穩定的測試 TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span><span class="sxs-lookup"><span data-stu-id="eb895-419">Temporary skip the flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)</span></span>
- <span data-ttu-id="eb895-420">讓事件處理常式流失測試呈現穩定狀態 (#10790)</span><span class="sxs-lookup"><span data-stu-id="eb895-420">Make the event handler leaking test stable (#10790)</span></span>
- <span data-ttu-id="eb895-421">在 CI YAML 中同步處理大小寫 (#10767) (感謝 @RDIL！)</span><span class="sxs-lookup"><span data-stu-id="eb895-421">Sync capitalization in CI YAML (#10767) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="eb895-422">新增用於事件處理常式流失修正的測試 (#10768)</span><span class="sxs-lookup"><span data-stu-id="eb895-422">Add test for the event handler leaking fix (#10768)</span></span>
- <span data-ttu-id="eb895-423">新增 Get-ChildItem 測試 (#10507) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-423">Add Get-ChildItem test (#10507) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-424">針對要切換到參數的測試，取代模擬兩可的語言，以確保正確性 (#10666) (感謝 @romero126！)</span><span class="sxs-lookup"><span data-stu-id="eb895-424">Replace ambiguous language for tests from switch to parameter for accuracy (#10666) (Thanks @romero126!)</span></span>
- <span data-ttu-id="eb895-425">將實驗性檢查新增至 ForEach-Object -Parallel 測試 (#10354) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="eb895-425">Add experimental check to ForEach-Object -Parallel tests (#10354) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="eb895-426">更新 Alpine 驗證的測試 (#10428)</span><span class="sxs-lookup"><span data-stu-id="eb895-426">Update tests for Alpine validation (#10428)</span></span>

### <a name="build-and-package-improvements"></a><span data-ttu-id="eb895-427">組建和套件的改善</span><span class="sxs-lookup"><span data-stu-id="eb895-427">Build and Package Improvements</span></span>

- <span data-ttu-id="eb895-428">修正協調套件組建的 Nuget 套件簽署 (#11316)</span><span class="sxs-lookup"><span data-stu-id="eb895-428">Fix Nuget package signing for Coordinated Package build (#11316)</span></span>
- <span data-ttu-id="eb895-429">更新 PowerShell 資源庫和 NuGet 的相依性 (#11323)</span><span class="sxs-lookup"><span data-stu-id="eb895-429">Update dependencies from PowerShell Gallery and NuGet (#11323)</span></span>
- <span data-ttu-id="eb895-430">將 Microsoft.ApplicationInsights 從 2.11.0 改成 2.12.0 (#11305)</span><span class="sxs-lookup"><span data-stu-id="eb895-430">Bump Microsoft.ApplicationInsights from 2.11.0 to 2.12.0 (#11305)</span></span>
- <span data-ttu-id="eb895-431">將 Microsoft.CodeAnalysis.CSharp 從 3.3.1 改成 3.4.0 (#11265)</span><span class="sxs-lookup"><span data-stu-id="eb895-431">Bump Microsoft.CodeAnalysis.CSharp from 3.3.1 to 3.4.0 (#11265)</span></span>
- <span data-ttu-id="eb895-432">更新 Debian 10 和 11 的套件 (#11236)</span><span class="sxs-lookup"><span data-stu-id="eb895-432">Updates packages for Debian 10 and 11 (#11236)</span></span>
- <span data-ttu-id="eb895-433">只在 RC 之前啟用實驗性功能 (#11162)</span><span class="sxs-lookup"><span data-stu-id="eb895-433">Only enable experimental features prior to RC (#11162)</span></span>
- <span data-ttu-id="eb895-434">更新 macOS 最小版本 (#11163)</span><span class="sxs-lookup"><span data-stu-id="eb895-434">Update macOS minimum version (#11163)</span></span>
- <span data-ttu-id="eb895-435">將 NJsonSchema 從 10.0.27 改成 10.0.28 (#11170)</span><span class="sxs-lookup"><span data-stu-id="eb895-435">Bump NJsonSchema from 10.0.27 to 10.0.28 (#11170)</span></span>
- <span data-ttu-id="eb895-436">正在針對 Preview.5 更新 README.md 中的連結和 metadata.json (#10854)</span><span class="sxs-lookup"><span data-stu-id="eb895-436">Updating links in README.md and metadata.json for Preview.5 (#10854)</span></span>
- <span data-ttu-id="eb895-437">選取用於進行 PowerShell 所擁有之合規性測試的檔案 (#10837)</span><span class="sxs-lookup"><span data-stu-id="eb895-437">Select the files for compliance tests which are owned by PowerShell (#10837)</span></span>
- <span data-ttu-id="eb895-438">允許建置 win7x86 msix 套件。</span><span class="sxs-lookup"><span data-stu-id="eb895-438">Allow win7x86 msix package to build.</span></span> <span data-ttu-id="eb895-439">(內部 10515)</span><span class="sxs-lookup"><span data-stu-id="eb895-439">(Internal 10515)</span></span>
- <span data-ttu-id="eb895-440">允許將語意版本傳遞至 NormalizeVersion 函式 (#11087)</span><span class="sxs-lookup"><span data-stu-id="eb895-440">Allow semantic versions to be passed to NormalizeVersion function (#11087)</span></span>
- <span data-ttu-id="eb895-441">將 .NET Core Framework 改成 3.1-preview.3 (#11079)</span><span class="sxs-lookup"><span data-stu-id="eb895-441">Bump .NET core framework to 3.1-preview.3 (#11079)</span></span>
- <span data-ttu-id="eb895-442">在 /src/Modules 中，將 PSReadLine 從 2.0.0-beta5 改成 2.0.0-beta6 (#11078)</span><span class="sxs-lookup"><span data-stu-id="eb895-442">Bump PSReadLine from 2.0.0-beta5 to 2.0.0-beta6 in /src/Modules (#11078)</span></span>
- <span data-ttu-id="eb895-443">將 Newtonsoft.Json 從 12.0.2 改成 12.0.3 (#11037) (#11038)</span><span class="sxs-lookup"><span data-stu-id="eb895-443">Bump Newtonsoft.Json from 12.0.2 to 12.0.3 (#11037) (#11038)</span></span>
- <span data-ttu-id="eb895-444">新增 Debian 10、11 和 CentOS 8 套件 (#11028)</span><span class="sxs-lookup"><span data-stu-id="eb895-444">Add Debian 10, 11 and CentOS 8 packages (#11028)</span></span>
- <span data-ttu-id="eb895-445">使用 ReleaseDate 欄位上傳 Build-Info Json 檔案 (#10986)</span><span class="sxs-lookup"><span data-stu-id="eb895-445">Upload Build-Info Json file with the ReleaseDate field (#10986)</span></span>
- <span data-ttu-id="eb895-446">將 .NET Core Framework 改成 3.1-preview.2 (#10993)</span><span class="sxs-lookup"><span data-stu-id="eb895-446">Bump .NET core framework to 3.1-preview.2 (#10993)</span></span>
- <span data-ttu-id="eb895-447">啟用 x86 MSIX 套件的組建 (#10934)</span><span class="sxs-lookup"><span data-stu-id="eb895-447">Enable build of x86 MSIX package (#10934)</span></span>
- <span data-ttu-id="eb895-448">更新 build.psm1 中的 dotnet SDK 安裝指令碼 URL (#10927)</span><span class="sxs-lookup"><span data-stu-id="eb895-448">Update the dotnet SDK install script URL in build.psm1 (#10927)</span></span>
- <span data-ttu-id="eb895-449">將 Markdig.Signed 從 0.17.1 改成 0.18.0 (#10887)</span><span class="sxs-lookup"><span data-stu-id="eb895-449">Bump Markdig.Signed from 0.17.1 to 0.18.0 (#10887)</span></span>
- <span data-ttu-id="eb895-450">將 ThreadJob 從 2.0.1 改成 2.0.2 (#10886)</span><span class="sxs-lookup"><span data-stu-id="eb895-450">Bump ThreadJob from 2.0.1 to 2.0.2 (#10886)</span></span>
- <span data-ttu-id="eb895-451">更新 AppX 資訊清單和封裝模組以符合 MS Store 需求 (#10878)</span><span class="sxs-lookup"><span data-stu-id="eb895-451">Update AppX Manifest and Packaging module to conform to MS Store requirements (#10878)</span></span>
- <span data-ttu-id="eb895-452">將 PowerShell SDK 的套件參考更新為 preview.5 (內部 10295)</span><span class="sxs-lookup"><span data-stu-id="eb895-452">Update package reference for PowerShell SDK to preview.5 (Internal 10295)</span></span>
- <span data-ttu-id="eb895-453">更新 ThirdPartyNotices.txt (#10834)</span><span class="sxs-lookup"><span data-stu-id="eb895-453">Update ThirdPartyNotices.txt (#10834)</span></span>
- <span data-ttu-id="eb895-454">將 Microsoft.PowerShell.Native 改成 7.0.0-preview.3 (#10826)</span><span class="sxs-lookup"><span data-stu-id="eb895-454">Bump Microsoft.PowerShell.Native to 7.0.0-preview.3 (#10826)</span></span>
- <span data-ttu-id="eb895-455">將 Microsoft.ApplicationInsights 從 2.10.0 改成 2.11.0 (#10608)</span><span class="sxs-lookup"><span data-stu-id="eb895-455">Bump Microsoft.ApplicationInsights from 2.10.0 to 2.11.0 (#10608)</span></span>
- <span data-ttu-id="eb895-456">將 NJsonSchema 從 10.0.24 改成 10.0.27 (#10756)</span><span class="sxs-lookup"><span data-stu-id="eb895-456">Bump NJsonSchema from 10.0.24 to 10.0.27 (#10756)</span></span>
- <span data-ttu-id="eb895-457">將 MacPorts 支援新增至建置系統 (#10736) (感謝 @Lucius-Q-User！)</span><span class="sxs-lookup"><span data-stu-id="eb895-457">Add MacPorts support to the build system (#10736) (Thanks @Lucius-Q-User!)</span></span>
- <span data-ttu-id="eb895-458">將 PackageManagement 從 1.4.4 改成 1.4.5 (#10728)</span><span class="sxs-lookup"><span data-stu-id="eb895-458">Bump PackageManagement from 1.4.4 to 1.4.5 (#10728)</span></span>
- <span data-ttu-id="eb895-459">將 NJsonSchema 從 10.0.23 改成 10.0.24 (#10635)</span><span class="sxs-lookup"><span data-stu-id="eb895-459">Bump NJsonSchema from 10.0.23 to 10.0.24 (#10635)</span></span>
- <span data-ttu-id="eb895-460">新增環境變數以區別 MSI 中的用戶端/伺服器遙測 (#10612)</span><span class="sxs-lookup"><span data-stu-id="eb895-460">Add environment variable to differentiate client/server telemetry in MSI (#10612)</span></span>
- <span data-ttu-id="eb895-461">將 PSDesiredStateConfiguration 從 2.0.3 改成 2.0.4 (#10603)</span><span class="sxs-lookup"><span data-stu-id="eb895-461">Bump PSDesiredStateConfiguration from 2.0.3 to 2.0.4 (#10603)</span></span>
- <span data-ttu-id="eb895-462">將 Microsoft.CodeAnalysis.CSharp 從 3.2.1 改成 3.3.1 (#10607)</span><span class="sxs-lookup"><span data-stu-id="eb895-462">Bump Microsoft.CodeAnalysis.CSharp from 3.2.1 to 3.3.1 (#10607)</span></span>
- <span data-ttu-id="eb895-463">更新為 .Net Core 3.0 RTM (#10604) (感謝 @bergmeister！)</span><span class="sxs-lookup"><span data-stu-id="eb895-463">Update to .Net Core 3.0 RTM (#10604) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="eb895-464">更新 MSIX 封裝，使版本符合 Windows 市集需求 (#10588)</span><span class="sxs-lookup"><span data-stu-id="eb895-464">Update MSIX packaging so the version to Windows Store requirements (#10588)</span></span>
- <span data-ttu-id="eb895-465">將 PowerShellGet 版本從 2.2 改成 2.2.1 (#10382)</span><span class="sxs-lookup"><span data-stu-id="eb895-465">Bump PowerShellGet version from 2.2 to 2.2.1 (#10382)</span></span>
- <span data-ttu-id="eb895-466">將 PackageManagement 版本從 1.4.3 改成 1.4.4 (#10383)</span><span class="sxs-lookup"><span data-stu-id="eb895-466">Bump PackageManagement version from 1.4.3 to 1.4.4 (#10383)</span></span>
- <span data-ttu-id="eb895-467">針對 7.0.0-preview.4 更新 README.md 和 metadata.json (內部 10011)</span><span class="sxs-lookup"><span data-stu-id="eb895-467">Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)</span></span>
- <span data-ttu-id="eb895-468">將 .Net Core 3.0 版從 Preview 9 升級為 RC1 (#10552) (感謝 @bergmeister！)</span><span class="sxs-lookup"><span data-stu-id="eb895-468">Upgrade .Net Core 3.0 version from Preview 9 to RC1 (#10552) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="eb895-469">修正 ExperimentalFeature 清單產生 (內部 9996)</span><span class="sxs-lookup"><span data-stu-id="eb895-469">Fix ExperimentalFeature list generation (Internal 9996)</span></span>
- <span data-ttu-id="eb895-470">將 PSReadLine 版本從 2.0.0-beta4 改成 2.0.0-beta5 (#10536)</span><span class="sxs-lookup"><span data-stu-id="eb895-470">Bump PSReadLine version from 2.0.0-beta4 to 2.0.0-beta5 (#10536)</span></span>
- <span data-ttu-id="eb895-471">修正發行組建指令碼以設定發行標籤</span><span class="sxs-lookup"><span data-stu-id="eb895-471">Fix release build script to set release tag</span></span>
- <span data-ttu-id="eb895-472">將 Microsoft.PowerShell.Native 的版本更新為 7.0.0-preview.2 (#10519)</span><span class="sxs-lookup"><span data-stu-id="eb895-472">Update version of Microsoft.PowerShell.Native to 7.0.0-preview.2 (#10519)</span></span>
- <span data-ttu-id="eb895-473">升級為 Netcoreapp3.0 preview9 (#10484) (感謝 @bergmeister！)</span><span class="sxs-lookup"><span data-stu-id="eb895-473">Upgrade to Netcoreapp3.0 preview9 (#10484) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="eb895-474">確定每日協調組建，了解其為每日組建 (#10464)</span><span class="sxs-lookup"><span data-stu-id="eb895-474">Make sure the daily coordinated build, knows it is a daily build (#10464)</span></span>
- <span data-ttu-id="eb895-475">更新合併的套件組建以發行每日組建 (#10449)</span><span class="sxs-lookup"><span data-stu-id="eb895-475">Update the combined package build to release the daily builds (#10449)</span></span>
- <span data-ttu-id="eb895-476">移除 AppVeyor 參考 (#10445) (感謝 @RDIL！)</span><span class="sxs-lookup"><span data-stu-id="eb895-476">Remove appveyor reference (#10445) (Thanks @RDIL!)</span></span>
- <span data-ttu-id="eb895-477">將 NJsonSchema 版本從 10.0.22 改成 10.0.23 (#10421)</span><span class="sxs-lookup"><span data-stu-id="eb895-477">Bump NJsonSchema version from 10.0.22 to 10.0.23 (#10421)</span></span>
- <span data-ttu-id="eb895-478">移除 linux-x64 組建資料夾的刪除功能，因為某些適用於 Alpine 的相依性需要該資料夾 (#10407)</span><span class="sxs-lookup"><span data-stu-id="eb895-478">Remove the deletion of linux-x64 build folder because some dependencies for Alpine need it (#10407)</span></span>

### <a name="documentation-and-help-content"></a><span data-ttu-id="eb895-479">文件和說明內容</span><span class="sxs-lookup"><span data-stu-id="eb895-479">Documentation and Help Content</span></span>

- <span data-ttu-id="eb895-480">針對每個版本，將變更記錄重構成一個記錄 (#11165)</span><span class="sxs-lookup"><span data-stu-id="eb895-480">Refactor change logs into one log per release (#11165)</span></span>
- <span data-ttu-id="eb895-481">修正適用於 PowerShell 7 線上說明文件的 FWLinks (#11071)</span><span class="sxs-lookup"><span data-stu-id="eb895-481">Fix FWLinks for PowerShell 7 online help documents (#11071)</span></span>
- <span data-ttu-id="eb895-482">更新 CONTRIBUTING.md (#11096) (感謝 @mklement0！)</span><span class="sxs-lookup"><span data-stu-id="eb895-482">Update CONTRIBUTING.md (#11096) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="eb895-483">修正 README.md 中的安裝文件連結 (#11083)</span><span class="sxs-lookup"><span data-stu-id="eb895-483">Fix installation doc links in README.md (#11083)</span></span>
- <span data-ttu-id="eb895-484">將範例新增至 install-powershell.ps1 指令碼 (#11024) (感謝 @kilasuit！)</span><span class="sxs-lookup"><span data-stu-id="eb895-484">Adds examples to install-powershell.ps1 script (#11024) (Thanks @kilasuit!)</span></span>
- <span data-ttu-id="eb895-485">修正 CHANGELOG.md 中的 Select-String emphasis 和 Import-DscResource (#10890)</span><span class="sxs-lookup"><span data-stu-id="eb895-485">Fix to Select-String emphasis and Import-DscResource in CHANGELOG.md (#10890)</span></span>
- <span data-ttu-id="eb895-486">從 powershell-beginners-guide.md 移除過時的連結 (#10926)</span><span class="sxs-lookup"><span data-stu-id="eb895-486">Remove the stale link from powershell-beginners-guide.md (#10926)</span></span>
- <span data-ttu-id="eb895-487">合併穩定和維護變更記錄 (#10527)</span><span class="sxs-lookup"><span data-stu-id="eb895-487">Merge stable and servicing change logs (#10527)</span></span>
- <span data-ttu-id="eb895-488">在組建文件中更新所使用的 .NET 版本 (#10775) (感謝 @Greg-Smulko！)</span><span class="sxs-lookup"><span data-stu-id="eb895-488">Update used .NET version in build docs (#10775) (Thanks @Greg-Smulko!)</span></span>
- <span data-ttu-id="eb895-489">在 powershell-beginners-guide.md 中將 MSDN 的連結取代為 docs.microsoft.com (#10778) (感謝 @iSazonov！)</span><span class="sxs-lookup"><span data-stu-id="eb895-489">Replace links from MSDN to docs.microsoft.com in powershell-beginners-guide.md (#10778) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="eb895-490">修正中斷的 DSC 概觀連結 (#10702)</span><span class="sxs-lookup"><span data-stu-id="eb895-490">Fix broken DSC overview link (#10702)</span></span>
- <span data-ttu-id="eb895-491">更新 Support_Question.md，以連結至 Stack Overflow 作為另一個社群資源 (#10638) (感謝 @mklement0！)</span><span class="sxs-lookup"><span data-stu-id="eb895-491">Update Support_Question.md to link to Stack Overflow as another community resource (#10638) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="eb895-492">將處理器架構新增至散發要求範本 (#10661)</span><span class="sxs-lookup"><span data-stu-id="eb895-492">Add processor architecture to distribution request template (#10661)</span></span>
- <span data-ttu-id="eb895-493">將新的 PowerShell MoL 書籍新增至了解 PowerShell 文件中 (#10602)</span><span class="sxs-lookup"><span data-stu-id="eb895-493">Add new PowerShell MoL book to learning PowerShell docs (#10602)</span></span>
- <span data-ttu-id="eb895-494">針對 v 6.1.6 和 v6.2.3 版本更新 README.md 和中繼資料 (#10523)</span><span class="sxs-lookup"><span data-stu-id="eb895-494">Update README.md and metadata for v6.1.6 and v6.2.3 releases (#10523)</span></span>
- <span data-ttu-id="eb895-495">修正 README.md 中的打字錯誤 (#10465) (感謝 @vedhasp！)</span><span class="sxs-lookup"><span data-stu-id="eb895-495">Fix a typo in README.md (#10465) (Thanks @vedhasp!)</span></span>
- <span data-ttu-id="eb895-496">將 PSKoans 模組的參考新增至學習資源文件中 (#10369) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="eb895-496">Add a reference to PSKoans module to Learning Resources documentation (#10369) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="eb895-497">針對 7.0.0-preview.3 更新 README.md 和 metadata.json (#10393)</span><span class="sxs-lookup"><span data-stu-id="eb895-497">Update README.md and metadata.json for 7.0.0-preview.3 (#10393)</span></span>
