---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: b12913cd10c2c505322c1f922a05ecc98987e830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203164"
---
# <span data-ttu-id="ba301-103">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-103">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="ba301-104">概要</span><span class="sxs-lookup"><span data-stu-id="ba301-104">SYNOPSIS</span></span>
<span data-ttu-id="ba301-105">從目前的主控台刪除中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-105">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="ba301-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ba301-106">SYNTAX</span></span>

### <span data-ttu-id="ba301-107">中斷點 (預設值)</span><span class="sxs-lookup"><span data-stu-id="ba301-107">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ba301-108">Id</span><span class="sxs-lookup"><span data-stu-id="ba301-108">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ba301-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ba301-109">DESCRIPTION</span></span>
<span data-ttu-id="ba301-110">**Remove-PSBreakpoint** Cmdlet 會刪除中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-110">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="ba301-111">輸入中斷點物件或中斷點識別碼。</span><span class="sxs-lookup"><span data-stu-id="ba301-111">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="ba301-112">當您移除中斷點時，中斷點物件就無法再使用或運作。</span><span class="sxs-lookup"><span data-stu-id="ba301-112">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="ba301-113">如果您將中斷點物件儲存在變數中，參考仍然存在，但中斷點無法運作。</span><span class="sxs-lookup"><span data-stu-id="ba301-113">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="ba301-114">**Remove-PSBreakpoint** 是設計來對 Windows PowerShell 指令碼進行偵錯的數個 Cmdlet 其中之一。</span><span class="sxs-lookup"><span data-stu-id="ba301-114">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging Windows PowerShell scripts.</span></span>
<span data-ttu-id="ba301-115">如需有關 Windows PowerShell 偵錯工具的詳細資訊，請參閱 about_Debuggers。</span><span class="sxs-lookup"><span data-stu-id="ba301-115">For more information about the Windows PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="ba301-116">範例</span><span class="sxs-lookup"><span data-stu-id="ba301-116">EXAMPLES</span></span>

### <span data-ttu-id="ba301-117">範例 1：移除所有中斷點</span><span class="sxs-lookup"><span data-stu-id="ba301-117">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="ba301-118">這個命令會刪除目前主控台中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-118">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="ba301-119">範例 2：移除指定的中斷點</span><span class="sxs-lookup"><span data-stu-id="ba301-119">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="ba301-120">此命令會刪除中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-120">This command deletes a breakpoint.</span></span>

<span data-ttu-id="ba301-121">第一個命令使用 Set-PSBreakpoint Cmdlet 在 Sample.ps1 指令碼中的 Name 變數上建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="ba301-122">然後，它會將中斷點物件儲存在 $B 變數中。</span><span class="sxs-lookup"><span data-stu-id="ba301-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="ba301-123">第二個命令使用 **Remove-PSBreakpoint** Cmdlet 來刪除新的中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-123">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="ba301-124">它使用管線運算子 (|) 將 $B 變數中的中斷點物件傳送至 **Remove-PSBreakpoint** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba301-124">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="ba301-125">由於此命令，如果您執行此指令碼，它會不間斷執行直到完成。</span><span class="sxs-lookup"><span data-stu-id="ba301-125">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="ba301-126">此外， **Get-PSBreakpoint** Cmdlet 不會傳回此中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-126">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="ba301-127">範例 3︰依識別碼移除中斷點</span><span class="sxs-lookup"><span data-stu-id="ba301-127">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="ba301-128">此命令會刪除具有中斷點識別碼 2 的中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-128">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="ba301-129">範例 4︰使用函式來移除所有中斷點</span><span class="sxs-lookup"><span data-stu-id="ba301-129">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="ba301-130">這個簡單函式會刪除目前主控台中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-130">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="ba301-131">它會使用 Get-PSBreakpoint Cmdlet 取得中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-131">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="ba301-132">然後，它會使用管線運算子 (|) 將中斷點傳送至會刪除這些中斷點的 **Remove-PSBreakpoint** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba301-132">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="ba301-133">如此一來，您可以輸入 `del-psb`，而不是較長的命令。</span><span class="sxs-lookup"><span data-stu-id="ba301-133">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="ba301-134">如果要儲存函式，請將它新增到您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="ba301-134">To save the function, add it to your Windows PowerShell profile.</span></span>

## <span data-ttu-id="ba301-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ba301-135">PARAMETERS</span></span>

### <span data-ttu-id="ba301-136">-Breakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-136">-Breakpoint</span></span>
<span data-ttu-id="ba301-137">指定要刪除的中斷點。</span><span class="sxs-lookup"><span data-stu-id="ba301-137">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="ba301-138">輸入包含中斷點物件的變數，或輸入可取得中斷點物件的命令，例如 **>disable-psbreakpoint** 命令。</span><span class="sxs-lookup"><span data-stu-id="ba301-138">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="ba301-139">您也可以使用管線將中斷點物件傳送至 **Remove-PSBreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="ba301-139">You can also pipe breakpoint objects to **Remove-PSBreakpoint** .</span></span>

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ba301-140">-Id</span><span class="sxs-lookup"><span data-stu-id="ba301-140">-Id</span></span>
<span data-ttu-id="ba301-141">指定此 Cmdlet 刪除其中斷點的中斷點識別碼。</span><span class="sxs-lookup"><span data-stu-id="ba301-141">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ba301-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ba301-142">-Confirm</span></span>
<span data-ttu-id="ba301-143">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ba301-143">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba301-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ba301-144">-WhatIf</span></span>
<span data-ttu-id="ba301-145">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ba301-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ba301-146">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ba301-146">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ba301-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ba301-147">CommonParameters</span></span>
<span data-ttu-id="ba301-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ba301-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ba301-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ba301-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ba301-150">輸入</span><span class="sxs-lookup"><span data-stu-id="ba301-150">INPUTS</span></span>

### <span data-ttu-id="ba301-151">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-151">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="ba301-152">您可以使用管線將中斷點物件傳送至 **Remove-PSBreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="ba301-152">You can pipe breakpoint objects to **Remove-PSBreakpoint** .</span></span>

## <span data-ttu-id="ba301-153">輸出</span><span class="sxs-lookup"><span data-stu-id="ba301-153">OUTPUTS</span></span>

### <span data-ttu-id="ba301-154">無</span><span class="sxs-lookup"><span data-stu-id="ba301-154">None</span></span>
<span data-ttu-id="ba301-155">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ba301-155">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ba301-156">注意</span><span class="sxs-lookup"><span data-stu-id="ba301-156">NOTES</span></span>

## <span data-ttu-id="ba301-157">相關連結</span><span class="sxs-lookup"><span data-stu-id="ba301-157">RELATED LINKS</span></span>

[<span data-ttu-id="ba301-158">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-158">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="ba301-159">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-159">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="ba301-160">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-160">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="ba301-161">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="ba301-161">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="ba301-162">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ba301-162">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
