---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: 575f696d74e6a7aa7cf864cbb559f15a25ac1a66
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203768"
---
# <span data-ttu-id="43be4-103">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="43be4-103">Invoke-Expression</span></span>

## <span data-ttu-id="43be4-104">概要</span><span class="sxs-lookup"><span data-stu-id="43be4-104">SYNOPSIS</span></span>
<span data-ttu-id="43be4-105">在本機電腦上執行命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="43be4-105">Runs commands or expressions on the local computer.</span></span>

## <span data-ttu-id="43be4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43be4-106">SYNTAX</span></span>

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## <span data-ttu-id="43be4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="43be4-107">DESCRIPTION</span></span>

<span data-ttu-id="43be4-108">此 `Invoke-Expression` Cmdlet 會將指定的字串評估或執行為命令，並傳回運算式或命令的結果。</span><span class="sxs-lookup"><span data-stu-id="43be4-108">The `Invoke-Expression` cmdlet evaluates or runs a specified string as a command and returns the results of the expression or command.</span></span> <span data-ttu-id="43be4-109">如果沒有 `Invoke-Expression` ，則會傳回在命令列提交的字串 () 不變更。</span><span class="sxs-lookup"><span data-stu-id="43be4-109">Without `Invoke-Expression`, a string submitted at the command line is returned (echoed) unchanged.</span></span>

<span data-ttu-id="43be4-110">運算式會在目前的範圍內進行評估和執行。</span><span class="sxs-lookup"><span data-stu-id="43be4-110">Expressions are evaluated and run in the current scope.</span></span> <span data-ttu-id="43be4-111">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="43be4-111">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="43be4-112">在腳本中使用 Cmdlet 時，請採取合理的預防措施 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="43be4-112">Take reasonable precautions when using the `Invoke-Expression` cmdlet in scripts.</span></span> <span data-ttu-id="43be4-113">當您使用 `Invoke-Expression` 來執行使用者輸入的命令時，請先確認命令是安全的，然後再執行它。</span><span class="sxs-lookup"><span data-stu-id="43be4-113">When using `Invoke-Expression` to run a command that the user enters, verify that the command is safe to run before running it.</span></span> <span data-ttu-id="43be4-114">一般而言，最好使用預先定義的輸入選項來設計您的指令碼，而不要允許自由輸入。</span><span class="sxs-lookup"><span data-stu-id="43be4-114">In general, it is best to design your script with predefined input options, rather than allowing freeform input.</span></span>

## <span data-ttu-id="43be4-115">範例</span><span class="sxs-lookup"><span data-stu-id="43be4-115">EXAMPLES</span></span>

### <span data-ttu-id="43be4-116">範例1：評估運算式</span><span class="sxs-lookup"><span data-stu-id="43be4-116">Example 1: Evaluate an expression</span></span>

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

<span data-ttu-id="43be4-117">這個範例示範 `Invoke-Expression` 如何使用來評估運算式。</span><span class="sxs-lookup"><span data-stu-id="43be4-117">This example demonstrates the use of `Invoke-Expression` to evaluate an expression.</span></span> <span data-ttu-id="43be4-118">如果沒有 `Invoke-Expression` ，則會列印運算式，但不會進行評估。</span><span class="sxs-lookup"><span data-stu-id="43be4-118">Without `Invoke-Expression`, the expression is printed, but not evaluated.</span></span>

<span data-ttu-id="43be4-119">第一個命令會將 `Get-Process` 字串)  (值指派給 `$Command` 變數。</span><span class="sxs-lookup"><span data-stu-id="43be4-119">The first command assigns a value of `Get-Process` (a string) to the `$Command` variable.</span></span>

<span data-ttu-id="43be4-120">第二個命令會顯示在命令列輸入變數名稱的效果。</span><span class="sxs-lookup"><span data-stu-id="43be4-120">The second command shows the effect of typing the variable name at the command line.</span></span> <span data-ttu-id="43be4-121">PowerShell 會回應字串。</span><span class="sxs-lookup"><span data-stu-id="43be4-121">PowerShell echoes the string.</span></span>

<span data-ttu-id="43be4-122">第三個命令會使用 `Invoke-Expression` 來評估字串。</span><span class="sxs-lookup"><span data-stu-id="43be4-122">The third command uses `Invoke-Expression` to evaluate the string.</span></span>

### <span data-ttu-id="43be4-123">範例2：在本機電腦上執行腳本</span><span class="sxs-lookup"><span data-stu-id="43be4-123">Example 2: Run a script on the local computer</span></span>

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

<span data-ttu-id="43be4-124">這些命令會用 `Invoke-Expression` 來在本機電腦上執行腳本 TestScript.ps1。</span><span class="sxs-lookup"><span data-stu-id="43be4-124">These commands use `Invoke-Expression` to run a script, TestScript.ps1, on the local computer.</span></span> <span data-ttu-id="43be4-125">兩個命令是相等的。</span><span class="sxs-lookup"><span data-stu-id="43be4-125">The two commands are equivalent.</span></span> <span data-ttu-id="43be4-126">第一個使用 **command** 參數指定要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="43be4-126">The first uses the **Command** parameter to specify the command to run.</span></span>
<span data-ttu-id="43be4-127">第二個會使用管線運算子 (`|`) 將命令字串傳送至 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="43be4-127">The second uses a pipeline operator (`|`) to send the command string to `Invoke-Expression`.</span></span>

### <span data-ttu-id="43be4-128">範例3：在變數中執行命令</span><span class="sxs-lookup"><span data-stu-id="43be4-128">Example 3: Run a command in a variable</span></span>

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

<span data-ttu-id="43be4-129">此範例會執行儲存在變數中的命令字串 `$Command` 。</span><span class="sxs-lookup"><span data-stu-id="43be4-129">This example runs a command string that is saved in the `$Command` variable.</span></span>

<span data-ttu-id="43be4-130">命令字串會以單引號括住，因為它包含一個變數， `$_` 代表目前的物件。</span><span class="sxs-lookup"><span data-stu-id="43be4-130">The command string is enclosed in single quotation marks because it includes a variable, `$_`, which represents the current object.</span></span> <span data-ttu-id="43be4-131">如果是以雙引號括住，則 `$_` 變數會在儲存至變數之前，以其值取代 `$Command` 。</span><span class="sxs-lookup"><span data-stu-id="43be4-131">If it were enclosed in double quotation marks, the `$_` variable would be replaced by its value before it was saved in the `$Command` variable.</span></span>

### <span data-ttu-id="43be4-132">範例4：取得並執行 Cmdlet 說明範例</span><span class="sxs-lookup"><span data-stu-id="43be4-132">Example 4: Get and run a cmdlet Help example</span></span>

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

<span data-ttu-id="43be4-133">此命令會取出並執行 Cmdlet 說明主題中的第一個範例 `Get-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="43be4-133">This command retrieves and runs the first example in the `Get-EventLog` cmdlet Help topic.</span></span>

<span data-ttu-id="43be4-134">若要執行不同 Cmdlet 的範例，請將變數的值變更 `$Cmdlet_name` 為 Cmdlet 的名稱。</span><span class="sxs-lookup"><span data-stu-id="43be4-134">To run an example of a different cmdlet, change the value of the `$Cmdlet_name` variable to the name of the cmdlet.</span></span> <span data-ttu-id="43be4-135">然後，將 `$Example_number` 變數變更為您想要執行的範例編號。</span><span class="sxs-lookup"><span data-stu-id="43be4-135">And, change the `$Example_number` variable to the example number you want to run.</span></span> <span data-ttu-id="43be4-136">如果範例編號無效，命令就會失敗。</span><span class="sxs-lookup"><span data-stu-id="43be4-136">The command fails if the example number is not valid.</span></span>

## <span data-ttu-id="43be4-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43be4-137">PARAMETERS</span></span>

### <span data-ttu-id="43be4-138">-Command</span><span class="sxs-lookup"><span data-stu-id="43be4-138">-Command</span></span>

<span data-ttu-id="43be4-139">指定要執行的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="43be4-139">Specifies the command or expression to run.</span></span> <span data-ttu-id="43be4-140">輸入命令或運算式，或輸入包含命令或運算式的變數。</span><span class="sxs-lookup"><span data-stu-id="43be4-140">Type the command or expression or enter a variable that contains the command or expression.</span></span> <span data-ttu-id="43be4-141">需要 **命令** 參數。</span><span class="sxs-lookup"><span data-stu-id="43be4-141">The **Command** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43be4-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43be4-142">CommonParameters</span></span>

<span data-ttu-id="43be4-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="43be4-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43be4-144">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="43be4-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="43be4-145">輸入</span><span class="sxs-lookup"><span data-stu-id="43be4-145">INPUTS</span></span>

### <span data-ttu-id="43be4-146">System.string 或 PSObject</span><span class="sxs-lookup"><span data-stu-id="43be4-146">System.String or PSObject</span></span>

<span data-ttu-id="43be4-147">您可以使用管線將代表命令的物件傳送至 `Invoke-Expression` 。</span><span class="sxs-lookup"><span data-stu-id="43be4-147">You can pipe an object that represents the command to `Invoke-Expression`.</span></span>
<span data-ttu-id="43be4-148">使用 `$Input` 自動變數來代表命令中的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="43be4-148">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="43be4-149">輸出</span><span class="sxs-lookup"><span data-stu-id="43be4-149">OUTPUTS</span></span>

### <span data-ttu-id="43be4-150">PSObject</span><span class="sxs-lookup"><span data-stu-id="43be4-150">PSObject</span></span>

<span data-ttu-id="43be4-151">傳回已叫用命令所產生的輸出 () **命令** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="43be4-151">Returns the output that is generated by the invoked command (the value of the **Command** parameter).</span></span>

## <span data-ttu-id="43be4-152">注意</span><span class="sxs-lookup"><span data-stu-id="43be4-152">NOTES</span></span>

<span data-ttu-id="43be4-153">在大部分情況下，您會使用 PowerShell 的呼叫運算子來叫用運算式，並達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="43be4-153">In most cases, you invoke expressions using PowerShell's call operator and achieve the same results.</span></span>
<span data-ttu-id="43be4-154">呼叫運算子是較安全的方法。</span><span class="sxs-lookup"><span data-stu-id="43be4-154">The call operator is a safer method.</span></span> <span data-ttu-id="43be4-155">如需詳細資訊，請參閱 [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)。</span><span class="sxs-lookup"><span data-stu-id="43be4-155">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span></span>

## <span data-ttu-id="43be4-156">相關連結</span><span class="sxs-lookup"><span data-stu-id="43be4-156">RELATED LINKS</span></span>

[<span data-ttu-id="43be4-157">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="43be4-157">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="43be4-158">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="43be4-158">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)
