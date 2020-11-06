---
description: 說明 PowerShell 中的範圍概念，並示範如何設定和變更元素的範圍。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 33a849d9dcd2c8f6d02f771630b718f0978b2ada
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354553"
---
# <a name="about-scopes"></a><span data-ttu-id="1b88c-104">關於範圍</span><span class="sxs-lookup"><span data-stu-id="1b88c-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="1b88c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="1b88c-105">Short description</span></span>
<span data-ttu-id="1b88c-106">說明 PowerShell 中的範圍概念，並示範如何設定和變更元素的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="1b88c-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="1b88c-107">Long description</span></span>

<span data-ttu-id="1b88c-108">PowerShell 會限制對變數、別名、函式和 PowerShell 磁片磁碟機的存取， (Psdrive) ，方法是限制可讀取和變更的位置。</span><span class="sxs-lookup"><span data-stu-id="1b88c-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="1b88c-109">PowerShell 會使用範圍規則，以確保您不會不慎變更不應該變更的專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="1b88c-110">以下是範圍的基本規則：</span><span class="sxs-lookup"><span data-stu-id="1b88c-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="1b88c-111">範圍可能會被嵌套。</span><span class="sxs-lookup"><span data-stu-id="1b88c-111">Scopes may nest.</span></span> <span data-ttu-id="1b88c-112">外部範圍稱為父範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="1b88c-113">任何嵌套的範圍都是該父系的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="1b88c-114">除非您明確地將專案設為私用，否則專案會在其建立所在的範圍和任何子範圍中顯示。</span><span class="sxs-lookup"><span data-stu-id="1b88c-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="1b88c-115">您可以在一或多個範圍中放置變數、別名、函式或 PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1b88c-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="1b88c-116">除非您明確指定不同的範圍，否則您在範圍內建立的專案只能在建立它的範圍內變更。</span><span class="sxs-lookup"><span data-stu-id="1b88c-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="1b88c-117">如果您在範圍中建立專案，且該專案與不同範圍中的專案共用其名稱，則原始專案可能會隱藏在新的專案下，但不會覆寫或變更。</span><span class="sxs-lookup"><span data-stu-id="1b88c-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="1b88c-118">PowerShell 範圍</span><span class="sxs-lookup"><span data-stu-id="1b88c-118">PowerShell Scopes</span></span>

<span data-ttu-id="1b88c-119">PowerShell 支援下列範圍：</span><span class="sxs-lookup"><span data-stu-id="1b88c-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="1b88c-120">全域：當 PowerShell 啟動時，或當您建立新的會話或執行時間時生效的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-120">Global: The scope that is in effect when PowerShell starts or when you create a new session or runspace.</span></span> <span data-ttu-id="1b88c-121">在全域範圍中建立 PowerShell 啟動時所出現的變數和函式，例如自動變數和喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="1b88c-122">您 PowerShell 設定檔中的變數、別名和函式也會在全域範圍中建立。</span><span class="sxs-lookup"><span data-stu-id="1b88c-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span> <span data-ttu-id="1b88c-123">全域範圍是會話中的根父範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-123">The global scope is the root parent scope in a session.</span></span>

- <span data-ttu-id="1b88c-124">Local：目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-124">Local: The current scope.</span></span> <span data-ttu-id="1b88c-125">區域範圍可以是全域範圍或任何其他範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-125">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="1b88c-126">腳本：指令檔執行時所建立的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-126">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="1b88c-127">只有腳本中的命令會在腳本範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="1b88c-127">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="1b88c-128">針對腳本中的命令，腳本範圍是區域範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-128">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="1b88c-129">**私** 用不是範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-129">**Private** is not a scope.</span></span> <span data-ttu-id="1b88c-130">它是一種 [選項](#private-option) ，可變更專案定義範圍之外的專案可見度。</span><span class="sxs-lookup"><span data-stu-id="1b88c-130">It is an [option](#private-option) that changes the visibility of an item outside of the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="1b88c-131">父系和子範圍</span><span class="sxs-lookup"><span data-stu-id="1b88c-131">Parent and Child Scopes</span></span>

<span data-ttu-id="1b88c-132">您可以藉由呼叫腳本或函式來建立新的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-132">You can create a new child scope by calling a script or function.</span></span> <span data-ttu-id="1b88c-133">呼叫範圍是父範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-133">The calling scope is the parent scope.</span></span> <span data-ttu-id="1b88c-134">呼叫的腳本或函數是子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-134">The called script or function is the child scope.</span></span>
<span data-ttu-id="1b88c-135">您呼叫的函式或腳本可能會呼叫其他函式，建立根範圍是全域範圍的子範圍階層。</span><span class="sxs-lookup"><span data-stu-id="1b88c-135">The functions or scripts you call may call other functions, creating a hierarchy of child scopes whose root scope is the global scope.</span></span>

<span data-ttu-id="1b88c-136">除非您明確地將專案設為私用，否則父範圍中的專案可供子範圍使用。</span><span class="sxs-lookup"><span data-stu-id="1b88c-136">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="1b88c-137">不過，除非您在建立專案時明確指定範圍，否則您在子範圍中建立和變更的專案不會影響父範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-137">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

> [!NOTE]
> <span data-ttu-id="1b88c-138">模組中的函式不會在呼叫範圍的子範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="1b88c-138">Functions from a module do not run in a child scope of the calling scope.</span></span>
> <span data-ttu-id="1b88c-139">模組會有自己的會話狀態，並連結至全域範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-139">Modules have their own session state that is linked to the global scope.</span></span>
> <span data-ttu-id="1b88c-140">所有模組程式碼會在具有自己的根範圍之範圍的模組特定階層中執行。</span><span class="sxs-lookup"><span data-stu-id="1b88c-140">All module code runs in a module-specific hierarchy of scopes that has its own root scope.</span></span>

## <a name="inheritance"></a><span data-ttu-id="1b88c-141">繼承</span><span class="sxs-lookup"><span data-stu-id="1b88c-141">Inheritance</span></span>

<span data-ttu-id="1b88c-142">子範圍不會繼承父範圍中的變數、別名和函式。</span><span class="sxs-lookup"><span data-stu-id="1b88c-142">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="1b88c-143">除非專案是私用的，否則子範圍可以查看父範圍中的專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-143">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="1b88c-144">而且，它可以藉由明確指定父範圍來變更專案，但是這些專案不是子範圍的一部分。</span><span class="sxs-lookup"><span data-stu-id="1b88c-144">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="1b88c-145">不過，會使用一組專案來建立子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-145">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="1b88c-146">通常，它會包含具有 **AllScope** 選項的所有別名。</span><span class="sxs-lookup"><span data-stu-id="1b88c-146">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="1b88c-147">本文稍後會討論這個選項。</span><span class="sxs-lookup"><span data-stu-id="1b88c-147">This option is discussed later in this article.</span></span> <span data-ttu-id="1b88c-148">它包含具有 **AllScope** 選項的所有變數，加上一些自動變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-148">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="1b88c-149">若要尋找特定範圍中的專案，請使用或的範圍 `Get-Variable` 參數 `Get-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-149">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="1b88c-150">例如，若要取得區域範圍中的所有變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="1b88c-150">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="1b88c-151">若要取得全域範圍中的所有變數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="1b88c-151">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="1b88c-152">範圍修飾符</span><span class="sxs-lookup"><span data-stu-id="1b88c-152">Scope Modifiers</span></span>

<span data-ttu-id="1b88c-153">變數、別名或函式名稱可以包含下列任何一個選擇性範圍修飾詞：</span><span class="sxs-lookup"><span data-stu-id="1b88c-153">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="1b88c-154">`global:` -指定名稱存在於 **全域** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="1b88c-154">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="1b88c-155">`local:` -指定名稱存在於 **區域** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="1b88c-155">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="1b88c-156">目前的範圍一律是 **區域** 範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-156">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="1b88c-157">`private:` -指定名稱是 **私** 用的，而且只有目前的範圍可見。</span><span class="sxs-lookup"><span data-stu-id="1b88c-157">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="1b88c-158">`script:` -指定名稱存在於 **腳本** 範圍中。</span><span class="sxs-lookup"><span data-stu-id="1b88c-158">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="1b88c-159">如果沒有最接近的上階腳本檔案， **腳本** 範圍就是最接近的上階腳本檔案範圍或 **全域** 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-159">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="1b88c-160">`using:` -用來存取在另一個範圍中定義的變數，並透過如和的 Cmdlet 執行腳本 `Start-Job` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-160">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="1b88c-161">`workflow:` -指定名稱存在於工作流程中。</span><span class="sxs-lookup"><span data-stu-id="1b88c-161">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="1b88c-162">注意： PowerShell Core 中不支援工作流程。</span><span class="sxs-lookup"><span data-stu-id="1b88c-162">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="1b88c-163">`<variable-namespace>` -PowerShell New-psdrive 提供者所建立的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="1b88c-163">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="1b88c-164">例如︰</span><span class="sxs-lookup"><span data-stu-id="1b88c-164">For example:</span></span>

  |  <span data-ttu-id="1b88c-165">命名空間</span><span class="sxs-lookup"><span data-stu-id="1b88c-165">Namespace</span></span>  |                    <span data-ttu-id="1b88c-166">描述</span><span class="sxs-lookup"><span data-stu-id="1b88c-166">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="1b88c-167">目前範圍中定義的別名</span><span class="sxs-lookup"><span data-stu-id="1b88c-167">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="1b88c-168">目前範圍中定義的環境變數</span><span class="sxs-lookup"><span data-stu-id="1b88c-168">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="1b88c-169">目前範圍中定義的函數</span><span class="sxs-lookup"><span data-stu-id="1b88c-169">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="1b88c-170">目前範圍中定義的變數</span><span class="sxs-lookup"><span data-stu-id="1b88c-170">Variables defined in the current scope</span></span>             |

<span data-ttu-id="1b88c-171">腳本的預設範圍是腳本範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-171">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="1b88c-172">函數和別名的預設範圍是區域範圍，即使它們是在腳本中定義也一樣。</span><span class="sxs-lookup"><span data-stu-id="1b88c-172">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="1b88c-173">使用範圍修飾符</span><span class="sxs-lookup"><span data-stu-id="1b88c-173">Using scope modifiers</span></span>

<span data-ttu-id="1b88c-174">若要指定新變數、別名或函數的範圍，請使用範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="1b88c-174">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="1b88c-175">變數中範圍修飾詞的語法為：</span><span class="sxs-lookup"><span data-stu-id="1b88c-175">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="1b88c-176">函數中的範圍修飾詞語法為：</span><span class="sxs-lookup"><span data-stu-id="1b88c-176">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="1b88c-177">下列不使用範圍修飾符的命令會在目前或 **區域** 範圍中建立變數：</span><span class="sxs-lookup"><span data-stu-id="1b88c-177">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="1b88c-178">若要在 **全域** 範圍中建立相同的變數，請使用範圍 `global:` 修飾符：</span><span class="sxs-lookup"><span data-stu-id="1b88c-178">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="1b88c-179">若要在 **腳本** 範圍中建立相同的變數，請使用 `script:` 範圍修飾符：</span><span class="sxs-lookup"><span data-stu-id="1b88c-179">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="1b88c-180">您也可以搭配函數使用範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="1b88c-180">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="1b88c-181">下列函式定義會在 **全域** 範圍中建立函數：</span><span class="sxs-lookup"><span data-stu-id="1b88c-181">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="1b88c-182">您也可以使用範圍修飾符來參考不同範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-182">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="1b88c-183">下列命令會參考 `$test` 變數，先在本機範圍，然後在全域範圍內：</span><span class="sxs-lookup"><span data-stu-id="1b88c-183">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="1b88c-184">`Using:`範圍修飾詞</span><span class="sxs-lookup"><span data-stu-id="1b88c-184">The `Using:` scope modifier</span></span>

<span data-ttu-id="1b88c-185">使用是一種特殊的範圍修飾詞，用來識別遠端命令中的本機變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-185">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="1b88c-186">如果沒有修飾詞，PowerShell 就會在遠端會話中定義遠端命令中的變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-186">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="1b88c-187">`Using`範圍修飾詞是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1b88c-187">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="1b88c-188">針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="1b88c-188">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="1b88c-189">`Using`下列內容支援範圍修飾符：</span><span class="sxs-lookup"><span data-stu-id="1b88c-189">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="1b88c-190">從遠端執行的命令，從 `Invoke-Command` 使用 **ComputerName** 、 **HostName** 、 **SSHConnection** 或 **Session** 參數開始， (遠端會話) </span><span class="sxs-lookup"><span data-stu-id="1b88c-190">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="1b88c-191">背景工作，以 `Start-Job` (跨進程會話開始) </span><span class="sxs-lookup"><span data-stu-id="1b88c-191">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="1b88c-192">執行緒作業，透過 `Start-ThreadJob` 或 `ForEach-Object -Parallel` (個別的執行緒會話啟動) </span><span class="sxs-lookup"><span data-stu-id="1b88c-192">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="1b88c-193">視內容而定，內嵌變數值是呼叫端範圍中資料的獨立複本，或是對它的參考。</span><span class="sxs-lookup"><span data-stu-id="1b88c-193">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="1b88c-194">在遠端和跨進程的會話中，它們一律是獨立的複本。</span><span class="sxs-lookup"><span data-stu-id="1b88c-194">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="1b88c-195">如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="1b88c-195">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="1b88c-196">線上程會話中，它們是以傳址方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="1b88c-196">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="1b88c-197">這表示可以修改不同執行緒中的呼叫範圍變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-197">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="1b88c-198">若要安全地修改變數，需要執行緒同步處理。</span><span class="sxs-lookup"><span data-stu-id="1b88c-198">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="1b88c-199">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="1b88c-199">For more information see:</span></span>

- [<span data-ttu-id="1b88c-200">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="1b88c-200">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)
- [<span data-ttu-id="1b88c-201">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="1b88c-201">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="1b88c-202">變數值的序列化</span><span class="sxs-lookup"><span data-stu-id="1b88c-202">Serialization of variable values</span></span>

<span data-ttu-id="1b88c-203">遠端執行的命令和背景工作會跨進程執行。</span><span class="sxs-lookup"><span data-stu-id="1b88c-203">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="1b88c-204">跨進程會話使用以 XML 為基礎的序列化和還原序列化，讓變數的值可以跨進程界限使用。</span><span class="sxs-lookup"><span data-stu-id="1b88c-204">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="1b88c-205">序列化程式會將物件轉換為包含原始物件屬性但不包含其方法的 **PSObject** 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-205">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="1b88c-206">針對一組有限的類型，還原序列化會將解除凍結物件回原始型別。</span><span class="sxs-lookup"><span data-stu-id="1b88c-206">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="1b88c-207">解除凍結物件是原始物件實例的複本。</span><span class="sxs-lookup"><span data-stu-id="1b88c-207">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="1b88c-208">它具有類型屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="1b88c-208">It has the type properties and methods.</span></span> <span data-ttu-id="1b88c-209">針對簡單類型（例如 **system.object** ），複本是精確的。</span><span class="sxs-lookup"><span data-stu-id="1b88c-209">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="1b88c-210">如果是複雜類型，則會完美複製。</span><span class="sxs-lookup"><span data-stu-id="1b88c-210">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="1b88c-211">例如，解除凍結憑證物件不包含私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1b88c-211">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="1b88c-212">所有其他類型的實例都是 **PSObject** 實例。</span><span class="sxs-lookup"><span data-stu-id="1b88c-212">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="1b88c-213">**PSTypeNames** 屬性包含 **前面加上** 還原序列化的原始型別名稱，例如 **Deserialized.System。Data DataTable**</span><span class="sxs-lookup"><span data-stu-id="1b88c-213">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="1b88c-214">AllScope 選項</span><span class="sxs-lookup"><span data-stu-id="1b88c-214">The AllScope Option</span></span>

<span data-ttu-id="1b88c-215">變數和別名具有可採用 **AllScope** 值的 **選項** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b88c-215">Variables and aliases have an **Option** property that can take a value of **AllScope**.</span></span> <span data-ttu-id="1b88c-216">具有 **AllScope** 屬性的專案會成為您所建立之任何子範圍的一部分，不過父範圍不會追溯這些專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-216">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="1b88c-217">具有 **AllScope** 屬性的專案會顯示在子範圍中，而且屬於該範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-217">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="1b88c-218">對任何範圍中的專案所做的變更，都會影響定義變數的所有範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-218">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="1b88c-219">管理領域</span><span class="sxs-lookup"><span data-stu-id="1b88c-219">Managing Scope</span></span>

<span data-ttu-id="1b88c-220">有數個 Cmdlet 具有 **範圍** 參數，可讓您取得或設定 (建立和變更特定範圍中) 專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-220">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="1b88c-221">使用下列命令，在您的會話中尋找具有 **範圍** 參數的所有 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="1b88c-221">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="1b88c-222">若要尋找在特定範圍中可見的變數，請使用的 `Scope` 參數 `Get-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-222">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="1b88c-223">可見的變數包括全域變數、父範圍中的變數，以及目前範圍中的變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-223">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="1b88c-224">例如，下列命令會取得在區域範圍中可見的變數：</span><span class="sxs-lookup"><span data-stu-id="1b88c-224">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="1b88c-225">若要在特定範圍內建立變數，請使用範圍修飾符或的 **範圍** 參數 `Set-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-225">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="1b88c-226">下列命令會在全域範圍中建立變數：</span><span class="sxs-lookup"><span data-stu-id="1b88c-226">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="1b88c-227">您也可以使用 `New-Alias` 、或 Cmdlet 的 scope 參數 `Set-Alias` `Get-Alias` 來指定範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-227">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="1b88c-228">下列命令會在全域範圍中建立別名：</span><span class="sxs-lookup"><span data-stu-id="1b88c-228">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="1b88c-229">若要取得特定範圍中的函式，請在範圍內使用 `Get-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1b88c-229">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="1b88c-230">`Get-Item`Cmdlet 沒有 **範圍** 參數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-230">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="1b88c-231">針對使用 **範圍** 參數的 Cmdlet，您也可以依編號參考範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-231">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="1b88c-232">此數位會描述某範圍與另一個範圍之間的相對位置。</span><span class="sxs-lookup"><span data-stu-id="1b88c-232">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="1b88c-233">範圍0代表目前或區域範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-233">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="1b88c-234">範圍1表示直屬父範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-234">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="1b88c-235">範圍2表示父範圍的父系，依此類推。</span><span class="sxs-lookup"><span data-stu-id="1b88c-235">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="1b88c-236">如果您已建立許多遞迴範圍，則編號的範圍會很有用。</span><span class="sxs-lookup"><span data-stu-id="1b88c-236">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="1b88c-237">使用點來源標記法搭配範圍</span><span class="sxs-lookup"><span data-stu-id="1b88c-237">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="1b88c-238">腳本和函式會遵循範圍的所有規則。</span><span class="sxs-lookup"><span data-stu-id="1b88c-238">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="1b88c-239">您可以在特定範圍中建立它們，除非您使用 Cmdlet 參數或範圍修飾符來變更該範圍，否則它們只會影響該範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-239">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="1b88c-240">但是，您可以使用點來源標記法，將腳本或函式新增至目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-240">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="1b88c-241">然後，當腳本在目前的範圍中執行時，腳本所建立的任何函式、別名和變數都會出現在目前的範圍中。</span><span class="sxs-lookup"><span data-stu-id="1b88c-241">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="1b88c-242">若要將函式新增至目前的範圍，請在函式呼叫中輸入點 (. ) 和函式名稱之前的空格。</span><span class="sxs-lookup"><span data-stu-id="1b88c-242">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="1b88c-243">例如，若要從腳本範圍中的 C：\Scripts 目錄執行 Sample.ps1 腳本 (腳本) 的預設值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="1b88c-243">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="1b88c-244">若要在本機範圍中執行 Sample.ps1 腳本，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="1b88c-244">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="1b88c-245">當您使用呼叫運算子 ( # A0) 來執行函式或腳本時，不會將它新增至目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-245">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="1b88c-246">下列範例會使用呼叫運算子：</span><span class="sxs-lookup"><span data-stu-id="1b88c-246">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="1b88c-247">您可以在 [about_operators](about_operators.md)中閱讀呼叫運算子的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1b88c-247">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="1b88c-248">在目前的範圍中，無法使用 Sample.ps1 腳本所建立的任何別名、函數或變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-248">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="1b88c-249">不含範圍的限制</span><span class="sxs-lookup"><span data-stu-id="1b88c-249">Restricting Without Scope</span></span>

<span data-ttu-id="1b88c-250">有些 PowerShell 概念類似于範圍或與範圍互動。</span><span class="sxs-lookup"><span data-stu-id="1b88c-250">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="1b88c-251">這些概念可能會與範圍或範圍行為混淆。</span><span class="sxs-lookup"><span data-stu-id="1b88c-251">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="1b88c-252">會話、模組和嵌套提示是獨立的環境，但它們不是會話中全域範圍的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-252">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="1b88c-253">工作階段</span><span class="sxs-lookup"><span data-stu-id="1b88c-253">Sessions</span></span>

<span data-ttu-id="1b88c-254">會話是 PowerShell 執行所在的環境。</span><span class="sxs-lookup"><span data-stu-id="1b88c-254">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="1b88c-255">當您在遠端電腦上建立會話時，PowerShell 會建立與遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="1b88c-255">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="1b88c-256">持續性連接可讓您將會話用於多個相關的命令。</span><span class="sxs-lookup"><span data-stu-id="1b88c-256">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="1b88c-257">由於會話是內含的環境，它有自己的範圍，但會話不是建立它的會話的子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-257">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="1b88c-258">會話會以自己的全域範圍開始。</span><span class="sxs-lookup"><span data-stu-id="1b88c-258">The session starts with its own global scope.</span></span> <span data-ttu-id="1b88c-259">此範圍與會話的全域範圍無關。</span><span class="sxs-lookup"><span data-stu-id="1b88c-259">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="1b88c-260">您可以在會話中建立子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-260">You can create child scopes in the session.</span></span> <span data-ttu-id="1b88c-261">例如，您可以執行腳本，在會話中建立子範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-261">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="1b88c-262">單元</span><span class="sxs-lookup"><span data-stu-id="1b88c-262">Modules</span></span>

<span data-ttu-id="1b88c-263">您可以使用 PowerShell 模組來共用和提供 PowerShell 工具。</span><span class="sxs-lookup"><span data-stu-id="1b88c-263">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="1b88c-264">模組是一個單位，可以包含 Cmdlet、腳本、函式、變數、別名和其他實用的專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-264">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="1b88c-265">除非明確定義，否則模組中的專案無法在模組之外存取。</span><span class="sxs-lookup"><span data-stu-id="1b88c-265">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="1b88c-266">因此，您可以將模組新增至您的會話，並使用公用專案，而不必擔心其他專案可能會覆寫會話中的 Cmdlet、腳本、函式和其他專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-266">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="1b88c-267">依預設，模組會載入目前 _會話狀態_ 的最上層，而不是目前的 _範圍_ 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-267">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_.</span></span> <span data-ttu-id="1b88c-268">目前的會話狀態可能是模組會話狀態或全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1b88c-268">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="1b88c-269">將模組新增至會話並不會變更範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-269">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="1b88c-270">如果您在全域範圍內，則會將模組載入到全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1b88c-270">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="1b88c-271">任何匯出都會放到全域資料表中。</span><span class="sxs-lookup"><span data-stu-id="1b88c-271">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="1b88c-272">如果您從 module1 _內_ 載入 module2，module2 就會載入至 [module1] 的會話狀態，而不是全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1b88c-272">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="1b88c-273">任何來自 module2 的匯出都會放置在 [module1] 會話狀態的上方。</span><span class="sxs-lookup"><span data-stu-id="1b88c-273">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="1b88c-274">如果您使用 `Import-Module -Scope local` ，則匯出會放入目前的範圍物件中，而不是放在最上層。</span><span class="sxs-lookup"><span data-stu-id="1b88c-274">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="1b88c-275">如果您是 _在模組中_ ，並使用 `Import-Module -Scope global` (或 `Import-Module -Global`) 載入另一個模組，該模組和其匯出會載入到全域會話狀態，而不是模組的本機會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1b88c-275">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="1b88c-276">這項功能是專為撰寫操作模組的模組所設計。</span><span class="sxs-lookup"><span data-stu-id="1b88c-276">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="1b88c-277">**WindowsCompatibility** 模組會執行此工作，以將 proxy 模組匯入到全域會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1b88c-277">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="1b88c-278">在會話狀態中，模組會有自己的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-278">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="1b88c-279">請考慮下列模組 `C:\temp\mod1.psm1` ：</span><span class="sxs-lookup"><span data-stu-id="1b88c-279">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="1b88c-280">現在，我們要建立一個全域變數 `$a` ，為它指定值，然後呼叫函數 **foo** 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-280">Now we create a global variable `$a`, give it a value and call the function **foo**.</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="1b88c-281">模組會宣告 `$a` 模組範圍中的變數，然後函式 **foo** 會輸出這兩個範圍中的變數值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-281">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="1b88c-282">嵌套提示</span><span class="sxs-lookup"><span data-stu-id="1b88c-282">Nested Prompts</span></span>

<span data-ttu-id="1b88c-283">嵌套提示沒有自己的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-283">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="1b88c-284">當您輸入嵌套提示字元時，嵌套提示字元是環境的子集。</span><span class="sxs-lookup"><span data-stu-id="1b88c-284">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="1b88c-285">但是，您仍然在本機範圍內。</span><span class="sxs-lookup"><span data-stu-id="1b88c-285">But, you remain within the local scope.</span></span>

<span data-ttu-id="1b88c-286">腳本有自己的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-286">Scripts do have their own scope.</span></span> <span data-ttu-id="1b88c-287">如果您要對腳本進行調試，而您到達腳本中的中斷點，請輸入腳本範圍。</span><span class="sxs-lookup"><span data-stu-id="1b88c-287">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="1b88c-288">私用選項</span><span class="sxs-lookup"><span data-stu-id="1b88c-288">Private Option</span></span>

<span data-ttu-id="1b88c-289">別名和變數具有可採用 **私** 用值的 **選項** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1b88c-289">Aliases and variables have an **Option** property that can take a value of **Private**.</span></span> <span data-ttu-id="1b88c-290">具有 **私** 用選項的專案可以在建立這些專案的範圍內加以查看和變更，但無法在該範圍之外查看或變更。</span><span class="sxs-lookup"><span data-stu-id="1b88c-290">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="1b88c-291">例如，如果您在全域範圍中建立具有私用選項的變數，然後執行腳本， `Get-Variable` 則腳本中的命令不會顯示私用變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-291">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="1b88c-292">在這個實例中使用全域範圍修飾詞，並不會顯示私用變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-292">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="1b88c-293">您可以使用 `New-Variable` 、、和 Cmdlet 的 option 參數， `Set-Variable` `New-Alias` `Set-Alias` 將 option 屬性的值設定為 Private。</span><span class="sxs-lookup"><span data-stu-id="1b88c-293">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="1b88c-294">可見度</span><span class="sxs-lookup"><span data-stu-id="1b88c-294">Visibility</span></span>

<span data-ttu-id="1b88c-295">變數或別名的 **可見度** 屬性會決定您是否可以在建立容器的容器之外查看該專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-295">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="1b88c-296">容器可以是模組、腳本或嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="1b88c-296">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="1b88c-297">可見度是針對容器所設計，其方式與 **選項** 屬性的 **私** 用值是針對範圍所設計。</span><span class="sxs-lookup"><span data-stu-id="1b88c-297">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="1b88c-298">**可見度** 屬性會採用 **公用** 和 **私** 用值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-298">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="1b88c-299">只有在建立私人可見度的容器中，才能查看並變更這些專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-299">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="1b88c-300">如果新增或匯入容器，則無法查看或變更具有私人可見度的專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-300">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="1b88c-301">由於可見度是針對容器而設計，因此在範圍內的運作方式不同。</span><span class="sxs-lookup"><span data-stu-id="1b88c-301">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="1b88c-302">如果您在全域範圍中建立具有私用可見度的專案，就無法在任何範圍中查看或變更專案。</span><span class="sxs-lookup"><span data-stu-id="1b88c-302">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="1b88c-303">如果您嘗試查看或變更具有私用可見度之變數的值，則 PowerShell 會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="1b88c-303">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="1b88c-304">您可以使用 `New-Variable` 和 `Set-Variable` Cmdlet 來建立具有私用可見度的變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-304">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="1b88c-305">範例</span><span class="sxs-lookup"><span data-stu-id="1b88c-305">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="1b88c-306">範例1：只變更腳本中的變數值</span><span class="sxs-lookup"><span data-stu-id="1b88c-306">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="1b88c-307">下列命令會變更 `$ConfirmPreference` 腳本中的變數值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-307">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="1b88c-308">此變更不會影響全域領域。</span><span class="sxs-lookup"><span data-stu-id="1b88c-308">The change does not affect the global scope.</span></span>

<span data-ttu-id="1b88c-309">首先，若要顯示 `$ConfirmPreference` 區域範圍中的變數值，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="1b88c-309">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="1b88c-310">建立包含下列命令的 Scope.ps1 腳本：</span><span class="sxs-lookup"><span data-stu-id="1b88c-310">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="1b88c-311">執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1b88c-311">Run the script.</span></span> <span data-ttu-id="1b88c-312">腳本會變更變數的值 `$ConfirmPreference` ，然後報告其在腳本範圍中的值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-312">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="1b88c-313">輸出應類似下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1b88c-313">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="1b88c-314">接下來，測試 `$ConfirmPreference` 目前範圍中變數的目前值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-314">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="1b88c-315">此範例顯示腳本範圍中變數值的變更，不會影響父範圍中的變數值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-315">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="1b88c-316">範例2：在不同範圍中查看變數值</span><span class="sxs-lookup"><span data-stu-id="1b88c-316">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="1b88c-317">您可以使用範圍修飾符來查看區域範圍和父範圍中的變數值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-317">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="1b88c-318">首先， `$test` 在全域範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-318">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="1b88c-319">接著，建立定義變數的 Sample.ps1 腳本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-319">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="1b88c-320">在腳本中，使用範圍修飾符來參考變數的全域或本機版本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-320">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="1b88c-321">在 Sample.ps1：</span><span class="sxs-lookup"><span data-stu-id="1b88c-321">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="1b88c-322">當您執行 Sample.ps1 時，輸出應該會與下列輸出類似：</span><span class="sxs-lookup"><span data-stu-id="1b88c-322">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="1b88c-323">當腳本完成時，只 `$test` 會在會話中定義的全域值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-323">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="1b88c-324">範例3：變更父範圍中的變數值</span><span class="sxs-lookup"><span data-stu-id="1b88c-324">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="1b88c-325">除非您使用私用選項或另一個方法來保護專案，否則您可以在父範圍中查看和變更變數的值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-325">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="1b88c-326">首先， `$test` 在全域範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-326">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="1b88c-327">接著，建立定義變數的 Sample.ps1 腳本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-327">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="1b88c-328">在腳本中，使用範圍修飾符來參考變數的全域或本機版本 `$test` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-328">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="1b88c-329">在 Sample.ps1：</span><span class="sxs-lookup"><span data-stu-id="1b88c-329">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="1b88c-330">當腳本完成時，的全域值 `$test` 會變更。</span><span class="sxs-lookup"><span data-stu-id="1b88c-330">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="1b88c-331">範例4：建立私用變數</span><span class="sxs-lookup"><span data-stu-id="1b88c-331">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="1b88c-332">私用變數是具有 **Option** 屬性的變數，其值為 *private* 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-332">A private variable is a variable that has an **Option** property that has a value of *Private*.</span></span> <span data-ttu-id="1b88c-333">*私* 用變數會由子範圍繼承，但是只能在建立這些變數的範圍內加以查看或變更。</span><span class="sxs-lookup"><span data-stu-id="1b88c-333">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="1b88c-334">下列命令會建立 `$ptest` 在區域範圍中呼叫的私用變數。</span><span class="sxs-lookup"><span data-stu-id="1b88c-334">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="1b88c-335">您可以 `$ptest` 在區域範圍中顯示和變更的值。</span><span class="sxs-lookup"><span data-stu-id="1b88c-335">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="1b88c-336">接著，建立包含下列命令的 Sample.ps1 腳本。</span><span class="sxs-lookup"><span data-stu-id="1b88c-336">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="1b88c-337">此命令會嘗試顯示和變更的值 `$ptest` 。</span><span class="sxs-lookup"><span data-stu-id="1b88c-337">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="1b88c-338">在 Sample.ps1：</span><span class="sxs-lookup"><span data-stu-id="1b88c-338">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="1b88c-339">`$ptest`變數在腳本範圍中看不到，輸出是空的。</span><span class="sxs-lookup"><span data-stu-id="1b88c-339">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="1b88c-340">範例5：在遠端命令中使用本機變數</span><span class="sxs-lookup"><span data-stu-id="1b88c-340">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="1b88c-341">針對在本機會話中建立之遠端命令中的變數，請使用 `Using` 範圍修飾符。</span><span class="sxs-lookup"><span data-stu-id="1b88c-341">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="1b88c-342">PowerShell 假設遠端命令中的變數是在遠端會話中建立的。</span><span class="sxs-lookup"><span data-stu-id="1b88c-342">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="1b88c-343">語法為：</span><span class="sxs-lookup"><span data-stu-id="1b88c-343">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="1b88c-344">例如，下列命令會 `$Cred` 在本機會話中建立變數，然後 `$Cred` 在遠端命令中使用該變數：</span><span class="sxs-lookup"><span data-stu-id="1b88c-344">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="1b88c-345">使用範圍是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1b88c-345">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="1b88c-346">在 PowerShell 2.0 中，若要指示在本機會話中建立的變數，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="1b88c-346">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="1b88c-347">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b88c-347">See also</span></span>

[<span data-ttu-id="1b88c-348">about_Variables</span><span class="sxs-lookup"><span data-stu-id="1b88c-348">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="1b88c-349">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="1b88c-349">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="1b88c-350">about_Functions</span><span class="sxs-lookup"><span data-stu-id="1b88c-350">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="1b88c-351">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="1b88c-351">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="1b88c-352">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="1b88c-352">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)
