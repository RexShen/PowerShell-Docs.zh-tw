---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 43958b376123202e152ceb2da3223cc2f22b0687
ms.sourcegitcommit: 165d10405d9db3a68c417a239d3181378fd02b9b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96935896"
---
# <span data-ttu-id="f7f02-103">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="f7f02-103">Measure-Command</span></span>

## <span data-ttu-id="f7f02-104">概要</span><span class="sxs-lookup"><span data-stu-id="f7f02-104">SYNOPSIS</span></span>
<span data-ttu-id="f7f02-105">測量執行指令碼區塊和 Cmdlet 所需的時間。</span><span class="sxs-lookup"><span data-stu-id="f7f02-105">Measures the time it takes to run script blocks and cmdlets.</span></span>

## <span data-ttu-id="f7f02-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7f02-106">SYNTAX</span></span>

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## <span data-ttu-id="f7f02-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f7f02-107">DESCRIPTION</span></span>

<span data-ttu-id="f7f02-108">此 `Measure-Command` Cmdlet 會在內部執行腳本區塊或 Cmdlet、執行作業的次數，並傳回執行時間。</span><span class="sxs-lookup"><span data-stu-id="f7f02-108">The `Measure-Command` cmdlet runs a script block or cmdlet internally, times the execution of the operation, and returns the execution time.</span></span>

> [!NOTE]
> <span data-ttu-id="f7f02-109">腳本區塊執行的方式是 `Measure-Command` 在目前的範圍中執行，而不是子範圍。</span><span class="sxs-lookup"><span data-stu-id="f7f02-109">Script blocks run by `Measure-Command` run in the current scope, not a child scope.</span></span>

## <span data-ttu-id="f7f02-110">範例</span><span class="sxs-lookup"><span data-stu-id="f7f02-110">EXAMPLES</span></span>

### <span data-ttu-id="f7f02-111">範例1：測量命令</span><span class="sxs-lookup"><span data-stu-id="f7f02-111">Example 1: Measure a command</span></span>

<span data-ttu-id="f7f02-112">這個範例會測量執行命令的時間，此 `Get-EventLog` 命令會取得 Windows PowerShell 事件記錄檔中的事件。</span><span class="sxs-lookup"><span data-stu-id="f7f02-112">This example measures the time it takes to run a `Get-EventLog` command that gets the events in the Windows PowerShell event log.</span></span>

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### <span data-ttu-id="f7f02-113">範例2：比較 Measure-Command 的兩個輸出</span><span class="sxs-lookup"><span data-stu-id="f7f02-113">Example 2: Compare two outputs from Measure-Command</span></span>

<span data-ttu-id="f7f02-114">第一個命令會測量處理遞迴命令所花費的時間 `Get-ChildItem` ，此命令會使用 **Path** 參數來取得 `.txt` `C:\Windows` 目錄及其子目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f7f02-114">The first command measures the time it takes to process a recursive `Get-ChildItem` command that uses the **Path** parameter to get only `.txt` files in the `C:\Windows` directory and its subdirectories.</span></span>

<span data-ttu-id="f7f02-115">第二個命令會測量處理遞迴命令所需的時間 `Get-ChildItem` ，此命令使用提供者特定的 ' 參數。</span><span class="sxs-lookup"><span data-stu-id="f7f02-115">The second command measures the time it takes to process a recursive `Get-ChildItem` command that uses the provider-specific \` parameter.</span></span>

<span data-ttu-id="f7f02-116">這些命令會顯示在 PowerShell 命令中使用提供者特定篩選器的值。</span><span class="sxs-lookup"><span data-stu-id="f7f02-116">These commands show the value of using a provider-specific filter in PowerShell commands.</span></span>

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### <span data-ttu-id="f7f02-117">範例3：將輸入輸送至 Measure-Command</span><span class="sxs-lookup"><span data-stu-id="f7f02-117">Example 3: Piping input to Measure-Command</span></span>

<span data-ttu-id="f7f02-118">`Measure-Command`傳送至 **運算式** 參數的腳本區塊可以使用輸送至的物件。</span><span class="sxs-lookup"><span data-stu-id="f7f02-118">Objects that are piped to `Measure-Command` are available to the script block that is passed to the **Expression** parameter.</span></span> <span data-ttu-id="f7f02-119">腳本區塊會針對管線上的每個物件執行一次。</span><span class="sxs-lookup"><span data-stu-id="f7f02-119">The script block is executed once for each object on the pipeline.</span></span>

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_; $i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### <span data-ttu-id="f7f02-120">範例4：顯示已測量命令的輸出</span><span class="sxs-lookup"><span data-stu-id="f7f02-120">Example 4: Displaying output of measured command</span></span>

<span data-ttu-id="f7f02-121">若要在中顯示運算式的輸出， `Measure-Command` 您可以使用管道 `Out-Default` 。</span><span class="sxs-lookup"><span data-stu-id="f7f02-121">To display output of expression in `Measure-Command` you can use a pipe to `Out-Default`.</span></span>

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### <span data-ttu-id="f7f02-122">範例5：測量子範圍中的執行</span><span class="sxs-lookup"><span data-stu-id="f7f02-122">Example 5: Measuring execution in a child scope</span></span>

<span data-ttu-id="f7f02-123">`Measure-Command` 在目前的範圍中執行腳本區塊，因此腳本區塊可以修改目前範圍中的值。</span><span class="sxs-lookup"><span data-stu-id="f7f02-123">`Measure-Command` runs the script block in the current scope, so the script block can modify values in the current scope.</span></span> <span data-ttu-id="f7f02-124">若要避免變更目前的範圍，您必須將腳本區塊包裝在大括弧 (`{}`) ，並使用叫用運算子 (`&`) 在子範圍中執行區塊。</span><span class="sxs-lookup"><span data-stu-id="f7f02-124">To avoid changes to the current scope, you must wrap the script block in braces (`{}`) and use the invocation operator (`&`) to execute the block in a child scope.</span></span>

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

<span data-ttu-id="f7f02-125">如需調用運算子的詳細資訊，請參閱 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-)。</span><span class="sxs-lookup"><span data-stu-id="f7f02-125">For more information about the invocation operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).</span></span>

## <span data-ttu-id="f7f02-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7f02-126">PARAMETERS</span></span>

### <span data-ttu-id="f7f02-127">-Expression</span><span class="sxs-lookup"><span data-stu-id="f7f02-127">-Expression</span></span>

<span data-ttu-id="f7f02-128">指定正在計時的運算式。</span><span class="sxs-lookup"><span data-stu-id="f7f02-128">Specifies the expression that is being timed.</span></span> <span data-ttu-id="f7f02-129">以大括弧括住運算式 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="f7f02-129">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7f02-130">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f7f02-130">-InputObject</span></span>

<span data-ttu-id="f7f02-131">系結至 **InputObject** 參數的物件是傳遞至 **Expression** 參數之腳本區塊的選擇性輸入。</span><span class="sxs-lookup"><span data-stu-id="f7f02-131">Objects bound to the **InputObject** parameter are optional input for the script block passed to the **Expression** parameter.</span></span> <span data-ttu-id="f7f02-132">在腳本區塊內， `$_` 可以用來參考管線中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="f7f02-132">Inside the script block, `$_` can be used to reference the current object in the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f7f02-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7f02-133">CommonParameters</span></span>

<span data-ttu-id="f7f02-134">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f7f02-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7f02-135">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f7f02-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7f02-136">輸入</span><span class="sxs-lookup"><span data-stu-id="f7f02-136">INPUTS</span></span>

### <span data-ttu-id="f7f02-137">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="f7f02-137">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f7f02-138">您可以使用管線將物件傳送至 `Measure-Command` 。</span><span class="sxs-lookup"><span data-stu-id="f7f02-138">You can pipe an object to `Measure-Command`.</span></span>

## <span data-ttu-id="f7f02-139">輸出</span><span class="sxs-lookup"><span data-stu-id="f7f02-139">OUTPUTS</span></span>

### <span data-ttu-id="f7f02-140">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="f7f02-140">System.TimeSpan</span></span>

<span data-ttu-id="f7f02-141">`Measure-Command` 傳回代表結果的時間範圍物件。</span><span class="sxs-lookup"><span data-stu-id="f7f02-141">`Measure-Command` returns a time span object that represents the result.</span></span>

## <span data-ttu-id="f7f02-142">注意</span><span class="sxs-lookup"><span data-stu-id="f7f02-142">NOTES</span></span>

## <span data-ttu-id="f7f02-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="f7f02-143">RELATED LINKS</span></span>

[<span data-ttu-id="f7f02-144">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f7f02-144">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="f7f02-145">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="f7f02-145">Trace-Command</span></span>](Trace-Command.md)

