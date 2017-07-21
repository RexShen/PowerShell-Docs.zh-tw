---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "了解 Windows PowerShell 名稱"
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 28c821c4a617b6ac775dbdda8ade3d15c3f218c3
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="learning-windows-powershell-names"></a><span data-ttu-id="aefbf-103">了解 Windows PowerShell 名稱</span><span class="sxs-lookup"><span data-stu-id="aefbf-103">Learning Windows PowerShell Names</span></span>
<span data-ttu-id="aefbf-104">了解大部分命令列介面的命令和命令參數名稱需要投入大量時間。</span><span class="sxs-lookup"><span data-stu-id="aefbf-104">Learning names of commands and command parameters is a significant time investment with most command-line interfaces.</span></span> <span data-ttu-id="aefbf-105">此問題在於不太有模式可循，因此唯一的了解方式是記住您需要定期使用的每個命令和每個參數。</span><span class="sxs-lookup"><span data-stu-id="aefbf-105">The issue is that there are very few patterns, so the only way to learn is by memorizing each command and each parameter that you need to use on a regular basis.</span></span>

<span data-ttu-id="aefbf-106">當您使用新命令或參數時，通常無法運用您既有的知識，而必須尋找及了解新名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-106">When you work with a new command or parameter, you cannot generally use what you already know; you have to find and learn a new name.</span></span> <span data-ttu-id="aefbf-107">如果您看一下介面如何從具有累加新增功能的一小組工具成長為功能性介面，便不難了解此結構無法標準化的原因。</span><span class="sxs-lookup"><span data-stu-id="aefbf-107">If you look at how interfaces grow from a small set of tools with incremental additions to functionality, it is easy to see why the structure is nonstandard.</span></span> <span data-ttu-id="aefbf-108">特別是命令名稱，乍聽之下可能很有邏輯 (因為每個命令都是個別工具)，但其實還有更好的方法來處理命令名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-108">With command names in particular, this may sound logical since each command is a separate tool, but there is a better way to handle command names.</span></span>

<span data-ttu-id="aefbf-109">大部分命令的建置目的是為了管理作業系統或應用程式的項目，例如服務或處理程序。</span><span class="sxs-lookup"><span data-stu-id="aefbf-109">Most commands are built to manage elements of the operating system or applications, such as services or processes.</span></span> <span data-ttu-id="aefbf-110">命令有各式各樣的名稱，不一定適合放入某個系列。</span><span class="sxs-lookup"><span data-stu-id="aefbf-110">The commands have a variety of names that may or may not fit into a family.</span></span> <span data-ttu-id="aefbf-111">例如，在 Windows 系統上，您可以使用 **net start** 和 **net stop** 命令來啟動及停止服務。</span><span class="sxs-lookup"><span data-stu-id="aefbf-111">For example, on Windows systems, you can use the **net start** and **net stop** commands to start and stop a service.</span></span> <span data-ttu-id="aefbf-112">Windows 有另一個更通用但名稱完全不同的服務控制工具 **sc**，不適合放入 **net** 服務命令的命名模式中。</span><span class="sxs-lookup"><span data-stu-id="aefbf-112">There is another more generalized service control tool for Windows that has a completely different name, **sc**, that does not fit into the naming pattern for the **net** service commands.</span></span> <span data-ttu-id="aefbf-113">為了管理處理程序，Windows 提供 **tasklist** 命令來列出處理程序，並提供 **taskkill** 命令來刪除處理程序。</span><span class="sxs-lookup"><span data-stu-id="aefbf-113">For process management, Windows has the **tasklist** command to list processes and the **taskkill** command to kill processes.</span></span>

<span data-ttu-id="aefbf-114">使用參數的命令沒有標準的參數規格。</span><span class="sxs-lookup"><span data-stu-id="aefbf-114">Commands that take parameters have irregular parameter specifications.</span></span> <span data-ttu-id="aefbf-115">您無法使用 **net start** 命令啟動遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="aefbf-115">You cannot use the **net start** command to start a service on a remote computer.</span></span> <span data-ttu-id="aefbf-116">**sc** 命令會啟動遠端電腦上的服務，但若要指定遠端電腦，您必須在其名稱前面加上雙反斜線。</span><span class="sxs-lookup"><span data-stu-id="aefbf-116">The **sc** command will start a service on a remote computer, but to specify the remote computer, you must prefix its name with a double backslash.</span></span> <span data-ttu-id="aefbf-117">例如，若要在名為 DC01 的遠端電腦上啟動多工緩衝處理器服務，您要輸入 **sc \\\\DC01 start spooler**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-117">For example, to start the spooler service on a remote computer named DC01, you would type **sc \\\\DC01 start spooler**.</span></span> <span data-ttu-id="aefbf-118">若要列出 DC01 上執行的工作，您必須使用表示「系統」的 **/S** 參數，並提供不含反斜線的名稱 DC01，例如：**tasklist /S DC01**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-118">To list tasks running on DC01, you need to use the **/S** (for "system") parameter and supply the name DC01 without backslashes, like this: **tasklist /S DC01**.</span></span>

<span data-ttu-id="aefbf-119">雖然服務與處理程序之間有重要的技術區別，但是這兩者都是電腦上明確定義生命週期的可管理項目範例。</span><span class="sxs-lookup"><span data-stu-id="aefbf-119">Although there are important technical distinctions between a service and a process, they are both examples of manageable elements on a computer that have a well-defined life cycle.</span></span> <span data-ttu-id="aefbf-120">您可能想要啟動或停止服務或處理程序，或是取得所有目前執行中的服務或處理程序清單。</span><span class="sxs-lookup"><span data-stu-id="aefbf-120">You may want to start or stop a service or process, or get a list of all currently running services or processes.</span></span> <span data-ttu-id="aefbf-121">換句話說，雖然服務和處理程序是不同的項目，但是我們對服務或處理程序執行的動作通常在概念上是相同的。</span><span class="sxs-lookup"><span data-stu-id="aefbf-121">In other words, although a service and a process are different things, the actions we perform on a service or a process are often conceptually the same.</span></span> <span data-ttu-id="aefbf-122">此外，藉由指定參數來自訂動作的選項在概念上也可能很類似。</span><span class="sxs-lookup"><span data-stu-id="aefbf-122">Furthermore, choices we may make to customize an action by specifying parameters may be conceptually similar as well.</span></span>

<span data-ttu-id="aefbf-123">Windows PowerShell 利用這些相似之處，減少為了解及使用 Cmdlet 所需知道的不同名稱數量。</span><span class="sxs-lookup"><span data-stu-id="aefbf-123">Windows PowerShell exploits these similarities to reduce the number of distinct names you need to know to understand and use cmdlets.</span></span>

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a><span data-ttu-id="aefbf-124">Cmdlet 使用「動詞-名詞」名稱降低記住命令的需求</span><span class="sxs-lookup"><span data-stu-id="aefbf-124">Cmdlets Use Verb-Noun Names to Reduce Command Memorization</span></span>
<span data-ttu-id="aefbf-125">Windows PowerShell 使用「動詞-名詞」命名系統，其中每個 Cmdlet 名稱是由一個標準動詞後面接著連字號和一個特定名詞所組成。</span><span class="sxs-lookup"><span data-stu-id="aefbf-125">Windows PowerShell uses a "verb-noun" naming system, where each cmdlet name consists of a standard verb hyphenated with a specific noun.</span></span> <span data-ttu-id="aefbf-126">Windows PowerShell 動詞不一定是英文動詞，但會表示 Windows PowerShell 中的特定動作。</span><span class="sxs-lookup"><span data-stu-id="aefbf-126">Windows PowerShell verbs are not always English verbs, but they express specific actions in Windows PowerShell.</span></span> <span data-ttu-id="aefbf-127">名詞很像是任何語言中的名詞，用於描述系統管理中重要物件的特定類型。</span><span class="sxs-lookup"><span data-stu-id="aefbf-127">Nouns are very much like nouns in any language, they describe specific types of objects that are important in system administration.</span></span> <span data-ttu-id="aefbf-128">藉由檢視一些動詞和名詞範例，就能輕鬆地示範這些由兩部分組成的名稱如何減少學習工作。</span><span class="sxs-lookup"><span data-stu-id="aefbf-128">It is easy to demonstrate how these two-part names reduce learning effort by looking at a few examples of verbs and nouns.</span></span>

<span data-ttu-id="aefbf-129">名詞的限制較少，但一律會描述命令的作用。</span><span class="sxs-lookup"><span data-stu-id="aefbf-129">Nouns are less restricted, but they should always describe what a command acts upon.</span></span> <span data-ttu-id="aefbf-130">Windows PowerShell 具有 **Get-Process**、**Stop-Process**、**Get-Service** 和 **Stop-Service** 等命令。</span><span class="sxs-lookup"><span data-stu-id="aefbf-130">Windows PowerShell has commands such as **Get-Process**, **Stop-Process**, **Get-Service**, and **Stop-Service**.</span></span>

<span data-ttu-id="aefbf-131">在兩個名詞和兩個動詞的案例中，一致性無法有效簡化學習。</span><span class="sxs-lookup"><span data-stu-id="aefbf-131">In the case of two nouns and two verbs, consistency does not simplify learning that much.</span></span> <span data-ttu-id="aefbf-132">不過，如果您檢視由 10 個動詞和 10 個名詞所組成的標準集合，則只需要了解 20 個字，就能使用這些字組成 100 個不同的命令名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-132">However, if you look at a standard set of 10 verbs and 10 nouns, you then have only 20 words to understand, but those words can be used to form 100 distinct command names.</span></span>

<span data-ttu-id="aefbf-133">您通常可以藉由讀取命令的名稱來辨識命令的功能，且新命令應該使用哪些名稱通常會很明顯。</span><span class="sxs-lookup"><span data-stu-id="aefbf-133">Frequently, you can recognize what a command does by reading its name, and it is usually apparent what name should be used for a new command.</span></span> <span data-ttu-id="aefbf-134">例如，電腦關機命令可能是 **Stop-Computer**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-134">For example, a computer shutdown command might be **Stop-Computer**.</span></span> <span data-ttu-id="aefbf-135">列出網路上所有電腦的命令可能是 **Get-Computer**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-135">A command that lists all computers on a network might be **Get-Computer**.</span></span> <span data-ttu-id="aefbf-136">取得系統日期的命令可能是 **Get-Date**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-136">The command that gets the system date is **Get-Date**.</span></span>

<span data-ttu-id="aefbf-137">您可以使用 **Get-Command** 的 **-Verb** 參數列出包含特定動詞的所有命令 (我們將在下一節詳細討論 **Get-Command**)。</span><span class="sxs-lookup"><span data-stu-id="aefbf-137">You can list all commands that include a particular verb with the **-Verb** parameter for **Get-Command** (We will discuss **Get-Command** in detail in the next section).</span></span> <span data-ttu-id="aefbf-138">例如，若要查看使用 **Get** 動詞的所有 Cmdlet，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="aefbf-138">For example, to see all cmdlets that use the verb **Get**, type:</span></span>

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

<span data-ttu-id="aefbf-139">**-Noun** 參數更是實用，因為它可讓您查看影響相同類型物件的一系列命令。</span><span class="sxs-lookup"><span data-stu-id="aefbf-139">The **-Noun** parameter is even more useful because it allows you to see a family of commands that affect the same type of object.</span></span> <span data-ttu-id="aefbf-140">例如，如果您想要查看哪些命令可用於管理服務，請輸入下列命令︰</span><span class="sxs-lookup"><span data-stu-id="aefbf-140">For example, if you want to see which commands are available for managing services, type following command:</span></span>

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

<span data-ttu-id="aefbf-141">即使命令使用「動詞-名詞」命名配置，也不一定是 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aefbf-141">A command is not necessarily a cmdlet, just because it has a verb-noun naming scheme.</span></span> <span data-ttu-id="aefbf-142">清除主控台視窗的命令 Clear-Host，即為具有「動詞-名詞」名稱但不是 Cmdlet 的原生 Windows PowerShell 命令範例之一。</span><span class="sxs-lookup"><span data-stu-id="aefbf-142">One example of a native Windows PowerShell command that is not a cmdlet but has a verb-noun name, is the command for clearing a console window, Clear-Host.</span></span> <span data-ttu-id="aefbf-143">Clear-Host 命令實際上為內部函式，如果對它執行 Get-Command 就能看到︰</span><span class="sxs-lookup"><span data-stu-id="aefbf-143">The Clear-Host command is actually an internal function, as you can see if you run Get-Command against it:</span></span>

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a><span data-ttu-id="aefbf-144">Cmdlet 使用標準參數</span><span class="sxs-lookup"><span data-stu-id="aefbf-144">Cmdlets Use Standard Parameters</span></span>
<span data-ttu-id="aefbf-145">如前所述，傳統命令列介面中所使用的命令通常不會有一致的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-145">As noted earlier, commands used in traditional command-line interfaces do not generally have consistent parameter names.</span></span> <span data-ttu-id="aefbf-146">有時候參數完全沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-146">Sometimes parameters do not have names at all.</span></span> <span data-ttu-id="aefbf-147">這種情況的參數通常是可快速輸入，但新使用者不容易了解的單字或縮寫字。</span><span class="sxs-lookup"><span data-stu-id="aefbf-147">When they do, they are often single-character or abbreviated words that can be typed rapidly but are not easily understood by new users.</span></span>

<span data-ttu-id="aefbf-148">不同於其他大部分傳統命令列介面，Windows PowerShell 會直接處理這些參數，並透過直接存取參數及開發人員指引來標準化參數名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-148">Unlike most other traditional command-line interfaces, Windows PowerShell processes parameters directly, and it uses this direct access to the parameters along with developer guidance to standardize parameter names.</span></span> <span data-ttu-id="aefbf-149">雖然這並不保證每個 Cmdlet 一律會符合標準，但會鼓勵其符合標準。</span><span class="sxs-lookup"><span data-stu-id="aefbf-149">Although this does not guarantee that every cmdlet will always conform to the standards, it does encourage it.</span></span>

> [!NOTE]
> <span data-ttu-id="aefbf-150">當您使用這些參數時，參數名稱前面一律會加上 '-'，讓 Windows PowerShell 清楚地將它們識別為參數。</span><span class="sxs-lookup"><span data-stu-id="aefbf-150">Parameter names always have a '-' prepended to them when you use them, to allow Windows PowerShell to clearly identify them as parameters.</span></span> <span data-ttu-id="aefbf-151">**Get-Command -Name Clear-Host** 範例中，參數的名稱為 **Name**，但會輸入為 -**Name**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-151">In the **Get-Command -Name Clear-Host** example, the parameter's name is **Name**, but it is entered as -**Name**.</span></span>

<span data-ttu-id="aefbf-152">以下是一些標準參數名稱和使用方式的一般特性。</span><span class="sxs-lookup"><span data-stu-id="aefbf-152">Here are some of the general characteristics of the standard parameter names and usages.</span></span>

#### <a name="the-help-parameter-"></a><span data-ttu-id="aefbf-153">說明參數 (?)</span><span class="sxs-lookup"><span data-stu-id="aefbf-153">The Help Parameter (?)</span></span>
<span data-ttu-id="aefbf-154">當您指定 **-?**</span><span class="sxs-lookup"><span data-stu-id="aefbf-154">When you specify the **-?**</span></span> <span data-ttu-id="aefbf-155">參數給任何 Cmdlet 時，不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="aefbf-155">parameter to any cmdlet, the cmdlet is not executed.</span></span> <span data-ttu-id="aefbf-156">相反地，Windows PowerShell 會顯示此 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="aefbf-156">Instead, Windows PowerShell displays help for the cmdlet.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="aefbf-157">一般參數</span><span class="sxs-lookup"><span data-stu-id="aefbf-157">Common Parameters</span></span>
<span data-ttu-id="aefbf-158">Windows PowerShell 有幾個稱為*一般參數*的參數。</span><span class="sxs-lookup"><span data-stu-id="aefbf-158">Windows PowerShell has several parameters known as *common parameters*.</span></span> <span data-ttu-id="aefbf-159">因為這些參數是由 Windows PowerShell 引擎所控制，所以每當 Cmdlet 實作參數時，這些參數一律會以相同方式運作。</span><span class="sxs-lookup"><span data-stu-id="aefbf-159">Because these parameters are controlled by the Windows PowerShell engine, whenever they are implemented by a cmdlet, they will always behave the same way.</span></span> <span data-ttu-id="aefbf-160">一般參數包括 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-160">The common parameters are **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, and **OutBuffer**.</span></span>

#### <a name="suggested-parameters"></a><span data-ttu-id="aefbf-161">建議的參數</span><span class="sxs-lookup"><span data-stu-id="aefbf-161">Suggested Parameters</span></span>
<span data-ttu-id="aefbf-162">Windows PowerShell 核心 Cmdlet 針對類似的參數使用標準名稱。</span><span class="sxs-lookup"><span data-stu-id="aefbf-162">The Windows PowerShell core cmdlets use standard names for similar parameters.</span></span> <span data-ttu-id="aefbf-163">雖然不會強制使用參數名稱，但針對使用方式有明確的指引，以鼓勵標準化。</span><span class="sxs-lookup"><span data-stu-id="aefbf-163">Although the use of parameter names is not enforced, there is explicit guidance for usage to encourage standardization.</span></span>

<span data-ttu-id="aefbf-164">例如，該指引建議命名指向電腦的參數時，依照 **ComputerName** 等名稱，而不是依照 Server、Host、System、Node 或其他常見的替代文字。</span><span class="sxs-lookup"><span data-stu-id="aefbf-164">For example, the guidance recommends naming a parameter that refers to a computer by name as **ComputerName**, rather than Server, Host, System, Node, or other common alternative words.</span></span> <span data-ttu-id="aefbf-165">重要的建議參數名稱包括 **Force**、**Exclude**、**Include**、**PassThru**、**Path**, 和 **CaseSensitive**。</span><span class="sxs-lookup"><span data-stu-id="aefbf-165">Among the important suggested parameter names are **Force**, **Exclude**, **Include**, **PassThru**, **Path**, and **CaseSensitive**.</span></span>

