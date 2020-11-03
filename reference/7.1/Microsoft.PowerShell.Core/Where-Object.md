---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: b5f4a64cceffa1f4f9884bb4de3211e129871ba7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205100"
---
# <span data-ttu-id="37db2-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-103">Where-Object</span></span>

## <span data-ttu-id="37db2-104">概要</span><span class="sxs-lookup"><span data-stu-id="37db2-104">SYNOPSIS</span></span>
<span data-ttu-id="37db2-105">根據屬性值從集合中選取物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="37db2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="37db2-106">SYNTAX</span></span>

### <span data-ttu-id="37db2-107">EqualSet (預設) </span><span class="sxs-lookup"><span data-stu-id="37db2-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="37db2-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="37db2-109">MatchSet</span><span class="sxs-lookup"><span data-stu-id="37db2-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="37db2-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="37db2-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="37db2-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="37db2-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="37db2-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-121">LikeSet</span><span class="sxs-lookup"><span data-stu-id="37db2-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="37db2-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="37db2-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="37db2-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="37db2-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="37db2-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="37db2-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-128">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="37db2-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="37db2-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="37db2-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="37db2-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-132">插圖</span><span class="sxs-lookup"><span data-stu-id="37db2-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="37db2-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="37db2-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="37db2-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="37db2-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="37db2-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### <span data-ttu-id="37db2-138">Not</span><span class="sxs-lookup"><span data-stu-id="37db2-138">Not</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## <span data-ttu-id="37db2-139">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="37db2-139">DESCRIPTION</span></span>

<span data-ttu-id="37db2-140">`Where-Object`Cmdlet 會從傳遞給它的物件集合中選取具有特定屬性值的物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-140">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="37db2-141">例如，您可以使用 `Where-Object` Cmdlet 來選取在特定日期之後建立的檔案、具有特定識別碼的事件，或使用特定 Windows 版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="37db2-141">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="37db2-142">從 Windows PowerShell 3.0 開始，有兩種不同的方式可建立 `Where-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="37db2-142">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="37db2-143">**腳本區塊** 。</span><span class="sxs-lookup"><span data-stu-id="37db2-143">**Script block** .</span></span> <span data-ttu-id="37db2-144">您可以使用指令碼區塊來指定屬性名稱、比較運算子及屬性值。</span><span class="sxs-lookup"><span data-stu-id="37db2-144">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="37db2-145">`Where-Object` 傳回腳本區塊語句為 true 的所有物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-145">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="37db2-146">例如，下列命令會取得一般優先順序類別中的處理常式，也就是 **PriorityClass** 屬性的值等於 normal 的進程。</span><span class="sxs-lookup"><span data-stu-id="37db2-146">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="37db2-147">所有 PowerShell 比較運算子都是有效的腳本區塊格式。</span><span class="sxs-lookup"><span data-stu-id="37db2-147">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="37db2-148">如需比較運算子的詳細資訊，請參閱 [about_Comparison_Operators](./About/about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="37db2-148">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="37db2-149">**比較語句** 。</span><span class="sxs-lookup"><span data-stu-id="37db2-149">**Comparison statement** .</span></span> <span data-ttu-id="37db2-150">您也可以撰寫較像自然語言的比較陳述式。</span><span class="sxs-lookup"><span data-stu-id="37db2-150">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="37db2-151">比較陳述式是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-151">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="37db2-152">例如，下列命令也會取得優先順序類別為 Normal 的進程。</span><span class="sxs-lookup"><span data-stu-id="37db2-152">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="37db2-153">這些命令是相等的，可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="37db2-153">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="37db2-154">從 Windows PowerShell 3.0 開始，會在 `Where-Object` 命令中加入比較運算子做為參數 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-154">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="37db2-155">除非另有指定，否則所有運算子都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-155">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="37db2-156">在 Windows PowerShell 3.0 之前，PowerShell 語言中的比較運算子只能在腳本區塊中使用。</span><span class="sxs-lookup"><span data-stu-id="37db2-156">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="37db2-157">當您提供單一 **屬性** 給時 `Where-Object` ，屬性的值會被視為布林運算式。</span><span class="sxs-lookup"><span data-stu-id="37db2-157">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="37db2-158">當 **長度** 的值不是零時，運算式會評估為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="37db2-158">When the value of **Length** is not zero, the expression evaluates to **True** .</span></span> <span data-ttu-id="37db2-159">例如：`('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="37db2-159">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="37db2-160">上述範例在功能上等同于：</span><span class="sxs-lookup"><span data-stu-id="37db2-160">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="37db2-161">範例</span><span class="sxs-lookup"><span data-stu-id="37db2-161">EXAMPLES</span></span>

### <span data-ttu-id="37db2-162">範例1：取得已停止的服務</span><span class="sxs-lookup"><span data-stu-id="37db2-162">Example 1: Get stopped services</span></span>

<span data-ttu-id="37db2-163">這些命令會取得目前已停止的所有服務清單。</span><span class="sxs-lookup"><span data-stu-id="37db2-163">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="37db2-164">`$_`自動變數代表每個傳遞給 Cmdlet 的物件 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-164">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="37db2-165">第一個命令使用腳本區塊格式，第二個命令使用比較語句格式。</span><span class="sxs-lookup"><span data-stu-id="37db2-165">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="37db2-166">這些命令是相等的，可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="37db2-166">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="37db2-167">範例2：根據工作集取得進程</span><span class="sxs-lookup"><span data-stu-id="37db2-167">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="37db2-168">這些命令會列出工作集大於 250 mb (KB) 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="37db2-168">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="37db2-169">Scriptblock 和語句語法是相等的，可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="37db2-169">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="37db2-170">範例3：根據進程名稱取得進程</span><span class="sxs-lookup"><span data-stu-id="37db2-170">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="37db2-171">這些命令會取得其 **ProcessName** 屬性值以字母開頭的處理常式 `p` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-171">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="37db2-172">**Match** 運算子可讓您使用正則運算式相符專案。</span><span class="sxs-lookup"><span data-stu-id="37db2-172">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="37db2-173">Scriptblock 和語句語法是相等的，可以交換使用。</span><span class="sxs-lookup"><span data-stu-id="37db2-173">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="37db2-174">範例4：使用比較語句格式</span><span class="sxs-lookup"><span data-stu-id="37db2-174">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="37db2-175">此範例示範如何使用 Cmdlet 的新比較語句格式 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-175">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="37db2-176">第一個命令使用比較陳述式格式。</span><span class="sxs-lookup"><span data-stu-id="37db2-176">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="37db2-177">此命令中不會使用任何別名，並且所有的參數都包括參數名稱。</span><span class="sxs-lookup"><span data-stu-id="37db2-177">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="37db2-178">第二個命令是更自然的比較命令格式使用方式。</span><span class="sxs-lookup"><span data-stu-id="37db2-178">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="37db2-179">`where`別名會取代為 `Where-Object` Cmdlet 名稱，並省略所有選擇性參數名稱。</span><span class="sxs-lookup"><span data-stu-id="37db2-179">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="37db2-180">範例5：根據屬性取得命令</span><span class="sxs-lookup"><span data-stu-id="37db2-180">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="37db2-181">此範例示範如何撰寫會傳回 True 或 False 的項目，或撰寫具有任何指定屬性值的命令。</span><span class="sxs-lookup"><span data-stu-id="37db2-181">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="37db2-182">每個範例都會顯示命令的腳本區塊和比較語句格式。</span><span class="sxs-lookup"><span data-stu-id="37db2-182">Each example shows both the script block and comparison statement formats for the command.</span></span>

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### <span data-ttu-id="37db2-183">範例6：使用多個條件</span><span class="sxs-lookup"><span data-stu-id="37db2-183">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="37db2-184">此範例說明如何建立 `Where-Object` 具有多個條件的命令。</span><span class="sxs-lookup"><span data-stu-id="37db2-184">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="37db2-185">此命令取得支援可更新之說明功能的非核心模組。</span><span class="sxs-lookup"><span data-stu-id="37db2-185">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="37db2-186">此命令會使用 Cmdlet 的 **ListAvailable** 參數 `Get-Module` 來取得電腦上的所有模組。</span><span class="sxs-lookup"><span data-stu-id="37db2-186">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="37db2-187">管線運算子 (`|`) 會將模組傳送至 `Where-Object` Cmdlet，此 Cmdlet 會取得名稱不是以 MICROSOFT 或 PS 開頭的模組，並且具有 **HelpInfoURI** 屬性的值，這會指示 PowerShell 在哪裡找到模組的已更新說明檔。</span><span class="sxs-lookup"><span data-stu-id="37db2-187">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="37db2-188">比較語句是由 **And** 邏輯運算子連接。</span><span class="sxs-lookup"><span data-stu-id="37db2-188">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="37db2-189">此範例使用指令碼區塊命令格式。</span><span class="sxs-lookup"><span data-stu-id="37db2-189">The example uses the script block command format.</span></span> <span data-ttu-id="37db2-190">邏輯運算子（例如 **and** 和 **Or** ）僅適用于腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="37db2-190">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="37db2-191">您無法在命令的比較語句格式中使用它們 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-191">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="37db2-192">如需 PowerShell 邏輯運算子的詳細資訊，請參閱 [about_Logical_Operators](./About/about_logical_operators.md)。</span><span class="sxs-lookup"><span data-stu-id="37db2-192">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="37db2-193">如需可更新之說明功能的詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="37db2-193">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="37db2-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="37db2-194">PARAMETERS</span></span>

### <span data-ttu-id="37db2-195">-包含</span><span class="sxs-lookup"><span data-stu-id="37db2-195">-CContains</span></span>

<span data-ttu-id="37db2-196">指出如果物件的屬性值與指定的值完全相符，此 Cmdlet 會從集合取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-196">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="37db2-197">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-197">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-198">例如：`Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="37db2-198">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="37db2-199">**包含** 是指值的集合，如果集合包含的專案與指定的值完全相符，則為 true。</span><span class="sxs-lookup"><span data-stu-id="37db2-199">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="37db2-200">如果輸入是單一物件，則 PowerShell 會將它轉換成一個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37db2-200">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="37db2-201">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-202">-CEQ</span><span class="sxs-lookup"><span data-stu-id="37db2-202">-CEQ</span></span>

<span data-ttu-id="37db2-203">指出此 Cmdlet 會在屬性值與指定的值相同時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-203">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="37db2-204">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-204">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-205">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-206">-CGE</span><span class="sxs-lookup"><span data-stu-id="37db2-206">-CGE</span></span>

<span data-ttu-id="37db2-207">指出此 Cmdlet 會在屬性值大於或等於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-207">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="37db2-208">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-208">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-209">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-209">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-210">-CGT</span><span class="sxs-lookup"><span data-stu-id="37db2-210">-CGT</span></span>

<span data-ttu-id="37db2-211">指出此 Cmdlet 會在屬性值大於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-211">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="37db2-212">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-212">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-213">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-213">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-214">-CIn</span><span class="sxs-lookup"><span data-stu-id="37db2-214">-CIn</span></span>

<span data-ttu-id="37db2-215">指出此 Cmdlet 會在屬性值包含指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-215">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="37db2-216">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-216">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-217">例如：`Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="37db2-217">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="37db2-218">**CIn** 類似 **包含** ，不同之處在于屬性和值的位置是相反的。</span><span class="sxs-lookup"><span data-stu-id="37db2-218">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="37db2-219">例如，下列陳述式都是 True。</span><span class="sxs-lookup"><span data-stu-id="37db2-219">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="37db2-220">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-221">-CLE</span><span class="sxs-lookup"><span data-stu-id="37db2-221">-CLE</span></span>

<span data-ttu-id="37db2-222">指出此 Cmdlet 會在屬性值小於或等於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-222">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="37db2-223">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-223">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-224">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-225">-CLike</span><span class="sxs-lookup"><span data-stu-id="37db2-225">-CLike</span></span>

<span data-ttu-id="37db2-226">指出此 Cmdlet 會在屬性值與包含萬用字元的值相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-226">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="37db2-227">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-227">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-228">例如：`Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="37db2-228">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="37db2-229">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-230">-CLT</span><span class="sxs-lookup"><span data-stu-id="37db2-230">-CLT</span></span>

<span data-ttu-id="37db2-231">指出此 Cmdlet 會在屬性值小於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-231">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="37db2-232">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-232">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-233">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-234">-CMatch</span><span class="sxs-lookup"><span data-stu-id="37db2-234">-CMatch</span></span>

<span data-ttu-id="37db2-235">指出此 Cmdlet 會在屬性值與指定的正則運算式相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-235">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="37db2-236">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-236">This operation is case-sensitive.</span></span> <span data-ttu-id="37db2-237">當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="37db2-237">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="37db2-238">例如：`Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="37db2-238">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="37db2-239">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-240">-CNE</span><span class="sxs-lookup"><span data-stu-id="37db2-240">-CNE</span></span>

<span data-ttu-id="37db2-241">指出此 Cmdlet 會在屬性值與指定的值不同時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-241">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="37db2-242">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-242">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-243">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-244">-Cnotcontains 是指</span><span class="sxs-lookup"><span data-stu-id="37db2-244">-CNotContains</span></span>

<span data-ttu-id="37db2-245">指出此 Cmdlet 會在物件的屬性值與指定的值不完全相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-245">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="37db2-246">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-246">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-247">例如：`Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="37db2-247">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="37db2-248">**NotContains** 和 **cnotcontains 是指** 指的是值的集合，而且當集合未包含任何與指定的值完全相符的專案時為 true。</span><span class="sxs-lookup"><span data-stu-id="37db2-248">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="37db2-249">如果輸入是單一物件，則 PowerShell 會將它轉換成一個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37db2-249">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="37db2-250">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-251">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="37db2-251">-CNotIn</span></span>

<span data-ttu-id="37db2-252">指出此 Cmdlet 會在屬性值與指定的值不完全相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-252">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="37db2-253">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-253">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-254">例如：`Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="37db2-254">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="37db2-255">**NotIn** 和 **CNotIn** 運算子類似 **NotContains** 和 **cnotcontains 是指** ，不同之處在于屬性和值的位置是相反的。</span><span class="sxs-lookup"><span data-stu-id="37db2-255">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="37db2-256">例如，下列陳述式為 True。</span><span class="sxs-lookup"><span data-stu-id="37db2-256">For example, the following statements are true.</span></span>

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-257">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="37db2-257">-CNotLike</span></span>

<span data-ttu-id="37db2-258">指出此 Cmdlet 會在屬性值與包含萬用字元的值不相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-258">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="37db2-259">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-259">This operation is case-sensitive.</span></span>

<span data-ttu-id="37db2-260">例如：`Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="37db2-260">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="37db2-261">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-262">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="37db2-262">-CNotMatch</span></span>

<span data-ttu-id="37db2-263">指出此 Cmdlet 會在屬性值與指定的正則運算式不相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-263">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="37db2-264">這項操作會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="37db2-264">This operation is case-sensitive.</span></span> <span data-ttu-id="37db2-265">當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="37db2-265">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="37db2-266">例如：`Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="37db2-266">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="37db2-267">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-268">-Contains</span><span class="sxs-lookup"><span data-stu-id="37db2-268">-Contains</span></span>

<span data-ttu-id="37db2-269">指出此 Cmdlet 會在物件的屬性值中有任何專案與指定的值完全相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-269">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="37db2-270">例如：`Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="37db2-270">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="37db2-271">如果屬性值包含單一物件，則 PowerShell 會將它轉換成一個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37db2-271">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="37db2-272">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-273">-EQ</span><span class="sxs-lookup"><span data-stu-id="37db2-273">-EQ</span></span>

<span data-ttu-id="37db2-274">指出此 Cmdlet 會在屬性值與指定的值相同時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-274">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="37db2-275">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-276">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="37db2-276">-FilterScript</span></span>

<span data-ttu-id="37db2-277">指定用來篩選物件的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="37db2-277">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="37db2-278">以大括弧括住腳本區塊 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="37db2-278">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="37db2-279">參數名稱 **FilterScript** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="37db2-279">The parameter name, **FilterScript** , is optional.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-280">-GE</span><span class="sxs-lookup"><span data-stu-id="37db2-280">-GE</span></span>

<span data-ttu-id="37db2-281">指出此 Cmdlet 會在屬性值大於或等於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-281">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="37db2-282">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-283">-GT</span><span class="sxs-lookup"><span data-stu-id="37db2-283">-GT</span></span>

<span data-ttu-id="37db2-284">指出此 Cmdlet 會在屬性值大於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-284">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="37db2-285">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-286">-In</span><span class="sxs-lookup"><span data-stu-id="37db2-286">-In</span></span>

<span data-ttu-id="37db2-287">指出此 Cmdlet 會在屬性值符合任何指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-287">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="37db2-288">例如：</span><span class="sxs-lookup"><span data-stu-id="37db2-288">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="37db2-289">如果 **value** 參數的值為單一物件，則 PowerShell 會將它轉換成一個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37db2-289">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="37db2-290">如果物件的屬性值是陣列，則 PowerShell 會使用參考相等來判斷是否相符。</span><span class="sxs-lookup"><span data-stu-id="37db2-290">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="37db2-291">`Where-Object` 只有當 **Property** 參數的值和 **值** 的任何值都是物件的相同實例時，才會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-291">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="37db2-292">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-293">-InputObject</span><span class="sxs-lookup"><span data-stu-id="37db2-293">-InputObject</span></span>

<span data-ttu-id="37db2-294">指定要篩選的物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-294">Specifies the objects to be filtered.</span></span> <span data-ttu-id="37db2-295">您也可以透過管道將物件傳送至 `Where-Object` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-295">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="37db2-296">當您搭配使用 **inputobject** 參數與時 `Where-Object` ，不會將命令結果傳送至，而是 `Where-Object` 會將 **inputobject** 值視為單一物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-296">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="37db2-297">即使值是命令結果的集合（例如），也是如此 `-InputObject (Get-Process)` 。</span><span class="sxs-lookup"><span data-stu-id="37db2-297">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="37db2-298">因為 **InputObject** 無法從物件陣列或集合傳回個別屬性，所以如果您使用來篩選物件的集合，而 `Where-Object` 這些物件具有已定義屬性中的特定值，您可以 `Where-Object` 在管線中使用，如本主題中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="37db2-298">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="37db2-299">-是</span><span class="sxs-lookup"><span data-stu-id="37db2-299">-Is</span></span>

<span data-ttu-id="37db2-300">指出此 Cmdlet 會在屬性值為指定之 .NET 型別的實例時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-300">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="37db2-301">使用方括號括住型別名稱。</span><span class="sxs-lookup"><span data-stu-id="37db2-301">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="37db2-302">例如， `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="37db2-302">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="37db2-303">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-303">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-304">-IsNot</span><span class="sxs-lookup"><span data-stu-id="37db2-304">-IsNot</span></span>

<span data-ttu-id="37db2-305">指出此 Cmdlet 會在屬性值不是指定之 .NET 型別的實例時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-305">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="37db2-306">例如， `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="37db2-306">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="37db2-307">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-307">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-308">-LE</span><span class="sxs-lookup"><span data-stu-id="37db2-308">-LE</span></span>

<span data-ttu-id="37db2-309">指出此 Cmdlet 會在屬性值小於或等於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-309">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="37db2-310">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-311">-Like</span><span class="sxs-lookup"><span data-stu-id="37db2-311">-Like</span></span>

<span data-ttu-id="37db2-312">指出此 Cmdlet 會在屬性值與包含萬用字元的值相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-312">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="37db2-313">例如：`Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="37db2-313">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="37db2-314">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-314">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-315">-LT</span><span class="sxs-lookup"><span data-stu-id="37db2-315">-LT</span></span>

<span data-ttu-id="37db2-316">指出此 Cmdlet 會在屬性值小於指定的值時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-316">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="37db2-317">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-317">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-318">-Match</span><span class="sxs-lookup"><span data-stu-id="37db2-318">-Match</span></span>

<span data-ttu-id="37db2-319">指出此 Cmdlet 會在屬性值與指定的正則運算式相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-319">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="37db2-320">當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="37db2-320">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="37db2-321">例如：`Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="37db2-321">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="37db2-322">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-323">-NE</span><span class="sxs-lookup"><span data-stu-id="37db2-323">-NE</span></span>

<span data-ttu-id="37db2-324">指出此 Cmdlet 會在屬性值與指定的值不同時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-324">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="37db2-325">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-326">-Not</span><span class="sxs-lookup"><span data-stu-id="37db2-326">-Not</span></span>

<span data-ttu-id="37db2-327">指出此 Cmdlet 會在屬性不存在或值為 null 或 false 時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-327">Indicates that this cmdlet gets objects if the property does not exist or has a value of null or false.</span></span>

<span data-ttu-id="37db2-328">例如：`Get-Service | where -Not "DependentServices"`</span><span class="sxs-lookup"><span data-stu-id="37db2-328">For example: `Get-Service | where -Not "DependentServices"`</span></span>

<span data-ttu-id="37db2-329">此參數是在 Windows PowerShell 6.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-329">This parameter was introduced in Windows PowerShell 6.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-330">-NotContains</span><span class="sxs-lookup"><span data-stu-id="37db2-330">-NotContains</span></span>

<span data-ttu-id="37db2-331">指出此 Cmdlet 會在屬性值中沒有任何專案與指定的值完全相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-331">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="37db2-332">例如：`Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="37db2-332">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="37db2-333">**NotContains** 是指值的集合，如果集合未包含任何與指定的值完全相符的專案，則為 true。</span><span class="sxs-lookup"><span data-stu-id="37db2-333">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="37db2-334">如果輸入是單一物件，則 PowerShell 會將它轉換成一個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37db2-334">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="37db2-335">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-335">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-336">-NotIn</span><span class="sxs-lookup"><span data-stu-id="37db2-336">-NotIn</span></span>

<span data-ttu-id="37db2-337">指出此 Cmdlet 會在屬性值與任何指定的值不完全相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-337">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="37db2-338">例如：`Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="37db2-338">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="37db2-339">如果 **value** 值是單一物件，則 PowerShell 會將它轉換成一個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37db2-339">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="37db2-340">如果物件的屬性值是陣列，則 PowerShell 會使用參考相等來判斷是否相符。</span><span class="sxs-lookup"><span data-stu-id="37db2-340">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="37db2-341">`Where-Object` 只有當 **屬性** 的值和 **值** 的任何值都不是物件的相同實例時，才會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-341">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="37db2-342">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-342">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-343">-NotLike</span><span class="sxs-lookup"><span data-stu-id="37db2-343">-NotLike</span></span>

<span data-ttu-id="37db2-344">指出此 Cmdlet 會在屬性值與包含萬用字元的值不相符時取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-344">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="37db2-345">例如：`Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="37db2-345">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="37db2-346">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-347">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="37db2-347">-NotMatch</span></span>

<span data-ttu-id="37db2-348">指出當屬性值與指定的正則運算式不相符時，此 Cmdlet 會取得物件。</span><span class="sxs-lookup"><span data-stu-id="37db2-348">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="37db2-349">當輸入是純量時，相符的值會儲存在 `$Matches` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="37db2-349">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="37db2-350">例如：`Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="37db2-350">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="37db2-351">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-351">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-352">-Property</span><span class="sxs-lookup"><span data-stu-id="37db2-352">-Property</span></span>

<span data-ttu-id="37db2-353">指定物件屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="37db2-353">Specifies the name of an object property.</span></span> <span data-ttu-id="37db2-354">參數名稱（ **Property** ）是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="37db2-354">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="37db2-355">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-355">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37db2-356">-Value</span><span class="sxs-lookup"><span data-stu-id="37db2-356">-Value</span></span>

<span data-ttu-id="37db2-357">指定屬性值。</span><span class="sxs-lookup"><span data-stu-id="37db2-357">Specifies a property value.</span></span> <span data-ttu-id="37db2-358">參數名稱， **值** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="37db2-358">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="37db2-359">此參數與下列比較參數搭配使用時，可接受萬用字元：</span><span class="sxs-lookup"><span data-stu-id="37db2-359">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="37db2-360">**CLike**</span><span class="sxs-lookup"><span data-stu-id="37db2-360">**CLike**</span></span>
- <span data-ttu-id="37db2-361">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="37db2-361">**CNotLike**</span></span>
- <span data-ttu-id="37db2-362">**喜歡**</span><span class="sxs-lookup"><span data-stu-id="37db2-362">**Like**</span></span>
- <span data-ttu-id="37db2-363">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="37db2-363">**NotLike**</span></span>

<span data-ttu-id="37db2-364">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="37db2-364">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="37db2-365">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="37db2-365">CommonParameters</span></span>

<span data-ttu-id="37db2-366">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="37db2-366">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="37db2-367">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="37db2-367">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="37db2-368">輸入</span><span class="sxs-lookup"><span data-stu-id="37db2-368">INPUTS</span></span>

### <span data-ttu-id="37db2-369">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="37db2-369">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="37db2-370">您可以透過管道將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37db2-370">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="37db2-371">輸出</span><span class="sxs-lookup"><span data-stu-id="37db2-371">OUTPUTS</span></span>

### <span data-ttu-id="37db2-372">Object</span><span class="sxs-lookup"><span data-stu-id="37db2-372">Object</span></span>

<span data-ttu-id="37db2-373">此 Cmdlet 會從輸入物件集傳回選取的專案。</span><span class="sxs-lookup"><span data-stu-id="37db2-373">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="37db2-374">注意</span><span class="sxs-lookup"><span data-stu-id="37db2-374">NOTES</span></span>

<span data-ttu-id="37db2-375">從 Windows PowerShell 4.0 開始， `Where` 且已 `ForEach` 新增方法來與集合搭配使用。</span><span class="sxs-lookup"><span data-stu-id="37db2-375">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="37db2-376">您可以在這裡閱讀更多有關這些新方法的資訊 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="37db2-376">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="37db2-377">相關連結</span><span class="sxs-lookup"><span data-stu-id="37db2-377">RELATED LINKS</span></span>

[<span data-ttu-id="37db2-378">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-378">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="37db2-379">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-379">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="37db2-380">Group-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-380">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="37db2-381">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-381">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="37db2-382">New-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-382">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="37db2-383">Select-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-383">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="37db2-384">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-384">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="37db2-385">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="37db2-385">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)

