---
description: 說明 PowerShell 中的範圍概念，並示範如何設定和變更元素的範圍。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 3e165867be5887ae15890f795531b5a3048c4550
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206888"
---
# <a name="about-scopes"></a><span data-ttu-id="a1101-104">關於範圍</span><span class="sxs-lookup"><span data-stu-id="a1101-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="a1101-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a1101-105">Short description</span></span>
<span data-ttu-id="a1101-106">說明 PowerShell 中的範圍概念，並示範如何設定和變更元素的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="a1101-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="a1101-107">Long description</span></span>

<span data-ttu-id="a1101-108">PowerShell 會限制對變數、別名、函式和 PowerShell 磁片磁碟機的存取， (Psdrive) ，方法是限制可讀取和變更的位置。</span><span class="sxs-lookup"><span data-stu-id="a1101-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="a1101-109">PowerShell 會使用範圍規則，以確保您不會不慎變更不應該變更的專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="a1101-110">以下是範圍的基本規則：</span><span class="sxs-lookup"><span data-stu-id="a1101-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="a1101-111">範圍可能會被嵌套。</span><span class="sxs-lookup"><span data-stu-id="a1101-111">Scopes may nest.</span></span> <span data-ttu-id="a1101-112">外部範圍稱為父範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="a1101-113">任何嵌套的範圍都是該父系的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="a1101-114">除非您明確地將專案設為私用，否則專案會在其建立所在的範圍和任何子範圍中顯示。</span><span class="sxs-lookup"><span data-stu-id="a1101-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="a1101-115">您可以在一或多個範圍中放置變數、別名、函式或 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="a1101-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="a1101-116">除非您明確指定不同的範圍，否則您在範圍內建立的專案只能在建立它的範圍內變更。</span><span class="sxs-lookup"><span data-stu-id="a1101-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="a1101-117">如果您在範圍中建立專案，且該專案與不同範圍中的專案共用其名稱，則原始專案可能會隱藏在新的專案下，但不會覆寫或變更。</span><span class="sxs-lookup"><span data-stu-id="a1101-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="a1101-118">PowerShell 範圍</span><span class="sxs-lookup"><span data-stu-id="a1101-118">PowerShell Scopes</span></span>

<span data-ttu-id="a1101-119">PowerShell 支援下列範圍：</span><span class="sxs-lookup"><span data-stu-id="a1101-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="a1101-120">Global： PowerShell 啟動時作用中的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-120">Global: The scope that is in effect when PowerShell starts.</span></span> <span data-ttu-id="a1101-121">在全域範圍中建立 PowerShell 啟動時所出現的變數和函式，例如自動變數和喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="a1101-122">您 PowerShell 設定檔中的變數、別名和函式也會在全域範圍中建立。</span><span class="sxs-lookup"><span data-stu-id="a1101-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span>

- <span data-ttu-id="a1101-123">Local：目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-123">Local: The current scope.</span></span> <span data-ttu-id="a1101-124">區域範圍可以是全域範圍或任何其他範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-124">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="a1101-125">腳本：指令檔執行時所建立的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-125">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="a1101-126">只有腳本中的命令會在腳本範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="a1101-126">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="a1101-127">針對腳本中的命令，腳本範圍是區域範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-127">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="a1101-128">**私** 用不是範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-128">**Private** is not a scope.</span></span> <span data-ttu-id="a1101-129">它是一種 [選項](#private-option) ，可變更專案定義範圍之外的專案可見度。</span><span class="sxs-lookup"><span data-stu-id="a1101-129">It is an [option](#private-option) that changes the visibility of an item outside of the the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="a1101-130">父系和子範圍</span><span class="sxs-lookup"><span data-stu-id="a1101-130">Parent and Child Scopes</span></span>

<span data-ttu-id="a1101-131">您可以藉由執行腳本或函式、建立會話，或啟動新的 PowerShell 實例來建立新的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-131">You can create a new scope by running a script or function, by creating a session, or by starting a new instance of PowerShell.</span></span> <span data-ttu-id="a1101-132">當您建立新的範圍時，結果會是 (原始範圍) 的父範圍，以及 () 建立之範圍的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-132">When you create a new scope, the result is a parent scope (the original scope) and a child scope (the scope that you created).</span></span>

<span data-ttu-id="a1101-133">在 PowerShell 中，所有範圍都是全域範圍的子範圍，但您可以建立許多範圍和許多遞迴範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-133">In PowerShell, all scopes are child scopes of the global scope, but you can create many scopes and many recursive scopes.</span></span>

<span data-ttu-id="a1101-134">除非您明確地將專案設為私用，否則父範圍中的專案可供子範圍使用。</span><span class="sxs-lookup"><span data-stu-id="a1101-134">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="a1101-135">不過，除非您在建立專案時明確指定範圍，否則您在子範圍中建立和變更的專案不會影響父範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-135">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

## <a name="inheritance"></a><span data-ttu-id="a1101-136">繼承</span><span class="sxs-lookup"><span data-stu-id="a1101-136">Inheritance</span></span>

<span data-ttu-id="a1101-137">子範圍不會繼承父範圍中的變數、別名和函式。</span><span class="sxs-lookup"><span data-stu-id="a1101-137">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="a1101-138">除非專案是私用的，否則子範圍可以查看父範圍中的專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-138">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="a1101-139">而且，它可以藉由明確指定父範圍來變更專案，但是這些專案不是子範圍的一部分。</span><span class="sxs-lookup"><span data-stu-id="a1101-139">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="a1101-140">不過，會使用一組專案來建立子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-140">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="a1101-141">通常，它會包含具有 **AllScope** 選項的所有別名。</span><span class="sxs-lookup"><span data-stu-id="a1101-141">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="a1101-142">本文稍後會討論這個選項。</span><span class="sxs-lookup"><span data-stu-id="a1101-142">This option is discussed later in this article.</span></span> <span data-ttu-id="a1101-143">它包含具有 **AllScope** 選項的所有變數，加上一些自動變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-143">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="a1101-144">若要尋找特定範圍中的專案，請使用或的範圍 `Get-Variable` 參數 `Get-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-144">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="a1101-145">例如，若要取得區域範圍中的所有變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="a1101-145">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="a1101-146">若要取得全域範圍中的所有變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="a1101-146">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="a1101-147">範圍修飾符</span><span class="sxs-lookup"><span data-stu-id="a1101-147">Scope Modifiers</span></span>

<span data-ttu-id="a1101-148">變數、別名或函式名稱可以包含下列任何一個選擇性範圍修飾詞：</span><span class="sxs-lookup"><span data-stu-id="a1101-148">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="a1101-149">`global:` -指定名稱存在於 **全域** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="a1101-149">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="a1101-150">`local:` -指定名稱存在於 **區域** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="a1101-150">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="a1101-151">目前的範圍一律是 **區域** 範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-151">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="a1101-152">`private:` -指定名稱是 **私** 用的，而且只有目前的範圍可見。</span><span class="sxs-lookup"><span data-stu-id="a1101-152">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="a1101-153">`script:` -指定名稱存在於 **腳本** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="a1101-153">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="a1101-154">如果沒有最接近的上階腳本檔案， **腳本** 範圍就是最接近的上階腳本檔案範圍或 **全域** 。</span><span class="sxs-lookup"><span data-stu-id="a1101-154">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="a1101-155">`using:` -用來存取在另一個範圍中定義的變數，並透過如和的 Cmdlet 執行腳本 `Start-Job` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-155">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="a1101-156">`workflow:` -指定名稱存在於工作流程中。</span><span class="sxs-lookup"><span data-stu-id="a1101-156">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="a1101-157">注意： PowerShell Core 中不支援工作流程。</span><span class="sxs-lookup"><span data-stu-id="a1101-157">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="a1101-158">`<variable-namespace>` -PowerShell New-psdrive 提供者所建立的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a1101-158">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="a1101-159">例如：</span><span class="sxs-lookup"><span data-stu-id="a1101-159">For example:</span></span>

  |  <span data-ttu-id="a1101-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="a1101-160">Namespace</span></span>  |                    <span data-ttu-id="a1101-161">描述</span><span class="sxs-lookup"><span data-stu-id="a1101-161">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="a1101-162">目前範圍中定義的別名</span><span class="sxs-lookup"><span data-stu-id="a1101-162">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="a1101-163">目前範圍中定義的環境變數</span><span class="sxs-lookup"><span data-stu-id="a1101-163">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="a1101-164">目前範圍中定義的函數</span><span class="sxs-lookup"><span data-stu-id="a1101-164">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="a1101-165">目前範圍中定義的變數</span><span class="sxs-lookup"><span data-stu-id="a1101-165">Variables defined in the current scope</span></span>             |

<span data-ttu-id="a1101-166">腳本的預設範圍是腳本範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-166">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="a1101-167">函數和別名的預設範圍是區域範圍，即使它們是在腳本中定義也一樣。</span><span class="sxs-lookup"><span data-stu-id="a1101-167">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="a1101-168">使用範圍修飾符</span><span class="sxs-lookup"><span data-stu-id="a1101-168">Using scope modifiers</span></span>

<span data-ttu-id="a1101-169">若要指定新變數、別名或函數的範圍，請使用範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="a1101-169">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="a1101-170">變數中範圍修飾詞的語法為：</span><span class="sxs-lookup"><span data-stu-id="a1101-170">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="a1101-171">函數中的範圍修飾詞語法為：</span><span class="sxs-lookup"><span data-stu-id="a1101-171">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="a1101-172">下列不使用範圍修飾符的命令會在目前或 **區域** 範圍中建立變數：</span><span class="sxs-lookup"><span data-stu-id="a1101-172">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="a1101-173">若要在 **全域** 範圍中建立相同的變數，請使用範圍 `global:` 修飾符：</span><span class="sxs-lookup"><span data-stu-id="a1101-173">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="a1101-174">若要在 **腳本** 範圍中建立相同的變數，請使用 `script:` 範圍修飾符：</span><span class="sxs-lookup"><span data-stu-id="a1101-174">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="a1101-175">您也可以搭配函數使用範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="a1101-175">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="a1101-176">下列函式定義會在 **全域** 範圍中建立函數：</span><span class="sxs-lookup"><span data-stu-id="a1101-176">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="a1101-177">您也可以使用範圍修飾符來參考不同範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-177">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="a1101-178">下列命令會參考 `$test` 變數，先在本機範圍，然後在全域範圍內：</span><span class="sxs-lookup"><span data-stu-id="a1101-178">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="a1101-179">`Using:`範圍修飾詞</span><span class="sxs-lookup"><span data-stu-id="a1101-179">The `Using:` scope modifier</span></span>

<span data-ttu-id="a1101-180">使用是一種特殊的範圍修飾詞，用來識別遠端命令中的本機變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-180">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="a1101-181">如果沒有修飾詞，PowerShell 就會在遠端會話中定義遠端命令中的變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-181">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="a1101-182">`Using`範圍修飾詞是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a1101-182">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="a1101-183">針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="a1101-183">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="a1101-184">`Using`下列內容支援範圍修飾符：</span><span class="sxs-lookup"><span data-stu-id="a1101-184">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="a1101-185">從遠端執行的命令，從 `Invoke-Command` 使用 **ComputerName** 、 **HostName** 、 **SSHConnection** 或 **Session** 參數開始， (遠端會話) </span><span class="sxs-lookup"><span data-stu-id="a1101-185">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="a1101-186">背景工作，以 `Start-Job` (跨進程會話開始) </span><span class="sxs-lookup"><span data-stu-id="a1101-186">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="a1101-187">透過 `Start-ThreadJob` (個別執行緒會話啟動的執行緒作業) </span><span class="sxs-lookup"><span data-stu-id="a1101-187">Thread jobs started via `Start-ThreadJob` (separate thread session)</span></span>

<span data-ttu-id="a1101-188">視內容而定，內嵌變數值是呼叫端範圍中資料的獨立複本，或是對它的參考。</span><span class="sxs-lookup"><span data-stu-id="a1101-188">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="a1101-189">在遠端和跨進程的會話中，它們一律是獨立的複本。</span><span class="sxs-lookup"><span data-stu-id="a1101-189">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="a1101-190">如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a1101-190">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="a1101-191">線上程會話中，它們是以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="a1101-191">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="a1101-192">這表示可以修改不同執行緒中的呼叫範圍變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-192">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="a1101-193">若要安全地修改變數，需要執行緒同步處理。</span><span class="sxs-lookup"><span data-stu-id="a1101-193">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="a1101-194">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="a1101-194">For more information see:</span></span>

- [<span data-ttu-id="a1101-195">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="a1101-195">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="a1101-196">變數值的序列化</span><span class="sxs-lookup"><span data-stu-id="a1101-196">Serialization of variable values</span></span>

<span data-ttu-id="a1101-197">遠端執行的命令和背景工作會跨進程執行。</span><span class="sxs-lookup"><span data-stu-id="a1101-197">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="a1101-198">跨進程會話使用以 XML 為基礎的序列化和還原序列化，讓變數的值可以跨進程界限使用。</span><span class="sxs-lookup"><span data-stu-id="a1101-198">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="a1101-199">序列化程式會將物件轉換為包含原始物件屬性但不包含其方法的 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="a1101-199">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="a1101-200">針對一組有限的類型，還原序列化會將解除凍結物件回原始型別。</span><span class="sxs-lookup"><span data-stu-id="a1101-200">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="a1101-201">解除凍結物件是原始物件實例的複本。</span><span class="sxs-lookup"><span data-stu-id="a1101-201">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="a1101-202">它具有類型屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="a1101-202">It has the type properties and methods.</span></span> <span data-ttu-id="a1101-203">針對簡單類型（例如 **system.object** ），複本是精確的。</span><span class="sxs-lookup"><span data-stu-id="a1101-203">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="a1101-204">如果是複雜類型，則會完美複製。</span><span class="sxs-lookup"><span data-stu-id="a1101-204">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="a1101-205">例如，解除凍結憑證物件不包含私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a1101-205">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="a1101-206">所有其他類型的實例都是 **PSObject** 實例。</span><span class="sxs-lookup"><span data-stu-id="a1101-206">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="a1101-207">**PSTypeNames** 屬性包含 **前面加上** 還原序列化的原始型別名稱，例如 **Deserialized.System。Data DataTable**</span><span class="sxs-lookup"><span data-stu-id="a1101-207">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="a1101-208">AllScope 選項</span><span class="sxs-lookup"><span data-stu-id="a1101-208">The AllScope Option</span></span>

<span data-ttu-id="a1101-209">變數和別名具有可採用 **AllScope** 值的 **選項** 屬性。</span><span class="sxs-lookup"><span data-stu-id="a1101-209">Variables and aliases have an **Option** property that can take a value of **AllScope** .</span></span> <span data-ttu-id="a1101-210">具有 **AllScope** 屬性的專案會成為您所建立之任何子範圍的一部分，不過父範圍不會追溯這些專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-210">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="a1101-211">具有 **AllScope** 屬性的專案會顯示在子範圍中，而且屬於該範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-211">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="a1101-212">對任何範圍中的專案所做的變更，都會影響定義變數的所有範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-212">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="a1101-213">管理領域</span><span class="sxs-lookup"><span data-stu-id="a1101-213">Managing Scope</span></span>

<span data-ttu-id="a1101-214">有數個 Cmdlet 具有 **範圍** 參數，可讓您取得或設定 (建立和變更特定範圍中) 專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-214">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="a1101-215">使用下列命令，在您的會話中尋找具有 **範圍** 參數的所有 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="a1101-215">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="a1101-216">若要尋找在特定範圍中可見的變數，請使用的 `Scope` 參數 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-216">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="a1101-217">可見的變數包括全域變數、父範圍中的變數，以及目前範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-217">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="a1101-218">例如，下列命令會取得在區域範圍中可見的變數：</span><span class="sxs-lookup"><span data-stu-id="a1101-218">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="a1101-219">若要在特定範圍內建立變數，請使用範圍修飾符或的 **範圍** 參數 `Set-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-219">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="a1101-220">下列命令會在全域範圍中建立變數：</span><span class="sxs-lookup"><span data-stu-id="a1101-220">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="a1101-221">您也可以使用 `New-Alias` 、或 Cmdlet 的 scope 參數 `Set-Alias` `Get-Alias` 來指定範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-221">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="a1101-222">下列命令會在全域範圍中建立別名：</span><span class="sxs-lookup"><span data-stu-id="a1101-222">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="a1101-223">若要取得特定範圍中的函式，請在範圍內使用 `Get-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1101-223">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="a1101-224">`Get-Item`Cmdlet 沒有 **範圍** 參數。</span><span class="sxs-lookup"><span data-stu-id="a1101-224">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="a1101-225">針對使用 **範圍** 參數的 Cmdlet，您也可以依編號參考範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-225">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="a1101-226">此數位會描述某範圍與另一個範圍之間的相對位置。</span><span class="sxs-lookup"><span data-stu-id="a1101-226">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="a1101-227">範圍0代表目前或區域範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-227">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="a1101-228">範圍1表示直屬父範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-228">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="a1101-229">範圍2表示父範圍的父系，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a1101-229">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="a1101-230">如果您已建立許多遞迴範圍，則編號的範圍會很有用。</span><span class="sxs-lookup"><span data-stu-id="a1101-230">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="a1101-231">使用點來源標記法搭配範圍</span><span class="sxs-lookup"><span data-stu-id="a1101-231">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="a1101-232">腳本和函式會遵循範圍的所有規則。</span><span class="sxs-lookup"><span data-stu-id="a1101-232">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="a1101-233">您可以在特定範圍中建立它們，除非您使用 Cmdlet 參數或範圍修飾符來變更該範圍，否則它們只會影響該範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-233">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="a1101-234">但是，您可以使用點來源標記法，將腳本或函式新增至目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-234">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="a1101-235">然後，當腳本在目前的範圍中執行時，腳本所建立的任何函式、別名和變數都會出現在目前的範圍中。</span><span class="sxs-lookup"><span data-stu-id="a1101-235">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="a1101-236">若要將函式新增至目前的範圍，請在函式呼叫中輸入點 (. ) 和函式名稱之前的空格。</span><span class="sxs-lookup"><span data-stu-id="a1101-236">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="a1101-237">例如，若要從腳本範圍中的 C：\Scripts 目錄執行 Sample.ps1 腳本 (腳本) 的預設值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a1101-237">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="a1101-238">若要在本機範圍中執行 Sample.ps1 腳本，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a1101-238">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="a1101-239">當您使用呼叫運算子 ( # A0) 來執行函式或腳本時，不會將它新增至目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-239">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="a1101-240">下列範例會使用呼叫運算子：</span><span class="sxs-lookup"><span data-stu-id="a1101-240">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="a1101-241">您可以在 [about_operators](about_operators.md)中閱讀呼叫運算子的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a1101-241">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="a1101-242">在目前的範圍中，無法使用 Sample.ps1 腳本所建立的任何別名、函數或變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-242">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="a1101-243">不含範圍的限制</span><span class="sxs-lookup"><span data-stu-id="a1101-243">Restricting Without Scope</span></span>

<span data-ttu-id="a1101-244">有些 PowerShell 概念類似于範圍或與範圍互動。</span><span class="sxs-lookup"><span data-stu-id="a1101-244">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="a1101-245">這些概念可能會與範圍或範圍行為混淆。</span><span class="sxs-lookup"><span data-stu-id="a1101-245">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="a1101-246">會話、模組和嵌套提示是獨立的環境，但它們不是會話中全域範圍的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-246">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="a1101-247">工作階段</span><span class="sxs-lookup"><span data-stu-id="a1101-247">Sessions</span></span>

<span data-ttu-id="a1101-248">會話是 PowerShell 執行所在的環境。</span><span class="sxs-lookup"><span data-stu-id="a1101-248">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="a1101-249">當您在遠端電腦上建立會話時，PowerShell 會建立與遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="a1101-249">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="a1101-250">持續性連接可讓您將會話用於多個相關的命令。</span><span class="sxs-lookup"><span data-stu-id="a1101-250">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="a1101-251">由於會話是內含的環境，它有自己的範圍，但會話不是建立它的會話的子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-251">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="a1101-252">會話會以自己的全域範圍開始。</span><span class="sxs-lookup"><span data-stu-id="a1101-252">The session starts with its own global scope.</span></span> <span data-ttu-id="a1101-253">此範圍與會話的全域範圍無關。</span><span class="sxs-lookup"><span data-stu-id="a1101-253">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="a1101-254">您可以在會話中建立子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-254">You can create child scopes in the session.</span></span> <span data-ttu-id="a1101-255">例如，您可以執行腳本，在會話中建立子範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-255">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="a1101-256">單元</span><span class="sxs-lookup"><span data-stu-id="a1101-256">Modules</span></span>

<span data-ttu-id="a1101-257">您可以使用 PowerShell 模組來共用和提供 PowerShell 工具。</span><span class="sxs-lookup"><span data-stu-id="a1101-257">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="a1101-258">模組是一個單位，可以包含 Cmdlet、腳本、函式、變數、別名和其他實用的專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-258">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="a1101-259">除非明確定義，否則模組中的專案無法在模組之外存取。</span><span class="sxs-lookup"><span data-stu-id="a1101-259">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="a1101-260">因此，您可以將模組新增至您的會話，並使用公用專案，而不必擔心其他專案可能會覆寫會話中的 Cmdlet、腳本、函式和其他專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-260">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="a1101-261">依預設，模組會載入目前 _會話狀態_ 的最上層，而不是目前的 _範圍_ 。</span><span class="sxs-lookup"><span data-stu-id="a1101-261">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_ .</span></span> <span data-ttu-id="a1101-262">目前的會話狀態可能是模組會話狀態或全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="a1101-262">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="a1101-263">將模組新增至會話並不會變更範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-263">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="a1101-264">如果您在全域範圍內，則會將模組載入到全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="a1101-264">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="a1101-265">任何匯出都會放到全域資料表中。</span><span class="sxs-lookup"><span data-stu-id="a1101-265">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="a1101-266">如果您從 module1 _內_ 載入 module2，module2 就會載入至 [module1] 的會話狀態，而不是全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="a1101-266">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="a1101-267">任何來自 module2 的匯出都會放置在 [module1] 會話狀態的上方。</span><span class="sxs-lookup"><span data-stu-id="a1101-267">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="a1101-268">如果您使用 `Import-Module -Scope local` ，則匯出會放入目前的範圍物件中，而不是放在最上層。</span><span class="sxs-lookup"><span data-stu-id="a1101-268">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="a1101-269">如果您是 _在模組中_ ，並使用 `Import-Module -Scope global` (或 `Import-Module -Global`) 載入另一個模組，該模組和其匯出會載入到全域會話狀態，而不是模組的本機會話狀態。</span><span class="sxs-lookup"><span data-stu-id="a1101-269">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="a1101-270">這項功能是專為撰寫操作模組的模組所設計。</span><span class="sxs-lookup"><span data-stu-id="a1101-270">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="a1101-271">**WindowsCompatibility** 模組會執行此工作，以將 proxy 模組匯入到全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="a1101-271">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="a1101-272">在會話狀態中，模組會有自己的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-272">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="a1101-273">請考慮下列模組 `C:\temp\mod1.psm1` ：</span><span class="sxs-lookup"><span data-stu-id="a1101-273">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="a1101-274">現在，我們要建立一個全域變數 `$a` ，為它指定值，然後呼叫函數 **foo** 。</span><span class="sxs-lookup"><span data-stu-id="a1101-274">Now we create a global variable `$a`, give it a value and call the function **foo** .</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="a1101-275">模組會宣告 `$a` 模組範圍中的變數，然後函式 **foo** 會輸出這兩個範圍中的變數值。</span><span class="sxs-lookup"><span data-stu-id="a1101-275">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="a1101-276">嵌套提示</span><span class="sxs-lookup"><span data-stu-id="a1101-276">Nested Prompts</span></span>

<span data-ttu-id="a1101-277">嵌套提示沒有自己的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-277">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="a1101-278">當您輸入嵌套提示字元時，嵌套提示字元是環境的子集。</span><span class="sxs-lookup"><span data-stu-id="a1101-278">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="a1101-279">但是，您仍然在本機範圍內。</span><span class="sxs-lookup"><span data-stu-id="a1101-279">But, you remain within the local scope.</span></span>

<span data-ttu-id="a1101-280">腳本有自己的範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-280">Scripts do have their own scope.</span></span> <span data-ttu-id="a1101-281">如果您要對腳本進行調試，而您到達腳本中的中斷點，請輸入腳本範圍。</span><span class="sxs-lookup"><span data-stu-id="a1101-281">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="a1101-282">私用選項</span><span class="sxs-lookup"><span data-stu-id="a1101-282">Private Option</span></span>

<span data-ttu-id="a1101-283">別名和變數具有可採用 **私** 用值的 **選項** 屬性。</span><span class="sxs-lookup"><span data-stu-id="a1101-283">Aliases and variables have an **Option** property that can take a value of **Private** .</span></span> <span data-ttu-id="a1101-284">具有 **私** 用選項的專案可以在建立這些專案的範圍內加以查看和變更，但無法在該範圍之外查看或變更。</span><span class="sxs-lookup"><span data-stu-id="a1101-284">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="a1101-285">例如，如果您在全域範圍中建立具有私用選項的變數，然後執行腳本， `Get-Variable` 則腳本中的命令不會顯示私用變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-285">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="a1101-286">在這個實例中使用全域範圍修飾詞，並不會顯示私用變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-286">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="a1101-287">您可以使用 `New-Variable` 、、和 Cmdlet 的 option 參數， `Set-Variable` `New-Alias` `Set-Alias` 將 option 屬性的值設定為 Private。</span><span class="sxs-lookup"><span data-stu-id="a1101-287">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="a1101-288">可見度</span><span class="sxs-lookup"><span data-stu-id="a1101-288">Visibility</span></span>

<span data-ttu-id="a1101-289">變數或別名的 **可見度** 屬性會決定您是否可以在建立容器的容器之外查看該專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-289">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="a1101-290">容器可以是模組、腳本或嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="a1101-290">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="a1101-291">可見度是針對容器所設計，其方式與 **選項** 屬性的 **私** 用值是針對範圍所設計。</span><span class="sxs-lookup"><span data-stu-id="a1101-291">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="a1101-292">**可見度** 屬性會採用 **公用** 和 **私** 用值。</span><span class="sxs-lookup"><span data-stu-id="a1101-292">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="a1101-293">只有在建立私人可見度的容器中，才能查看並變更這些專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-293">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="a1101-294">如果新增或匯入容器，則無法查看或變更具有私人可見度的專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-294">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="a1101-295">由於可見度是針對容器而設計，因此在範圍內的運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="a1101-295">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="a1101-296">如果您在全域範圍中建立具有私用可見度的專案，就無法在任何範圍中查看或變更專案。</span><span class="sxs-lookup"><span data-stu-id="a1101-296">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="a1101-297">如果您嘗試查看或變更具有私用可見度之變數的值，則 PowerShell 會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a1101-297">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="a1101-298">您可以使用 `New-Variable` 和 `Set-Variable` Cmdlet 來建立具有私用可見度的變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-298">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="a1101-299">範例</span><span class="sxs-lookup"><span data-stu-id="a1101-299">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="a1101-300">範例1：只變更腳本中的變數值</span><span class="sxs-lookup"><span data-stu-id="a1101-300">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="a1101-301">下列命令會變更 `$ConfirmPreference` 腳本中的變數值。</span><span class="sxs-lookup"><span data-stu-id="a1101-301">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="a1101-302">此變更不會影響全域領域。</span><span class="sxs-lookup"><span data-stu-id="a1101-302">The change does not affect the global scope.</span></span>

<span data-ttu-id="a1101-303">首先，若要顯示 `$ConfirmPreference` 區域範圍中的變數值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a1101-303">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="a1101-304">建立包含下列命令的 Scope.ps1 腳本：</span><span class="sxs-lookup"><span data-stu-id="a1101-304">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="a1101-305">執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="a1101-305">Run the script.</span></span> <span data-ttu-id="a1101-306">腳本會變更變數的值 `$ConfirmPreference` ，然後報告其在腳本範圍中的值。</span><span class="sxs-lookup"><span data-stu-id="a1101-306">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="a1101-307">輸出應類似下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a1101-307">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="a1101-308">接下來，測試 `$ConfirmPreference` 目前範圍中變數的目前值。</span><span class="sxs-lookup"><span data-stu-id="a1101-308">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="a1101-309">此範例顯示腳本範圍中變數值的變更，不會影響父範圍中的變數值。</span><span class="sxs-lookup"><span data-stu-id="a1101-309">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="a1101-310">範例2：在不同範圍中查看變數值</span><span class="sxs-lookup"><span data-stu-id="a1101-310">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="a1101-311">您可以使用範圍修飾符來查看區域範圍和父範圍中的變數值。</span><span class="sxs-lookup"><span data-stu-id="a1101-311">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="a1101-312">首先， `$test` 在全域範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-312">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="a1101-313">接著，建立定義變數的 Sample.ps1 腳本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-313">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="a1101-314">在腳本中，使用範圍修飾符來參考變數的全域或本機版本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-314">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="a1101-315">在 Sample.ps1：</span><span class="sxs-lookup"><span data-stu-id="a1101-315">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="a1101-316">當您執行 Sample.ps1 時，輸出應該會與下列輸出類似：</span><span class="sxs-lookup"><span data-stu-id="a1101-316">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="a1101-317">當腳本完成時，只 `$test` 會在會話中定義的全域值。</span><span class="sxs-lookup"><span data-stu-id="a1101-317">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="a1101-318">範例3：變更父範圍中的變數值</span><span class="sxs-lookup"><span data-stu-id="a1101-318">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="a1101-319">除非您使用私用選項或另一個方法來保護專案，否則您可以在父範圍中查看和變更變數的值。</span><span class="sxs-lookup"><span data-stu-id="a1101-319">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="a1101-320">首先， `$test` 在全域範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-320">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="a1101-321">接著，建立定義變數的 Sample.ps1 腳本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-321">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="a1101-322">在腳本中，使用範圍修飾符來參考變數的全域或本機版本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-322">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="a1101-323">在 Sample.ps1：</span><span class="sxs-lookup"><span data-stu-id="a1101-323">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="a1101-324">當腳本完成時，的全域值 `$test` 會變更。</span><span class="sxs-lookup"><span data-stu-id="a1101-324">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="a1101-325">範例4：建立私用變數</span><span class="sxs-lookup"><span data-stu-id="a1101-325">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="a1101-326">私用變數是具有 **Option** 屬性的變數，其值為 *private* 。</span><span class="sxs-lookup"><span data-stu-id="a1101-326">A private variable is a variable that has an **Option** property that has a value of *Private* .</span></span> <span data-ttu-id="a1101-327">*私* 用變數會由子範圍繼承，但是只能在建立這些變數的範圍內加以查看或變更。</span><span class="sxs-lookup"><span data-stu-id="a1101-327">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="a1101-328">下列命令會建立 `$ptest` 在區域範圍中呼叫的私用變數。</span><span class="sxs-lookup"><span data-stu-id="a1101-328">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="a1101-329">您可以 `$ptest` 在區域範圍中顯示和變更的值。</span><span class="sxs-lookup"><span data-stu-id="a1101-329">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="a1101-330">接著，建立包含下列命令的 Sample.ps1 腳本。</span><span class="sxs-lookup"><span data-stu-id="a1101-330">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="a1101-331">此命令會嘗試顯示和變更的值 `$ptest` 。</span><span class="sxs-lookup"><span data-stu-id="a1101-331">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="a1101-332">在 Sample.ps1：</span><span class="sxs-lookup"><span data-stu-id="a1101-332">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="a1101-333">`$ptest`變數在腳本範圍中看不到，輸出是空的。</span><span class="sxs-lookup"><span data-stu-id="a1101-333">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="a1101-334">範例5：在遠端命令中使用本機變數</span><span class="sxs-lookup"><span data-stu-id="a1101-334">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="a1101-335">針對在本機會話中建立之遠端命令中的變數，請使用 `Using` 範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="a1101-335">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="a1101-336">PowerShell 假設遠端命令中的變數是在遠端會話中建立的。</span><span class="sxs-lookup"><span data-stu-id="a1101-336">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="a1101-337">語法為：</span><span class="sxs-lookup"><span data-stu-id="a1101-337">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="a1101-338">例如，下列命令會 `$Cred` 在本機會話中建立變數，然後 `$Cred` 在遠端命令中使用該變數：</span><span class="sxs-lookup"><span data-stu-id="a1101-338">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="a1101-339">使用範圍是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a1101-339">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="a1101-340">在 PowerShell 2.0 中，若要指示在本機會話中建立的變數，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="a1101-340">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="a1101-341">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1101-341">See also</span></span>

[<span data-ttu-id="a1101-342">about_Variables</span><span class="sxs-lookup"><span data-stu-id="a1101-342">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="a1101-343">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="a1101-343">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="a1101-344">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a1101-344">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="a1101-345">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="a1101-345">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="a1101-346">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="a1101-346">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)
