---
title: 您想知道有關於 ShouldProcess 的一切 (英文)
description: ShouldProcess 是一項經常遭到忽視的重要功能。 WhatIf 和 Confirm 參數可讓您輕鬆地將這項功能新增至您的函式。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1d9110302a191b90bd11bdf742f77704a8c9d6f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149481"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="8311d-104">您想知道有關於 ShouldProcess 的一切 (英文)</span><span class="sxs-lookup"><span data-stu-id="8311d-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="8311d-105">PowerShell 函式有多項功能，可大幅改善使用者與其互動的方式。</span><span class="sxs-lookup"><span data-stu-id="8311d-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="8311d-106">經常遭到忽視的一項重要功能是 `-WhatIf` 和 `-Confirm` 支援，而且這項功能可以很輕鬆地新增至您的函式。</span><span class="sxs-lookup"><span data-stu-id="8311d-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="8311d-107">在本文中，我們將深入探討如何實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="8311d-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="8311d-108">本文的[原始版本][]出自 [@KevinMarquette][] 所撰寫的部落格。</span><span class="sxs-lookup"><span data-stu-id="8311d-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="8311d-109">PowerShell 小組感謝 Kevin 分享的內容。</span><span class="sxs-lookup"><span data-stu-id="8311d-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="8311d-110">請前往 [PowerShellExplained.com][] 瀏覽他的部落格。</span><span class="sxs-lookup"><span data-stu-id="8311d-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="8311d-111">這是您可以在函式中啟用的簡單功能，為需要的使用者提供安全的網路。</span><span class="sxs-lookup"><span data-stu-id="8311d-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="8311d-112">沒有什麼會比第一次執行您知道可能會有危險的命令更可怕的。</span><span class="sxs-lookup"><span data-stu-id="8311d-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="8311d-113">選擇使用 `-WhatIf` 執行命令，會有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="8311d-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="8311d-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8311d-114">CommonParameters</span></span>

<span data-ttu-id="8311d-115">在探討如何執行這些 [常見的][] 參數之前，我想要快速瞭解它們的使用方式。</span><span class="sxs-lookup"><span data-stu-id="8311d-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="8311d-116">使用 -WhatIf</span><span class="sxs-lookup"><span data-stu-id="8311d-116">Using -WhatIf</span></span>

<span data-ttu-id="8311d-117">當命令支援 `-WhatIf` 參數時，可讓您查看命令所執行的動作，而不是進行變更。</span><span class="sxs-lookup"><span data-stu-id="8311d-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="8311d-118">這是測試命令影響的好方法，特別是在您執行一些破壞性的動作之前。</span><span class="sxs-lookup"><span data-stu-id="8311d-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="8311d-119">如果命令正確地實作 `ShouldProcess`，應該會顯示其所進行的所有變更。</span><span class="sxs-lookup"><span data-stu-id="8311d-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="8311d-120">以下是使用萬用字元來刪除多個檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="8311d-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="8311d-121">使用 -Confirm</span><span class="sxs-lookup"><span data-stu-id="8311d-121">Using -Confirm</span></span>

<span data-ttu-id="8311d-122">支援 `-WhatIf` 的命令也支援 `-Confirm`。</span><span class="sxs-lookup"><span data-stu-id="8311d-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="8311d-123">這可讓您在執行動作之前，先行確認。</span><span class="sxs-lookup"><span data-stu-id="8311d-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="8311d-124">在此情況下，您有多種選擇可讓您繼續、略過變更或停止執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="8311d-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="8311d-125">說明提示會描述諸如此類的每個選項。</span><span class="sxs-lookup"><span data-stu-id="8311d-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="8311d-126">當地語系化</span><span class="sxs-lookup"><span data-stu-id="8311d-126">Localization</span></span>

<span data-ttu-id="8311d-127">此提示會在 PowerShell 中當地語系化，因此語言會根據您作業系統的語言而變更。</span><span class="sxs-lookup"><span data-stu-id="8311d-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="8311d-128">這也是 PowerShell 為您管理的又一件事。</span><span class="sxs-lookup"><span data-stu-id="8311d-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="8311d-129">切換參數</span><span class="sxs-lookup"><span data-stu-id="8311d-129">Switch parameters</span></span>

<span data-ttu-id="8311d-130">讓我們快速查看將值傳遞給切換參數的方法。</span><span class="sxs-lookup"><span data-stu-id="8311d-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="8311d-131">我呼叫此函式的主要原因，是您通常會想要將參數值傳遞給您呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="8311d-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="8311d-132">第一種方法是特定的參數語法，可用於所有參數，不過您大多會看到它用於切換參數。</span><span class="sxs-lookup"><span data-stu-id="8311d-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="8311d-133">您可以指定冒號，將值附加至參數。</span><span class="sxs-lookup"><span data-stu-id="8311d-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="8311d-134">您可以使用變數來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="8311d-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="8311d-135">第二種方法是使用雜湊表來展開值。</span><span class="sxs-lookup"><span data-stu-id="8311d-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="8311d-136">如果您不熟悉雜湊表或展開，我還有另一篇文章，其中涵蓋 [您想知道的雜湊表所有相關內容][]。</span><span class="sxs-lookup"><span data-stu-id="8311d-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="8311d-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="8311d-137">SupportsShouldProcess</span></span>

<span data-ttu-id="8311d-138">啟用 `-WhatIf` 和 `-Confirm` 支援的第一個步驟，是在函式的 `CmdletBinding` 中指定 `SupportsShouldProcess`。</span><span class="sxs-lookup"><span data-stu-id="8311d-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="8311d-139">藉由以這種方式指定 `SupportsShouldProcess`，我們現在可以使用 `-WhatIf` (或 `-Confirm`) 來呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="8311d-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="8311d-140">請注意，我並未建立名稱為 `-WhatIf` 的參數。</span><span class="sxs-lookup"><span data-stu-id="8311d-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="8311d-141">指定 `SupportsShouldProcess` 會自動為我們將其建立。</span><span class="sxs-lookup"><span data-stu-id="8311d-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="8311d-142">當我們在 `Test-ShouldProcess`上指定 `-WhatIf` 參數時，我們所呼叫的某些項目也會執行 `-WhatIf` 處理流程。</span><span class="sxs-lookup"><span data-stu-id="8311d-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="8311d-143">信任但需要確認</span><span class="sxs-lookup"><span data-stu-id="8311d-143">Trust but verify</span></span>

<span data-ttu-id="8311d-144">這裡存在一些危險，那就是信任您所呼叫的所有項目都會繼承 `-WhatIf` 值。</span><span class="sxs-lookup"><span data-stu-id="8311d-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="8311d-145">在其餘的範例中，我將假設它沒有作用，而且在呼叫其他命令時非常明確。</span><span class="sxs-lookup"><span data-stu-id="8311d-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="8311d-146">建議您採取相同動作。</span><span class="sxs-lookup"><span data-stu-id="8311d-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

<span data-ttu-id="8311d-147">稍後當您進一步瞭解所有過程中的所有部分之後，我將會更清楚地回顧細節。</span><span class="sxs-lookup"><span data-stu-id="8311d-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="8311d-148">$PSCmdlet.ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="8311d-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="8311d-149">可讓您執行 `SupportsShouldProcess` 的方法是 `$PSCmdlet.ShouldProcess`。</span><span class="sxs-lookup"><span data-stu-id="8311d-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="8311d-150">您會呼叫 `$PSCmdlet.ShouldProcess(...)`，查看是否應該處理一些邏輯，而 PowerShell 會負責其餘部分。</span><span class="sxs-lookup"><span data-stu-id="8311d-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="8311d-151">讓我們從以下範例開始：</span><span class="sxs-lookup"><span data-stu-id="8311d-151">Let's start with an example:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

<span data-ttu-id="8311d-152">`$PSCmdlet.ShouldProcess($file.name)` 的呼叫會檢查 `-WhatIf` (和 `-Confirm` 參數)，然後據此加以處理。</span><span class="sxs-lookup"><span data-stu-id="8311d-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="8311d-153">`-WhatIf` 會導致 `ShouldProcess` 輸出變更的描述，並傳回 `$false`：</span><span class="sxs-lookup"><span data-stu-id="8311d-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="8311d-154">使用 `-Confirm` 的呼叫會暫停執行指令碼，並提示使用者選擇繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8311d-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="8311d-155">如果使用者選取 `Y`，它會傳回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="8311d-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="8311d-156">`$PSCmdlet.ShouldProcess` 很棒的功能，就是它會提高詳細資訊輸出至雙倍。</span><span class="sxs-lookup"><span data-stu-id="8311d-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="8311d-157">在執行 `ShouldProcess` 時，我經常會依賴這項功能。</span><span class="sxs-lookup"><span data-stu-id="8311d-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="8311d-158">多載</span><span class="sxs-lookup"><span data-stu-id="8311d-158">Overloads</span></span>

<span data-ttu-id="8311d-159">有幾個適用於 `$PSCmdlet.ShouldProcess` 的不同多載 (具有不同的參數) 可用於自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="8311d-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="8311d-160">我們已經看到上述範例中的第一個。</span><span class="sxs-lookup"><span data-stu-id="8311d-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="8311d-161">讓我們仔細檢視。</span><span class="sxs-lookup"><span data-stu-id="8311d-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="8311d-162">這會產生包含函式名稱和目標 (參數值) 的輸出。</span><span class="sxs-lookup"><span data-stu-id="8311d-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="8311d-163">將第二個參數指定為會使用作業值的作業，而不是訊息中的函數名稱。</span><span class="sxs-lookup"><span data-stu-id="8311d-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="8311d-164">下一個選項是指定三個參數，可以充分自訂訊息。</span><span class="sxs-lookup"><span data-stu-id="8311d-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="8311d-165">使用三個參數時，第一個是完整的訊息。</span><span class="sxs-lookup"><span data-stu-id="8311d-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="8311d-166">第二個參數仍會在 `-Confirm` 訊息輸出中使用。</span><span class="sxs-lookup"><span data-stu-id="8311d-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="8311d-167">快速參數參考</span><span class="sxs-lookup"><span data-stu-id="8311d-167">Quick parameter reference</span></span>

<span data-ttu-id="8311d-168">如果您只是要找出應該使用的參數，以下是快速參考，顯示參數如何變更不同 `-WhatIf` 情況中的訊息。</span><span class="sxs-lookup"><span data-stu-id="8311d-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="8311d-169">我通常會搭配兩個參數來使用它。</span><span class="sxs-lookup"><span data-stu-id="8311d-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="8311d-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="8311d-170">ShouldProcessReason</span></span>

<span data-ttu-id="8311d-171">我們有第四個多載，比其他多載更進階。</span><span class="sxs-lookup"><span data-stu-id="8311d-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="8311d-172">它可讓您取得執行 `ShouldProcess` 的原因。</span><span class="sxs-lookup"><span data-stu-id="8311d-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="8311d-173">我在這裡只是為了完整性而加入此內容，因為我們可以改為只檢查 `$WhatIf` 是否為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="8311d-173">I'm only adding this here for completeness because we can just check if `$WhatIf` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="8311d-174">我們必須將 `$reason` 變數傳遞至第四個參數，做為具有 `[ref]` 的參考變數。</span><span class="sxs-lookup"><span data-stu-id="8311d-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="8311d-175">`ShouldProcess` 以 `None` 或 `WhatIf` 值填入 `$reason`。</span><span class="sxs-lookup"><span data-stu-id="8311d-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="8311d-176">我不會說這個很實用，而且我沒有理由要使用它。</span><span class="sxs-lookup"><span data-stu-id="8311d-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="8311d-177">放置位置</span><span class="sxs-lookup"><span data-stu-id="8311d-177">Where to place it</span></span>

<span data-ttu-id="8311d-178">您可以使用 `ShouldProcess` 讓指令碼更安全。</span><span class="sxs-lookup"><span data-stu-id="8311d-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="8311d-179">當您的指令碼進行變更時，就會用到它。</span><span class="sxs-lookup"><span data-stu-id="8311d-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="8311d-180">我想要盡可能將 `$PSCmdlet.ShouldProcess` 呼叫放在最接近變更的位置。</span><span class="sxs-lookup"><span data-stu-id="8311d-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="8311d-181">如果我正在處理項目集合，則會針對每個項目呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8311d-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="8311d-182">因此，呼叫會放在 foreach 迴圈內。</span><span class="sxs-lookup"><span data-stu-id="8311d-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="8311d-183">我緊鄰變更放置 `ShouldProcess` 的原因，就是在指定 `-WhatIf` 時，我想要盡可能多執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="8311d-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="8311d-184">若是可以，我想要執行設定和驗證，讓使用者看到那些錯誤。</span><span class="sxs-lookup"><span data-stu-id="8311d-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="8311d-185">我也想要在驗證我的專案的 Pester 測試中使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="8311d-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="8311d-186">如果我有一個很難在 pester 中模擬的邏輯，我通常可以將它包裝在 `ShouldProcess` 中，然後在我的測試中使用 `-WhatIf` 來呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8311d-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="8311d-187">您最好是測試部分程式碼，而不是什麼程式碼都不進行測試。</span><span class="sxs-lookup"><span data-stu-id="8311d-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="8311d-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="8311d-188">$WhatIfPreference</span></span>

<span data-ttu-id="8311d-189">我們所擁有的第一個喜好設定變數是 `$WhatIfPreference`。</span><span class="sxs-lookup"><span data-stu-id="8311d-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="8311d-190">依預設，這會是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="8311d-190">This is `$false` by default.</span></span> <span data-ttu-id="8311d-191">如果您將它設定為 `$true` 則您的函式會執行，如同您指定 `-WhatIf` 一樣。</span><span class="sxs-lookup"><span data-stu-id="8311d-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="8311d-192">如果您在工作階段中進行這項設定，則所有命令都會執行 `-WhatIf` 執行。</span><span class="sxs-lookup"><span data-stu-id="8311d-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="8311d-193">當您使用 `-WhatIf` 呼叫函式時，`$WhatIfPreference` 的值會設定為函式範圍內的 `$true`。</span><span class="sxs-lookup"><span data-stu-id="8311d-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="8311d-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="8311d-194">ConfirmImpact</span></span>

<span data-ttu-id="8311d-195">我大部分的範例都適用於 `-WhatIf`，但目前為止的所有內容也可以搭配 `-Confirm` 一起使用，藉此提示使用者。</span><span class="sxs-lookup"><span data-stu-id="8311d-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="8311d-196">您可以將函式的 `ConfirmImpact` 設定為 [高]，它會提示使用者，如同使用 `-Confirm` 呼叫一般。</span><span class="sxs-lookup"><span data-stu-id="8311d-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="8311d-197">因為 `High` 的影響，`Test-ShouldProcess` 的這個呼叫正在執行 `-Confirm` 動作。</span><span class="sxs-lookup"><span data-stu-id="8311d-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="8311d-198">最顯著的問題是，缺少了提示使用者之後，在其他指令碼中就更不方便使用了。</span><span class="sxs-lookup"><span data-stu-id="8311d-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="8311d-199">在此案例中，我們可以將 `$false` 傳遞至 `-Confirm` 以隱藏提示。</span><span class="sxs-lookup"><span data-stu-id="8311d-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="8311d-200">我將在稍後的章節中討論如何新增 `-Force` 支援。</span><span class="sxs-lookup"><span data-stu-id="8311d-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="8311d-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="8311d-201">$ConfirmPreference</span></span>

<span data-ttu-id="8311d-202">`$ConfirmPreference` 是自動變數，可控制 `ConfirmImpact` 要求您確認執行的時機。</span><span class="sxs-lookup"><span data-stu-id="8311d-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="8311d-203">以下為適用於 `$ConfirmPreference` 與 `ConfirmImpact` 的可能值。</span><span class="sxs-lookup"><span data-stu-id="8311d-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="8311d-204">使用這些值，您可以針對每個函式指定不同的影響層級。</span><span class="sxs-lookup"><span data-stu-id="8311d-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="8311d-205">如果您的 `$ConfirmPreference` 設定為高於 `ConfirmImpact` 的值，系統就不會提示您確認執行。</span><span class="sxs-lookup"><span data-stu-id="8311d-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="8311d-206">根據預設，`$ConfirmPreference` 會設為 `High` 且 `ConfirmImpact` 為 `Medium`。</span><span class="sxs-lookup"><span data-stu-id="8311d-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="8311d-207">如果您想要讓函式自動提示使用者，請將您的 `ConfirmImpact` 設定為 `High`。</span><span class="sxs-lookup"><span data-stu-id="8311d-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="8311d-208">若它具有破壞性，請將其設定為 `Medium`；如果在生產環境中執行此命令始終安全無虞，則使用 `Low`。</span><span class="sxs-lookup"><span data-stu-id="8311d-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="8311d-209">如果您將其設定為 `none`，即使已指定 `-Confirm` 也不會提示 (但仍會提供您 `-WhatIf` 支援)。</span><span class="sxs-lookup"><span data-stu-id="8311d-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="8311d-210">若是使用 `-Confirm` 呼叫函式，則 `$ConfirmPreference` 的值會設定為函式範圍內的 `Low`。</span><span class="sxs-lookup"><span data-stu-id="8311d-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="8311d-211">隱藏已嵌套的確認提示</span><span class="sxs-lookup"><span data-stu-id="8311d-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="8311d-212">您所呼叫的函式可以挑選 `$ConfirmPreference`。</span><span class="sxs-lookup"><span data-stu-id="8311d-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="8311d-213">這可以建立您新增確認提示的情況，而您呼叫的函式也會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="8311d-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="8311d-214">我要做的是，指定當我已經處理提示時，所呼叫的命令上指定 `-Confirm:$false`。</span><span class="sxs-lookup"><span data-stu-id="8311d-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

<span data-ttu-id="8311d-215">這會讓我們回到先前的警告：當 `-WhatIf` 未傳遞至函式，以及 `-Confirm` 傳遞至函式時，會有一些細微的差異。</span><span class="sxs-lookup"><span data-stu-id="8311d-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="8311d-216">我保證我稍後會回頭探討這個。</span><span class="sxs-lookup"><span data-stu-id="8311d-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="8311d-217">$PSCmdlet.ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="8311d-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="8311d-218">如果您需要的控制比 `ShouldProcess` 提供的更多，您可以使用 `ShouldContinue`直接觸發提示。</span><span class="sxs-lookup"><span data-stu-id="8311d-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="8311d-219">`ShouldContinue` 會忽略 `$ConfirmPreference`、`ConfirmImpact`、`-Confirm`、`$WhatIfPreference` 和 `-WhatIf`，因為它會在每次執行時發出提示。</span><span class="sxs-lookup"><span data-stu-id="8311d-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="8311d-220">快速概覽，`ShouldProcess` 和 `ShouldContinue` 很容易混淆。</span><span class="sxs-lookup"><span data-stu-id="8311d-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="8311d-221">我通常會記得使用 `ShouldProcess`，因為該參數在 `CmdletBinding` 中稱為 `SupportsShouldProcess`。</span><span class="sxs-lookup"><span data-stu-id="8311d-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="8311d-222">在幾乎所有情況下，您都應該使用 `ShouldProcess`。</span><span class="sxs-lookup"><span data-stu-id="8311d-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="8311d-223">這就是我先討論此方法的原因。</span><span class="sxs-lookup"><span data-stu-id="8311d-223">That is why I covered that method first.</span></span>

<span data-ttu-id="8311d-224">讓我們看看 `ShouldContinue` 運作的狀況。</span><span class="sxs-lookup"><span data-stu-id="8311d-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="8311d-225">這可讓我們以較少的選項來提供更簡單的提示。</span><span class="sxs-lookup"><span data-stu-id="8311d-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="8311d-226">`ShouldContinue` 的最大問題是，它會要求使用者以互動方式執行，因為它會一律提示使用者。</span><span class="sxs-lookup"><span data-stu-id="8311d-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="8311d-227">您應該一律建立可供其他指令碼使用的工具。</span><span class="sxs-lookup"><span data-stu-id="8311d-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="8311d-228">藉由執行 `-Force`，您就可以執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8311d-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="8311d-229">我稍後會重新探討這個想法。</span><span class="sxs-lookup"><span data-stu-id="8311d-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="8311d-230">全部皆是</span><span class="sxs-lookup"><span data-stu-id="8311d-230">Yes to all</span></span>

<span data-ttu-id="8311d-231">這會自動使用 `ShouldProcess` 來處理，但我們必須針對 `ShouldContinue` 執行更多工作。</span><span class="sxs-lookup"><span data-stu-id="8311d-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="8311d-232">有第二個方法多載，我們必須以按照參考資料傳入幾個值來控制邏輯。</span><span class="sxs-lookup"><span data-stu-id="8311d-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

<span data-ttu-id="8311d-233">我新增了一個 `foreach` 迴圈和一個集合，以顯示顯示其運作狀況。</span><span class="sxs-lookup"><span data-stu-id="8311d-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="8311d-234">我從 `if` 的陳述式中提取了 `ShouldContinue` 呼叫，使其更便於讀取。</span><span class="sxs-lookup"><span data-stu-id="8311d-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="8311d-235">使用四個參數來呼叫方法，開始變得有點累贅，但我嘗試讓它看起來像我一樣乾淨俐落。</span><span class="sxs-lookup"><span data-stu-id="8311d-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="8311d-236">實作 -Force</span><span class="sxs-lookup"><span data-stu-id="8311d-236">Implementing -Force</span></span>

<span data-ttu-id="8311d-237">`ShouldProcess` 而 `ShouldContinue` 需要以不同的方式來實作 `-Force`。</span><span class="sxs-lookup"><span data-stu-id="8311d-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="8311d-238">這些實作的訣竅在於應該一律執行 `ShouldProcess`，但如果指定 `-Force`，則不應該執行 `ShouldContinue`。</span><span class="sxs-lookup"><span data-stu-id="8311d-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="8311d-239">ShouldProcess -Force</span><span class="sxs-lookup"><span data-stu-id="8311d-239">ShouldProcess -Force</span></span>

<span data-ttu-id="8311d-240">如果您將 `ConfirmImpact` 設定為 `high`，則使用者要嘗試的第一件事，就是以 `-Force` 將它隱藏。</span><span class="sxs-lookup"><span data-stu-id="8311d-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="8311d-241">總之，這是我做的第一件事。</span><span class="sxs-lookup"><span data-stu-id="8311d-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="8311d-242">如果您還記得 `ConfirmImpact` 一節，他們實際上需要呼叫它，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8311d-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="8311d-243">並非所有人都瞭解他們需要這麼做，而且 `-Confirm:$false` 不會隱藏 `ShouldContinue`。</span><span class="sxs-lookup"><span data-stu-id="8311d-243">Not everyone realizes they need to do that and `-Confirm:$false` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="8311d-244">因此，我們應該為使用者的例行性實作 `-Force`。</span><span class="sxs-lookup"><span data-stu-id="8311d-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="8311d-245">請在此檢視這個完整範例：</span><span class="sxs-lookup"><span data-stu-id="8311d-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="8311d-246">我們會新增自己的 `-Force` 參數作為參數，並使用在 `CmdletBinding` 中新增 `SupportsShouldProcess` 時可用的 `$Confirm` 自動參數。</span><span class="sxs-lookup"><span data-stu-id="8311d-246">We add our own `-Force` switch as a parameter and use the `$Confirm` automatic parameter that is available when adding `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="8311d-247">專注在這裡的 `-Force` 邏輯：</span><span class="sxs-lookup"><span data-stu-id="8311d-247">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="8311d-248">如果使用者指定 `-Force`，除非使用者也指定 `-Confirm`，否則我們會想要隱藏確認提示。</span><span class="sxs-lookup"><span data-stu-id="8311d-248">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="8311d-249">這可讓使用者強制執行變更，但仍會確認變更。</span><span class="sxs-lookup"><span data-stu-id="8311d-249">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="8311d-250">然後，我們會在本機範圍中設定 `$ConfirmPreference`，讓我們呼叫 `ShouldProcess` 探索它。</span><span class="sxs-lookup"><span data-stu-id="8311d-250">Then we set `$ConfirmPreference` in the local scope where our call to `ShouldProcess` discoverers it.</span></span>

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="8311d-251">如果有人同時指定 `-Force` 和 `-WhatIf`，則 `-WhatIf` 需要優先執行。</span><span class="sxs-lookup"><span data-stu-id="8311d-251">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="8311d-252">這個方法會保留 `-WhatIf` 流程，因為 `ShouldProcess` 一律會執行。</span><span class="sxs-lookup"><span data-stu-id="8311d-252">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="8311d-253">請勿在 `ShouldProcess` 的 if 陳述式內加入 `$Force` 值的檢查。</span><span class="sxs-lookup"><span data-stu-id="8311d-253">Do not add a check for the `$Force` value inside the if statement with the `ShouldProcess`.</span></span> <span data-ttu-id="8311d-254">這是此特定情況的反模式，僅管這是我在下一節中針對 `ShouldContinue` 所告訴您的內容。</span><span class="sxs-lookup"><span data-stu-id="8311d-254">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="8311d-255">ShouldContinue -Force</span><span class="sxs-lookup"><span data-stu-id="8311d-255">ShouldContinue -Force</span></span>

<span data-ttu-id="8311d-256">這是使用 `ShouldContinue` 執行 `-Force` 的正確方式。</span><span class="sxs-lookup"><span data-stu-id="8311d-256">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="8311d-257">只要將 `$Force` 放在 `-or` 運算子的左側，就可以優先接受評估。</span><span class="sxs-lookup"><span data-stu-id="8311d-257">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="8311d-258">以這種方式撰寫，會導致 `if` 陳述式的執行發生短路。</span><span class="sxs-lookup"><span data-stu-id="8311d-258">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="8311d-259">如果 `$force` 為 `$true`，則不會執行 `ShouldContinue`。</span><span class="sxs-lookup"><span data-stu-id="8311d-259">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="8311d-260">在此情況下，我們不需要擔心 `-Confirm` 或 `-WhatIf`，因為 `ShouldContinue` 不提供支援。</span><span class="sxs-lookup"><span data-stu-id="8311d-260">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="8311d-261">這就是為什麼需要以不同於 `ShouldProcess` 的方式來處理。</span><span class="sxs-lookup"><span data-stu-id="8311d-261">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="8311d-262">範圍問題</span><span class="sxs-lookup"><span data-stu-id="8311d-262">Scope issues</span></span>

<span data-ttu-id="8311d-263">使用 `-WhatIf` 和 `-Confirm` 應該會套用至函式內的所有項目，以及它們所呼叫的所有項目。</span><span class="sxs-lookup"><span data-stu-id="8311d-263">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="8311d-264">若要這麼做，請在函式的本機範圍中，將 `$WhatIfPreference` 設定為 `$true`，或將 `$ConfirmPreference` 設定為 `Low`。</span><span class="sxs-lookup"><span data-stu-id="8311d-264">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="8311d-265">當您呼叫其他函式時，`ShouldProcess` 的呼叫會使用這些值。</span><span class="sxs-lookup"><span data-stu-id="8311d-265">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="8311d-266">在大部分的情況下，這實際上會正常運作。</span><span class="sxs-lookup"><span data-stu-id="8311d-266">This actually works correctly most of the time.</span></span> <span data-ttu-id="8311d-267">每當您在相同的範圍內呼叫內建 Cmdlet 或函式時，這個方法都會正常運作。</span><span class="sxs-lookup"><span data-stu-id="8311d-267">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="8311d-268">當您從主控台呼叫指令碼模組中的指令碼或函式時，這個方法也會正常運作。</span><span class="sxs-lookup"><span data-stu-id="8311d-268">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="8311d-269">當指令碼或指令碼模組呼叫其他指令碼模組中的函式時，在該單一特定位置，這個方法就是無法運作。</span><span class="sxs-lookup"><span data-stu-id="8311d-269">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="8311d-270">這可能不是很大的問題，但您建立或從 PSGallery 中提取的大部分模組都是指令碼模組。</span><span class="sxs-lookup"><span data-stu-id="8311d-270">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="8311d-271">核心問題在於，若從其他指令碼模組中的函式呼叫，則指令碼模組不會繼承 `$WhatIfPreference` 或 `$ConfirmPreference` (以及其他數個參數) 的值。</span><span class="sxs-lookup"><span data-stu-id="8311d-271">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="8311d-272">將此摘要當做一般規則的最佳方式在於，此方式適用於二進位模組，而且絕對不會信任它來處理指令碼模組。</span><span class="sxs-lookup"><span data-stu-id="8311d-272">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="8311d-273">如果您不確定，無論是進行測試或是直接假設它無法正常運作，</span><span class="sxs-lookup"><span data-stu-id="8311d-273">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="8311d-274">我個人都認為這樣非常危險；因為它會產生一些情況，讓您將 `-WhatIf` 支援新增至多個模組，以便在隔離中正常運作，但無法在彼此呼叫時正常運作。</span><span class="sxs-lookup"><span data-stu-id="8311d-274">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="8311d-275">我們有 GitHub RFC 致力於修正此問題。</span><span class="sxs-lookup"><span data-stu-id="8311d-275">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="8311d-276">如需詳細資訊，請參閱 [將執行喜好設定傳播至指令碼模組範圍之外][RFC]。</span><span class="sxs-lookup"><span data-stu-id="8311d-276">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="8311d-277">關閉時</span><span class="sxs-lookup"><span data-stu-id="8311d-277">In closing</span></span>

<span data-ttu-id="8311d-278">我必須在每次需要使用 `ShouldProcess` 時，都要查閱如何使用。</span><span class="sxs-lookup"><span data-stu-id="8311d-278">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="8311d-279">我花了很長的時間來區分 `ShouldProcess` 與 `ShouldContinue`。</span><span class="sxs-lookup"><span data-stu-id="8311d-279">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="8311d-280">我幾乎都需要查詢要使用的參數。</span><span class="sxs-lookup"><span data-stu-id="8311d-280">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="8311d-281">因此，如果您仍不時感到困惑，請不用擔心。</span><span class="sxs-lookup"><span data-stu-id="8311d-281">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="8311d-282">我們會在您需要時提供這篇文章。</span><span class="sxs-lookup"><span data-stu-id="8311d-282">This article will be here when you need it.</span></span> <span data-ttu-id="8311d-283">我確定我自己會經常參考它。</span><span class="sxs-lookup"><span data-stu-id="8311d-283">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="8311d-284">如果您喜歡這篇文章，請使用下列連結，在 Twitter 上與我分享您的看法。</span><span class="sxs-lookup"><span data-stu-id="8311d-284">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="8311d-285">我總是喜歡收到因為我所寫的內容而獲致價值的使用者的消息。</span><span class="sxs-lookup"><span data-stu-id="8311d-285">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[常見的]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[您想知道的雜湊表所有相關內容]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
