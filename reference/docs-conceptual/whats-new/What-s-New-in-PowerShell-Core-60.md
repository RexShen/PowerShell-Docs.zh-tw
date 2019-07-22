---
title: PowerShell Core 6.0 的新功能
description: PowerShell Core 6.0 中發行的新功能與變更
ms.date: 08/06/2018
ms.openlocfilehash: e1218a38398f4d86829cf2b4ba6a3a882675eaab
ms.sourcegitcommit: 09f02ccef56ef30e7a9ca901f8d3713724960c68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843924"
---
# <a name="whats-new-in-powershell-core-60"></a><span data-ttu-id="14461-103">PowerShell Core 6.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="14461-103">What's New in PowerShell Core 6.0</span></span>

<span data-ttu-id="14461-104">[PowerShell Core 6.0][github] 是新的 PowerShell 版本，其為跨平台 (Windows、macOS 和 Linux)、開放原始碼，並針對異質環境和混合式雲端所建置。</span><span class="sxs-lookup"><span data-stu-id="14461-104">[PowerShell Core 6.0][github] is a new edition of PowerShell that is cross-platform (Windows, macOS, and Linux), open-source, and built for heterogeneous environments and the hybrid cloud.</span></span>

## <a name="moved-from-net-framework-to-net-core"></a><span data-ttu-id="14461-105">從 .NET Framework 移至 .NET Core</span><span class="sxs-lookup"><span data-stu-id="14461-105">Moved from .NET Framework to .NET Core</span></span>

<span data-ttu-id="14461-106">PowerShell Core 使用 [.NET Core 2.0][] 作為其執行階段。</span><span class="sxs-lookup"><span data-stu-id="14461-106">PowerShell Core uses [.NET Core 2.0][] as its runtime.</span></span>
<span data-ttu-id="14461-107">.NET Core 2.0 可讓 PowerShell Core 作用於多個平台 (Windows、macOS 和 Linux)。</span><span class="sxs-lookup"><span data-stu-id="14461-107">.NET Core 2.0 enables PowerShell Core to work on multiple platforms (Windows, macOS, and Linux).</span></span>
<span data-ttu-id="14461-108">PowerShell Core 也會公開 .NET Core 2.0 所提供的 API 集，以用於 PowerShell Cmdlet 和指令碼中。</span><span class="sxs-lookup"><span data-stu-id="14461-108">PowerShell Core also exposes the API set offered by .NET Core 2.0 to be used in PowerShell cmdlets and scripts.</span></span>

<span data-ttu-id="14461-109">Windows PowerShell 已使用 .NET Framework 執行階段來裝載 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="14461-109">Windows PowerShell used the .NET Framework runtime to host the PowerShell engine.</span></span>
<span data-ttu-id="14461-110">這表示 Windows PowerShell 會公開 .NET Framework 所提供的 API 集。</span><span class="sxs-lookup"><span data-stu-id="14461-110">This means that Windows PowerShell exposes the API set offered by .NET Framework.</span></span>

<span data-ttu-id="14461-111">.NET Core 與 .NET Framework 之間共用的 API 定義為 [.NET Standard][] 的一部分。</span><span class="sxs-lookup"><span data-stu-id="14461-111">The APIs shared between .NET Core and .NET Framework are defined as part of [.NET Standard][].</span></span>

<span data-ttu-id="14461-112">如需這如何影響 PowerShell Core 與 Windows PowerShell 之間模組/指令碼相容性的詳細資訊，請參閱[與 Windows PowerShell 的回溯相容性](#backwards-compatibility-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="14461-112">For more information on how this affects module/script compatibility between PowerShell Core and Windows PowerShell, see [Backwards compatibility with Windows PowerShell](#backwards-compatibility-with-windows-powershell).</span></span>

## <a name="support-for-macos-and-linux"></a><span data-ttu-id="14461-113">macOS 和 Linux 支援</span><span class="sxs-lookup"><span data-stu-id="14461-113">Support for macOS and Linux</span></span>

<span data-ttu-id="14461-114">PowerShell 現在正式支援 macOS 和 Linux，包含：</span><span class="sxs-lookup"><span data-stu-id="14461-114">PowerShell now officially supports macOS and Linux, including:</span></span>

- <span data-ttu-id="14461-115">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="14461-115">Windows 7, 8.1, and 10</span></span>
- <span data-ttu-id="14461-116">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="14461-116">Windows Server 2008 R2, 2012 R2, 2016</span></span>
- <span data-ttu-id="14461-117">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="14461-117">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
- <span data-ttu-id="14461-118">Ubuntu 14.04、16.04 和 17.04</span><span class="sxs-lookup"><span data-stu-id="14461-118">Ubuntu 14.04, 16.04, and 17.04</span></span>
- <span data-ttu-id="14461-119">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="14461-119">Debian 8.7+, and 9</span></span>
- <span data-ttu-id="14461-120">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="14461-120">CentOS 7</span></span>
- <span data-ttu-id="14461-121">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="14461-121">Red Hat Enterprise Linux 7</span></span>
- <span data-ttu-id="14461-122">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="14461-122">OpenSUSE 42.2</span></span>
- <span data-ttu-id="14461-123">Fedora 25、26</span><span class="sxs-lookup"><span data-stu-id="14461-123">Fedora 25, 26</span></span>
- <span data-ttu-id="14461-124">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="14461-124">macOS 10.12+</span></span>

<span data-ttu-id="14461-125">我們的社群也提供下列平台的套件，但未正式進行支援：</span><span class="sxs-lookup"><span data-stu-id="14461-125">Our community has also contributed packages for the following platforms, but they are not officially supported:</span></span>

- <span data-ttu-id="14461-126">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="14461-126">Arch Linux</span></span>
- <span data-ttu-id="14461-127">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="14461-127">Kali Linux</span></span>
- <span data-ttu-id="14461-128">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="14461-128">AppImage (works on multiple Linux platforms)</span></span>

<span data-ttu-id="14461-129">我們也會有下列平台的實驗性 (不支援) 版本：</span><span class="sxs-lookup"><span data-stu-id="14461-129">We also have experimental (unsupported) releases for the following platforms:</span></span>

- <span data-ttu-id="14461-130">ARM32/ARM64 上的 Windows</span><span class="sxs-lookup"><span data-stu-id="14461-130">Windows on ARM32/ARM64</span></span>
- <span data-ttu-id="14461-131">Raspbian (Stretch)</span><span class="sxs-lookup"><span data-stu-id="14461-131">Raspbian (Stretch)</span></span>

<span data-ttu-id="14461-132">已對 PowerShell Core 6.0 進行許多變更，讓它在非 Windows 系統上運作地更好。</span><span class="sxs-lookup"><span data-stu-id="14461-132">A number of changes were made to in PowerShell Core 6.0 to make it work better on non-Windows systems.</span></span>
<span data-ttu-id="14461-133">其中有些是也會影響 Windows 的最新變更。</span><span class="sxs-lookup"><span data-stu-id="14461-133">Some of these are breaking changes, which also affect Windows.</span></span>
<span data-ttu-id="14461-134">其他只會出現或適用於 PowerShell Core 的非 Windows 安裝。</span><span class="sxs-lookup"><span data-stu-id="14461-134">Others are only present or applicable in non-Windows installations of PowerShell Core.</span></span>

- <span data-ttu-id="14461-135">已在 Unix 平台上新增原生命令萬用字元支援。</span><span class="sxs-lookup"><span data-stu-id="14461-135">Added support for native command globbing on Unix platforms.</span></span>
- <span data-ttu-id="14461-136">`more` 功能會使用 Linux `$PAGER`，且預設為 `less`。</span><span class="sxs-lookup"><span data-stu-id="14461-136">The `more` functionality respects the Linux `$PAGER` and defaults to `less`.</span></span>
  <span data-ttu-id="14461-137">這表示，您現在可以搭配使用萬用字元與原生二進位檔/命令 (例如，`ls *.txt`)。</span><span class="sxs-lookup"><span data-stu-id="14461-137">This means you can now use wildcards with native binaries/commands (for example, `ls *.txt`).</span></span> <span data-ttu-id="14461-138">(#3463)</span><span class="sxs-lookup"><span data-stu-id="14461-138">(#3463)</span></span>
- <span data-ttu-id="14461-139">在處理原生命令引數時自動逸出結尾反斜線。</span><span class="sxs-lookup"><span data-stu-id="14461-139">Trailing backslash is automatically escaped when dealing with native command arguments.</span></span> <span data-ttu-id="14461-140">(#4965)</span><span class="sxs-lookup"><span data-stu-id="14461-140">(#4965)</span></span>
- <span data-ttu-id="14461-141">因為目前不支援 Script 簽署，所以在非 Windows 平台上執行 PowerShell 時會忽略 `-ExecutionPolicy` 參數。</span><span class="sxs-lookup"><span data-stu-id="14461-141">Ignore the `-ExecutionPolicy` switch when running PowerShell on non-Windows platforms because script signing is not currently supported.</span></span> <span data-ttu-id="14461-142">(#3481)</span><span class="sxs-lookup"><span data-stu-id="14461-142">(#3481)</span></span>
- <span data-ttu-id="14461-143">已修正 ConsoleHost，可在 Unix 平台上使用 `NoEcho`。</span><span class="sxs-lookup"><span data-stu-id="14461-143">Fixed ConsoleHost to honor `NoEcho` on Unix platforms.</span></span> <span data-ttu-id="14461-144">(#3801)</span><span class="sxs-lookup"><span data-stu-id="14461-144">(#3801)</span></span>
- <span data-ttu-id="14461-145">已修正 `Get-Help`，支援 Unix 平台上的不區分大小寫模式比對。</span><span class="sxs-lookup"><span data-stu-id="14461-145">Fixed `Get-Help` to support case insensitive pattern matching on Unix platforms.</span></span> <span data-ttu-id="14461-146">(#3852)</span><span class="sxs-lookup"><span data-stu-id="14461-146">(#3852)</span></span>
- <span data-ttu-id="14461-147">`powershell` 手冊頁已新增至套件</span><span class="sxs-lookup"><span data-stu-id="14461-147">`powershell` man-page added to package</span></span>

### <a name="logging"></a><span data-ttu-id="14461-148">記錄</span><span class="sxs-lookup"><span data-stu-id="14461-148">Logging</span></span>

<span data-ttu-id="14461-149">在 macOS 上，PowerShell 使用原生 `os_log` API 來登入 Apple 的[統一記錄系統][os_log]。</span><span class="sxs-lookup"><span data-stu-id="14461-149">On macOS, PowerShell uses the native `os_log` APIs to log to Apple's [unified logging system][os_log].</span></span>
<span data-ttu-id="14461-150">在 Linux 上，PowerShell 使用 [Syslog][]，這是一種通用記錄解決方案。</span><span class="sxs-lookup"><span data-stu-id="14461-150">On Linux, PowerShell uses [Syslog][], a ubiquitous logging solution.</span></span>

### <a name="filesystem"></a><span data-ttu-id="14461-151">Filesystem</span><span class="sxs-lookup"><span data-stu-id="14461-151">Filesystem</span></span>

<span data-ttu-id="14461-152">已在 macOS 和 Linux 上進行許多變更，可支援 Windows 上傳統不支援的檔案名稱字元：</span><span class="sxs-lookup"><span data-stu-id="14461-152">A number of changes have been made on macOS and Linux to support filename characters not traditionally supported on Windows:</span></span>

- <span data-ttu-id="14461-153">提供給 Cmdlet 的路徑現在不區分斜線 (/ 和 \ 都是作為目錄分隔符號)</span><span class="sxs-lookup"><span data-stu-id="14461-153">Paths given to cmdlets are now slash-agnostic (both / and \ work as directory separator)</span></span>
- <span data-ttu-id="14461-154">現在預設會支援並使用 XDG 基底目錄規格：</span><span class="sxs-lookup"><span data-stu-id="14461-154">XDG Base Directory Specification is now respected and used by default:</span></span>
  - <span data-ttu-id="14461-155">Linux/macOS 設定檔路徑位於 `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="14461-155">The Linux/macOS profile path is located at `~/.config/powershell/profile.ps1`</span></span>
  - <span data-ttu-id="14461-156">歷程記錄儲存路徑位於 `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="14461-156">The history save path is located at `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`</span></span>
  - <span data-ttu-id="14461-157">使用者模組路徑位於 `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="14461-157">The user module path is located at `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="14461-158">支援 Unix 上包含冒號字元的檔案和資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="14461-158">Support for file and folder names containing the colon character on Unix.</span></span> <span data-ttu-id="14461-159">(#4959)</span><span class="sxs-lookup"><span data-stu-id="14461-159">(#4959)</span></span>
- <span data-ttu-id="14461-160">支援包含逗號的指令碼名稱或完整路徑。</span><span class="sxs-lookup"><span data-stu-id="14461-160">Support for script names or full paths that have commas.</span></span> <span data-ttu-id="14461-161">(#4136) (感謝 [@TimCurwick](https://github.com/TimCurwick)！)</span><span class="sxs-lookup"><span data-stu-id="14461-161">(#4136) (Thanks to [@TimCurwick](https://github.com/TimCurwick)!)</span></span>
- <span data-ttu-id="14461-162">偵測何時使用 `-LiteralPath` 來抑制導覽 Cmdlet 的萬用字元展開。</span><span class="sxs-lookup"><span data-stu-id="14461-162">Detect when `-LiteralPath` is used to suppress wildcard expansion for navigation cmdlets.</span></span> <span data-ttu-id="14461-163">(#5038)</span><span class="sxs-lookup"><span data-stu-id="14461-163">(#5038)</span></span>
- <span data-ttu-id="14461-164">已更新 `Get-ChildItem`，使其運作更像 \*nix `ls -R` 和 Windows `DIR /S` 原生命令。</span><span class="sxs-lookup"><span data-stu-id="14461-164">Updated `Get-ChildItem` to work more like the \*nix `ls -R` and the Windows `DIR /S` native commands.</span></span>
  <span data-ttu-id="14461-165">`Get-ChildItem` 現在會傳回在遞迴式搜尋期間發生的符號連結，而且不會搜尋這些連結設為目標的目錄。</span><span class="sxs-lookup"><span data-stu-id="14461-165">`Get-ChildItem` now returns the symbolic links encountered during a recursive search and does not search the directories that those links target.</span></span> <span data-ttu-id="14461-166">(#3780)</span><span class="sxs-lookup"><span data-stu-id="14461-166">(#3780)</span></span>

### <a name="case-sensitivity"></a><span data-ttu-id="14461-167">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="14461-167">Case sensitivity</span></span>

<span data-ttu-id="14461-168">Linux 和 macOS 是要區分大小寫，而 Windows 不區分大小寫，同時保留大小寫。</span><span class="sxs-lookup"><span data-stu-id="14461-168">Linux and macOS tend to be case-sensitive while Windows is case-insensitive while preserving case.</span></span>
<span data-ttu-id="14461-169">一般情況下，PowerShell 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="14461-169">In general, PowerShell is case insensitive.</span></span>

<span data-ttu-id="14461-170">例如，在 macOS 和 Linux 上，環境變數區分大小寫，因此已標準化 `PSModulePath` 環境變數的大小寫。</span><span class="sxs-lookup"><span data-stu-id="14461-170">For example, environment variables are case-sensitive on macOS and Linux, so the casing of the `PSModulePath` environment variable has been standardized.</span></span> <span data-ttu-id="14461-171">(#3255) `Import-Module` 在使用檔案路徑來決定模組名稱時不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="14461-171">(#3255) `Import-Module` is case insensitive when it's using a file path to determine the module's name.</span></span> <span data-ttu-id="14461-172">(#5097)</span><span class="sxs-lookup"><span data-stu-id="14461-172">(#5097)</span></span>

## <a name="support-for-side-by-side-installations"></a><span data-ttu-id="14461-173">並存安裝支援</span><span class="sxs-lookup"><span data-stu-id="14461-173">Support for side-by-side installations</span></span>

<span data-ttu-id="14461-174">分別從 Windows PowerShell 安裝、設定和執行 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="14461-174">PowerShell Core is installed, configured, and executed separately from Windows PowerShell.</span></span>
<span data-ttu-id="14461-175">PowerShell Core 具有「可攜式」ZIP 套件。</span><span class="sxs-lookup"><span data-stu-id="14461-175">PowerShell Core has a "portable" ZIP package.</span></span>
<span data-ttu-id="14461-176">使用 ZIP 套件，即可在磁碟的任何位置安裝任意數目的版本，包含採用 PowerShell 作為相依性之應用程式的本機版本。</span><span class="sxs-lookup"><span data-stu-id="14461-176">Using the ZIP package, you can install any number of versions anywhere on disk, including local to an application that takes PowerShell as a dependency.</span></span>
<span data-ttu-id="14461-177">並存安裝可以更輕鬆地測試新的 PowerShell 版本，並在一段時間移轉現有指令碼。</span><span class="sxs-lookup"><span data-stu-id="14461-177">Side-by-side installation makes it easier to test new versions of PowerShell and migrating existing scripts over time.</span></span>
<span data-ttu-id="14461-178">因為指令碼可以固定到其所需的特定版本，所以並存也會啟用回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="14461-178">Side-by-side also enables backwards compatibility as scripts can be pinned to specific versions that they require.</span></span>

> [!NOTE]
> <span data-ttu-id="14461-179">根據預設，Windows 上以 MSI 為基礎的安裝程式會執行就地更新安裝。</span><span class="sxs-lookup"><span data-stu-id="14461-179">By default, the MSI-based installer on Windows does an in-place update install.</span></span>
>

## <a name="renamed-powershellexe-to-pwshexe"></a><span data-ttu-id="14461-180">已將 `powershell(.exe)` 重新命名為 `pwsh(.exe)`</span><span class="sxs-lookup"><span data-stu-id="14461-180">Renamed `powershell(.exe)` to `pwsh(.exe)`</span></span>

<span data-ttu-id="14461-181">已將 PowerShell Core 的二進位檔名稱從 `powershell(.exe)` 變更為 `pwsh(.exe)`。</span><span class="sxs-lookup"><span data-stu-id="14461-181">The binary name for PowerShell Core has been changed from `powershell(.exe)` to `pwsh(.exe)`.</span></span>
<span data-ttu-id="14461-182">這項變更提供決定性方式，讓使用者在電腦上執行 PowerShell Core，以支援並存 Windows PowerShell 和 PowerShell Core 安裝。</span><span class="sxs-lookup"><span data-stu-id="14461-182">This change provides a deterministic way for users to run PowerShell Core on machines to support side-by-side Windows PowerShell and PowerShell Core installations.</span></span>
<span data-ttu-id="14461-183">`pwsh` 也會較短，而且更容易鍵入。</span><span class="sxs-lookup"><span data-stu-id="14461-183">`pwsh` is also much shorter and easier to type.</span></span>

<span data-ttu-id="14461-184">其他從 `powershell.exe` 到 `pwsh(.exe)` 的變更：</span><span class="sxs-lookup"><span data-stu-id="14461-184">Additional changes to `pwsh(.exe)` from `powershell.exe`:</span></span>

- <span data-ttu-id="14461-185">已將第一個位置參數從 `-Command` 變更為 `-File`。</span><span class="sxs-lookup"><span data-stu-id="14461-185">Changed the first positional parameter from `-Command` to `-File`.</span></span>
  <span data-ttu-id="14461-186">這項變更會修正 PowerShell 指令碼中 `#!` 的使用方式 (也稱為狀況)，而 PowerShell 指令碼要在非 Windows 平台上從非 PowerShell 殼層執行。</span><span class="sxs-lookup"><span data-stu-id="14461-186">This change fixes the usage of `#!` (aka as a shebang) in PowerShell scripts that are being executed from non-PowerShell shells on non-Windows platforms.</span></span>
  <span data-ttu-id="14461-187">這也表示您可以執行 `pwsh foo.ps1` 或 `pwsh fooScript` 這類命令，但未指定 `-File`。</span><span class="sxs-lookup"><span data-stu-id="14461-187">It also means that you can run commands like `pwsh foo.ps1` or `pwsh fooScript` without specifying `-File`.</span></span>
  <span data-ttu-id="14461-188">不過，這項變更需要您在嘗試執行 `pwsh.exe -Command Get-Command` 這類命令時明確指定 `-c` 或 `-Command`。</span><span class="sxs-lookup"><span data-stu-id="14461-188">However, this change requires that you explicitly specify `-c` or `-Command` when trying to run commands like `pwsh.exe -Command Get-Command`.</span></span> <span data-ttu-id="14461-189">(#4019)</span><span class="sxs-lookup"><span data-stu-id="14461-189">(#4019)</span></span>
- <span data-ttu-id="14461-190">PowerShell Core 接受 `-i` (或 `-Interactive`) 參數，指出互動式殼層。</span><span class="sxs-lookup"><span data-stu-id="14461-190">PowerShell Core accepts the `-i` (or `-Interactive`) switch to indicate an interactive shell.</span></span> <span data-ttu-id="14461-191">(#3558) 這可讓 PowerShell 用作 Unix 平台上的預設殼層。</span><span class="sxs-lookup"><span data-stu-id="14461-191">(#3558) This allows PowerShell to be used as a default shell on Unix platforms.</span></span>
- <span data-ttu-id="14461-192">已從 `pwsh.exe` 移除 `-importsystemmodules` 和 `-psconsoleFile` 參數。</span><span class="sxs-lookup"><span data-stu-id="14461-192">Removed parameters `-importsystemmodules` and `-psconsoleFile` from `pwsh.exe`.</span></span> <span data-ttu-id="14461-193">(#4995)</span><span class="sxs-lookup"><span data-stu-id="14461-193">(#4995)</span></span>
- <span data-ttu-id="14461-194">已變更 `pwsh -version` 以及 `pwsh.exe` 的內建說明，以配合其他原生工具。</span><span class="sxs-lookup"><span data-stu-id="14461-194">Changed `pwsh -version` and built-in help for `pwsh.exe` to align with other native tools.</span></span> <span data-ttu-id="14461-195">(#4958 與 #4931) (感謝 [@iSazonov](https://github.com/iSazonov))</span><span class="sxs-lookup"><span data-stu-id="14461-195">(#4958 & #4931) (Thanks [@iSazonov](https://github.com/iSazonov))</span></span>
- <span data-ttu-id="14461-196">`-File` 和 `-Command` 的引數錯誤訊息無效，而且結束碼符合 Unix 標準 (#4573)</span><span class="sxs-lookup"><span data-stu-id="14461-196">Invalid argument error messages for `-File` and `-Command` and exit codes consistent with Unix standards (#4573)</span></span>
- <span data-ttu-id="14461-197">已在 Windows 上新增 `-WindowStyle` 參數。</span><span class="sxs-lookup"><span data-stu-id="14461-197">Added `-WindowStyle` parameter on Windows.</span></span> <span data-ttu-id="14461-198">(#4573) 同樣地，非 Windows 平台上以套件為基礎的安裝更新就是就地更新。</span><span class="sxs-lookup"><span data-stu-id="14461-198">(#4573) Similarly, package-based installations updates on non-Windows platforms are in-place updates.</span></span>

## <a name="backwards-compatibility-with-windows-powershell"></a><span data-ttu-id="14461-199">與 Windows PowerShell 的回溯相容性</span><span class="sxs-lookup"><span data-stu-id="14461-199">Backwards compatibility with Windows PowerShell</span></span>

<span data-ttu-id="14461-200">PowerShell Core 的目標是盡可能保持與 Windows PowerShell 相容。</span><span class="sxs-lookup"><span data-stu-id="14461-200">The goal of PowerShell Core is to remain as compatible as possible with Windows PowerShell.</span></span>
<span data-ttu-id="14461-201">PowerShell Core 會使用 [.NET Standard][] 2.0，以提供與現有 .NET 組件的二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="14461-201">PowerShell Core uses [.NET Standard][] 2.0 to provide binary compatibility with existing .NET assemblies.</span></span>
<span data-ttu-id="14461-202">許多 PowerShell 模組都與這些組件相依 (通常是 DLL)，因此 .NET Standard 可讓它們繼續使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="14461-202">Many PowerShell modules depend on these assemblies (often times DLLs), so .NET Standard allows them to continue working with .NET Core.</span></span>
<span data-ttu-id="14461-203">PowerShell Core 也包含查看已知資料夾 (例如，全域組件快取通常在磁碟上的位置) 的啟發學習法，以尋找 .NET Framework DLL 相依性。</span><span class="sxs-lookup"><span data-stu-id="14461-203">PowerShell Core also includes a heuristic to look in well-known folders--like where the Global Assembly Cache typically resides on disk--to find .NET Framework DLL dependencies.</span></span>

<span data-ttu-id="14461-204">您可以在 [.NET 部落格][]、此 [YouTube][] 影片以及 GitHub 上的這個[常見問題集][]中，深入了解 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="14461-204">You can learn more about .NET Standard on the [.NET Blog][], in this [YouTube][] video, and via this [FAQ][] on GitHub.</span></span>

<span data-ttu-id="14461-205">已致力於確定 PowerShell 語言和「內建」模組 (例如 `Microsoft.PowerShell.Management`、`Microsoft.PowerShell.Utility` 等) 的運作方式與在 Windows PowerShell 中一樣。</span><span class="sxs-lookup"><span data-stu-id="14461-205">Best efforts have been made to ensure that the PowerShell language and "built-in" modules (like `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, etc.) work the same as they do in Windows PowerShell.</span></span>
<span data-ttu-id="14461-206">在許多情況下，於社群的協助下，我們已將新功能和 Bug 修正新增至這些 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-206">In many cases, with the help of the community, we've added new capabilities and bug fixes to those cmdlets.</span></span>
<span data-ttu-id="14461-207">在某些情況下，因為基礎.NET 層中遺失相依性，所以功能已移除或無法使用。</span><span class="sxs-lookup"><span data-stu-id="14461-207">In some cases, due to a missing dependency in underlying .NET layers, functionality was removed or is unavailable.</span></span>

<span data-ttu-id="14461-208">隨附為 Windows 一部分的大部分模組 (例如，`DnsClient`、`Hyper-V`、`NetTCPIP`、`Storage` 等) 以及包含 Azure 和 Office 的其他 Microsoft 產品都尚未「明確地」  移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="14461-208">Most of the modules that ship as part of Windows (for example, `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, etc.) and other Microsoft products including Azure and Office have not been *explicitly* ported to .NET Core yet.</span></span>
<span data-ttu-id="14461-209">PowerShell 小組正在與這些產品小組和團隊合作，驗證其現有模組並將其移植到 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="14461-209">The PowerShell team is working with these product groups and teams to validate and port their existing modules to PowerShell Core.</span></span>
<span data-ttu-id="14461-210">使用 .NET Standard 和 [CDXML][]，其中許多傳統 Windows PowerShell 模組似乎作用於 PowerShell Core，但尚未正式驗證而且未正式支援。</span><span class="sxs-lookup"><span data-stu-id="14461-210">With .NET Standard and [CDXML][], many of these traditional Windows PowerShell modules do seem to work in PowerShell Core, but they have not been formally validated, and they are not formally supported.</span></span>

<span data-ttu-id="14461-211">安裝 [`WindowsPSModulePath`][windowspsmodulepath] 模組，即可將 Windows PowerShell `PSModulePath` 附加至 PowerShell Core `PSModulePath`，以使用 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="14461-211">By installing the [`WindowsPSModulePath`][windowspsmodulepath] module, you can use Windows PowerShell modules by appending the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="14461-212">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="14461-212">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="14461-213">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="14461-213">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a><span data-ttu-id="14461-214">Docker 支援</span><span class="sxs-lookup"><span data-stu-id="14461-214">Docker support</span></span>

<span data-ttu-id="14461-215">PowerShell Core 支援所有支援之主要平台 (包含多個 Linux 發行版本、Windows Server Core 和 Nano Server) 的 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="14461-215">PowerShell Core adds support for Docker containers for all the major platforms we support (including multiple Linux distros, Windows Server Core, and Nano Server).</span></span>

<span data-ttu-id="14461-216">如需完整清單，請參閱 [`microsoft/powershell`Docker Hub][docker-hub] 上的標記。</span><span class="sxs-lookup"><span data-stu-id="14461-216">For a complete list, check out the tags on [`microsoft/powershell` on Docker Hub][docker-hub].</span></span>
<span data-ttu-id="14461-217">如需 Docker 和 PowerShell Core 的詳細資訊，請參閱 GitHub 上的 [Docker][]。</span><span class="sxs-lookup"><span data-stu-id="14461-217">For more information on Docker and PowerShell Core, see [Docker][] on GitHub.</span></span>

## <a name="ssh-based-powershell-remoting"></a><span data-ttu-id="14461-218">以 SSH 為基礎的 PowerShell 遠端</span><span class="sxs-lookup"><span data-stu-id="14461-218">SSH-based PowerShell Remoting</span></span>

<span data-ttu-id="14461-219">除了傳統以 WinRM 為基礎的 PSRP 之外，PowerShell 遠端通訊協定 (PSRP) 現在還可以與 Secure Shell (SSH) 通訊協定搭配運作。</span><span class="sxs-lookup"><span data-stu-id="14461-219">The PowerShell Remoting Protocol (PSRP) now works with the Secure Shell (SSH) protocol in addition to the traditional WinRM-based PSRP.</span></span>

<span data-ttu-id="14461-220">這表示您可以使用 `Enter-PSSession` 和 `New-PSSession` 這類 Cmdlet，並使用 SSH 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="14461-220">This means that you can use cmdlets like `Enter-PSSession` and `New-PSSession` and authenticate using SSH.</span></span>
<span data-ttu-id="14461-221">您只需要向以 OpenSSH 為基礎的 SSH 伺服器註冊 PowerShell 作為子系統，而且您可以使用具有傳統 `PSSession` 語意且以現有 SSH 為基礎的驗證機制 (例如密碼或私密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="14461-221">All you have to do is register PowerShell as a subsystem with an OpenSSH-based SSH server, and you can use your existing SSH-based authenticate mechanisms (like passwords or private keys) with the traditional `PSSession` semantics.</span></span>

<span data-ttu-id="14461-222">如需設定和使用以 SSH 為基礎遠端的詳細資訊，請參閱[透過 SSH 的 PowerShell 遠端][ssh-remoting]。</span><span class="sxs-lookup"><span data-stu-id="14461-222">For more information on configuring and using SSH-based remoting, see [PowerShell Remoting over SSH][ssh-remoting].</span></span>

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a><span data-ttu-id="14461-223">預設編碼是沒有 BOM 的 UTF-8 (New-ModuleManifest 除外)</span><span class="sxs-lookup"><span data-stu-id="14461-223">Default encoding is UTF-8 without a BOM except for New-ModuleManifest</span></span>

<span data-ttu-id="14461-224">過去，`Get-Content`、`Set-Content` 這類 Windows PowerShell Cmdlet 已使用不同編碼，例如 ASCII 和 UTF-16。</span><span class="sxs-lookup"><span data-stu-id="14461-224">In the past, Windows PowerShell cmdlets like `Get-Content`, `Set-Content` used different encodings, such as ASCII and UTF-16.</span></span>
<span data-ttu-id="14461-225">編碼預設值中的變化已在混合使用 Cmdlet 但未指定編碼時產生問題。</span><span class="sxs-lookup"><span data-stu-id="14461-225">The variance in encoding defaults created problems when mixing cmdlets without specifying an encoding.</span></span>

<span data-ttu-id="14461-226">非 Windows 平台傳統上會使用 UTF-8，但未使用位元組順序標記 (BOM) 作為文字檔的預設編碼。</span><span class="sxs-lookup"><span data-stu-id="14461-226">Non-Windows platforms traditionally use UTF-8 without a Byte Order Mark (BOM) as the default encoding for text files.</span></span>
<span data-ttu-id="14461-227">其他 Windows 應用程式和工具不會使用 UTF-16，而是使用無 BOM 的 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="14461-227">More Windows applications and tools are moving away from UTF-16 and towards BOM-less UTF-8 encoding.</span></span>
<span data-ttu-id="14461-228">PowerShell Core 會變更預設編碼，以符合更廣泛的生態系統。</span><span class="sxs-lookup"><span data-stu-id="14461-228">PowerShell Core changes the default encoding to conform with the broader ecosystems.</span></span>

<span data-ttu-id="14461-229">這表示，使用 `-Encoding` 參數的所有內建 Cmdlet 預設都會使用 `UTF8NoBOM` 值。</span><span class="sxs-lookup"><span data-stu-id="14461-229">This means that all built-in cmdlets that use the `-Encoding` parameter use the `UTF8NoBOM` value by default.</span></span>
<span data-ttu-id="14461-230">這項變更會影響下列 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="14461-230">The following cmdlets are affected by this change:</span></span>

- <span data-ttu-id="14461-231">Add-Content</span><span class="sxs-lookup"><span data-stu-id="14461-231">Add-Content</span></span>
- <span data-ttu-id="14461-232">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="14461-232">Export-Clixml</span></span>
- <span data-ttu-id="14461-233">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="14461-233">Export-Csv</span></span>
- <span data-ttu-id="14461-234">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="14461-234">Export-PSSession</span></span>
- <span data-ttu-id="14461-235">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="14461-235">Format-Hex</span></span>
- <span data-ttu-id="14461-236">Get-Content</span><span class="sxs-lookup"><span data-stu-id="14461-236">Get-Content</span></span>
- <span data-ttu-id="14461-237">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="14461-237">Import-Csv</span></span>
- <span data-ttu-id="14461-238">Out-File</span><span class="sxs-lookup"><span data-stu-id="14461-238">Out-File</span></span>
- <span data-ttu-id="14461-239">Select-String</span><span class="sxs-lookup"><span data-stu-id="14461-239">Select-String</span></span>
- <span data-ttu-id="14461-240">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="14461-240">Send-MailMessage</span></span>
- <span data-ttu-id="14461-241">Set-Content</span><span class="sxs-lookup"><span data-stu-id="14461-241">Set-Content</span></span>

<span data-ttu-id="14461-242">這些 Cmdlet 也已進行更新，讓 `-Encoding` 參數普遍接受 `System.Text.Encoding`。</span><span class="sxs-lookup"><span data-stu-id="14461-242">These cmdlets have also been updated so that the `-Encoding` parameter universally accepts `System.Text.Encoding`.</span></span>

<span data-ttu-id="14461-243">`$OutputEncoding` 的預設值也已變更為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="14461-243">The default value of `$OutputEncoding` has also been changed to UTF-8.</span></span>

<span data-ttu-id="14461-244">最佳做法是您應該使用 `-Encoding` 參數明確設定指令碼中編碼，跨平台產生決定性行為。</span><span class="sxs-lookup"><span data-stu-id="14461-244">As a best practice, you should explicitly set encodings in scripts using the `-Encoding` parameter to produce deterministic behavior across platforms.</span></span>

<span data-ttu-id="14461-245">`New-ModuleManifest` Cmdlet 沒有**編碼**參數。</span><span class="sxs-lookup"><span data-stu-id="14461-245">`New-ModuleManifest` cmdlet does not have **Encoding** parameter.</span></span> <span data-ttu-id="14461-246">使用 `New-ModuleManifest` cmdlet 建立之模組資訊清單 (.psd1) 檔案的編碼會視環境而定：如果它是在 Linux 上執行的 PowerShell 核心，則編碼為 UTF-8 (無 BOM)；否則編碼為 UTF-16 (包含 BOM)。</span><span class="sxs-lookup"><span data-stu-id="14461-246">The encoding of the module manifest (.psd1) file created with `New-ModuleManifest` cmdlet depends on environment: if it is PowerShell Core running on Linux then encoding is UTF-8 (no BOM); otherwise encoding is UTF-16 (with BOM).</span></span> <span data-ttu-id="14461-247">(#3940)</span><span class="sxs-lookup"><span data-stu-id="14461-247">(#3940)</span></span>

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a><span data-ttu-id="14461-248">支援含 & 符號 (`&`) 之管線的背景 (#3360)</span><span class="sxs-lookup"><span data-stu-id="14461-248">Support backgrounding of pipelines with ampersand (`&`) (#3360)</span></span>

<span data-ttu-id="14461-249">將 `&` 置於管線結尾，會將管線執行為 PowerShell 作業。</span><span class="sxs-lookup"><span data-stu-id="14461-249">Putting `&` at the end of a pipeline causes the pipeline to be run as a PowerShell job.</span></span>
<span data-ttu-id="14461-250">管線在背景時，會傳回作業物件。</span><span class="sxs-lookup"><span data-stu-id="14461-250">When a pipeline is backgrounded, a job object is returned.</span></span>
<span data-ttu-id="14461-251">管線執行為作業之後，即可使用所有標準 `*-Job` Cmdlet 來管理作業。</span><span class="sxs-lookup"><span data-stu-id="14461-251">Once the pipeline is running as a job, all of the standard `*-Job` cmdlets can be used to manage the job.</span></span>
<span data-ttu-id="14461-252">管線中所使用的變數 (忽略處理序特定變數) 會自動複製至作業，因此 `Copy-Item $foo $bar &` 就會運作。</span><span class="sxs-lookup"><span data-stu-id="14461-252">Variables (ignoring process-specific variables) used in the pipeline are automatically copied to the job so `Copy-Item $foo $bar &` just works.</span></span>
<span data-ttu-id="14461-253">作業也會在目前目錄中執行，而不是使用者的主目錄。</span><span class="sxs-lookup"><span data-stu-id="14461-253">The job is also run in the current directory instead of the user's home directory.</span></span>
<span data-ttu-id="14461-254">如需 PowerShell 作業的詳細資訊，請參閱 [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs)。</span><span class="sxs-lookup"><span data-stu-id="14461-254">For more information about PowerShell jobs, see [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="14461-255">語意化版本控制系統</span><span class="sxs-lookup"><span data-stu-id="14461-255">Semantic versioning</span></span>

- <span data-ttu-id="14461-256">讓 `SemanticVersion` 與 `SemVer 2.0` 相容。</span><span class="sxs-lookup"><span data-stu-id="14461-256">Made `SemanticVersion` compatible with `SemVer 2.0`.</span></span> <span data-ttu-id="14461-257">(#5037) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-257">(#5037) (Thanks [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-258">已將 `New-ModuleManifest` 中的預設 `ModuleVersion` 變更為 `0.0.1`，以符合 SemVer。</span><span class="sxs-lookup"><span data-stu-id="14461-258">Changed default `ModuleVersion` in `New-ModuleManifest` to `0.0.1` to align with SemVer.</span></span> <span data-ttu-id="14461-259">(#4842) (感謝 [@LDSpits](https://github.com/LDSpits))</span><span class="sxs-lookup"><span data-stu-id="14461-259">(#4842) (Thanks [@LDSpits](https://github.com/LDSpits))</span></span>
- <span data-ttu-id="14461-260">已將 `semver` 新增為 `System.Management.Automation.SemanticVersion` 的類型加速器。</span><span class="sxs-lookup"><span data-stu-id="14461-260">Added `semver` as a type accelerator for `System.Management.Automation.SemanticVersion`.</span></span> <span data-ttu-id="14461-261">(#4142) (感謝 [@oising](https://github.com/oising)！)</span><span class="sxs-lookup"><span data-stu-id="14461-261">(#4142) (Thanks to [@oising](https://github.com/oising)!)</span></span>
- <span data-ttu-id="14461-262">已啟用 `SemanticVersion` 執行個體與只使用 `Major` 和 `Minor` 版本值所建構之 `Version` 執行個體之間的比較。</span><span class="sxs-lookup"><span data-stu-id="14461-262">Enabled comparison between a `SemanticVersion` instance and a `Version` instance that is constructed only with `Major` and `Minor` version values.</span></span>

## <a name="language-updates"></a><span data-ttu-id="14461-263">語言更新</span><span class="sxs-lookup"><span data-stu-id="14461-263">Language updates</span></span>

- <span data-ttu-id="14461-264">實作 Unicode 逸出剖析，讓使用者可以使用 Unicode 字元作為引數、字串或變數名稱。</span><span class="sxs-lookup"><span data-stu-id="14461-264">Implement Unicode escape parsing so that users can use Unicode characters as arguments, strings, or variable names.</span></span> <span data-ttu-id="14461-265">(#3958) (感謝 [@rkeithhill](https://github.com/rkeithhill)！)</span><span class="sxs-lookup"><span data-stu-id="14461-265">(#3958) (Thanks to [@rkeithhill](https://github.com/rkeithhill)!)</span></span>
- <span data-ttu-id="14461-266">已新增 ESC 的新逸出字元：`` `e``</span><span class="sxs-lookup"><span data-stu-id="14461-266">Added new escape character for ESC: `` `e``</span></span>
- <span data-ttu-id="14461-267">已新增將列舉轉換為字串的支援 (#4318) (感謝 [@KirkMunro](https://github.com/KirkMunro))</span><span class="sxs-lookup"><span data-stu-id="14461-267">Added support for converting enums to string (#4318) (Thanks [@KirkMunro](https://github.com/KirkMunro))</span></span>
- <span data-ttu-id="14461-268">已修正將單一項目陣列轉型為泛型集合。</span><span class="sxs-lookup"><span data-stu-id="14461-268">Fixed casting single element array to a generic collection.</span></span> <span data-ttu-id="14461-269">(#3170)</span><span class="sxs-lookup"><span data-stu-id="14461-269">(#3170)</span></span>
- <span data-ttu-id="14461-270">已新增多載至 `..` 運算子的字元範圍，讓 `'a'..'z'` 傳回從 'a' 到 'z' 的字元。</span><span class="sxs-lookup"><span data-stu-id="14461-270">Added character range overload to the `..` operator, so `'a'..'z'` returns characters from 'a' to 'z'.</span></span> <span data-ttu-id="14461-271">(#5026) (感謝 [@IISResetMe](https://github.com/IISResetMe)！)</span><span class="sxs-lookup"><span data-stu-id="14461-271">(#5026) (Thanks [@IISResetMe](https://github.com/IISResetMe)!)</span></span>
- <span data-ttu-id="14461-272">已修正變數指派不會覆寫唯讀變數</span><span class="sxs-lookup"><span data-stu-id="14461-272">Fixed variable assignment to not overwrite read-only variables</span></span>
- <span data-ttu-id="14461-273">將指令碼 Cmdlet 加上點時，將自動變數的區域變數推送至 'DottedScopes' (#4709)</span><span class="sxs-lookup"><span data-stu-id="14461-273">Push locals of automatic variables to 'DottedScopes' when dotting script cmdlets (#4709)</span></span>
- <span data-ttu-id="14461-274">在分割運算子中啟用「單行、多行」選項的使用 (#4721) (感謝 [@iSazonov](https://github.com/iSazonov))</span><span class="sxs-lookup"><span data-stu-id="14461-274">Enable use of 'Singleline, Multiline' option in split operator (#4721) (Thanks [@iSazonov](https://github.com/iSazonov))</span></span>

## <a name="engine-updates"></a><span data-ttu-id="14461-275">引擎更新</span><span class="sxs-lookup"><span data-stu-id="14461-275">Engine updates</span></span>

- <span data-ttu-id="14461-276">`$PSVersionTable` 有四個新屬性：</span><span class="sxs-lookup"><span data-stu-id="14461-276">`$PSVersionTable` has four new properties:</span></span>
  - <span data-ttu-id="14461-277">`PSEdition`:這在 PowerShell Core 上設定為 `Core`，而在 Windows PowerShell 上設定為 `Desktop`</span><span class="sxs-lookup"><span data-stu-id="14461-277">`PSEdition`: This is set to `Core` on PowerShell Core and `Desktop` on Windows PowerShell</span></span>
  - <span data-ttu-id="14461-278">`GitCommitId`:這是在其中建置 PowerShell 之 Git 分支或標記的 Git 認可識別碼。</span><span class="sxs-lookup"><span data-stu-id="14461-278">`GitCommitId`: This is the Git commit ID of the Git branch or tag where PowerShell was built.</span></span>
    <span data-ttu-id="14461-279">在發行的組建上，它可能會與 `PSVersion` 相同。</span><span class="sxs-lookup"><span data-stu-id="14461-279">On released builds, it will likely be the same as `PSVersion`.</span></span>
  - <span data-ttu-id="14461-280">`OS`:這是 `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription` 所傳回的作業系統版本字串</span><span class="sxs-lookup"><span data-stu-id="14461-280">`OS`: This is an OS version string returned by `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`</span></span>
  - <span data-ttu-id="14461-281">`Platform`:這是 `[System.Environment]::OSVersion.Platform` 所傳回。它在 Windows 上設定為 `Win32NT`、在 macOS 上設為 `Unix`，而在 Linux 上設定為 `Unix`。</span><span class="sxs-lookup"><span data-stu-id="14461-281">`Platform`: This is returned by `[System.Environment]::OSVersion.Platform` It is set to `Win32NT` on Windows, `Unix` on macOS, and `Unix` on Linux.</span></span>
- <span data-ttu-id="14461-282">已從 `$PSVersionTable` 移除 `BuildVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="14461-282">Removed the `BuildVersion` property from `$PSVersionTable`.</span></span>
  <span data-ttu-id="14461-283">此屬性已緊密繫結至 Windows 組建版本。</span><span class="sxs-lookup"><span data-stu-id="14461-283">This property was strongly tied to the Windows build version.</span></span>
  <span data-ttu-id="14461-284">相反地，建議您使用 `GitCommitId` 擷取 PowerShell Core 的確切組建版本。</span><span class="sxs-lookup"><span data-stu-id="14461-284">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span> <span data-ttu-id="14461-285">(#3877) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-285">(#3877) (Thanks to [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-286">已從 `$PSVersionTable` 移除 `ClrVersion` 屬性。</span><span class="sxs-lookup"><span data-stu-id="14461-286">Remove `ClrVersion` property from `$PSVersionTable`.</span></span>
  <span data-ttu-id="14461-287">此屬性與 .NET Core 無關，而且基於不適用於 PowerShell 的特定舊版用途，已在 .NET Core 中予以保留。</span><span class="sxs-lookup"><span data-stu-id="14461-287">This property is irrelevant for .NET Core, and was only preserved in .NET Core for specific legacy purposes that are inapplicable to PowerShell.</span></span>
- <span data-ttu-id="14461-288">已新增三個新的自動變數，以決定是否在指定的 OS 中執行 PowerShell：`$IsWindows`、`$IsMacOs` 和 `$IsLinux`。</span><span class="sxs-lookup"><span data-stu-id="14461-288">Added three new automatic variables to determine whether PowerShell is running in a given OS: `$IsWindows`, `$IsMacOs`, and `$IsLinux`.</span></span>
- <span data-ttu-id="14461-289">將 `GitCommitId` 新增至 PowerShell Core 橫幅。</span><span class="sxs-lookup"><span data-stu-id="14461-289">Add `GitCommitId` to PowerShell Core banner.</span></span>
  <span data-ttu-id="14461-290">現在，啟動 PowerShell 取得版本之後，不需要立即執行 `$PSVersionTable`！</span><span class="sxs-lookup"><span data-stu-id="14461-290">Now you don't have to run `$PSVersionTable` as soon as you start PowerShell to get the version!</span></span> <span data-ttu-id="14461-291">(#3916) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-291">(#3916) (Thanks to [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-292">在 `$PSHome` 中新增稱為 `powershell.config.json` 的 JSON 設定檔，以儲存啟動時間之前所需的一些設定 (例如 `ExecutionPolicy`)。</span><span class="sxs-lookup"><span data-stu-id="14461-292">Add a JSON config file called `powershell.config.json` in `$PSHome` to store some settings required before startup time (e.g. `ExecutionPolicy`).</span></span>
- <span data-ttu-id="14461-293">執行 Windows 的 EXE 時不會封鎖管線</span><span class="sxs-lookup"><span data-stu-id="14461-293">Don't block pipeline when running Windows EXE's</span></span>
- <span data-ttu-id="14461-294">已啟用 COM 集合的列舉。</span><span class="sxs-lookup"><span data-stu-id="14461-294">Enabled enumeration of COM collections.</span></span> <span data-ttu-id="14461-295">(#4553)</span><span class="sxs-lookup"><span data-stu-id="14461-295">(#4553)</span></span>

## <a name="cmdlet-updates"></a><span data-ttu-id="14461-296">Cmdlet 更新</span><span class="sxs-lookup"><span data-stu-id="14461-296">Cmdlet updates</span></span>

### <a name="new-cmdlets"></a><span data-ttu-id="14461-297">新的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14461-297">New cmdlets</span></span>

- <span data-ttu-id="14461-298">將 `Get-Uptime` 新增至 `Microsoft.PowerShell.Utility`。</span><span class="sxs-lookup"><span data-stu-id="14461-298">Add `Get-Uptime` to `Microsoft.PowerShell.Utility`.</span></span>
- <span data-ttu-id="14461-299">新增 `Remove-Alias` 命令。</span><span class="sxs-lookup"><span data-stu-id="14461-299">Add `Remove-Alias` Command.</span></span> <span data-ttu-id="14461-300">(#5143) (感謝 [@PowershellNinja](https://github.com/PowershellNinja)！)</span><span class="sxs-lookup"><span data-stu-id="14461-300">(#5143) (Thanks [@PowershellNinja](https://github.com/PowershellNinja)!)</span></span>
- <span data-ttu-id="14461-301">將 `Remove-Service` 新增至管理模組。</span><span class="sxs-lookup"><span data-stu-id="14461-301">Add `Remove-Service` to Management module.</span></span> <span data-ttu-id="14461-302">(#4858) (感謝 [@joandrsn](https://github.com/joandrsn)！)</span><span class="sxs-lookup"><span data-stu-id="14461-302">(#4858) (Thanks [@joandrsn](https://github.com/joandrsn)!)</span></span>

### <a name="web-cmdlets"></a><span data-ttu-id="14461-303">Web Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14461-303">Web cmdlets</span></span>

- <span data-ttu-id="14461-304">新增 Web Cmdlet 的憑證驗證支援。</span><span class="sxs-lookup"><span data-stu-id="14461-304">Add certificate authentication support for web cmdlets.</span></span> <span data-ttu-id="14461-305">(#4646) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-305">(#4646) (Thanks [@markekraus](https://github.com/markekraus))</span></span>
- <span data-ttu-id="14461-306">將內容標頭的支援新增至 Web Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-306">Add support for content headers to web cmdlets.</span></span> <span data-ttu-id="14461-307">(#4494 與 #4640) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-307">(#4494 & #4640) (Thanks [@markekraus](https://github.com/markekraus))</span></span>
- <span data-ttu-id="14461-308">將多個連結標頭支援新增至 Web Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-308">Add multiple link header support to Web Cmdlets.</span></span> <span data-ttu-id="14461-309">(#5265) (感謝 [@markekraus](https://github.com/markekraus)！)</span><span class="sxs-lookup"><span data-stu-id="14461-309">(#5265) (Thanks [@markekraus](https://github.com/markekraus)!)</span></span>
- <span data-ttu-id="14461-310">Web Cmdlet 中支援連結標頭分頁 (#3828)</span><span class="sxs-lookup"><span data-stu-id="14461-310">Support Link header pagination in web cmdlets (#3828)</span></span>
  - <span data-ttu-id="14461-311">針對 `Invoke-WebRequest`，回應包含連結標頭時，我們會將 RelationLink 屬性 (property) 建立為呈現 URL 和 `rel` 屬性 (attribute) 的 Dictionary，並確定 URL 是絕對 URL，讓開發人員更方便使用。</span><span class="sxs-lookup"><span data-stu-id="14461-311">For `Invoke-WebRequest`, when the response includes a Link header we create a RelationLink property as a Dictionary representing the URLs and `rel` attributes and ensure the URLs are absolute to make it easier for the developer to use.</span></span>
  - <span data-ttu-id="14461-312">針對 `Invoke-RestMethod`，回應包含連結標頭時，我們會公開 `-FollowRelLink` 參數以自動遵循 `next` `rel` 連結，直到它們不再存在或叫用選擇性 `-MaximumFollowRelLink` 參數值。</span><span class="sxs-lookup"><span data-stu-id="14461-312">For `Invoke-RestMethod`, when the response includes a Link header we expose a `-FollowRelLink` switch to automatically follow `next` `rel` links until they no longer exist or once we hit the optional `-MaximumFollowRelLink` parameter value.</span></span>
- <span data-ttu-id="14461-313">將 `-CustomMethod` 參數新增至 Web Cmdlet，以允許非標準方法動詞。</span><span class="sxs-lookup"><span data-stu-id="14461-313">Add `-CustomMethod` parameter to web cmdlets to allow for non-standard method verbs.</span></span> <span data-ttu-id="14461-314">(#3142) (感謝 [@Lee303](https://github.com/Lee303)！)</span><span class="sxs-lookup"><span data-stu-id="14461-314">(#3142) (Thanks to [@Lee303](https://github.com/Lee303)!)</span></span>
- <span data-ttu-id="14461-315">將 `SslProtocol` 支援新增至 Web Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-315">Add `SslProtocol` support to Web Cmdlets.</span></span> <span data-ttu-id="14461-316">(#5329) (感謝 [@markekraus](https://github.com/markekraus)！)</span><span class="sxs-lookup"><span data-stu-id="14461-316">(#5329) (Thanks [@markekraus](https://github.com/markekraus)!)</span></span>
- <span data-ttu-id="14461-317">將多部分支援新增至 Web Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-317">Add Multipart support to web cmdlets.</span></span> <span data-ttu-id="14461-318">(#4782) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-318">(#4782) (Thanks [@markekraus](https://github.com/markekraus))</span></span>
- <span data-ttu-id="14461-319">將 `-NoProxy` 新增至 Web Cmdlet，讓它們忽略整個系統 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="14461-319">Add `-NoProxy` to web cmdlets so that they ignore the system-wide proxy setting.</span></span> <span data-ttu-id="14461-320">(#3447) (感謝 [@TheFlyingCorpse](https://github.com/TheFlyingCorpse)！)</span><span class="sxs-lookup"><span data-stu-id="14461-320">(#3447) (Thanks to [@TheFlyingCorpse](https://github.com/TheFlyingCorpse)!)</span></span>
- <span data-ttu-id="14461-321">Web Cmdlet 的使用者代理程式現在報告作業系統平台 (#4937) (感謝 [@LDSpits](https://github.com/LDSpits))</span><span class="sxs-lookup"><span data-stu-id="14461-321">User Agent of Web Cmdlets now reports the OS platform (#4937) (Thanks [@LDSpits](https://github.com/LDSpits))</span></span>
- <span data-ttu-id="14461-322">將 `-SkipHeaderValidation` 參數新增至 Web Cmdlet 以支援新增標頭，而不驗證標頭值。</span><span class="sxs-lookup"><span data-stu-id="14461-322">Add `-SkipHeaderValidation` switch to web cmdlets to support adding headers without validating the header value.</span></span> <span data-ttu-id="14461-323">(#4085)</span><span class="sxs-lookup"><span data-stu-id="14461-323">(#4085)</span></span>
- <span data-ttu-id="14461-324">必要時，讓 Web Cmdlet 不驗證伺服器的 HTTPS 憑證。</span><span class="sxs-lookup"><span data-stu-id="14461-324">Enable web cmdlets to not validate the HTTPS certificate of the server if required.</span></span>
- <span data-ttu-id="14461-325">將驗證參數新增至 Web Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-325">Add authentication parameters to web cmdlets.</span></span> <span data-ttu-id="14461-326">(#5052) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-326">(#5052) (Thanks [@markekraus](https://github.com/markekraus))</span></span>
  - <span data-ttu-id="14461-327">新增提供三個選項的 `-Authentication`：Basic、OAuth 與 Bearer。</span><span class="sxs-lookup"><span data-stu-id="14461-327">Add `-Authentication` that provides three options: Basic, OAuth, and Bearer.</span></span>
  - <span data-ttu-id="14461-328">新增 `-Token`，以取得 [OAuth] 和 [持有人] 選項的持有人權杖。</span><span class="sxs-lookup"><span data-stu-id="14461-328">Add `-Token` to get the bearer token for OAuth and Bearer options.</span></span>
  - <span data-ttu-id="14461-329">新增 `-AllowUnencryptedAuthentication`，以略過任何非 HTTPS 的傳輸配置所提供的驗證。</span><span class="sxs-lookup"><span data-stu-id="14461-329">Add `-AllowUnencryptedAuthentication` to bypass authentication that is provided for any transport scheme other than HTTPS.</span></span>
- <span data-ttu-id="14461-330">將 `-ResponseHeadersVariable` 新增至 `Invoke-RestMethod`，以啟用擷取回應標頭。</span><span class="sxs-lookup"><span data-stu-id="14461-330">Add `-ResponseHeadersVariable` to `Invoke-RestMethod` to enable the capture of response headers.</span></span> <span data-ttu-id="14461-331">(#4888) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-331">(#4888) (Thanks [@markekraus](https://github.com/markekraus))</span></span>
- <span data-ttu-id="14461-332">修正 Web Cmdlet，以在回應狀態碼為不成功時於例外狀況中包含 HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="14461-332">Fix web cmdlets to include the HTTP response in the exception when the response status code is not success.</span></span> <span data-ttu-id="14461-333">(#3201)</span><span class="sxs-lookup"><span data-stu-id="14461-333">(#3201)</span></span>
- <span data-ttu-id="14461-334">將 Web Cmdlet `UserAgent` 從 `WindowsPowerShell` 變更為 `PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="14461-334">Change web cmdlets `UserAgent` from `WindowsPowerShell` to `PowerShell`.</span></span> <span data-ttu-id="14461-335">(#4914) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-335">(#4914) (Thanks [@markekraus](https://github.com/markekraus))</span></span>
- <span data-ttu-id="14461-336">將明確 `ContentType` 偵測新增至 `Invoke-RestMethod` (#4692)</span><span class="sxs-lookup"><span data-stu-id="14461-336">Add explicit `ContentType` detection to `Invoke-RestMethod` (#4692)</span></span>
- <span data-ttu-id="14461-337">修正 Web Cmdlet `-SkipHeaderValidation`，以使用非標準使用者代理程式標頭。</span><span class="sxs-lookup"><span data-stu-id="14461-337">Fix web cmdlets `-SkipHeaderValidation` to work with non-standard User-Agent headers.</span></span> <span data-ttu-id="14461-338">(#4479 與 #4512) (感謝 [@markekraus](https://github.com/markekraus))</span><span class="sxs-lookup"><span data-stu-id="14461-338">(#4479 & #4512) (Thanks [@markekraus](https://github.com/markekraus))</span></span>

### <a name="json-cmdlets"></a><span data-ttu-id="14461-339">JSON Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14461-339">JSON cmdlets</span></span>

- <span data-ttu-id="14461-340">將 `-AsHashtable` 新增至 `ConvertFrom-Json`，以改回傳回 `Hashtable`。</span><span class="sxs-lookup"><span data-stu-id="14461-340">Add `-AsHashtable` to `ConvertFrom-Json` to return a `Hashtable` instead.</span></span> <span data-ttu-id="14461-341">(#5043) (感謝 [@bergmeister](https://github.com/bergmeister)！)</span><span class="sxs-lookup"><span data-stu-id="14461-341">(#5043) (Thanks [@bergmeister](https://github.com/bergmeister)!)</span></span>
- <span data-ttu-id="14461-342">搭配使用更美觀的格式器與 `ConvertTo-Json` 輸出。</span><span class="sxs-lookup"><span data-stu-id="14461-342">Use prettier formatter with `ConvertTo-Json` output.</span></span> <span data-ttu-id="14461-343">(#2787) (感謝 @kittholland！)</span><span class="sxs-lookup"><span data-stu-id="14461-343">(#2787) (Thanks to @kittholland!)</span></span>
- <span data-ttu-id="14461-344">將 `Jobject` 序列化支援新增至 `ConvertTo-Json`。</span><span class="sxs-lookup"><span data-stu-id="14461-344">Add `Jobject` serialization support to `ConvertTo-Json`.</span></span> <span data-ttu-id="14461-345">(#5141)</span><span class="sxs-lookup"><span data-stu-id="14461-345">(#5141)</span></span>
- <span data-ttu-id="14461-346">修正 `ConvertFrom-Json`，以還原序列化管線中一起建構完整 JSON 字串的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="14461-346">Fix `ConvertFrom-Json` to deserialize an array of strings from the pipeline that together construct a complete JSON string.</span></span>
  <span data-ttu-id="14461-347">這會修正新行破壞 JSON 剖析的情況。</span><span class="sxs-lookup"><span data-stu-id="14461-347">This fixes some cases where newlines would break JSON parsing.</span></span> <span data-ttu-id="14461-348">(#3823)</span><span class="sxs-lookup"><span data-stu-id="14461-348">(#3823)</span></span>
- <span data-ttu-id="14461-349">移除針對 `System.Array` 所定義的 `AliasProperty "Count"`。</span><span class="sxs-lookup"><span data-stu-id="14461-349">Remove the `AliasProperty "Count"` defined for `System.Array`.</span></span>
  <span data-ttu-id="14461-350">這會移除部分 `ConvertFrom-Json` 輸出的多餘 `Count` 屬性。</span><span class="sxs-lookup"><span data-stu-id="14461-350">This removes the extraneous `Count` property on some `ConvertFrom-Json` output.</span></span> <span data-ttu-id="14461-351">(#3231) (感謝 [@PetSerAl](https://github.com/PetSerAl)！)</span><span class="sxs-lookup"><span data-stu-id="14461-351">(#3231) (Thanks to [@PetSerAl](https://github.com/PetSerAl)!)</span></span>

### <a name="csv-cmdlets"></a><span data-ttu-id="14461-352">CSV Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14461-352">CSV cmdlets</span></span>

- <span data-ttu-id="14461-353">`Import-Csv` 現在支援 W3C 擴充記錄檔格式 (#2482) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-353">`Import-Csv` now supports the W3C Extended Log File Format (#2482) (Thanks [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-354">新增對 `Import-Csv` 和 `ConvertFrom-Csv` 的 `PSTypeName` 支援。</span><span class="sxs-lookup"><span data-stu-id="14461-354">Add `PSTypeName` Support for `Import-Csv` and `ConvertFrom-Csv`.</span></span> <span data-ttu-id="14461-355">(#5389) (感謝 [@markekraus](https://github.com/markekraus)！)</span><span class="sxs-lookup"><span data-stu-id="14461-355">(#5389) (Thanks [@markekraus](https://github.com/markekraus)!)</span></span>
- <span data-ttu-id="14461-356">讓 `Import-Csv` 支援 `CR`、`LF` 和 `CRLF` 作為行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="14461-356">Make `Import-Csv` support `CR`, `LF`, and `CRLF` as line delimiters.</span></span> <span data-ttu-id="14461-357">(#5363) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-357">(#5363) (Thanks [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-358">將 `-NoTypeInformation` 設為 `Export-Csv` 和 `ConvertTo-Csv` 的預設值。</span><span class="sxs-lookup"><span data-stu-id="14461-358">Make `-NoTypeInformation` the default on `Export-Csv` and `ConvertTo-Csv`.</span></span> <span data-ttu-id="14461-359">(#5164) (感謝 [@markekraus](https://github.com/markekraus)！)</span><span class="sxs-lookup"><span data-stu-id="14461-359">(#5164) (Thanks [@markekraus](https://github.com/markekraus)!)</span></span>

### <a name="service-cmdlets"></a><span data-ttu-id="14461-360">服務 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14461-360">Service cmdlets</span></span>

- <span data-ttu-id="14461-361">將 `UserName`、`Description`、`DelayedAutoStart`、`BinaryPathName` 和 `StartupType` 屬性新增至 `Get-Service` 所傳回的 `ServiceController` 物件。</span><span class="sxs-lookup"><span data-stu-id="14461-361">Add properties `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, and `StartupType` to the `ServiceController` objects returned by `Get-Service`.</span></span> <span data-ttu-id="14461-362">(#4907) (感謝 [@joandrsn](https://github.com/joandrsn))</span><span class="sxs-lookup"><span data-stu-id="14461-362">(#4907) (Thanks [@joandrsn](https://github.com/joandrsn))</span></span>
- <span data-ttu-id="14461-363">新增功能以在 `Set-Service` 命令上設定認證。</span><span class="sxs-lookup"><span data-stu-id="14461-363">Add functionality to set credentials on `Set-Service` command.</span></span> <span data-ttu-id="14461-364">(#4844) (感謝 [@joandrsn](https://github.com/joandrsn))</span><span class="sxs-lookup"><span data-stu-id="14461-364">(#4844) (Thanks [@joandrsn](https://github.com/joandrsn))</span></span>

### <a name="other-cmdlets"></a><span data-ttu-id="14461-365">其他 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="14461-365">Other cmdlets</span></span>

- <span data-ttu-id="14461-366">將參數新增至稱為 `-FollowSymlink` 並依需求周遊符號連結的 `Get-ChildItem` ，同時檢查連結迴圈。</span><span class="sxs-lookup"><span data-stu-id="14461-366">Add a parameter to `Get-ChildItem` called `-FollowSymlink` that traverses symlinks on demand, with checks for link loops.</span></span> <span data-ttu-id="14461-367">(#4020)</span><span class="sxs-lookup"><span data-stu-id="14461-367">(#4020)</span></span>
- <span data-ttu-id="14461-368">更新 `Add-Type` 以支援 `CSharpVersion7`。</span><span class="sxs-lookup"><span data-stu-id="14461-368">Update `Add-Type` to support `CSharpVersion7`.</span></span> <span data-ttu-id="14461-369">(#3933) (感謝 [@iSazonov](https://github.com/iSazonov))</span><span class="sxs-lookup"><span data-stu-id="14461-369">(#3933) (Thanks to [@iSazonov](https://github.com/iSazonov))</span></span>
- <span data-ttu-id="14461-370">在找到較好的解決方案之前，因使用不支援的 API 而移除 `Microsoft.PowerShell.LocalAccounts` 模組。</span><span class="sxs-lookup"><span data-stu-id="14461-370">Remove the `Microsoft.PowerShell.LocalAccounts` module due to the use of unsupported APIs until a better solution is found.</span></span> <span data-ttu-id="14461-371">(#4302)</span><span class="sxs-lookup"><span data-stu-id="14461-371">(#4302)</span></span>
- <span data-ttu-id="14461-372">在找到較好的解決方案之前，因使用不支援的 API 而移除 `Microsoft.PowerShell.Diagnostics` 中的 `*-Counter` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="14461-372">Remove the `*-Counter` cmdlets in `Microsoft.PowerShell.Diagnostics` due to the use of unsupported APIs until a better solution is found.</span></span> <span data-ttu-id="14461-373">(#4303)</span><span class="sxs-lookup"><span data-stu-id="14461-373">(#4303)</span></span>
- <span data-ttu-id="14461-374">新增對 `Invoke-Item -Path <folder>` 的支援。</span><span class="sxs-lookup"><span data-stu-id="14461-374">Add support for `Invoke-Item -Path <folder>`.</span></span> <span data-ttu-id="14461-375">(#4262)</span><span class="sxs-lookup"><span data-stu-id="14461-375">(#4262)</span></span>
- <span data-ttu-id="14461-376">將 `-Extension` 和 `-LeafBase` 參數新增至 `Split-Path`，讓您可以分割副檔名與檔案名稱其餘部分之間的路徑。</span><span class="sxs-lookup"><span data-stu-id="14461-376">Add `-Extension` and `-LeafBase` switches to `Split-Path` so that you can split paths between the filename extension and the rest of the filename.</span></span> <span data-ttu-id="14461-377">(#2721) (感謝 [@powercode](https://github.com/powercode)！)</span><span class="sxs-lookup"><span data-stu-id="14461-377">(#2721) (Thanks to [@powercode](https://github.com/powercode)!)</span></span>
- <span data-ttu-id="14461-378">將 `-Top` 和 `-Bottom` 參數新增至 `Sort-Object` 以進行「前/後 N 個」排序</span><span class="sxs-lookup"><span data-stu-id="14461-378">Add parameters `-Top` and `-Bottom` to `Sort-Object` for Top/Bottom N sort</span></span>
- <span data-ttu-id="14461-379">將 `CodeProperty "Parent"` 新增至 `System.Diagnostics.Process`，以公開處理序的父處理序。</span><span class="sxs-lookup"><span data-stu-id="14461-379">Expose a process' parent process by adding the `CodeProperty "Parent"` to `System.Diagnostics.Process`.</span></span> <span data-ttu-id="14461-380">(#2850) (感謝 [@powercode](https://github.com/powercode)！)</span><span class="sxs-lookup"><span data-stu-id="14461-380">(#2850) (Thanks to [@powercode](https://github.com/powercode)!)</span></span>
- <span data-ttu-id="14461-381">針對 `Get-Process` 的記憶體資料行，使用 MB，而非 KB</span><span class="sxs-lookup"><span data-stu-id="14461-381">Use MB instead of KB for memory columns of `Get-Process`</span></span>
- <span data-ttu-id="14461-382">新增 `Out-String` 的 `-NoNewLine` 參數。</span><span class="sxs-lookup"><span data-stu-id="14461-382">Add `-NoNewLine` switch for `Out-String`.</span></span> <span data-ttu-id="14461-383">(#5056) (感謝 [@raghav710](https://github.com/raghav710))</span><span class="sxs-lookup"><span data-stu-id="14461-383">(#5056) (Thanks [@raghav710](https://github.com/raghav710))</span></span>
- <span data-ttu-id="14461-384">`Move-Item` Cmdlet 接受 `-Include`、`-Exclude` 和 `-Filter` 參數。</span><span class="sxs-lookup"><span data-stu-id="14461-384">`Move-Item` cmdlet honors `-Include`, `-Exclude`, and `-Filter` parameters.</span></span> <span data-ttu-id="14461-385">(#3878)</span><span class="sxs-lookup"><span data-stu-id="14461-385">(#3878)</span></span>
- <span data-ttu-id="14461-386">允許在 `Remove-Item` 的登錄路徑中使用 `*`。</span><span class="sxs-lookup"><span data-stu-id="14461-386">Allow `*` to be used in registry path for `Remove-Item`.</span></span> <span data-ttu-id="14461-387">(#4866)</span><span class="sxs-lookup"><span data-stu-id="14461-387">(#4866)</span></span>
- <span data-ttu-id="14461-388">將 `-Title` 新增至 `Get-Credential`，並統一跨平台的提示體驗。</span><span class="sxs-lookup"><span data-stu-id="14461-388">Add `-Title` to `Get-Credential` and unify the prompt experience across platforms.</span></span>
- <span data-ttu-id="14461-389">將 `-TimeOut` 參數新增至 `Test-Connection`。</span><span class="sxs-lookup"><span data-stu-id="14461-389">Add the `-TimeOut` parameter to `Test-Connection`.</span></span> <span data-ttu-id="14461-390">(#2492)</span><span class="sxs-lookup"><span data-stu-id="14461-390">(#2492)</span></span>
- <span data-ttu-id="14461-391">`Get-AuthenticodeSignature` Cmdlet 現在可以取得檔案簽章時間戳記。</span><span class="sxs-lookup"><span data-stu-id="14461-391">`Get-AuthenticodeSignature` cmdlets can now get file signature timestamp.</span></span> <span data-ttu-id="14461-392">(#4061)</span><span class="sxs-lookup"><span data-stu-id="14461-392">(#4061)</span></span>
- <span data-ttu-id="14461-393">從 `Get-Help` 移除不支援的 `-ShowWindow` 參數。</span><span class="sxs-lookup"><span data-stu-id="14461-393">Remove unsupported `-ShowWindow` switch from `Get-Help`.</span></span> <span data-ttu-id="14461-394">(#4903)</span><span class="sxs-lookup"><span data-stu-id="14461-394">(#4903)</span></span>
- <span data-ttu-id="14461-395">修正 `Get-Content -Delimiter`，以在所傳回陣列項目中不包含分隔符號 (#3706) (感謝 [@mklement0](https://github.com/mklement0))</span><span class="sxs-lookup"><span data-stu-id="14461-395">Fix `Get-Content -Delimiter` to not include the delimiter in the array elements returned (#3706) (Thanks [@mklement0](https://github.com/mklement0))</span></span>
- <span data-ttu-id="14461-396">將 `Meta`、`Charset` 和 `Transitional` 參數新增至 `ConvertTo-HTML` (#4184) (感謝 [@ergo3114](https://github.com/ergo3114))</span><span class="sxs-lookup"><span data-stu-id="14461-396">Add `Meta`, `Charset`, and `Transitional` parameters to `ConvertTo-HTML` (#4184) (Thanks [@ergo3114](https://github.com/ergo3114))</span></span>
- <span data-ttu-id="14461-397">將 `WindowsUBR` 和 `WindowsVersion` 屬性新增至 `Get-ComputerInfo` 結果</span><span class="sxs-lookup"><span data-stu-id="14461-397">Add `WindowsUBR` and `WindowsVersion` properties to `Get-ComputerInfo` result</span></span>
- <span data-ttu-id="14461-398">將 `-Group` 參數新增至 `Get-Verb`</span><span class="sxs-lookup"><span data-stu-id="14461-398">Add `-Group` parameter to `Get-Verb`</span></span>
- <span data-ttu-id="14461-399">將 `ShouldProcess` 支援新增至 `New-FileCatalog` 和 `Test-FileCatalog` (修正 `-WhatIf` 和 `-Confirm`)。</span><span class="sxs-lookup"><span data-stu-id="14461-399">Add `ShouldProcess` support to `New-FileCatalog` and `Test-FileCatalog` (fixes `-WhatIf` and `-Confirm`).</span></span> <span data-ttu-id="14461-400">(#3074) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-400">(#3074) (Thanks to [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-401">將 `-WhatIf` 參數新增至 `Start-Process` Cmdlet (#4735) (感謝 [@sarithsutha](https://github.com/sarithsutha))</span><span class="sxs-lookup"><span data-stu-id="14461-401">Add `-WhatIf` switch to `Start-Process` cmdlet (#4735) (Thanks [@sarithsutha](https://github.com/sarithsutha))</span></span>
- <span data-ttu-id="14461-402">針對 `ValidateNotNullOrEmpty` 新增太多現有參數。</span><span class="sxs-lookup"><span data-stu-id="14461-402">Add `ValidateNotNullOrEmpty` too many existing parameters.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="14461-403">Tab 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="14461-403">Tab completion</span></span>

- <span data-ttu-id="14461-404">已根據執行階段變數值增強 Tab 鍵自動完成中的型別推斷。</span><span class="sxs-lookup"><span data-stu-id="14461-404">Enhanced the type inference in tab completion based on runtime variable values.</span></span> <span data-ttu-id="14461-405">(#2744) (感謝 [@powercode](https://github.com/powercode)！)在下列情況下，這會啟用 Tab 鍵自動完成：</span><span class="sxs-lookup"><span data-stu-id="14461-405">(#2744) (Thanks to [@powercode](https://github.com/powercode)!) This enables tab completion in situations like:</span></span>

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- <span data-ttu-id="14461-406">新增 `Select-Object` 之 `-Property` 的雜湊表 Tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="14461-406">Add Hashtable tab completion for `-Property` of `Select-Object`.</span></span> <span data-ttu-id="14461-407">(#3625) (感謝 [@powercode](https://github.com/powercode))</span><span class="sxs-lookup"><span data-stu-id="14461-407">(#3625) (Thanks to [@powercode](https://github.com/powercode))</span></span>
- <span data-ttu-id="14461-408">啟用 `Select-Object` 之 `-ExcludeProperty` 和 `-ExpandProperty` 的引數自動完成。</span><span class="sxs-lookup"><span data-stu-id="14461-408">Enable argument auto-completion for `-ExcludeProperty` and `-ExpandProperty` of `Select-Object`.</span></span> <span data-ttu-id="14461-409">(#3443) (感謝 [@iSazonov](https://github.com/iSazonov)！)</span><span class="sxs-lookup"><span data-stu-id="14461-409">(#3443) (Thanks to [@iSazonov](https://github.com/iSazonov)!)</span></span>
- <span data-ttu-id="14461-410">修正 Tab 鍵自動完成中的 Bug，讓 `native.exe --<tab>` 呼叫原生完成器。</span><span class="sxs-lookup"><span data-stu-id="14461-410">Fix a bug in tab completion to make `native.exe --<tab>` call into native completer.</span></span> <span data-ttu-id="14461-411">(#3633) (感謝 [@powercode](https://github.com/powercode)！)</span><span class="sxs-lookup"><span data-stu-id="14461-411">(#3633) (Thanks to [@powercode](https://github.com/powercode)!)</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="14461-412">最新變更</span><span class="sxs-lookup"><span data-stu-id="14461-412">Breaking changes</span></span>

<span data-ttu-id="14461-413">我們已引進 PowerShell Core 6.0 中的許多最新變更。</span><span class="sxs-lookup"><span data-stu-id="14461-413">We've introduced a number of breaking changes in PowerShell Core 6.0.</span></span>
<span data-ttu-id="14461-414">若要更詳細地深入閱讀這些變更，請參閱 [PowerShell Core 6.0 的最新變更][breaking-changes]。</span><span class="sxs-lookup"><span data-stu-id="14461-414">To read more about them in detail, see [Breaking Changes in PowerShell Core 6.0][breaking-changes].</span></span>

## <a name="debugging"></a><span data-ttu-id="14461-415">偵錯</span><span class="sxs-lookup"><span data-stu-id="14461-415">Debugging</span></span>

- <span data-ttu-id="14461-416">`Invoke-Command -ComputerName` 的遠端逐步執行偵錯支援。</span><span class="sxs-lookup"><span data-stu-id="14461-416">Support for remote step-in debugging for `Invoke-Command -ComputerName`.</span></span> <span data-ttu-id="14461-417">(#3015)</span><span class="sxs-lookup"><span data-stu-id="14461-417">(#3015)</span></span>
- <span data-ttu-id="14461-418">啟用 PowerShell Core 中的繫結器偵錯記錄</span><span class="sxs-lookup"><span data-stu-id="14461-418">Enable binder debug logging in PowerShell Core</span></span>

## <a name="filesystem-updates"></a><span data-ttu-id="14461-419">Filesystem 更新</span><span class="sxs-lookup"><span data-stu-id="14461-419">Filesystem updates</span></span>

- <span data-ttu-id="14461-420">從 UNC 路徑啟用 Filesystem 提供者的使用。</span><span class="sxs-lookup"><span data-stu-id="14461-420">Enable usage of the Filesystem provider from a UNC path.</span></span> <span data-ttu-id="14461-421">($4998)</span><span class="sxs-lookup"><span data-stu-id="14461-421">($4998)</span></span>
- <span data-ttu-id="14461-422">`Split-Path` 現在使用 UNC root</span><span class="sxs-lookup"><span data-stu-id="14461-422">`Split-Path` now works with UNC roots</span></span>
- <span data-ttu-id="14461-423">現在，無引數之 `cd` 的行為會如同 `cd ~`</span><span class="sxs-lookup"><span data-stu-id="14461-423">`cd` with no arguments now behaves as `cd ~`</span></span>
- <span data-ttu-id="14461-424">已修正 PowerShell Core，允許使用長度超過 260 個字元的路徑。</span><span class="sxs-lookup"><span data-stu-id="14461-424">Fixed PowerShell Core to allow use of paths that are more than 260 characters long.</span></span> <span data-ttu-id="14461-425">(#3960)</span><span class="sxs-lookup"><span data-stu-id="14461-425">(#3960)</span></span>

## <a name="bug-fixes-and-performance-improvements"></a><span data-ttu-id="14461-426">Bug 修正和效能改善</span><span class="sxs-lookup"><span data-stu-id="14461-426">Bug fixes and performance improvements</span></span>

<span data-ttu-id="14461-427">我們已跨 PowerShell 進行「許多」  效能改善，包含在啟動時間、各種內建 Cmdlet 以及與原生二進位檔的互動中。</span><span class="sxs-lookup"><span data-stu-id="14461-427">We've made *many* improvements to performance across PowerShell, including in startup time, various built-in cmdlets, and interaction with native binaries.</span></span>

<span data-ttu-id="14461-428">我們也已修正 PowerShell Core 內的一些 Bug。</span><span class="sxs-lookup"><span data-stu-id="14461-428">We've also fixed a number of bugs within PowerShell Core.</span></span>
<span data-ttu-id="14461-429">如需修正和變更的完整清單，請參閱 GitHub 上的[變更記錄][]。</span><span class="sxs-lookup"><span data-stu-id="14461-429">For a complete list of fixes and changes, check out our [changelog][] on GitHub.</span></span>

## <a name="telemetry"></a><span data-ttu-id="14461-430">遙測</span><span class="sxs-lookup"><span data-stu-id="14461-430">Telemetry</span></span>

- <span data-ttu-id="14461-431">PowerShell Core 6.0 已將遙測新增至主控台主機，以報告兩個值 (#3620)：</span><span class="sxs-lookup"><span data-stu-id="14461-431">PowerShell Core 6.0 added telemetry to the console host to report two values (#3620):</span></span>
  - <span data-ttu-id="14461-432">作業系統平台 (`$PSVersionTable.OSDescription`)</span><span class="sxs-lookup"><span data-stu-id="14461-432">the OS platform (`$PSVersionTable.OSDescription`)</span></span>
  - <span data-ttu-id="14461-433">確切 PowerShell 版本 (`$PSVersionTable.GitCommitId`)</span><span class="sxs-lookup"><span data-stu-id="14461-433">the exact version of PowerShell (`$PSVersionTable.GitCommitId`)</span></span>

<span data-ttu-id="14461-434">如果您想要退出這個遙測，只需使用下列其中一個值來建立 `POWERSHELL_TELEMETRY_OPTOUT` 環境變數：`true`、`1` 或 `yes`。</span><span class="sxs-lookup"><span data-stu-id="14461-434">If you want to opt-out of this telemetry, simply create `POWERSHELL_TELEMETRY_OPTOUT` environment variable with one of the following values: `true`, `1` or `yes`.</span></span>
<span data-ttu-id="14461-435">建立變數會略過第一次執行 PowerShell 之前的所有遙測。</span><span class="sxs-lookup"><span data-stu-id="14461-435">Creating the variable bypasses all telemetry even before the first run of PowerShell.</span></span>
<span data-ttu-id="14461-436">我們也打算公開此遙測資料，以及我們在[社群儀表板][community-dashboard]中從遙測搜集到的見解。</span><span class="sxs-lookup"><span data-stu-id="14461-436">We also plan on exposing this telemetry data and the insights we glean from the telemetry in the [community dashboard][community-dashboard].</span></span>
<span data-ttu-id="14461-437">您可以深入了解我們如何在這個[部落格文章][telemetry-blog]中使用這項資料。</span><span class="sxs-lookup"><span data-stu-id="14461-437">You can find out more about how we use this data in this [blog post][telemetry-blog].</span></span>

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[變更記錄]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET 部落格]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[常見問題集]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[FAQ]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
