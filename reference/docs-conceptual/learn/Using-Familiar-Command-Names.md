---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用熟悉的命令名稱
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030888"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="2dcba-103">使用熟悉的命令名稱</span><span class="sxs-lookup"><span data-stu-id="2dcba-103">Using familiar command names</span></span>

<span data-ttu-id="2dcba-104">PowerShell 支援別名，以使用替代名稱來參考命令。</span><span class="sxs-lookup"><span data-stu-id="2dcba-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="2dcba-105">別名讓具有其他殼層使用體驗的使用者能夠使用他們已經知道的常見命令名稱，在 PowerShell 中執行類似作業。</span><span class="sxs-lookup"><span data-stu-id="2dcba-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="2dcba-106">別名會將新名稱與另一個命令產生關聯。</span><span class="sxs-lookup"><span data-stu-id="2dcba-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="2dcba-107">例如，PowerShell 具有會清除輸出視窗的內部函式 `Clear-Host`。</span><span class="sxs-lookup"><span data-stu-id="2dcba-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="2dcba-108">您可以在命令提示字元中輸入 `cls` 或 `clear` 別名。</span><span class="sxs-lookup"><span data-stu-id="2dcba-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="2dcba-109">PowerShell 會解譯這些別名並執行 `Clear-Host` 函式。</span><span class="sxs-lookup"><span data-stu-id="2dcba-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="2dcba-110">此功能可協助使用者學習 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2dcba-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="2dcba-111">首先，大部分的 **cmd.exe** 與 Unix 使用者都具備他們已經透過名稱知道的大量命令技能。</span><span class="sxs-lookup"><span data-stu-id="2dcba-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="2dcba-112">PowerShell 對應項可能不會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="2dcba-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="2dcba-113">不過，結果非常接近，足以讓使用者在不知道 PowerShell 命令名稱的情況下執行動作。</span><span class="sxs-lookup"><span data-stu-id="2dcba-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="2dcba-114">在學習新的命令殼層時，「手指記憶」是挫折的另一個主要來源。</span><span class="sxs-lookup"><span data-stu-id="2dcba-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="2dcba-115">如果您已使用 **cmd.exe** 多年，您可能會反過來輸入 `cls` 命令來清除畫面。</span><span class="sxs-lookup"><span data-stu-id="2dcba-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="2dcba-116">如果沒有 `Clear-Host` 的別名，您就會收到錯誤訊息，而且不知道該怎麼清除輸出。</span><span class="sxs-lookup"><span data-stu-id="2dcba-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="2dcba-117">下列清單顯示一些您可以在 PowerShell 中使用的常見 **cmd.exe** 與 Unix 命令：</span><span class="sxs-lookup"><span data-stu-id="2dcba-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="2dcba-118">cat</span><span class="sxs-lookup"><span data-stu-id="2dcba-118">cat</span></span>|<span data-ttu-id="2dcba-119">dir</span><span class="sxs-lookup"><span data-stu-id="2dcba-119">dir</span></span>|<span data-ttu-id="2dcba-120">mount</span><span class="sxs-lookup"><span data-stu-id="2dcba-120">mount</span></span>|<span data-ttu-id="2dcba-121">rm</span><span class="sxs-lookup"><span data-stu-id="2dcba-121">rm</span></span>|
|<span data-ttu-id="2dcba-122">cd</span><span class="sxs-lookup"><span data-stu-id="2dcba-122">cd</span></span>|<span data-ttu-id="2dcba-123">echo</span><span class="sxs-lookup"><span data-stu-id="2dcba-123">echo</span></span>|<span data-ttu-id="2dcba-124">move</span><span class="sxs-lookup"><span data-stu-id="2dcba-124">move</span></span>|<span data-ttu-id="2dcba-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="2dcba-125">rmdir</span></span>|
|<span data-ttu-id="2dcba-126">chdir</span><span class="sxs-lookup"><span data-stu-id="2dcba-126">chdir</span></span>|<span data-ttu-id="2dcba-127">erase</span><span class="sxs-lookup"><span data-stu-id="2dcba-127">erase</span></span>|<span data-ttu-id="2dcba-128">popd</span><span class="sxs-lookup"><span data-stu-id="2dcba-128">popd</span></span>|<span data-ttu-id="2dcba-129">sleep</span><span class="sxs-lookup"><span data-stu-id="2dcba-129">sleep</span></span>|
|<span data-ttu-id="2dcba-130">clear</span><span class="sxs-lookup"><span data-stu-id="2dcba-130">clear</span></span>|<span data-ttu-id="2dcba-131">h</span><span class="sxs-lookup"><span data-stu-id="2dcba-131">h</span></span>|<span data-ttu-id="2dcba-132">ps</span><span class="sxs-lookup"><span data-stu-id="2dcba-132">ps</span></span>|<span data-ttu-id="2dcba-133">sort</span><span class="sxs-lookup"><span data-stu-id="2dcba-133">sort</span></span>|
|<span data-ttu-id="2dcba-134">cls</span><span class="sxs-lookup"><span data-stu-id="2dcba-134">cls</span></span>|<span data-ttu-id="2dcba-135">history</span><span class="sxs-lookup"><span data-stu-id="2dcba-135">history</span></span>|<span data-ttu-id="2dcba-136">pushd</span><span class="sxs-lookup"><span data-stu-id="2dcba-136">pushd</span></span>|<span data-ttu-id="2dcba-137">tee</span><span class="sxs-lookup"><span data-stu-id="2dcba-137">tee</span></span>|
|<span data-ttu-id="2dcba-138">copy</span><span class="sxs-lookup"><span data-stu-id="2dcba-138">copy</span></span>|<span data-ttu-id="2dcba-139">kill</span><span class="sxs-lookup"><span data-stu-id="2dcba-139">kill</span></span>|<span data-ttu-id="2dcba-140">pwd</span><span class="sxs-lookup"><span data-stu-id="2dcba-140">pwd</span></span>|<span data-ttu-id="2dcba-141">type</span><span class="sxs-lookup"><span data-stu-id="2dcba-141">type</span></span>|
|<span data-ttu-id="2dcba-142">del</span><span class="sxs-lookup"><span data-stu-id="2dcba-142">del</span></span>|<span data-ttu-id="2dcba-143">lp</span><span class="sxs-lookup"><span data-stu-id="2dcba-143">lp</span></span>|<span data-ttu-id="2dcba-144">r</span><span class="sxs-lookup"><span data-stu-id="2dcba-144">r</span></span>|<span data-ttu-id="2dcba-145">write</span><span class="sxs-lookup"><span data-stu-id="2dcba-145">write</span></span>|
|<span data-ttu-id="2dcba-146">diff</span><span class="sxs-lookup"><span data-stu-id="2dcba-146">diff</span></span>|<span data-ttu-id="2dcba-147">ls</span><span class="sxs-lookup"><span data-stu-id="2dcba-147">ls</span></span>|<span data-ttu-id="2dcba-148">ren</span><span class="sxs-lookup"><span data-stu-id="2dcba-148">ren</span></span>||

<span data-ttu-id="2dcba-149">`Get-Alias` Cmdlet 會顯示與別名相關聯之原生 PowerShell 命令的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="2dcba-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="2dcba-150">解譯標準別名</span><span class="sxs-lookup"><span data-stu-id="2dcba-150">Interpreting standard aliases</span></span>

<span data-ttu-id="2dcba-151">先前提到的別名是專為與其他命令殼層名稱相容所設計。</span><span class="sxs-lookup"><span data-stu-id="2dcba-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="2dcba-152">PowerShell 內建的大部分別名都是基於簡潔性而設計的。</span><span class="sxs-lookup"><span data-stu-id="2dcba-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="2dcba-153">較短的名稱比較容易輸入，但如果您不知道它們指的是什麼，就會變得不容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="2dcba-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="2dcba-154">PowerShell 別名試圖在清晰度與簡潔性之間做出妥協。</span><span class="sxs-lookup"><span data-stu-id="2dcba-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="2dcba-155">PowerShell 會針對常見名詞與指令動詞使用一組標準別名。</span><span class="sxs-lookup"><span data-stu-id="2dcba-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="2dcba-156">範例縮寫：</span><span class="sxs-lookup"><span data-stu-id="2dcba-156">Example abbreviations:</span></span>

| <span data-ttu-id="2dcba-157">名詞或指令動詞</span><span class="sxs-lookup"><span data-stu-id="2dcba-157">Noun or Verb</span></span> | <span data-ttu-id="2dcba-158">縮寫</span><span class="sxs-lookup"><span data-stu-id="2dcba-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="2dcba-159">Get</span><span class="sxs-lookup"><span data-stu-id="2dcba-159">Get</span></span>          | <span data-ttu-id="2dcba-160">g</span><span class="sxs-lookup"><span data-stu-id="2dcba-160">g</span></span>            |
| <span data-ttu-id="2dcba-161">Set</span><span class="sxs-lookup"><span data-stu-id="2dcba-161">Set</span></span>          | <span data-ttu-id="2dcba-162">s</span><span class="sxs-lookup"><span data-stu-id="2dcba-162">s</span></span>            |
| <span data-ttu-id="2dcba-163">Item</span><span class="sxs-lookup"><span data-stu-id="2dcba-163">Item</span></span>         | <span data-ttu-id="2dcba-164">i</span><span class="sxs-lookup"><span data-stu-id="2dcba-164">i</span></span>            |
| <span data-ttu-id="2dcba-165">Location</span><span class="sxs-lookup"><span data-stu-id="2dcba-165">Location</span></span>     | <span data-ttu-id="2dcba-166">l</span><span class="sxs-lookup"><span data-stu-id="2dcba-166">l</span></span>            |
| <span data-ttu-id="2dcba-167">Command</span><span class="sxs-lookup"><span data-stu-id="2dcba-167">Command</span></span>      | <span data-ttu-id="2dcba-168">cm</span><span class="sxs-lookup"><span data-stu-id="2dcba-168">cm</span></span>           |
| <span data-ttu-id="2dcba-169">Alias</span><span class="sxs-lookup"><span data-stu-id="2dcba-169">Alias</span></span>        | <span data-ttu-id="2dcba-170">al</span><span class="sxs-lookup"><span data-stu-id="2dcba-170">al</span></span>           |

<span data-ttu-id="2dcba-171">當您知道縮寫名稱，就能了解這些別名。</span><span class="sxs-lookup"><span data-stu-id="2dcba-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="2dcba-172">Cmdlet 名稱</span><span class="sxs-lookup"><span data-stu-id="2dcba-172">Cmdlet name</span></span>    | <span data-ttu-id="2dcba-173">Alias</span><span class="sxs-lookup"><span data-stu-id="2dcba-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="2dcba-174">gi</span><span class="sxs-lookup"><span data-stu-id="2dcba-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="2dcba-175">si</span><span class="sxs-lookup"><span data-stu-id="2dcba-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="2dcba-176">gl</span><span class="sxs-lookup"><span data-stu-id="2dcba-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="2dcba-177">sl</span><span class="sxs-lookup"><span data-stu-id="2dcba-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="2dcba-178">gcm</span><span class="sxs-lookup"><span data-stu-id="2dcba-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="2dcba-179">gal</span><span class="sxs-lookup"><span data-stu-id="2dcba-179">gal</span></span>   |

<span data-ttu-id="2dcba-180">一旦您熟悉 PowerShell 別名之後，很容易就能猜出 **sal** 別名是指 `Set-Alias`。</span><span class="sxs-lookup"><span data-stu-id="2dcba-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="2dcba-181">建立新別名</span><span class="sxs-lookup"><span data-stu-id="2dcba-181">Creating new aliases</span></span>

<span data-ttu-id="2dcba-182">您可以使用 `Set-Alias` Cmdlet 來建立自己的別名。</span><span class="sxs-lookup"><span data-stu-id="2dcba-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="2dcba-183">例如，下列陳述式會建立先前所討論的標準 Cmdlet 別名：</span><span class="sxs-lookup"><span data-stu-id="2dcba-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="2dcba-184">在內部，PowerShell 會在啟動期間使用類似命令，但這些別名無法變更。</span><span class="sxs-lookup"><span data-stu-id="2dcba-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="2dcba-185">如果您嘗試執行這其中一個命令，則會收到說明無法修改別名的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2dcba-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="2dcba-186">例如：</span><span class="sxs-lookup"><span data-stu-id="2dcba-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
