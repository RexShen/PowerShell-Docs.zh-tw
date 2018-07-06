---
ms.date: 05/17/2018
keywords: powershell, core
title: PowerShell Core 6.0 的已知問題
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309603"
---
# <a name="known-issues-for-powershell-60"></a><span data-ttu-id="07fe1-103">PowerShell Core 6.0 的已知問題</span><span class="sxs-lookup"><span data-stu-id="07fe1-103">Known Issues for PowerShell 6.0</span></span>

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a><span data-ttu-id="07fe1-104">非 Windows 平台上的 PowerShell 已知問題</span><span class="sxs-lookup"><span data-stu-id="07fe1-104">Known Issues for PowerShell on Non-Windows Platforms</span></span>

<span data-ttu-id="07fe1-105">Linux 和 macOS 上的 Alpha 版 PowerShell 大部分功能都可運作，但有一些重大的限制和可用性問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-105">Alpha releases of PowerShell on Linux and macOS are mostly functional but do have some significant limitations and usability issues.</span></span> <span data-ttu-id="07fe1-106">Linux 和 macOS 上的 Beta 版 PowerShell 比 Alpha 版功能完整且穩定，但仍可能缺少某個功能集，而且可能包含錯誤 (bug)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-106">Beta releases of PowerShell on Linux and macOS are more functional and stable than alpha releases, but still may be lacking some set of features, and can contain bugs.</span></span> <span data-ttu-id="07fe1-107">在某些情況下，這些問題只是尚未修正的錯誤 (bug)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-107">In some cases, these issues are simply bugs that haven't been fixed yet.</span></span> <span data-ttu-id="07fe1-108">而針對其他情況 (像是 ls、cp 等的預設別名情況)，我們則正在向社群尋求有關我們所做選擇的意見反應。</span><span class="sxs-lookup"><span data-stu-id="07fe1-108">In other cases (as with the default aliases for ls, cp, etc.), we are looking for feedback from the community regarding the choices we make.</span></span>

<span data-ttu-id="07fe1-109">注意：由於許多基礎子系統都很相似，因此 Linux 和 macOS 上的 PowerShell 在功能和錯誤 (bug) 方面都趨向於擁有相同的成熟度。</span><span class="sxs-lookup"><span data-stu-id="07fe1-109">Note: Due to the similarities of many underlying subsystems, PowerShell on Linux and macOS tend to share the same level of maturity in both features and bugs.</span></span> <span data-ttu-id="07fe1-110">除了下列所述之外，本節中的問題都同時適用於這兩種作業系統。</span><span class="sxs-lookup"><span data-stu-id="07fe1-110">Except as noted below, the issues in this section will apply to both operating systems.</span></span>

### <a name="case-sensitivity-in-powershell"></a><span data-ttu-id="07fe1-111">PowerShell 中的大小寫之分</span><span class="sxs-lookup"><span data-stu-id="07fe1-111">Case-sensitivity in PowerShell</span></span>

<span data-ttu-id="07fe1-112">在過去，除了幾個例外之外，PowerShell 一直是一律不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="07fe1-112">Historically, PowerShell has been uniformly case-insensitive, with few exceptions.</span></span> <span data-ttu-id="07fe1-113">在 UNIX 型作業系統中，是由檔案系統主導區分大小寫，而 PowerShell 則是遵守檔案系統的標準；這會透過一些明顯和不明顯的方式公開。</span><span class="sxs-lookup"><span data-stu-id="07fe1-113">On UNIX-like operating systems, the file system is predominantly case-sensitive and PowerShell adheres to the standard of the file system; this is exposed through a number of ways, obvious and non-obvious.</span></span>

#### <a name="directly"></a><span data-ttu-id="07fe1-114">直接</span><span class="sxs-lookup"><span data-stu-id="07fe1-114">Directly</span></span>

- <span data-ttu-id="07fe1-115">在 PowerShell 中指定檔案時，必須使用正確的大小寫。</span><span class="sxs-lookup"><span data-stu-id="07fe1-115">When specifying a file in PowerShell, the correct case must be used.</span></span>

#### <a name="indirectly"></a><span data-ttu-id="07fe1-116">間接</span><span class="sxs-lookup"><span data-stu-id="07fe1-116">Indirectly</span></span>

- <span data-ttu-id="07fe1-117">如果指令碼嘗試載入某個模組，而該模組名稱的大小寫不正確，載入模組時就會失敗。</span><span class="sxs-lookup"><span data-stu-id="07fe1-117">If a script tries to load a module and the module name is not cased correctly, then the module load will fail.</span></span> <span data-ttu-id="07fe1-118">如果參考模組時所依據的名稱與實際的檔案名稱不符，可能會導致現有的指令碼發生問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-118">This may cause a problem with existing scripts if the name by which the module is referenced doesn't match the actual file name.</span></span>
- <span data-ttu-id="07fe1-119">如果檔案名稱大小寫錯誤，Tab 鍵自動完成將不會自動完成。</span><span class="sxs-lookup"><span data-stu-id="07fe1-119">Tab-completion will not auto-complete if the file name case is wrong.</span></span> <span data-ttu-id="07fe1-120">要完成的片段必須大小寫正確。</span><span class="sxs-lookup"><span data-stu-id="07fe1-120">The fragment to complete must be cased properly.</span></span> <span data-ttu-id="07fe1-121">(用於完成類型名稱和類型成員的完成會區分大小寫)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-121">(Completion is case-insensitive for type name and type member completions.)</span></span>

### <a name="ps1-file-extensions"></a><span data-ttu-id="07fe1-122">.PS1 副檔名</span><span class="sxs-lookup"><span data-stu-id="07fe1-122">.PS1 File Extensions</span></span>

<span data-ttu-id="07fe1-123">PowerShell 指令碼的結尾必須是 `.ps1`，解譯器才能瞭解如何在目前的處理序中載入並執行它們。</span><span class="sxs-lookup"><span data-stu-id="07fe1-123">PowerShell scripts must end in `.ps1` for the interpreter to understand how to load and run them in the current process.</span></span> <span data-ttu-id="07fe1-124">在目前的處理序中執行指令碼是預期的 PowerShell 平常行為。</span><span class="sxs-lookup"><span data-stu-id="07fe1-124">Running scripts in the current process is the expected usual behavior for PowerShell.</span></span> <span data-ttu-id="07fe1-125">您可以將 `#!` 魔術數字新增到沒有 `.ps1` 副檔名的指令碼中，但這會導致指令碼在新的 PowerShell 執行個體中執行，而使得指令碼在交換物件時無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-125">The `#!` magic number may be added to a script that doesn't have a `.ps1` extension, but this will cause the script to be run in a new PowerShell instance preventing the script from working properly when interchanging objects.</span></span> <span data-ttu-id="07fe1-126">(注意：從 `bash` 或另一個殼層執行 PowerShell 指令碼時，可能會需要這樣的行為)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-126">(Note: this may be the desirable behavior when executing a PowerShell script from `bash` or another shell.)</span></span>

### <a name="missing-command-aliases"></a><span data-ttu-id="07fe1-127">缺少命令別名</span><span class="sxs-lookup"><span data-stu-id="07fe1-127">Missing command aliases</span></span>

<span data-ttu-id="07fe1-128">在 Linux/macOS 上，已移除基本命令的「便利別名」`ls`、`cp`、`mv`、`rm`、`cat`、`man`、`mount`、`ps`。</span><span class="sxs-lookup"><span data-stu-id="07fe1-128">On Linux/macOS, the "convenience aliases" for the basic commands `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` have been removed.</span></span> <span data-ttu-id="07fe1-129">在 Windows 上，為了使用者方便，PowerShell 提供一組與 Linux 命令名稱對應的別名。</span><span class="sxs-lookup"><span data-stu-id="07fe1-129">On Windows, PowerShell provides a set of aliases that map to Linux command names for user convenience.</span></span> <span data-ttu-id="07fe1-130">在 Linux/macOS 發行版本上的預設 PowerShell 中則已移除這些別名，以允許在不指定路徑的情況下，即可執行原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="07fe1-130">These aliases have been removed from the default PowerShell on Linux/macOS distributions, allowing the native executable to be run without specifying a path.</span></span>

<span data-ttu-id="07fe1-131">此做法有優缺點。</span><span class="sxs-lookup"><span data-stu-id="07fe1-131">There are pros and cons to doing this.</span></span> <span data-ttu-id="07fe1-132">移除別名可讓 PowerShell 使用者接觸到原生命令體驗，但會降低殼層中的功能，因為原生命令會傳回字串而不是物件。</span><span class="sxs-lookup"><span data-stu-id="07fe1-132">Removing the aliases exposes the native command experience to the PowerShell user, but reduces functionality in the shell because the native commands return strings instead of objects.</span></span>

> [!NOTE]
> <span data-ttu-id="07fe1-133">這正是 PowerShell 小組尋求意見反應的領域。</span><span class="sxs-lookup"><span data-stu-id="07fe1-133">This is an area where the PowerShell team is looking for feedback.</span></span>
> <span data-ttu-id="07fe1-134">慣用的解決方案是什麼？</span><span class="sxs-lookup"><span data-stu-id="07fe1-134">What is the preferred solution?</span></span> <span data-ttu-id="07fe1-135">我們應該維持這個做法，還是將便利別名加回？</span><span class="sxs-lookup"><span data-stu-id="07fe1-135">Should we leave it as is or add the convenience aliases back?</span></span> <span data-ttu-id="07fe1-136">請參閱[問題 #929](https://github.com/PowerShell/PowerShell/issues/929) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-136">See [Issue #929](https://github.com/PowerShell/PowerShell/issues/929).</span></span>

### <a name="missing-wildcard-globbing-support"></a><span data-ttu-id="07fe1-137">缺少萬用字元支援</span><span class="sxs-lookup"><span data-stu-id="07fe1-137">Missing Wildcard (globbing) Support</span></span>

<span data-ttu-id="07fe1-138">目前，PowerShell 執行萬用字元擴充的對象僅限 Windows 上的內建 Cmdlet、外部命令或二進位檔，以及 Linux 上的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="07fe1-138">Currently, PowerShell only does wildcard expansion (globbing) for built-in cmdlets on Windows, and for external commands or binaries as well as cmdlets on Linux.</span></span> <span data-ttu-id="07fe1-139">這意謂著 `ls
*.txt` 這類命令將會失敗，因為 PowerShell 不會擴充星號來比對檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="07fe1-139">This means that a command like `ls
*.txt` will fail because the asterisk will not be expanded to match file names.</span></span> <span data-ttu-id="07fe1-140">您可以藉由使用相當於 `ls` 的 PowerShell 內建命令來執行 `ls (gci *.txt | % name)`，或更簡單就執行 `gci *.txt`，以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-140">You can work around this by doing `ls (gci *.txt | % name)` or, more simply, `gci *.txt` using the PowerShell built-in equivalent to `ls`.</span></span>

<span data-ttu-id="07fe1-141">請參閱 [#954](https://github.com/PowerShell/PowerShell/issues/954) 來提供我們有關如何改進 Linux/macOS 上萬用字元體驗的意見反應。</span><span class="sxs-lookup"><span data-stu-id="07fe1-141">See [#954](https://github.com/PowerShell/PowerShell/issues/954) to give us feedback on how to improve the globbing experience on Linux/macOS.</span></span>

### <a name="net-framework-vs-net-core-framework"></a><span data-ttu-id="07fe1-142">.NET Framework 與 .NET Core Framework 的比較</span><span class="sxs-lookup"><span data-stu-id="07fe1-142">.NET Framework vs .NET Core Framework</span></span>

<span data-ttu-id="07fe1-143">Linux/macOS 上的 PowerShell 使用 .NET Core，這是 Microsoft Windows 上完整 .NET Framework 的子集。</span><span class="sxs-lookup"><span data-stu-id="07fe1-143">PowerShell on Linux/macOS uses .NET Core which is a subset of the full .NET Framework on Microsoft Windows.</span></span> <span data-ttu-id="07fe1-144">這相當重要，因為 PowerShell 可讓您直接存取基礎架構類型、方法等。因此，在 Windows 上執行的指令碼可能無法在非 Windows 平台上執行，因為架構差異的緣故。</span><span class="sxs-lookup"><span data-stu-id="07fe1-144">This is significant because PowerShell provides direct access to the underlying framework types, methods, etc. As a result, scripts that run on Windows may not run on non-Windows platforms because of the differences in the frameworks.</span></span> <span data-ttu-id="07fe1-145">如需有關 .NET Core Framework 的詳細資訊，請參閱 <https://dotnetfoundation.org/net-core> \(英文\)</span><span class="sxs-lookup"><span data-stu-id="07fe1-145">For more information about .NET Core Framework, see <https://dotnetfoundation.org/net-core></span></span>

<span data-ttu-id="07fe1-146">隨著 [.NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) 的推出，.NET Core 2.0 將會帶回許多出現在完整 .NET Framework 中的傳統類型和方法。</span><span class="sxs-lookup"><span data-stu-id="07fe1-146">With the advent of [.NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 will bring back many of the traditional types and methods present in the full .NET Framework.</span></span> <span data-ttu-id="07fe1-147">這意謂著 PowerShell Core 將能夠原封不動地載入許多傳統 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="07fe1-147">This means that PowerShell Core will be able to load many traditional Windows PowerShell modules without modification.</span></span> <span data-ttu-id="07fe1-148">您可以從[這裡](https://github.com/PowerShell/PowerShell/projects/4)追蹤我們的 .NET Standard 2.0 相關工作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-148">You can follow our .NET Standard 2.0 related work [here](https://github.com/PowerShell/PowerShell/projects/4).</span></span>

### <a name="redirection-issues"></a><span data-ttu-id="07fe1-149">重新導向問題</span><span class="sxs-lookup"><span data-stu-id="07fe1-149">Redirection Issues</span></span>

<span data-ttu-id="07fe1-150">所有平台上的 PowerShell 都不支援輸入重新導向。</span><span class="sxs-lookup"><span data-stu-id="07fe1-150">Input redirection is not supported in PowerShell on any platform.</span></span>
[<span data-ttu-id="07fe1-151">問題 #1629</span><span class="sxs-lookup"><span data-stu-id="07fe1-151">Issue #1629</span></span>](https://github.com/PowerShell/PowerShell/issues/1629)

<span data-ttu-id="07fe1-152">請使用 `Get-Content` 將檔案的內容寫入至管線中。</span><span class="sxs-lookup"><span data-stu-id="07fe1-152">Use `Get-Content` to write the contents of a file into the pipeline.</span></span>

<span data-ttu-id="07fe1-153">使用預設的 UTF-8 編碼時，重新導向的輸出將會包含 Unicode 位元組順序標記 (BOM)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-153">Redirected output will contain the Unicode byte order mark (BOM) when the default UTF-8 encoding is used.</span></span> <span data-ttu-id="07fe1-154">與不預期會有 BOM 的公用程式搭配運作，或將 BOM 附加至檔案時，BOM 會導致發生問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-154">The BOM will cause problems when working with utilities that do not expect it or when appending to a file.</span></span> <span data-ttu-id="07fe1-155">請使用 `-Encoding Ascii` 來寫入 ASCII 文字 (因為不是 Unicode，所以不會有 BOM)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-155">Use `-Encoding Ascii` to write ASCII text (which, not being Unicode, will not have a BOM).</span></span> <span data-ttu-id="07fe1-156">(注意：請參閱 [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71)，以提供有關改進所有平台 PowerShell Core 編碼體驗的意見反應。</span><span class="sxs-lookup"><span data-stu-id="07fe1-156">(Note: see [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) to give us feedback on improving the encoding experience for PowerShell Core across all platforms.</span></span> <span data-ttu-id="07fe1-157">我們正努力支援不含 BOM 的 UTF-8，並可能變更各個平台上各種 Cmdlet 的編碼行為)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-157">We are working to support UTF-8 without a BOM and potentially changing the encoding defaults for various cmdlets across platforms.)</span></span>

### <a name="job-control"></a><span data-ttu-id="07fe1-158">工作控制</span><span class="sxs-lookup"><span data-stu-id="07fe1-158">Job Control</span></span>

<span data-ttu-id="07fe1-159">Linux/macOS 上的 PowerShell 不支援工作控制。</span><span class="sxs-lookup"><span data-stu-id="07fe1-159">There is no job-control support in PowerShell on Linux/macOS.</span></span>
<span data-ttu-id="07fe1-160">無法使用 `fg` 和 `bg` 命令。</span><span class="sxs-lookup"><span data-stu-id="07fe1-160">The `fg` and `bg` commands are not available.</span></span>

<span data-ttu-id="07fe1-161">目前，您可以使用 [PowerShell 工作](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs)來跨所有平台執行工作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-161">For the time being, you can use [PowerShell jobs](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) which do work across all platforms.</span></span>

### <a name="remoting-support"></a><span data-ttu-id="07fe1-162">遠端處理支援</span><span class="sxs-lookup"><span data-stu-id="07fe1-162">Remoting Support</span></span>

<span data-ttu-id="07fe1-163">目前，PowerShell Core 支援在 macOS 和 Linux 上使用基本驗證，以及在 Linux 上使用 NTLM 型驗證，透過 WSMan 進行 PowerShell 遠端處理 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-163">Currently, PowerShell Core supports PowerShell Remoting (PSRP) over WSMan with Basic authentication on macOS and Linux, and with NTLM-based authentication on Linux.</span></span> <span data-ttu-id="07fe1-164">(不支援 Kerberos 型驗證)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-164">(Kerberos-based authentication is not supported.)</span></span>

<span data-ttu-id="07fe1-165">WSMan 型遠端處理的工作是在 [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) 存放庫中進行的。</span><span class="sxs-lookup"><span data-stu-id="07fe1-165">The work for WSMan-based remoting is being done in the [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) repo.</span></span>

<span data-ttu-id="07fe1-166">PowerShell Core 也支援在所有平台上 (Windows、macOS 及 Linux) 透過 SSH 進行 PowerShell 遠端處理 (PSRP)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-166">PowerShell Core also supports PowerShell Remoting (PSRP) over SSH on all platforms (Windows, macOS, and Linux).</span></span> <span data-ttu-id="07fe1-167">雖然目前在生產環境中不支援此功能，但您可以從[這裡](../core-powershell/ssh-remoting-in-powershell-core.md)深入瞭解如何設定此功能。</span><span class="sxs-lookup"><span data-stu-id="07fe1-167">While this is not currently supported in production, you can learn more about setting this up [here](../core-powershell/ssh-remoting-in-powershell-core.md).</span></span>

### <a name="just-enough-administration-jea-support"></a><span data-ttu-id="07fe1-168">Just-Enough-Administration (JEA) 支援</span><span class="sxs-lookup"><span data-stu-id="07fe1-168">Just-Enough-Administration (JEA) Support</span></span>

<span data-ttu-id="07fe1-169">Linux/macOS 上的 PowerShell 目前不支援可建立有限系統管理 (JEA) 遠端處理端點的功能。</span><span class="sxs-lookup"><span data-stu-id="07fe1-169">The ability to create constrained administration (JEA) remoting endpoints is not currently available in PowerShell on Linux/macOS.</span></span> <span data-ttu-id="07fe1-170">此功能目前不在 6.0 的範圍內，但我們會考慮在 6.0 之後納入，因為它需要大量的設計工作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-170">This feature is currently not in scope for 6.0 and something we will consider post 6.0 as it requires significant design work.</span></span>

### <a name="sudo-exec-and-powershell"></a><span data-ttu-id="07fe1-171">`sudo`、`exec` 及 PowerShell</span><span class="sxs-lookup"><span data-stu-id="07fe1-171">`sudo`, `exec`, and PowerShell</span></span>

<span data-ttu-id="07fe1-172">由於 PowerShell 會在記憶體中執行大多數命令 (例如 Python 或 Ruby)，因此您無法將 sudo 直接與 PowerShell 內建項搭配使用。(當然，您可以從 sudo 執行 `powershell`)。如果有必要從 PowerShell 內搭配 sudo 執行 PowerShell Cmdlet (例如 `sudo Set-Date 8/18/2016`)，則您會執行 `sudo powershell Set-Date 8/18/2016`。</span><span class="sxs-lookup"><span data-stu-id="07fe1-172">Because PowerShell runs most commands in memory (like Python or Ruby), you can't use sudo directly with PowerShell built-ins. (You can, of course, run `powershell` from sudo.) If it is necessary to run a PowerShell cmdlet from within PowerShell with sudo, for example, `sudo Set-Date 8/18/2016`, then you would do `sudo powershell Set-Date 8/18/2016`.</span></span> <span data-ttu-id="07fe1-173">同樣地，您無法直接執行 PowerShell 內建項。</span><span class="sxs-lookup"><span data-stu-id="07fe1-173">Likewise, you can't exec a PowerShell built-in directly.</span></span> <span data-ttu-id="07fe1-174">您將必須改為執行 `exec powershell item_to_exec`。</span><span class="sxs-lookup"><span data-stu-id="07fe1-174">Instead you would have to do `exec powershell item_to_exec`.</span></span>

<span data-ttu-id="07fe1-175">此問題目前已納入 #3232 一併追蹤。</span><span class="sxs-lookup"><span data-stu-id="07fe1-175">This issue is currently being tracked as part of #3232.</span></span>

### <a name="missing-cmdlets"></a><span data-ttu-id="07fe1-176">缺少 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="07fe1-176">Missing Cmdlets</span></span>

<span data-ttu-id="07fe1-177">在 PowerShell 中一般可用的大量命令 (Cmdlet) 在 Linux/macOS 上並無法使用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-177">A large number of the commands (cmdlets) normally available in PowerShell are not available on Linux/macOS.</span></span> <span data-ttu-id="07fe1-178">在許多情況下，這些命令在這些平台上並沒有意義 (例如 Windows 特定的功能，像是登錄)。</span><span class="sxs-lookup"><span data-stu-id="07fe1-178">In many cases, these commands make no sense on these platforms (e.g. Windows-specific features like the registry).</span></span> <span data-ttu-id="07fe1-179">其他命令 (例如服務控制命令 Get/Start/Stop-Service) 則雖然存在，但卻沒有作用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-179">Other commands like the service control commands (Get/Start/Stop-Service) are present, but not functional.</span></span> <span data-ttu-id="07fe1-180">未來的版本將會更正這些問題，修正無效的 Cmdlet 並隨著時間新增新的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="07fe1-180">Future releases will correct these problems, fixing the broken cmdlets and adding new ones over time.</span></span>

### <a name="command-availability"></a><span data-ttu-id="07fe1-181">命令可用性</span><span class="sxs-lookup"><span data-stu-id="07fe1-181">Command Availability</span></span>

<span data-ttu-id="07fe1-182">下表列出已知在 Linux/macOS 上的 PowerShell 中無法運作的命令。</span><span class="sxs-lookup"><span data-stu-id="07fe1-182">The following table lists commands that are known not to work in PowerShell on Linux/macOS.</span></span>

<table>
<th><span data-ttu-id="07fe1-183">命令</span><span class="sxs-lookup"><span data-stu-id="07fe1-183">Commands</span></span></th><th><span data-ttu-id="07fe1-184">作業狀態</span><span class="sxs-lookup"><span data-stu-id="07fe1-184">Operational State</span></span></th><th><span data-ttu-id="07fe1-185">注意</span><span class="sxs-lookup"><span data-stu-id="07fe1-185">Notes</span></span></th>
<tr>
<td><span data-ttu-id="07fe1-186">Get-Service、New-Service、Restart-Service、Resume-Service、Set-Service、Start-Service、Stop-Service、Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="07fe1-186">Get-Service, New-Service, Restart-Service, Resume-Service, Set-Service, Start-Service, Stop-Service, Suspend-Service</span></span>
<td><span data-ttu-id="07fe1-187">無法使用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-187">Not available.</span></span>
<td><span data-ttu-id="07fe1-188">系統將無法辨識這些命令。</span><span class="sxs-lookup"><span data-stu-id="07fe1-188">These commands will not be recognized.</span></span> <span data-ttu-id="07fe1-189">在未來的版本中應該會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-189">This should be fixed in a future release.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-190">Get-Acl、Set-Acl</span><span class="sxs-lookup"><span data-stu-id="07fe1-190">Get-Acl, Set-Acl</span></span>
<td><span data-ttu-id="07fe1-191">無法使用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-191">Not available.</span></span>
<td><span data-ttu-id="07fe1-192">系統將無法辨識這些命令。</span><span class="sxs-lookup"><span data-stu-id="07fe1-192">These commands will not be recognized.</span></span> <span data-ttu-id="07fe1-193">在未來的版本中應該會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-193">This should be fixed in a future release.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-194">Get-AuthenticodeSignature、Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="07fe1-194">Get-AuthenticodeSignature, Set-AuthenticodeSignature</span></span>
<td><span data-ttu-id="07fe1-195">無法使用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-195">Not available.</span></span>
<td><span data-ttu-id="07fe1-196">系統將無法辨識這些命令。</span><span class="sxs-lookup"><span data-stu-id="07fe1-196">These commands will not be recognized.</span></span> <span data-ttu-id="07fe1-197">在未來的版本中應該會修正此問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-197">This should be fixed in a future release.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-198">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="07fe1-198">Wait-Process</span></span>
<td><span data-ttu-id="07fe1-199">可以使用，但無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-199">Available, doesn't work properly.</span></span> <td><span data-ttu-id="07fe1-200">例如 `Start-Process gvim -PassThru | Wait-Process` 沒有作用；無法等候處理序。</span><span class="sxs-lookup"><span data-stu-id="07fe1-200">For example `Start-Process gvim -PassThru | Wait-Process` doesn't work; it fails to wait for the process.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-201">Register-PSSessionConfiguration、Unregister-PSSessionConfiguration、Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="07fe1-201">Register-PSSessionConfiguration, Unregister-PSSessionConfiguration, Get-PSSessionConfiguration</span></span>
<td><span data-ttu-id="07fe1-202">可以使用，但沒有作用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-202">Available but doesn't work.</span></span>
<td><span data-ttu-id="07fe1-203">會撰寫一則錯誤訊息，指出命令無法運作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-203">Writes an error message indicating that the commands are not working.</span></span> <span data-ttu-id="07fe1-204">在未來的版本中應該會修正這些問題。</span><span class="sxs-lookup"><span data-stu-id="07fe1-204">These should be fixed in a future release.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-205">Get-Event、New-Event、Register-EngineEvent、Register-WmiEvent、Remove-Event、Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="07fe1-205">Get-Event, New-Event, Register-EngineEvent, Register-WmiEvent, Remove-Event, Unregister-Event</span></span>
<td><span data-ttu-id="07fe1-206">可以使用，但沒有任何可用的事件來源。</span><span class="sxs-lookup"><span data-stu-id="07fe1-206">Available but no event sources are available.</span></span>
<td><span data-ttu-id="07fe1-207">PowerShell 事件處理命令存在，但與這些命令搭配使用的大多數事件來源 (例如 System.Timers.Timer) 在 Linux 上都未提供，使得這些命令在 Alpha 版中毫無用處。</span><span class="sxs-lookup"><span data-stu-id="07fe1-207">The PowerShell eventing commands are present but most of the event sources used with the commands (such as System.Timers.Timer) are not available on Linux making the commands useless in the Alpha release.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-208">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="07fe1-208">Set-ExecutionPolicy</span></span>
<td><span data-ttu-id="07fe1-209">可以使用，但沒有作用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-209">Available but doesn't work.</span></span>
<td><span data-ttu-id="07fe1-210">會傳回一則訊息，指出在此平台上並不支援。</span><span class="sxs-lookup"><span data-stu-id="07fe1-210">Returns a message saying not supported on this platform.</span></span> <span data-ttu-id="07fe1-211">執行原則是一個以使用者為焦點的「安全帶」，可協助防止使用者犯下重大錯誤。</span><span class="sxs-lookup"><span data-stu-id="07fe1-211">Execution policy is a user-focused "safety belt" that helps prevent the user from making expensive mistakes.</span></span> <span data-ttu-id="07fe1-212">它不是一個安全性界限。</span><span class="sxs-lookup"><span data-stu-id="07fe1-212">It is not a security boundary.</span></span>
</tr>
<tr>
<td><span data-ttu-id="07fe1-213">New-PSSessionOption、New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="07fe1-213">New-PSSessionOption, New-PSTransportOption</span></span>
<td><span data-ttu-id="07fe1-214">可以使用，但 New-PSSession 沒有作用。</span><span class="sxs-lookup"><span data-stu-id="07fe1-214">Available but New-PSSession doesn't work.</span></span>
<td><span data-ttu-id="07fe1-215">由於 New-PSSession 可運作，因此目前並未驗證 New-PSSessionOption 和 New-PSTransportOption 是否可運作。</span><span class="sxs-lookup"><span data-stu-id="07fe1-215">New-PSSessionOption and New-PSTransportOption are not currently verified to work now that New-PSSession works.</span></span>
</tr>
</table>