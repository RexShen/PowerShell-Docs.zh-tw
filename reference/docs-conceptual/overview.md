---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: 什麼是 PowerShell？
description: 本文介紹 PowerShell 指令碼環境及其功能。
ms.openlocfilehash: 91fc580af9a3adf43a24c40b4aaf3f1843882705
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500771"
---
# <a name="what-is-powershell"></a><span data-ttu-id="64d57-104">什麼是 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="64d57-104">What is PowerShell?</span></span>

<span data-ttu-id="64d57-105">PowerShell 是跨平台的工作自動化及設定管理架構，由命令列殼層與指令碼語言組成。</span><span class="sxs-lookup"><span data-stu-id="64d57-105">PowerShell is a cross-platform task automation and configuration management framework, consisting of a command-line shell and scripting language.</span></span> <span data-ttu-id="64d57-106">不同於大部分的殼層可接受及傳回文字，PowerShell 以 .NET Common Language Runtime (CLR) 為建置基礎，並接受及傳回 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="64d57-106">Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.</span></span> <span data-ttu-id="64d57-107">這種從根本上的變更，打造了全新的自動化工具與方法。</span><span class="sxs-lookup"><span data-stu-id="64d57-107">This fundamental change brings entirely new tools and methods for automation.</span></span>

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a><span data-ttu-id="64d57-108">輸出是以物件為基礎的</span><span class="sxs-lookup"><span data-stu-id="64d57-108">Output is object-based</span></span>

<span data-ttu-id="64d57-109">不同於傳統的命令列介面，PowerShell Cmdlet 是設計來處理物件。</span><span class="sxs-lookup"><span data-stu-id="64d57-109">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="64d57-110">物件是結構化的資訊，而不僅僅是出現在畫面上的字元字串。</span><span class="sxs-lookup"><span data-stu-id="64d57-110">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="64d57-111">命令輸出一律會攜帶您在需要時可以使用的額外資訊。</span><span class="sxs-lookup"><span data-stu-id="64d57-111">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="64d57-112">如果您過去曾使用文字處理工具來處理資料，將會發現它們的行為與在 PowerShell 中使用時不同。</span><span class="sxs-lookup"><span data-stu-id="64d57-112">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="64d57-113">在大部分情況下，您不需要使用文字處理工具來擷取特定資訊。</span><span class="sxs-lookup"><span data-stu-id="64d57-113">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="64d57-114">您可以使用標準的 PowerShell 物件語法，直接存取部分資料。</span><span class="sxs-lookup"><span data-stu-id="64d57-114">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="64d57-115">命令系列可進行擴充</span><span class="sxs-lookup"><span data-stu-id="64d57-115">The command family is extensible</span></span>

<span data-ttu-id="64d57-116">`cmd.exe` 之類的介面無法讓您直接擴充內建的命令集。</span><span class="sxs-lookup"><span data-stu-id="64d57-116">Interfaces such as `cmd.exe` don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="64d57-117">您可以建立外部命令列工具在 `cmd.exe` 中執行。</span><span class="sxs-lookup"><span data-stu-id="64d57-117">You can create external command-line tools that run in `cmd.exe`.</span></span> <span data-ttu-id="64d57-118">但這些外部工具不會提供任何服務，例如說明整合。</span><span class="sxs-lookup"><span data-stu-id="64d57-118">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="64d57-119">`cmd.exe` 自己不會知道這些外部工具是有效的命令。</span><span class="sxs-lookup"><span data-stu-id="64d57-119">`cmd.exe` doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="64d57-120">PowerShell 中的命令稱為 _Cmdlet_ 。</span><span class="sxs-lookup"><span data-stu-id="64d57-120">The commands in PowerShell are known as _cmdlets_ .</span></span> <span data-ttu-id="64d57-121">您可以個別使用每個 Cmdlet，但合併使用來執行複雜的工作時，更見其功效。</span><span class="sxs-lookup"><span data-stu-id="64d57-121">You can use each cmdlet separately, but their power is realized when you combine them to perform complex tasks.</span></span> <span data-ttu-id="64d57-122">如同許多殼層，PowerShell 可讓您存取電腦上的檔案系統。</span><span class="sxs-lookup"><span data-stu-id="64d57-122">Like many shells, PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="64d57-123">PowerShell「提供者」可讓您像存取檔案系統般容易地存取其他資料存放區 (如登錄及憑證存放區)。</span><span class="sxs-lookup"><span data-stu-id="64d57-123">PowerShell _providers_ enable you to access other data stores, such as the registry and the certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="64d57-124">您可以使用經過編譯的程式碼或指令碼，建立自己的 Cmdlet 與函式模組。</span><span class="sxs-lookup"><span data-stu-id="64d57-124">You can create your own cmdlet and function modules using compiled code or scripts.</span></span> <span data-ttu-id="64d57-125">模組可將 Cmdlet 與提供者新增到殼層。</span><span class="sxs-lookup"><span data-stu-id="64d57-125">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="64d57-126">PowerShell 也支援類似於 UNIX 殼層指令碼及 `cmd.exe` 批次檔案的指令碼。</span><span class="sxs-lookup"><span data-stu-id="64d57-126">PowerShell also supports scripts that are analogous to UNIX shell scripts and `cmd.exe` batch files.</span></span>

## <a name="support-for-command-aliases"></a><span data-ttu-id="64d57-127">支援命令別名</span><span class="sxs-lookup"><span data-stu-id="64d57-127">Support for command aliases</span></span>

<span data-ttu-id="64d57-128">PowerShell 支援別名，以使用替代名稱來參考命令。</span><span class="sxs-lookup"><span data-stu-id="64d57-128">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="64d57-129">別名讓具有其他殼層使用體驗的使用者能夠使用他們已經知道的常見命令名稱，在 PowerShell 中執行類似作業。</span><span class="sxs-lookup"><span data-stu-id="64d57-129">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="64d57-130">別名會將新名稱與另一個命令產生關聯。</span><span class="sxs-lookup"><span data-stu-id="64d57-130">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="64d57-131">例如，PowerShell 具有會清除輸出視窗的內部函式 `Clear-Host`。</span><span class="sxs-lookup"><span data-stu-id="64d57-131">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="64d57-132">您可以在命令提示字元中輸入 `cls` 或 `clear` 別名。</span><span class="sxs-lookup"><span data-stu-id="64d57-132">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="64d57-133">PowerShell 會解譯這些別名並執行 `Clear-Host` 函式。</span><span class="sxs-lookup"><span data-stu-id="64d57-133">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="64d57-134">此功能可協助使用者學習 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="64d57-134">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="64d57-135">首先，大部分的 `cmd.exe` 與 Unix 使用者都具備一大套完整的命令，而且使用者也都知道其名稱。</span><span class="sxs-lookup"><span data-stu-id="64d57-135">First, most `cmd.exe` and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="64d57-136">PowerShell 對應項可能不會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="64d57-136">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="64d57-137">不過，結果非常接近，足以讓使用者在不知道 PowerShell 命令名稱的情況下執行動作。</span><span class="sxs-lookup"><span data-stu-id="64d57-137">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="64d57-138">在學習新的命令殼層時，「肌肉記憶」是另一大挫折來源。</span><span class="sxs-lookup"><span data-stu-id="64d57-138">"Muscle memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="64d57-139">若您已使用 `cmd.exe` 多年，可能會反身鍵入 `cls` 命令來清除畫面。</span><span class="sxs-lookup"><span data-stu-id="64d57-139">If you have used `cmd.exe` for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="64d57-140">如果沒有 `Clear-Host` 的別名，您就會收到錯誤訊息，而且不知道該怎麼清除輸出。</span><span class="sxs-lookup"><span data-stu-id="64d57-140">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="64d57-141">PowerShell 會處理主控台輸入和顯示</span><span class="sxs-lookup"><span data-stu-id="64d57-141">PowerShell handles console input and display</span></span>

<span data-ttu-id="64d57-142">當您輸入命令時，PowerShell 一律會直接處理命令列輸入。</span><span class="sxs-lookup"><span data-stu-id="64d57-142">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="64d57-143">PowerShell 也會將您在畫面上看到的輸出格式化。</span><span class="sxs-lookup"><span data-stu-id="64d57-143">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="64d57-144">此差異十分重要，因為它可以減少每個 Cmdlet 所需的工作。</span><span class="sxs-lookup"><span data-stu-id="64d57-144">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="64d57-145">它會確保您一律可以使用與任何 Cmdlet 相同的方式來執行動作。</span><span class="sxs-lookup"><span data-stu-id="64d57-145">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="64d57-146">Cmdlet 開發人員不需要撰寫程式碼來剖析命令列引數，或將輸出格式化。</span><span class="sxs-lookup"><span data-stu-id="64d57-146">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="64d57-147">傳統命令列工具有其專屬方法來要求和顯示說明。</span><span class="sxs-lookup"><span data-stu-id="64d57-147">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="64d57-148">有一些命令列工具會使用 `/?` 觸發說明顯示，另有一些則會使用 `-?`、`/H`，甚至是 `//`。</span><span class="sxs-lookup"><span data-stu-id="64d57-148">Some command-line tools use `/?` to trigger the Help display; others use `-?`, `/H`, or even `//`.</span></span> <span data-ttu-id="64d57-149">有一部分會在 GUI 視窗中顯示說明，而不是在主控台顯示中。</span><span class="sxs-lookup"><span data-stu-id="64d57-149">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="64d57-150">如果您使用錯誤的參數，工具可能會忽略您輸入的內容，並開始自動執行工作。</span><span class="sxs-lookup"><span data-stu-id="64d57-150">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="64d57-151">因為 PowerShell 會自動剖析及處理命令列，所以 `-?` 參數一律表示「顯示此命令的說明」。</span><span class="sxs-lookup"><span data-stu-id="64d57-151">Since PowerShell automatically parses and processes the command line, the `-?` parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="64d57-152">如果您在 PowerShell 中執行圖形應用程式，即會開啟應用程式的視窗。</span><span class="sxs-lookup"><span data-stu-id="64d57-152">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="64d57-153">只有在處理您提供的命令列輸入或傳回給主控台視窗的應用程式輸出時，PowerShell 才會介入。</span><span class="sxs-lookup"><span data-stu-id="64d57-153">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="64d57-154">它不會影響應用程式的內部運作方式。</span><span class="sxs-lookup"><span data-stu-id="64d57-154">It does not affect how the application works internally.</span></span>

## <a name="powershell-has-a-pipeline"></a><span data-ttu-id="64d57-155">PowerShell 具有管線</span><span class="sxs-lookup"><span data-stu-id="64d57-155">PowerShell has a pipeline</span></span>

<span data-ttu-id="64d57-156">管線可說是用於命令列介面中最重要的概念。</span><span class="sxs-lookup"><span data-stu-id="64d57-156">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="64d57-157">若運用得當，管線將能減少使用複雜命令，讓您能夠更清楚地觀察工作的流程。</span><span class="sxs-lookup"><span data-stu-id="64d57-157">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work.</span></span> <span data-ttu-id="64d57-158">管線中的每個命令都會將其輸出逐項傳遞給下一個命令。</span><span class="sxs-lookup"><span data-stu-id="64d57-158">Each command in a pipeline passes its output, item by item, to the next command.</span></span> <span data-ttu-id="64d57-159">命令不需要每次處理一個以上的項目。</span><span class="sxs-lookup"><span data-stu-id="64d57-159">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="64d57-160">結果就是減少使用資源，而且立即得到輸出。</span><span class="sxs-lookup"><span data-stu-id="64d57-160">The result is reduced resource consumption and the ability to get output immediately.</span></span>

<span data-ttu-id="64d57-161">用於管線的標記法類似於其他殼層中所使用的標記法。</span><span class="sxs-lookup"><span data-stu-id="64d57-161">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="64d57-162">乍看之下，PowerShell 中的管線差異可能並不明顯。</span><span class="sxs-lookup"><span data-stu-id="64d57-162">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="64d57-163">雖然您會在畫面上看到文字，但 PowerShell 會在命令之間使用管線來傳送物件 (而非文字)。</span><span class="sxs-lookup"><span data-stu-id="64d57-163">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

<span data-ttu-id="64d57-164">例如，如果您使用 `Out-Host` Cmdlet 強制逐頁顯示另一個命令的輸出，則輸出看起來就像畫面上所顯示的一般文字 (分成數頁)：</span><span class="sxs-lookup"><span data-stu-id="64d57-164">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="64d57-165">分頁還會降低 CPU 使用率，因為處理控制權會在其已準備好要顯示的完成頁面時移轉給 `Out-Host` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64d57-165">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="64d57-166">管線中在它前面的 Cmdlet 會暫停執行，直到輸出的下一個分頁可供使用為止。</span><span class="sxs-lookup"><span data-stu-id="64d57-166">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

### <a name="objects-in-the-pipeline"></a><span data-ttu-id="64d57-167">管線中的物件</span><span class="sxs-lookup"><span data-stu-id="64d57-167">Objects in the pipeline</span></span>

<span data-ttu-id="64d57-168">當您在 PowerShell 中執行 Cmdlet 時，您會看到文字輸出，這是因為在主控台視窗中必須將物件呈現為文字。</span><span class="sxs-lookup"><span data-stu-id="64d57-168">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="64d57-169">文字輸出可能不會顯示要輸出之物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="64d57-169">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="64d57-170">例如，請考慮 `Get-Location` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64d57-170">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="64d57-171">文字輸出是資訊的摘要，並不是由 `Get-Location` 所傳回之物件的完整呈現。</span><span class="sxs-lookup"><span data-stu-id="64d57-171">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="64d57-172">輸出中的標題是由處理序新增的，它會將資料格式化以便在畫面上顯示。</span><span class="sxs-lookup"><span data-stu-id="64d57-172">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

```powershell
Get-Location
```

```Output
Path
----
C:\
```

<span data-ttu-id="64d57-173">使用管線將輸出傳送給 `Get-Member` Cmdlet 時，會顯示 `Get-Location` 所傳回之物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="64d57-173">Piping the output to the `Get-Member` cmdlet displays information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="64d57-174">`Get-Location` 會傳回 **PathInfo** 物件，其中包含目前的路徑與其他資訊。</span><span class="sxs-lookup"><span data-stu-id="64d57-174">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

## <a name="built-in-help-system"></a><span data-ttu-id="64d57-175">內建說明系統</span><span class="sxs-lookup"><span data-stu-id="64d57-175">Built-in help system</span></span>

<span data-ttu-id="64d57-176">一如 Unix `man` 頁面，PowerShell 包含詳細的說明文章，解釋了 PowerShell 概念與命令語法。</span><span class="sxs-lookup"><span data-stu-id="64d57-176">Similar to Unix `man` pages, PowerShell includes detailed help articles that explain PowerShell concepts and command syntax.</span></span> <span data-ttu-id="64d57-177">您可以在命令提示字元中使用 [Get-Help][] Cmdlet 來顯示這些文章，或在線上的 PowerShell 文件中，檢視這些文章的最新更新版本。</span><span class="sxs-lookup"><span data-stu-id="64d57-177">Use the [Get-Help][] cmdlet to display these articles at the command prompt or view the most recently updated versions of these articles in the PowerShell documentation online.</span></span>

## <a name="next-steps"></a><span data-ttu-id="64d57-178">後續步驟</span><span class="sxs-lookup"><span data-stu-id="64d57-178">Next steps</span></span>

<span data-ttu-id="64d57-179">若要深入了解 PowerShell，請參閱此網站的＜ **了解 PowerShell** ＞一節。</span><span class="sxs-lookup"><span data-stu-id="64d57-179">To learn more about PowerShell, see the **Learning PowerShell** section of this site.</span></span>

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
