---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 9530e3bc15360245de334a6f45ff35883181a41e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203327"
---
# <span data-ttu-id="bf8c2-103">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-103">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="bf8c2-104">概要</span><span class="sxs-lookup"><span data-stu-id="bf8c2-104">SYNOPSIS</span></span>
<span data-ttu-id="bf8c2-105">在目前的主控台中啟用中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-105">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="bf8c2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf8c2-106">SYNTAX</span></span>

### <span data-ttu-id="bf8c2-107">Id (預設值)</span><span class="sxs-lookup"><span data-stu-id="bf8c2-107">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf8c2-108">中斷點</span><span class="sxs-lookup"><span data-stu-id="bf8c2-108">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="bf8c2-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bf8c2-109">DESCRIPTION</span></span>

<span data-ttu-id="bf8c2-110">此 `Enable-PSBreakpoint` Cmdlet 會重新啟用已停用的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-110">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="bf8c2-111">您可以使用它來啟用所有中斷點，或是藉由提供中斷點物件或識別碼來啟用特定中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-111">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="bf8c2-112">中斷點是腳本中的某個點，會暫時停止執行，讓您可以檢查腳本的狀態。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-112">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="bf8c2-113">新建立的中斷點會自動啟用，但可使用來停用 `Disable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-113">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="bf8c2-114">技術上來說，這個 Cmdlet 會將中斷點物件的 **Enabled** 屬性值變更為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-114">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True** .</span></span>

<span data-ttu-id="bf8c2-115">`Enable-PSBreakpoint` 是數個設計用來偵測 PowerShell 腳本的 Cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-115">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="bf8c2-116">如需 PowerShell 偵錯工具的詳細資訊，請參閱 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-116">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="bf8c2-117">範例</span><span class="sxs-lookup"><span data-stu-id="bf8c2-117">EXAMPLES</span></span>

### <span data-ttu-id="bf8c2-118">範例 1：啟用所有中斷點</span><span class="sxs-lookup"><span data-stu-id="bf8c2-118">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="bf8c2-119">此範例會啟用目前會話中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-119">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="bf8c2-120">使用別名時，此範例可以縮寫為 `gbp | ebp` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-120">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="bf8c2-121">範例 2：透過識別碼啟用中斷點</span><span class="sxs-lookup"><span data-stu-id="bf8c2-121">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="bf8c2-122">此範例會使用中斷點識別碼來啟用多個中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-122">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="bf8c2-123">範例 3：啟用停用的中斷點</span><span class="sxs-lookup"><span data-stu-id="bf8c2-123">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="bf8c2-124">此範例會重新啟用已停用的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-124">This example re-enables a breakpoint that has been disabled.</span></span>

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="bf8c2-125">`Set-PSBreakpoint`在腳本中，將 **Name** `Sample.ps1` 中斷點物件儲存在變數中的 Name 變數上建立中斷點 `$B` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-125">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="bf8c2-126">**PassThru** 參數會顯示中斷點的 **Enabled** 屬性值為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-126">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False** .</span></span>

<span data-ttu-id="bf8c2-127">`Enable-PSBreakpoint` 重新啟用中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-127">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="bf8c2-128">同樣地，使用 **PassThru** 參數時，會看到 **Enabled** 屬性的值為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-128">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True** .</span></span>

### <span data-ttu-id="bf8c2-129">範例 4：使用變數啟用中斷點</span><span class="sxs-lookup"><span data-stu-id="bf8c2-129">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="bf8c2-130">這個範例會使用中斷點物件來啟用一組中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-130">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="bf8c2-131">`Get-PSBreakpoint` 取得中斷點，並將它們儲存在 `$B` 變數中。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-131">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="bf8c2-132">使用 **中斷點** 參數 `Enable-PSBreakpoint` 可啟用中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-132">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="bf8c2-133">這個範例相當於正在執行 `Enable-PSBreakpoint -Id 3, 5` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-133">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="bf8c2-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf8c2-134">PARAMETERS</span></span>

### <span data-ttu-id="bf8c2-135">-Breakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-135">-Breakpoint</span></span>

<span data-ttu-id="bf8c2-136">指定要啟用的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-136">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="bf8c2-137">提供包含中斷點的變數，或提供可取得中斷點物件的命令（例如） `Get-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-137">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="bf8c2-138">您也可以透過管線將中斷點物件傳送至 `Enable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-138">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

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

### <span data-ttu-id="bf8c2-139">-Id</span><span class="sxs-lookup"><span data-stu-id="bf8c2-139">-Id</span></span>

<span data-ttu-id="bf8c2-140">指定要啟用之中斷點的 **識別碼** 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-140">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="bf8c2-141">預設值為所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-141">The default value is all breakpoints.</span></span>
<span data-ttu-id="bf8c2-142">依數位或在變數中提供 **識別碼** 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-142">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="bf8c2-143">您無法以管道傳送 **識別碼** 至 `Enable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-143">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="bf8c2-144">若要尋找中斷點的 **識別碼** ，請使用 `Get-PSBreakpoint` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-144">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

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

### <span data-ttu-id="bf8c2-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bf8c2-145">-PassThru</span></span>

<span data-ttu-id="bf8c2-146">傳回物件，表示要啟用的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-146">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="bf8c2-147">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-147">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf8c2-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bf8c2-148">-Confirm</span></span>

<span data-ttu-id="bf8c2-149">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bf8c2-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bf8c2-150">-WhatIf</span></span>

<span data-ttu-id="bf8c2-151">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bf8c2-152">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-152">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="bf8c2-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf8c2-153">CommonParameters</span></span>

<span data-ttu-id="bf8c2-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf8c2-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf8c2-156">輸入</span><span class="sxs-lookup"><span data-stu-id="bf8c2-156">INPUTS</span></span>

### <span data-ttu-id="bf8c2-157">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-157">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="bf8c2-158">您可以使用管線將中斷點物件傳送至 `Enable-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-158">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="bf8c2-159">輸出</span><span class="sxs-lookup"><span data-stu-id="bf8c2-159">OUTPUTS</span></span>

### <span data-ttu-id="bf8c2-160">無或 System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-160">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="bf8c2-161">當您使用 **PassThru** 參數時，會傳回 `Enable-PSBreakpoint` 代表已啟用之中斷點的中斷點物件。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-161">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="bf8c2-162">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-162">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="bf8c2-163">注意</span><span class="sxs-lookup"><span data-stu-id="bf8c2-163">NOTES</span></span>

- <span data-ttu-id="bf8c2-164">`Enable-PSBreakpoint`如果您嘗試啟用已啟用的中斷點，此 Cmdlet 並不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-164">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="bf8c2-165">因此，即使只有少數中斷點已停用，您也可以啟用所有中斷點而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-165">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="bf8c2-166">當您使用 Cmdlet 來建立中斷點時，中斷點就會啟用 `Set-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-166">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="bf8c2-167">您不需要啟用新建立的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bf8c2-167">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="bf8c2-168">相關連結</span><span class="sxs-lookup"><span data-stu-id="bf8c2-168">RELATED LINKS</span></span>

[<span data-ttu-id="bf8c2-169">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-169">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="bf8c2-170">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-170">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="bf8c2-171">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="bf8c2-171">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="bf8c2-172">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-172">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="bf8c2-173">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="bf8c2-173">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
