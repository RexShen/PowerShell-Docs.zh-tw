---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 名稱
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: a4f7e12c2b30e8ae6d1cf5a125d613d2d7558c34
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851250"
---
# <a name="learning-powershell-names"></a><span data-ttu-id="e489d-103">了解 PowerShell 名稱</span><span class="sxs-lookup"><span data-stu-id="e489d-103">Learning PowerShell names</span></span>

<span data-ttu-id="e489d-104">您需要針對大部分命令列介面投入大量時間來學習命令與參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-104">Learning names of commands and parameters requires a significant time investment with most command-line interfaces.</span></span> <span data-ttu-id="e489d-105">問題在於模式很少。</span><span class="sxs-lookup"><span data-stu-id="e489d-105">The issue is that there are few patterns.</span></span> <span data-ttu-id="e489d-106">記憶是學習您需定期使用之參數與命令的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="e489d-106">Memorization is only way to learn the commands and parameters that you need to use on a regular basis.</span></span>

<span data-ttu-id="e489d-107">當您使用新的命令或參數時，不能總是使用您已經知道的項目。</span><span class="sxs-lookup"><span data-stu-id="e489d-107">When you work with a new command or parameter, you can't always use what you already know.</span></span> <span data-ttu-id="e489d-108">您必須尋找並學習新名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-108">You have to find and learn a new name.</span></span> <span data-ttu-id="e489d-109">傳統上，命令列介面會從一小組工具開始，並隨著累加的新增項目而成長。</span><span class="sxs-lookup"><span data-stu-id="e489d-109">Traditionally, command-line interfaces start with a small set of tools and grow with incremental additions.</span></span> <span data-ttu-id="e489d-110">很容易就能理解為什麼沒有標準結構。</span><span class="sxs-lookup"><span data-stu-id="e489d-110">It's easy to see why there's no standard structure.</span></span>
<span data-ttu-id="e489d-111">這似乎就是命令名稱的邏輯，因為每個命令都是一個單獨的工具。</span><span class="sxs-lookup"><span data-stu-id="e489d-111">This seems logical for command names since each command is a separate tool.</span></span> <span data-ttu-id="e489d-112">PowerShell 提供更好的方式來處理命令名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-112">PowerShell has a better way to handle command names.</span></span>

## <a name="learning-command-names-in-traditional-shells"></a><span data-ttu-id="e489d-113">學習傳統殼層中的命令名稱</span><span class="sxs-lookup"><span data-stu-id="e489d-113">Learning command names in traditional shells</span></span>

<span data-ttu-id="e489d-114">大部分命令的建置目的是為了管理作業系統或應用程式的項目，例如服務或處理程序。</span><span class="sxs-lookup"><span data-stu-id="e489d-114">Most commands are built to manage elements of the operating system or applications, such as services or processes.</span></span> <span data-ttu-id="e489d-115">命令的名稱不一定適合某個系列。</span><span class="sxs-lookup"><span data-stu-id="e489d-115">The commands have names that may or may not fit into a family.</span></span> <span data-ttu-id="e489d-116">例如，在 Windows 系統上，您可以使用 `net start` 與 `net stop` 命令來啟動及停止服務。</span><span class="sxs-lookup"><span data-stu-id="e489d-116">For example, on Windows systems, you can use the `net start` and `net stop` commands to start and stop a service.</span></span> <span data-ttu-id="e489d-117">**Sc.exe** 是另一個適用於 Windows 的服務控制工具。</span><span class="sxs-lookup"><span data-stu-id="e489d-117">**Sc.exe** is another service control tool for Windows.</span></span> <span data-ttu-id="e489d-118">該名稱不符合 **net.exe** 服務命令的命名模式。</span><span class="sxs-lookup"><span data-stu-id="e489d-118">That name does not fit into the naming pattern for the **net.exe** service commands.</span></span> <span data-ttu-id="e489d-119">為了管理處理序，Windows 提供 **tasklist.exe** 命令來列出處理序，並提供 **taskkill.exe** 命令來刪除處理序。</span><span class="sxs-lookup"><span data-stu-id="e489d-119">For process management, Windows has the **tasklist.exe** command to list processes and the **taskkill.exe** command to kill processes.</span></span>

<span data-ttu-id="e489d-120">此外，這些命令也沒有標準的參數規格。</span><span class="sxs-lookup"><span data-stu-id="e489d-120">Also, these commands have irregular parameter specifications.</span></span> <span data-ttu-id="e489d-121">您無法使用 `net start` 命令來啟動遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="e489d-121">You can't use the `net start` command to start a service on a remote computer.</span></span> <span data-ttu-id="e489d-122">**sc.exe** 命令可以啟動遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="e489d-122">The **sc.exe** command can start a service on a remote computer.</span></span> <span data-ttu-id="e489d-123">但是，若要指定遠端電腦，您必須在其名稱前面加上雙反斜線。</span><span class="sxs-lookup"><span data-stu-id="e489d-123">But to specify the remote computer, you must prefix its name with a double backslash.</span></span> <span data-ttu-id="e489d-124">若要在名為 DC01 的遠端電腦上啟動多工緩衝處理器服務，您要輸入 `sc.exe \\DC01 start spooler`。</span><span class="sxs-lookup"><span data-stu-id="e489d-124">To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.</span></span>
<span data-ttu-id="e489d-125">若要列出在 DC01 上執行的工作，請使用 **/S** 參數與不含反斜線的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-125">To list tasks running on DC01, you use the **/S** parameter and the computer name without backslashes.</span></span> <span data-ttu-id="e489d-126">例如，`tasklist /S DC01`。</span><span class="sxs-lookup"><span data-stu-id="e489d-126">For example, `tasklist /S DC01`.</span></span>

> [!NOTE]
> <span data-ttu-id="e489d-127">在 PowerShell v6 之前，`sc` 是 `Set-Content` Cmdlet 的別名。</span><span class="sxs-lookup"><span data-stu-id="e489d-127">Prior to PowerShell v6, `sc` was an alias for the `Set-Content` cmdlet.</span></span> <span data-ttu-id="e489d-128">若要執行 **sc.exe** 命令，您必須包含副檔名。</span><span class="sxs-lookup"><span data-stu-id="e489d-128">To run the **sc.exe** command, you must include the file extension.</span></span>

<span data-ttu-id="e489d-129">服務與處理序是電腦上具有明確定義之生命週期且可管理的元素範例。</span><span class="sxs-lookup"><span data-stu-id="e489d-129">Services and processes are examples of manageable elements on a computer that have well-defined life cycles.</span></span> <span data-ttu-id="e489d-130">您可能會啟動或停止服務與處理序，或是取得所有目前執行中的服務或處理序清單。</span><span class="sxs-lookup"><span data-stu-id="e489d-130">You may start or stop services and processes, or get a list of all currently running services or processes.</span></span> <span data-ttu-id="e489d-131">雖然它們之間有重要的技術區別，但您在服務和處理序上執行的動作在概念上是一樣的。</span><span class="sxs-lookup"><span data-stu-id="e489d-131">Although there are important technical distinctions between them, the actions you perform on services and processes are conceptually the same.</span></span> <span data-ttu-id="e489d-132">此外，透過指定參數來自訂動作的選項在概念上也可能很類似。</span><span class="sxs-lookup"><span data-stu-id="e489d-132">Furthermore, the choices we make to customize an action by specifying parameters may be conceptually similar as well.</span></span>

<span data-ttu-id="e489d-133">PowerShell 利用這些相似之處，來減少學習及使用 Cmdlet 時需要知道之不同名稱的數量。</span><span class="sxs-lookup"><span data-stu-id="e489d-133">PowerShell exploits these similarities to reduce the number of distinct names you need to know to understand and use cmdlets.</span></span>

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a><span data-ttu-id="e489d-134">Cmdlet 使用「指令動詞-名詞」名稱降低記住命令的需求</span><span class="sxs-lookup"><span data-stu-id="e489d-134">Cmdlets use verb-noun names to reduce command memorization</span></span>

<span data-ttu-id="e489d-135">PowerShell 會使用「指令動詞-名詞」命名系統。</span><span class="sxs-lookup"><span data-stu-id="e489d-135">PowerShell uses a "verb-noun" naming system.</span></span> <span data-ttu-id="e489d-136">每個 Cmdlet 名稱都是由一個標準指令動詞、連字號及一個特定名詞所組成的。</span><span class="sxs-lookup"><span data-stu-id="e489d-136">Each cmdlet name consists of a standard verb hyphenated with a specific noun.</span></span> <span data-ttu-id="e489d-137">PowerShell 指令動詞不一定是英文動詞，但會表示 PowerShell 中的特定動作。</span><span class="sxs-lookup"><span data-stu-id="e489d-137">PowerShell verbs are not always English verbs, but they express specific actions in PowerShell.</span></span> <span data-ttu-id="e489d-138">名詞非常類似任何語言中的名詞。</span><span class="sxs-lookup"><span data-stu-id="e489d-138">Nouns are very much like nouns in any language.</span></span> <span data-ttu-id="e489d-139">它們會說明系統管理中重要物件的特定類型。</span><span class="sxs-lookup"><span data-stu-id="e489d-139">They describe specific types of objects that are important in system administration.</span></span> <span data-ttu-id="e489d-140">透過查看一些範例，就能輕鬆地示範這些由兩部分組成的名稱如何減少學習的投入量。</span><span class="sxs-lookup"><span data-stu-id="e489d-140">It's easy to demonstrate how these two-part names reduce learning effort by looking at a few examples.</span></span>

<span data-ttu-id="e489d-141">PowerShell 提供一組建議的標準指令動詞。</span><span class="sxs-lookup"><span data-stu-id="e489d-141">PowerShell has a recommended set of standard verbs.</span></span> <span data-ttu-id="e489d-142">名詞的限制較少，但一律會說明指令動詞的作用。</span><span class="sxs-lookup"><span data-stu-id="e489d-142">Nouns are less restricted, but always describe what the verb acts upon.</span></span> <span data-ttu-id="e489d-143">PowerShell 提供 `Get-Process`、`Stop-Process`、`Get-Service` 與 `Stop-Service` 之類的命令。</span><span class="sxs-lookup"><span data-stu-id="e489d-143">PowerShell has commands such as `Get-Process`, `Stop-Process`, `Get-Service`, and `Stop-Service`.</span></span>

<span data-ttu-id="e489d-144">針對這個含有兩個名詞與指令動詞的範例，一致性無法有效簡化學習。</span><span class="sxs-lookup"><span data-stu-id="e489d-144">For this example of two nouns and verbs, consistency does not simplify learning that much.</span></span> <span data-ttu-id="e489d-145">將該清單擴充為具有 10 個指令動詞與 10 個名詞的標準化集合。</span><span class="sxs-lookup"><span data-stu-id="e489d-145">Extend that list to a standardized set of 10 verbs and 10 nouns.</span></span> <span data-ttu-id="e489d-146">現在您只需學習 20 個單字。</span><span class="sxs-lookup"><span data-stu-id="e489d-146">Now you only have 20 words to understand.</span></span>
<span data-ttu-id="e489d-147">但那些單字可組合以形成 100 個完全不同的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-147">But those words can be combined to form 100 distinct command names.</span></span>

<span data-ttu-id="e489d-148">透過閱讀 PowerShell 命令的名稱，很容易就能了解該命令的功用。</span><span class="sxs-lookup"><span data-stu-id="e489d-148">It's easy to understand what a PowerShell command does by reading its name.</span></span> <span data-ttu-id="e489d-149">關閉電腦的命令是 `Stop-Computer`。</span><span class="sxs-lookup"><span data-stu-id="e489d-149">The command to shut down a computer is `Stop-Computer`.</span></span> <span data-ttu-id="e489d-150">列出網路上所有電腦的命令是 `Get-Computer`。</span><span class="sxs-lookup"><span data-stu-id="e489d-150">The command to list all computers on a network is `Get-Computer`.</span></span> <span data-ttu-id="e489d-151">取得系統日期的命令是 `Get-Date`。</span><span class="sxs-lookup"><span data-stu-id="e489d-151">The command to get the system date is `Get-Date`.</span></span>

<span data-ttu-id="e489d-152">您可以針對 `Get-Command` 使用 **Verb** 參數來列出包含特定指令動詞的所有命令。</span><span class="sxs-lookup"><span data-stu-id="e489d-152">You can list all commands that include a particular verb with the **Verb** parameter for `Get-Command`.</span></span> <span data-ttu-id="e489d-153">例如，若要查看使用 `Get` 指令動詞的所有 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="e489d-153">For example, to see all cmdlets that use the verb `Get`, type:</span></span>

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

<span data-ttu-id="e489d-154">使用 **Noun** 參數來查看會影響相同類型物件的一系列命令。</span><span class="sxs-lookup"><span data-stu-id="e489d-154">Use the **Noun** parameter to see a family of commands that affect the same type of object.</span></span> <span data-ttu-id="e489d-155">例如，執行下列命令來查看可用於管理服務的命令：</span><span class="sxs-lookup"><span data-stu-id="e489d-155">For example, run following command to see the commands  available for managing services:</span></span>

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a><span data-ttu-id="e489d-156">Cmdlet 使用標準參數</span><span class="sxs-lookup"><span data-stu-id="e489d-156">Cmdlets use standard parameters</span></span>

<span data-ttu-id="e489d-157">如前所述，傳統命令列介面中所使用的命令不一定會有一致的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-157">As noted earlier, commands used in traditional command-line interfaces don't always have consistent parameter names.</span></span> <span data-ttu-id="e489d-158">參數通常是可輕鬆輸入，但新使用者不容易了解的單一字元或縮寫單字。</span><span class="sxs-lookup"><span data-stu-id="e489d-158">Parameters are often single-character or abbreviated words that are easy to type but aren't easily understood by new users.</span></span>

<span data-ttu-id="e489d-159">不同於其他大部分傳統命令列介面，PowerShell 會直接處理參數，並透過直接存取參數及開發人員指導方針來將參數名稱標準化。</span><span class="sxs-lookup"><span data-stu-id="e489d-159">Unlike most other traditional command-line interfaces, PowerShell processes parameters directly, and it uses this direct access to the parameters along with developer guidance to standardize parameter names.</span></span> <span data-ttu-id="e489d-160">此指導方針鼓勵但不保證每個 Cmdlet 都符合標準。</span><span class="sxs-lookup"><span data-stu-id="e489d-160">This guidance encourages but does not guarantee that every cmdlet conforms to the standard.</span></span>

<span data-ttu-id="e489d-161">PowerShell 也會將參數分隔符號標準化。</span><span class="sxs-lookup"><span data-stu-id="e489d-161">PowerShell also standardizes the parameter separator.</span></span> <span data-ttu-id="e489d-162">參數名稱前面一定會加上 '-' 並搭配一個 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="e489d-162">Parameter names always have a '-' prepended to them with a PowerShell command.</span></span> <span data-ttu-id="e489d-163">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="e489d-163">Consider the following example:</span></span>

```powershell
Get-Command -Name Clear-Host
```

<span data-ttu-id="e489d-164">參數的名稱是 **Name**，但在命令列上用來作為參數時會輸入為 `-Name`。</span><span class="sxs-lookup"><span data-stu-id="e489d-164">The parameter's name is **Name**, but it is typed as `-Name` when used on the command line as a parameter.</span></span>

<span data-ttu-id="e489d-165">以下是一些標準參數名稱和使用方式的一般特性。</span><span class="sxs-lookup"><span data-stu-id="e489d-165">Here are some of the general characteristics of the standard parameter names and usages.</span></span>

### <a name="the-help-parameter-"></a><span data-ttu-id="e489d-166">說明參數 (?)</span><span class="sxs-lookup"><span data-stu-id="e489d-166">The Help parameter (?)</span></span>

<span data-ttu-id="e489d-167">當您在任何 Cmdlet 上指定 `-?` 參數時，PowerShell 會顯示該 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="e489d-167">When you specify the `-?` parameter on any cmdlet, PowerShell displays help for the cmdlet.</span></span>
<span data-ttu-id="e489d-168">未執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e489d-168">The cmdlet is not executed.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="e489d-169">一般參數</span><span class="sxs-lookup"><span data-stu-id="e489d-169">Common parameters</span></span>

<span data-ttu-id="e489d-170">PowerShell 提供數個「一般參數」。</span><span class="sxs-lookup"><span data-stu-id="e489d-170">PowerShell has several *common parameters*.</span></span> <span data-ttu-id="e489d-171">這些參數是由 PowerShell 引擎所控制。</span><span class="sxs-lookup"><span data-stu-id="e489d-171">These parameters are controlled by the PowerShell engine.</span></span> <span data-ttu-id="e489d-172">一般參數一律會以相同方式運作。</span><span class="sxs-lookup"><span data-stu-id="e489d-172">Common parameters always behave the same way.</span></span> <span data-ttu-id="e489d-173">一般參數包括 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**。</span><span class="sxs-lookup"><span data-stu-id="e489d-173">The common parameters are **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, and **OutBuffer**.</span></span>

### <a name="recommended-parameter-names"></a><span data-ttu-id="e489d-174">建議的參數名稱</span><span class="sxs-lookup"><span data-stu-id="e489d-174">Recommended parameter names</span></span>

<span data-ttu-id="e489d-175">PowerShell 核心 Cmdlet 會針對類似的參數使用標準名稱。</span><span class="sxs-lookup"><span data-stu-id="e489d-175">The PowerShell core cmdlets use standard names for similar parameters.</span></span> <span data-ttu-id="e489d-176">不會強制使用這些標準名稱，但有明確的指導方針來鼓勵標準化。</span><span class="sxs-lookup"><span data-stu-id="e489d-176">The use of these standard names is not enforced, but there is explicit guidance to encourage standardization.</span></span>

<span data-ttu-id="e489d-177">例如，參考電腦之參數的建議名稱是 **ComputerName**，而不是 Server、Host、System、Node 或其他常見的替代項目。</span><span class="sxs-lookup"><span data-stu-id="e489d-177">For example, the recommended name for a parameter that refers to a computer is **ComputerName**, rather than Server, Host, System, Node, or some other common alternative.</span></span> <span data-ttu-id="e489d-178">其他重要的建議參數名稱包括 **Force**、**Exclude**、**Include**、**PassThru**、**Path** 與 **CaseSensitive**。</span><span class="sxs-lookup"><span data-stu-id="e489d-178">Other important recommended parameter names are **Force**, **Exclude**, **Include**, **PassThru**, **Path**, and **CaseSensitive**.</span></span>