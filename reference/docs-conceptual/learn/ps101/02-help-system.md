---
title: 說明系統
description: 掌握說明系統是順利使用 PowerShell 的關鍵。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 43d2de7e1f59ce5e980c192decb5309d3f6d0ff8
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438109"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="42d78-103">第 2 章 - 說明系統</span><span class="sxs-lookup"><span data-stu-id="42d78-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="42d78-104">兩組 IT 專業人員在無法存取電腦的情況下參加筆試，以確定其 PowerShell 技能等級。</span><span class="sxs-lookup"><span data-stu-id="42d78-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="42d78-105">PowerShell 初學者一組，專家在另一組。</span><span class="sxs-lookup"><span data-stu-id="42d78-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="42d78-106">根據測試結果，這兩組之間的技能等級似乎差異不大。</span><span class="sxs-lookup"><span data-stu-id="42d78-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="42d78-107">這兩組又接受一次與上次類似的測試。</span><span class="sxs-lookup"><span data-stu-id="42d78-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="42d78-108">這一次他們可使用搭載 PowerShell 但無法存取網際網路的電腦。</span><span class="sxs-lookup"><span data-stu-id="42d78-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="42d78-109">第二次測試的結果顯示這兩組的技能等級有相當大的差異。</span><span class="sxs-lookup"><span data-stu-id="42d78-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="42d78-110">專家不一定知道答案，但他們知道如何找到答案。</span><span class="sxs-lookup"><span data-stu-id="42d78-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="42d78-111">這兩組人員的第一次和第二次測試結果有何差異？</span><span class="sxs-lookup"><span data-stu-id="42d78-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="42d78-112">這兩次測試結果的差異在於，專家並不記得如何使用 PowerShell 中的數千種命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="42d78-113">他們十分瞭解如何使用 PowerShell 中的說明系統。</span><span class="sxs-lookup"><span data-stu-id="42d78-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="42d78-114">因此，他們可以在需要時找到必要的命令，並且在找到命令後，知道如何使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="42d78-115">我聽說 PowerShell 的發明人 Jeffrey Snover 也曾數次提到類似的故事。</span><span class="sxs-lookup"><span data-stu-id="42d78-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="42d78-116">掌握說明系統是順利使用 PowerShell 的關鍵。</span><span class="sxs-lookup"><span data-stu-id="42d78-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="42d78-117">可搜尋性</span><span class="sxs-lookup"><span data-stu-id="42d78-117">Discoverability</span></span>

<span data-ttu-id="42d78-118">PowerShell 中的編譯命令稱為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="42d78-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="42d78-119">Cmdlet 發音為「command-let」(而非 CMD-let)。</span><span class="sxs-lookup"><span data-stu-id="42d78-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="42d78-120">Cmdlet 名稱為單數形式的「動詞-名詞」命令，因此更易於發掘。</span><span class="sxs-lookup"><span data-stu-id="42d78-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="42d78-121">例如，用來判斷正在執行哪些流程的 Cmdlet 是 `Get-Process`，而用來擷取服務清單及其狀態的 Cmdlet 則是 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="42d78-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="42d78-122">PowerShell 中還有其他類型的命令，例如本書稍後將提到的別名和函式。</span><span class="sxs-lookup"><span data-stu-id="42d78-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="42d78-123">「PowerShell 命令」一詞是通稱，通常用來泛指在 PowerShell 中任何類型的命令，不論是 Cmdlet、函式或別名。</span><span class="sxs-lookup"><span data-stu-id="42d78-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="42d78-124">PowerShell 中的三個核心 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="42d78-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="42d78-125">`Get-Member` (在第 3 章介紹)</span><span class="sxs-lookup"><span data-stu-id="42d78-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="42d78-126">我經常被問到的一個問題是，要如何確定 PowerShell 中的命令為何？</span><span class="sxs-lookup"><span data-stu-id="42d78-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="42d78-127">`Get-Command` 和 `Get-Help` 都可以用來判斷命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="42d78-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="42d78-128">Get-Help</span></span>

<span data-ttu-id="42d78-129">`Get-Help` 是多用途命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="42d78-130">`Get-Help` 可協助您瞭解在找到命令後如何使用。</span><span class="sxs-lookup"><span data-stu-id="42d78-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="42d78-131">`Get-Help` 也可以用來協助您找到命令，但相較於 `Get-Command`，其使用不同但更間接的方式。</span><span class="sxs-lookup"><span data-stu-id="42d78-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="42d78-132">使用 `Get-Help` 來尋找命令時，它會先根據提供的輸入來搜尋命令名稱的萬用字元相符項目。</span><span class="sxs-lookup"><span data-stu-id="42d78-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="42d78-133">如果找不到相符的結果，則會搜尋說明主題本身，如果還是找不到相符的結果，則會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="42d78-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="42d78-134">相對於普遍的看法，`Get-Help` 可用來尋找沒有說明主題的命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="42d78-135">關於 PowerShell 中的說明系統，首先您需要瞭解如何使用 `Get-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="42d78-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="42d78-136">下列命令可用來顯示 `Get-Help` 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Outpout
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="42d78-137">從 PowerShell 第 3 版開始，PowerShell 說明不會隨附於作業系統。</span><span class="sxs-lookup"><span data-stu-id="42d78-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="42d78-138">第一次為命令執行 `Get-Help` 時，會顯示上一則訊息。</span><span class="sxs-lookup"><span data-stu-id="42d78-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="42d78-139">如果使用的是 `help` 函式或 `man` 別名，而不是 `Get-Help` Cmdlet，就不會收到此提示。</span><span class="sxs-lookup"><span data-stu-id="42d78-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="42d78-140">若按 <kbd>Y</kbd> 來表示「是」，則會執行 `Update-Help` Cmdlet，預設需要網際網路存取權限。</span><span class="sxs-lookup"><span data-stu-id="42d78-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="42d78-141">可以大寫或小寫指定 `Y`。</span><span class="sxs-lookup"><span data-stu-id="42d78-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="42d78-142">下載說明並完成更新之後，就會針對指定的命令傳回說明主題：</span><span class="sxs-lookup"><span data-stu-id="42d78-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="42d78-143">請花一些時間在電腦上執行該範例，檢閱輸出，並記下資訊的分組方式：</span><span class="sxs-lookup"><span data-stu-id="42d78-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="42d78-144">NAME</span><span class="sxs-lookup"><span data-stu-id="42d78-144">NAME</span></span>
- <span data-ttu-id="42d78-145">概要</span><span class="sxs-lookup"><span data-stu-id="42d78-145">SYNOPSIS</span></span>
- <span data-ttu-id="42d78-146">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42d78-146">SYNTAX</span></span>
- <span data-ttu-id="42d78-147">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="42d78-147">DESCRIPTION</span></span>
- <span data-ttu-id="42d78-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="42d78-148">RELATED LINKS</span></span>
- <span data-ttu-id="42d78-149">REMARKS</span><span class="sxs-lookup"><span data-stu-id="42d78-149">REMARKS</span></span>

<span data-ttu-id="42d78-150">如您所見，說明主題可能包含大量的資訊，這甚至不是全部的說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="42d78-151">雖然參數不是 PowerShell 所特有，但可用來向命令提供輸入。</span><span class="sxs-lookup"><span data-stu-id="42d78-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="42d78-152">`Get-Help` 有許多參數，可指定參數以傳回整個說明主題或其中的子集。</span><span class="sxs-lookup"><span data-stu-id="42d78-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="42d78-153">顯示在上一組結果中說明主題的語法部分，列出 `Get-Help` 的所有參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="42d78-154">乍看之下，似乎相同的參數被列了六次。</span><span class="sxs-lookup"><span data-stu-id="42d78-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="42d78-155">語法部分中的每個不同區塊都是參數集。</span><span class="sxs-lookup"><span data-stu-id="42d78-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="42d78-156">這表示 `Get-Help` Cmdlet 有六個不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="42d78-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="42d78-157">如果仔細查看，您會注意到每個參數集中至少有一個不同的參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="42d78-158">參數集是互斥的。</span><span class="sxs-lookup"><span data-stu-id="42d78-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="42d78-159">一旦使用了某個參數集所獨有的參數，就只能使用包含在該參數集中的參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="42d78-160">例如，不能同時指定 **Full** 和 **Detailed** 參數，因為其分別來自不同的參數集。</span><span class="sxs-lookup"><span data-stu-id="42d78-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="42d78-161">下列每個參數都位於不同的參數集內：</span><span class="sxs-lookup"><span data-stu-id="42d78-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="42d78-162">完整</span><span class="sxs-lookup"><span data-stu-id="42d78-162">Full</span></span>
- <span data-ttu-id="42d78-163">詳細</span><span class="sxs-lookup"><span data-stu-id="42d78-163">Detailed</span></span>
- <span data-ttu-id="42d78-164">範例</span><span class="sxs-lookup"><span data-stu-id="42d78-164">Examples</span></span>
- <span data-ttu-id="42d78-165">線上</span><span class="sxs-lookup"><span data-stu-id="42d78-165">Online</span></span>
- <span data-ttu-id="42d78-166">參數</span><span class="sxs-lookup"><span data-stu-id="42d78-166">Parameter</span></span>
- <span data-ttu-id="42d78-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="42d78-167">ShowWindow</span></span>

<span data-ttu-id="42d78-168">在語法區段中，所有晦澀的語法 (例如方括弧和角括弧) 均分別代表某些含義，我們將在本書的附錄 A 中討論。</span><span class="sxs-lookup"><span data-stu-id="42d78-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="42d78-169">儘管這些語法很重要，但對於不熟悉且不常用到 PowerShell 的使用者而言，通常很難記住這些晦澀的語法。</span><span class="sxs-lookup"><span data-stu-id="42d78-169">While important, learning what the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="42d78-170">如需更深入瞭解晦澀語法，請參閱[附錄 A][]。</span><span class="sxs-lookup"><span data-stu-id="42d78-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="42d78-171">對於初學者來說，除了使用一般語言之外，還有更簡單的方法可以取得相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="42d78-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="42d78-172">指定 `Get-Help` 的 **Full** 參數後，會傳回整個說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="42d78-173">請花一些時間在電腦上執行該範例，檢閱輸出，並記下資訊的分組方式：</span><span class="sxs-lookup"><span data-stu-id="42d78-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="42d78-174">NAME</span><span class="sxs-lookup"><span data-stu-id="42d78-174">NAME</span></span>
- <span data-ttu-id="42d78-175">概要</span><span class="sxs-lookup"><span data-stu-id="42d78-175">SYNOPSIS</span></span>
- <span data-ttu-id="42d78-176">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42d78-176">SYNTAX</span></span>
- <span data-ttu-id="42d78-177">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="42d78-177">DESCRIPTION</span></span>
- <span data-ttu-id="42d78-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="42d78-178">PARAMETERS</span></span>
- <span data-ttu-id="42d78-179">輸入</span><span class="sxs-lookup"><span data-stu-id="42d78-179">INPUTS</span></span>
- <span data-ttu-id="42d78-180">輸出</span><span class="sxs-lookup"><span data-stu-id="42d78-180">OUTPUTS</span></span>
- <span data-ttu-id="42d78-181">注意</span><span class="sxs-lookup"><span data-stu-id="42d78-181">NOTES</span></span>
- <span data-ttu-id="42d78-182">範例</span><span class="sxs-lookup"><span data-stu-id="42d78-182">EXAMPLES</span></span>
- <span data-ttu-id="42d78-183">相關連結</span><span class="sxs-lookup"><span data-stu-id="42d78-183">RELATED LINKS</span></span>

<span data-ttu-id="42d78-184">請注意，使用 **Full** 參數會傳回數個額外的區段，其中一個是 PARAMETERS 區段，其提供的資訊比晦澀的 SYNTAX 區段更多。</span><span class="sxs-lookup"><span data-stu-id="42d78-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="42d78-185">**Full** 參數是切換參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="42d78-186">不需要值的參數稱為「切換參數」。</span><span class="sxs-lookup"><span data-stu-id="42d78-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="42d78-187">已指定切換參數時，其值為 true，否則為 false。</span><span class="sxs-lookup"><span data-stu-id="42d78-187">When a switch parameter is specified, it's value is true and when it's not, it's value is false.</span></span>

<span data-ttu-id="42d78-188">如果您已在 PowerShell 主控台中完成本章的作業，會注意到在您還來不及閱讀前畫面上已掠過上一個顯示 `Get-Help` 完整說明主題的命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="42d78-189">還有一個更好的辦法。</span><span class="sxs-lookup"><span data-stu-id="42d78-189">There's a better way.</span></span>

<span data-ttu-id="42d78-190">`Help` 函式透過管道將 `Get-Help` 傳送至名為 `more` ，其傳送的對象是 Windows 中 `more.com` 可執行檔的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="42d78-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="42d78-191">在 PowerShell 主控台中，`help` 一次可提供一頁說明。</span><span class="sxs-lookup"><span data-stu-id="42d78-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="42d78-192">在 ISE 中，其運作方式與 `Get-Help`相同。</span><span class="sxs-lookup"><span data-stu-id="42d78-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="42d78-193">建議您使用 `help` 函式，而不是 `Get-Help` Cmdlet，因為前者可提供較好的體驗，而只需要較少的輸入。</span><span class="sxs-lookup"><span data-stu-id="42d78-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="42d78-194">不過，輸入較少不一定是件好事。</span><span class="sxs-lookup"><span data-stu-id="42d78-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="42d78-195">如果您要將命令另存為指令碼或與其他人共用，請務必使用完整的 Cmdlet 和參數名稱。</span><span class="sxs-lookup"><span data-stu-id="42d78-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="42d78-196">完整名稱為自我描述，讓它們更容易瞭解。</span><span class="sxs-lookup"><span data-stu-id="42d78-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="42d78-197">試想要如何讓下一個人看得懂這個命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="42d78-198">可能是您。</span><span class="sxs-lookup"><span data-stu-id="42d78-198">It could be you.</span></span> <span data-ttu-id="42d78-199">您的同事和將來您自己會因此而感謝您。</span><span class="sxs-lookup"><span data-stu-id="42d78-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="42d78-200">嘗試在 Windows 10 實驗室環境電腦上的 PowerShell 主控台中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="42d78-201">當您在 Windows 10 實驗室環境的電腦上執行上述這些命令時，您是否注意到其輸出有任何差異？</span><span class="sxs-lookup"><span data-stu-id="42d78-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="42d78-202">除了最後兩項一次傳回一頁結果外，並無任何差異。</span><span class="sxs-lookup"><span data-stu-id="42d78-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="42d78-203">使用 `Help` 函式和 <kbd>Ctrl</kbd>+<kbd>C</kbd> 會取消在 PowerShell 主控台中執行的命令時，會使用 <kbd>空格鍵</kbd> 來顯示下一頁的內容。</span><span class="sxs-lookup"><span data-stu-id="42d78-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="42d78-204">第一個範例使用 `Get-Help` Cmdlet，第二個範例使用 `Help` 函式，而第三個範例在使用 `Help` 函式時會省略 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="42d78-205">**Name** 是位置參數，在該範例中是按照位置來使用此參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="42d78-206">這表示您可以指定值，而不需指定參數名稱，只要值本身是在正確的位置中指定即可。</span><span class="sxs-lookup"><span data-stu-id="42d78-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="42d78-207">如何得知要在哪個位置指定值？</span><span class="sxs-lookup"><span data-stu-id="42d78-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="42d78-208">如下列範例所示，透過閱讀說明來瞭解。</span><span class="sxs-lookup"><span data-stu-id="42d78-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="42d78-209">請注意，在上一個範例中搭配使用 **Parameter** 參數與 Help 函數時，只會傳回 **Name** 參數的說明主題中的資訊。</span><span class="sxs-lookup"><span data-stu-id="42d78-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="42d78-210">比起嘗試手動篩選動輒上百頁說明主題，這種方式更為簡便。</span><span class="sxs-lookup"><span data-stu-id="42d78-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="42d78-211">根據這些結果，您可以看到 **Name** 參數是位置參數，而且在按位置使用時必須在位置零 (第一個位置) 指定。</span><span class="sxs-lookup"><span data-stu-id="42d78-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="42d78-212">如果指定了參數名稱，則參數的指定順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="42d78-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="42d78-213">另一個重要的資訊是，**Name** 參數值的預期資料類型必須是單一字串，並且以 `<String>` 表示。</span><span class="sxs-lookup"><span data-stu-id="42d78-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="42d78-214">如果它接受多個字串，則資料類型會列為 `<String[]>`。</span><span class="sxs-lookup"><span data-stu-id="42d78-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="42d78-215">有時候您不想要顯示命令的所有說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="42d78-216">除了 **Full** 外，還可以使用 `Get-Help` 或 `Help` 等其他參數來指定。</span><span class="sxs-lookup"><span data-stu-id="42d78-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="42d78-217">嘗試在 Windows 10 實驗室環境電腦上執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="42d78-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="42d78-218">我通常會將 `help <command name>` 與 **Full** 或 **Online** 參數搭配使用。</span><span class="sxs-lookup"><span data-stu-id="42d78-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="42d78-219">如果只對範例感興趣，可使用 **Examples** 參數，如果只對特定參數感興趣，可使用 **Parameter** 參數。</span><span class="sxs-lookup"><span data-stu-id="42d78-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="42d78-220">**ShowWindow** 參數可在單獨的搜尋視窗中開啟說明主題，如果您有多個監視器，可以在另一台監視器上顯示此視窗。</span><span class="sxs-lookup"><span data-stu-id="42d78-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="42d78-221">我會避免使用 **ShowWindow** 參數，因為存在不會顯示整個說明主題的已知錯誤。</span><span class="sxs-lookup"><span data-stu-id="42d78-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="42d78-222">如果要在個別的視窗中顯示說明，建議使用 **Online** 參數，或使用 **Full** 參數，然後透過管道將結果傳送至 `Out-GridView`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="42d78-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="42d78-223">`Out-GridView` Cmdlet 和 `Get-Help` Cmdlet 的 **ShowWindow** 參數都需要具備 GUI (圖形化使用者介面) 的作業系統。</span><span class="sxs-lookup"><span data-stu-id="42d78-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="42d78-224">如果嘗試在使用伺服器核心 (無 GUI) 安裝選項安裝的 Windows Server 上使用其中一種，則會產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="42d78-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="42d78-225">若要使用 `Get-Help` 來尋找命令，請在 **Name** 參數中使用星號 (`*`) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="42d78-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="42d78-226">指定搜尋命令所使用的字詞，做為 **Name** 參數的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="42d78-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="42d78-227">在上述範例中，不需要 `*` 萬用字元，而且省略後產生的結果相同。</span><span class="sxs-lookup"><span data-stu-id="42d78-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="42d78-228">`Get-Help` 會自動在背景中加入萬用字元。</span><span class="sxs-lookup"><span data-stu-id="42d78-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="42d78-229">上一個命令會與在處理序兩端指定 `*` 萬用字元產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="42d78-230">我偏好加上這些萬用字元，因為這個選項向來可以得到一致的結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="42d78-231">另外，在某些情況下需要用到這些萬用字元，而其他情況則不需要。</span><span class="sxs-lookup"><span data-stu-id="42d78-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="42d78-232">如果在值的中間加入萬用字元，就不會再對您指定的值自動加入萬用字元。</span><span class="sxs-lookup"><span data-stu-id="42d78-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="42d78-233">除非將 `*` 萬用字元加入至 `pr*cess` 的開頭、結尾或開頭和結尾，否則該命令不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="42d78-234">如果指定的值是以破折號開頭，則會產生錯誤，因為 PowerShell 會將其轉譯為參數名稱，但 `Get-Help` Cmdlet 沒有這類的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="42d78-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="42d78-235">如果嘗試尋找以 `-process` 結尾的命令，您只需要將 `*` 萬用字元新增至值的開頭。</span><span class="sxs-lookup"><span data-stu-id="42d78-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="42d78-236">使用 `Get-Help` 搜尋 PowerShell 命令時，請使用較為模糊而不要太特定的搜尋內容。</span><span class="sxs-lookup"><span data-stu-id="42d78-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="42d78-237">先前搜尋 `process` 時只找到名稱中包含 `process` 的命令，並且只傳回這些結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="42d78-238">使用 `Get-Help` 來搜尋 `processes` 時，它找不到與命令名稱相符的項目，因此它會搜尋系統上 PowerShell 中的每個說明主題，並傳回找到的任何相符項目。</span><span class="sxs-lookup"><span data-stu-id="42d78-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="42d78-239">這會導致傳回大量的結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="42d78-240">使用 `Help` 來搜尋 `process`，傳回 10 個結果，而使用該命令來搜尋 `processes`，則會傳回 68 個結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="42d78-241">如果只找到一個結果，將會顯示說明主題本身，而不會顯示命令清單。</span><span class="sxs-lookup"><span data-stu-id="42d78-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="42d78-242">現在來破解一個迷思，亦即在 PowerShell 中的 `Help` 只能找到有說明主題的命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="42d78-243">請注意，在上一個範例中，`more` 沒有說明主題，但是 PowerShell 中的 `Help` 系統可以找到它。</span><span class="sxs-lookup"><span data-stu-id="42d78-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="42d78-244">它只會找到一個相符的項目，並傳回基本語法資訊，因此，當命令沒有說明主題時，您就會看到基本語法資訊。</span><span class="sxs-lookup"><span data-stu-id="42d78-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="42d78-245">PowerShell 包含許多概念 (關於) 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="42d78-246">下列命令可用來傳回有關系統上所有**關於**說明主題的清單。</span><span class="sxs-lookup"><span data-stu-id="42d78-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="42d78-247">將結果限制為一個「關於」說明主題，會顯示實際的說明主題，而不是傳回清單。</span><span class="sxs-lookup"><span data-stu-id="42d78-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="42d78-248">您必須更新 PowerShell 中的說明系統，才會顯示**關於**的說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="42d78-249">若因為某些原因而導致電腦上的說明系統初始更新失敗，則在 `Update-Help` Cmdlet 成功執行之前，檔案將無法使用。</span><span class="sxs-lookup"><span data-stu-id="42d78-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="42d78-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="42d78-250">Get-Command</span></span>

<span data-ttu-id="42d78-251">`Get-Command` 的設計目的是要協助您尋找命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="42d78-252">執行不含任何參數的 `Get-Command` 會傳回系統上所有命令的清單。</span><span class="sxs-lookup"><span data-stu-id="42d78-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="42d78-253">下列範例示範如何使用 `Get-Command` Cmdlet 來判斷命令可用於處理流程的命令：</span><span class="sxs-lookup"><span data-stu-id="42d78-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="42d78-254">請注意，在上一個範例執行 `Get-Command` 時，使用 **Noun** 參數，並將 `Process` 指定為 **Noun** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="42d78-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="42d78-255">如果您不知道如何使用 `Get-Command` Cmdlet，該怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="42d78-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="42d78-256">您可以使用 `Get-Help` 來顯示 `Get-Command` 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="42d78-257">**Name**、**Noun** 和 **Verb** 參數都接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="42d78-257">The **Name**, **Noun**, and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="42d78-258">下列範例會顯示如何搭配使用 **Name** 參數和萬用字元：</span><span class="sxs-lookup"><span data-stu-id="42d78-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="42d78-259">我不喜歡搭配使用萬用字元與 `Get-Command` 的 **Name** 參數，因為它也會傳回不是原生 PowerShell 命令的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="42d78-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="42d78-260">如果您要搭配使用 **Name** 參數與萬用字元，我議使用 **CommandType** 參數來限制結果。</span><span class="sxs-lookup"><span data-stu-id="42d78-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="42d78-261">更好的選項是使用 **Verb** 或 **Noun** 參數或兩者，因為只有 PowerShell 命令同時具有動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="42d78-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="42d78-262">在說明主題中發現錯誤嗎？</span><span class="sxs-lookup"><span data-stu-id="42d78-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="42d78-263">好消息是，PowerShell 的說明主題為已開放原始碼，可以在 GitHub 上的 [PowerShell-Docs][] 存放庫中取得。</span><span class="sxs-lookup"><span data-stu-id="42d78-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="42d78-264">公開修正結果，您不只可為自己修正不正確的資訊，還可以幫助其他人。</span><span class="sxs-lookup"><span data-stu-id="42d78-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="42d78-265">您只要派生 GitHub 上的 PowerShell 文件存放庫，更新說明主題，並提交提取要求即可。</span><span class="sxs-lookup"><span data-stu-id="42d78-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="42d78-266">接受提取要求之後，所有人都可以使用已更正的文件。</span><span class="sxs-lookup"><span data-stu-id="42d78-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="42d78-267">更新說明</span><span class="sxs-lookup"><span data-stu-id="42d78-267">Updating Help</span></span>

<span data-ttu-id="42d78-268">有關請求的命令的首次說明，在 PowerShell 說明主題的本機複本中已更新。</span><span class="sxs-lookup"><span data-stu-id="42d78-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="42d78-269">建議定期更新說明系統，因為「說明」內容可能會不定時更新。</span><span class="sxs-lookup"><span data-stu-id="42d78-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="42d78-270">`Update-Help` Cmdlet 是用來更新說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="42d78-271">根據預設，它需要存取網際網路，而且您需要以系統管理員的身分提高權限來執行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="42d78-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="42d78-272">有幾個模組傳回錯誤，這種情況並不常見。</span><span class="sxs-lookup"><span data-stu-id="42d78-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="42d78-273">如果電腦無法存取網際網路，您可以在另一部可存取網際網路的電腦上使用 `Save-Help` Cmdlet，先將已更新的說明資訊儲存到網路上的檔案共用，然後使用 `Update-Help` 的 **SourcePath** 參數為說明主題指定此網路位置。</span><span class="sxs-lookup"><span data-stu-id="42d78-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="42d78-274">請考慮在 PowerShell 中設定排程工作，或將一些邏輯新增至您的設定檔指令碼，以定期更新電腦上的說明內容。</span><span class="sxs-lookup"><span data-stu-id="42d78-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="42d78-275">設定檔指令碼將於後續章節中討論。</span><span class="sxs-lookup"><span data-stu-id="42d78-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="42d78-276">摘要</span><span class="sxs-lookup"><span data-stu-id="42d78-276">Summary</span></span>

<span data-ttu-id="42d78-277">在本章中，您已瞭解如何使用 `Get-Help` 和 `Get-Command` 尋找命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="42d78-278">您已學會藉由說明系統，瞭解如何在找到命令後使用這些命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="42d78-279">您也已瞭解如何在有可用的更新時，更新說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="42d78-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="42d78-280">建議您可以一天學習一個 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="42d78-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="42d78-281">檢閱</span><span class="sxs-lookup"><span data-stu-id="42d78-281">Review</span></span>

1. <span data-ttu-id="42d78-282">`Get-Service` 的 **DisplayName** 參數是否為按照位置使用的參數？</span><span class="sxs-lookup"><span data-stu-id="42d78-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="42d78-283">`Get-Process` Cmdlet 有多少個參數集合？</span><span class="sxs-lookup"><span data-stu-id="42d78-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="42d78-284">有哪些 PowerShell 命令可用來處理事件記錄檔？</span><span class="sxs-lookup"><span data-stu-id="42d78-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="42d78-285">有哪些 PowerShell 命令可用來傳回在電腦上執行的 PowerShell 流程的清單？</span><span class="sxs-lookup"><span data-stu-id="42d78-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="42d78-286">如何更新儲存在電腦上的 PowerShell 說明內容？</span><span class="sxs-lookup"><span data-stu-id="42d78-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="42d78-287">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="42d78-287">Recommended Reading</span></span>

<span data-ttu-id="42d78-288">若需深入瞭解本章所提到的主題，建議閱讀下列 PowerShell 說明主題。</span><span class="sxs-lookup"><span data-stu-id="42d78-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="42d78-289">[Get-Help][]</span><span class="sxs-lookup"><span data-stu-id="42d78-289">[Get-Help][]</span></span>
- <span data-ttu-id="42d78-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="42d78-290">[Get-Command][]</span></span>
- <span data-ttu-id="42d78-291">[Update-Help][]</span><span class="sxs-lookup"><span data-stu-id="42d78-291">[Update-Help][]</span></span>
- <span data-ttu-id="42d78-292">[Save-Help][]</span><span class="sxs-lookup"><span data-stu-id="42d78-292">[Save-Help][]</span></span>
- <span data-ttu-id="42d78-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="42d78-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="42d78-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="42d78-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="42d78-295">在下一章中，您將瞭解 `Get-Member` Cmdlet 以及物件、屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="42d78-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[附錄 A]: appendix-a.md
[Appendix A]: appendix-a.md
