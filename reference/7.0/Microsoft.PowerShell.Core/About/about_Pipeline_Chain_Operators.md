---
description: 描述 `&&` PowerShell 中使用和運算子的連結管線 `||` 。
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,cmdlet
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 107d5eacb7b9629a42d5eef53e0c7c66a522f32e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207835"
---
# <a name="about-pipeline-chain-operators"></a><span data-ttu-id="47dec-104">關於管線鏈運算子</span><span class="sxs-lookup"><span data-stu-id="47dec-104">About Pipeline Chain Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="47dec-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="47dec-105">Short description</span></span>

<span data-ttu-id="47dec-106">描述 `&&` PowerShell 中使用和運算子的連結管線 `||` 。</span><span class="sxs-lookup"><span data-stu-id="47dec-106">Describes chaining pipelines with the `&&` and `||` operators in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="47dec-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="47dec-107">Long description</span></span>

<span data-ttu-id="47dec-108">從 PowerShell 7 開始，PowerShell 會執行 `&&` 和 `||` 運算子，以有條件地鏈出管線。</span><span class="sxs-lookup"><span data-stu-id="47dec-108">Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="47dec-109">這些運算子在 PowerShell 中已知為 *管線鏈運算子* ，類似于 POSIX shell （例如 bash、zsh 和 sh）中的 [和或清單](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) ，以及 Windows 命令介面中的 [條件式處理符號](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="47dec-109">These operators are known in PowerShell as *pipeline chain operators* , and are similar to [AND-OR lists](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX shells like bash, zsh and sh, as well as [conditional processing symbols](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in the Windows Command Shell (cmd.exe).</span></span>

<span data-ttu-id="47dec-110">如果左側管線成功，`&&` 運算子就會執行右側管線。</span><span class="sxs-lookup"><span data-stu-id="47dec-110">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="47dec-111">反過來說，如果左側管線失敗，`||` 運算子就會執行右側管線。</span><span class="sxs-lookup"><span data-stu-id="47dec-111">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

<span data-ttu-id="47dec-112">這些運算子會使用 `$?` 和 `$LASTEXITCODE` 變數來判斷管線是否失敗。</span><span class="sxs-lookup"><span data-stu-id="47dec-112">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="47dec-113">這可讓您將其與原生命令搭配使用，而不只是與 Cmdlet 或函式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="47dec-113">This allows you to use them with native commands and not just with cmdlets or functions.</span></span> <span data-ttu-id="47dec-114">例如：</span><span class="sxs-lookup"><span data-stu-id="47dec-114">For example:</span></span>

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a><span data-ttu-id="47dec-115">範例</span><span class="sxs-lookup"><span data-stu-id="47dec-115">Examples</span></span>

#### <a name="two-successful-commands"></a><span data-ttu-id="47dec-116">兩個成功的命令</span><span class="sxs-lookup"><span data-stu-id="47dec-116">Two successful commands</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a><span data-ttu-id="47dec-117">第一個命令失敗，導致第二個未執行</span><span class="sxs-lookup"><span data-stu-id="47dec-117">First command fails, causing second not to be executed</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a><span data-ttu-id="47dec-118">第一個命令成功，因此不會執行第二個命令</span><span class="sxs-lookup"><span data-stu-id="47dec-118">First command succeeds, so the second command is not executed</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a><span data-ttu-id="47dec-119">第一個命令失敗，所以會執行第二個命令</span><span class="sxs-lookup"><span data-stu-id="47dec-119">First command fails, so the second command is executed</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

<span data-ttu-id="47dec-120">管線成功是由變數的值所定義 `$?` ，而 PowerShell 會根據其執行狀態，在執行管線之後自動設定。</span><span class="sxs-lookup"><span data-stu-id="47dec-120">Pipeline success is defined by the value of the `$?` variable, which PowerShell automatically sets after executing a pipeline based on its execution status.</span></span>
<span data-ttu-id="47dec-121">這表示管線鏈運算子具有下列等價：</span><span class="sxs-lookup"><span data-stu-id="47dec-121">This means that pipeline chain operators have the following equivalence:</span></span>

```powershell
Test-Command '1' && Test-Command '2'
```

<span data-ttu-id="47dec-122">的運作方式與</span><span class="sxs-lookup"><span data-stu-id="47dec-122">works the same as</span></span>

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

<span data-ttu-id="47dec-123">及</span><span class="sxs-lookup"><span data-stu-id="47dec-123">and</span></span>

```powershell
Test-Command '1' || Test-Command '2'
```

<span data-ttu-id="47dec-124">的運作方式與</span><span class="sxs-lookup"><span data-stu-id="47dec-124">works the same as</span></span>

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a><span data-ttu-id="47dec-125">從管線鏈指派</span><span class="sxs-lookup"><span data-stu-id="47dec-125">Assignment from pipeline chains</span></span>

<span data-ttu-id="47dec-126">從管線鏈指派變數，會將鏈中的所有管線串連：</span><span class="sxs-lookup"><span data-stu-id="47dec-126">Assigning a variable from a pipeline chain takes the concatenation of all the pipelines in the chain:</span></span>

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

<span data-ttu-id="47dec-127">如果從管線鏈指派期間發生腳本終止錯誤，指派不會成功：</span><span class="sxs-lookup"><span data-stu-id="47dec-127">If a script-terminating error occurs during assignment from a pipeline chain, the assignment does not succeed:</span></span>

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a><span data-ttu-id="47dec-128">運算子語法和優先順序</span><span class="sxs-lookup"><span data-stu-id="47dec-128">Operator syntax and precedence</span></span>

<span data-ttu-id="47dec-129">不同于其他運算子， `&&` 並 `||` 操作管線，例如或之類的運算式 `+` `-and` 。</span><span class="sxs-lookup"><span data-stu-id="47dec-129">Unlike other operators, `&&` and `||` operate on pipelines, rather than on expressions like `+` or `-and`, for example.</span></span>

<span data-ttu-id="47dec-130">`&&` 與 `||` 管線 () 或重新導向 () 具有較低的優先順序 `|` `>` ，但優先順序高於作業運算子 (`&`) 、指派 (`=`) 或分號 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="47dec-130">`&&` and `||` have a lower precedence than piping (`|`) or redirection (`>`), but a higher precedence than job operators (`&`), assignment (`=`) or semicolons (`;`).</span></span> <span data-ttu-id="47dec-131">這表示管線鏈內的管線可以個別重新導向，而且整個管線鏈可以背景執行、指派給變數或分隔為語句。</span><span class="sxs-lookup"><span data-stu-id="47dec-131">This means that pipelines within a pipeline chain can be individually redirected, and that entire pipeline chains can be backgrounded, assigned to variables, or separated as statements.</span></span>

<span data-ttu-id="47dec-132">若要在管線鏈中使用較低優先順序的語法，請考慮使用括弧 `(...)` 。</span><span class="sxs-lookup"><span data-stu-id="47dec-132">To use lower precedence syntax within a pipeline chain, consider the use of parentheses `(...)`.</span></span>
<span data-ttu-id="47dec-133">同樣地，若要在管線鏈內內嵌語句， `$(...)` 可以使用子運算式。</span><span class="sxs-lookup"><span data-stu-id="47dec-133">Similarly, to embed a statement within a pipeline chain, a subexpression `$(...)` can be used.</span></span>
<span data-ttu-id="47dec-134">這有助於將原生命令與控制流程結合：</span><span class="sxs-lookup"><span data-stu-id="47dec-134">This can be useful for combining native commands with control flow:</span></span>

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

<span data-ttu-id="47dec-135">從 PowerShell 7 起，這些語法的行為已變更，因此 `$?` 當命令在括弧或子運算式內成功或失敗時，會如預期般設定。</span><span class="sxs-lookup"><span data-stu-id="47dec-135">As of PowerShell 7, the behaviour of these syntaxes has been changed so that `$?` is set as expected when a command succeeds or fails within parentheses or a subexpression.</span></span>

<span data-ttu-id="47dec-136">與 PowerShell 中的大部分其他運算子相同， `&&` 而且 `||` 也是 *左關聯* 的，這表示它們是從左方群組。</span><span class="sxs-lookup"><span data-stu-id="47dec-136">Like most other operators in PowerShell, `&&` and `||` are also *left-associative* , meaning they group from the left.</span></span> <span data-ttu-id="47dec-137">例如：</span><span class="sxs-lookup"><span data-stu-id="47dec-137">For example:</span></span>

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

<span data-ttu-id="47dec-138">將分組為：</span><span class="sxs-lookup"><span data-stu-id="47dec-138">will group as:</span></span>

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

<span data-ttu-id="47dec-139">相當於：</span><span class="sxs-lookup"><span data-stu-id="47dec-139">being equivalent to:</span></span>

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a><span data-ttu-id="47dec-140">錯誤互動</span><span class="sxs-lookup"><span data-stu-id="47dec-140">Error interaction</span></span>

<span data-ttu-id="47dec-141">管線鏈運算子不會吸收錯誤。</span><span class="sxs-lookup"><span data-stu-id="47dec-141">Pipeline chain operators do not absorb errors.</span></span> <span data-ttu-id="47dec-142">當管線鏈中的語句擲回腳本終止錯誤時，管線鏈就會終止。</span><span class="sxs-lookup"><span data-stu-id="47dec-142">When a statement in a pipeline chain throws a script-terminating error, the pipeline chain is terminated.</span></span>

<span data-ttu-id="47dec-143">例如：</span><span class="sxs-lookup"><span data-stu-id="47dec-143">For example:</span></span>

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

<span data-ttu-id="47dec-144">即使在攔截到錯誤時，管線鏈仍會終止：</span><span class="sxs-lookup"><span data-stu-id="47dec-144">Even when the error is caught, the pipeline chain is still terminated:</span></span>

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

<span data-ttu-id="47dec-145">如果錯誤為非終止，或只終止管線，管線鏈會繼續進行，並遵循 `$?` 下列值：</span><span class="sxs-lookup"><span data-stu-id="47dec-145">If an error is non-terminating, or only terminates a pipeline, the pipeline chain continues, respecting the value of `$?`:</span></span>

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a><span data-ttu-id="47dec-146">連結管線而非命令</span><span class="sxs-lookup"><span data-stu-id="47dec-146">Chaining pipelines rather than commands</span></span>

<span data-ttu-id="47dec-147">管線鏈運算子的名稱可以用來串連管線，而不只是命令。</span><span class="sxs-lookup"><span data-stu-id="47dec-147">Pipeline chain operators, by their name, can be used to chain pipelines, rather than just commands.</span></span> <span data-ttu-id="47dec-148">這符合其他 shell 的行為，但 *可讓您* 更難以判斷：</span><span class="sxs-lookup"><span data-stu-id="47dec-148">This matches the behavior of other shells, but can make *success* harder to determine:</span></span>

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

<span data-ttu-id="47dec-149">請注意， `Write-Output 'All done!'` 因為在 `Test-NotTwo` 產生非終止錯誤之後被視為失敗，所以不會執行。</span><span class="sxs-lookup"><span data-stu-id="47dec-149">Note that `Write-Output 'All done!'` is not executed, since `Test-NotTwo` is deemed to have failed after generating the non-terminating error.</span></span>

## <a name="see-also"></a><span data-ttu-id="47dec-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47dec-150">See also</span></span>

- [<span data-ttu-id="47dec-151">about_Operators</span><span class="sxs-lookup"><span data-stu-id="47dec-151">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="47dec-152">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="47dec-152">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="47dec-153">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="47dec-153">about_pipelines</span></span>](about_pipelines.md)
