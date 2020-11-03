---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 66ef0cec2bfdb1aa70b97001830811f68c68b911
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204672"
---
# <span data-ttu-id="7340a-103">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-103">Disable-PSBreakpoint</span></span>

## <span data-ttu-id="7340a-104">概要</span><span class="sxs-lookup"><span data-stu-id="7340a-104">SYNOPSIS</span></span>
<span data-ttu-id="7340a-105">在目前的主控台中停用中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-105">Disables the breakpoints in the current console.</span></span>

## <span data-ttu-id="7340a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7340a-106">SYNTAX</span></span>

### <span data-ttu-id="7340a-107">中斷點 (預設值)</span><span class="sxs-lookup"><span data-stu-id="7340a-107">Breakpoint (Default)</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7340a-108">Id</span><span class="sxs-lookup"><span data-stu-id="7340a-108">Id</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7340a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7340a-109">DESCRIPTION</span></span>

<span data-ttu-id="7340a-110">**>disable-psbreakpoint 指令程式** 會停用中斷點，以確保在執行腳本時不會叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-110">The **Disable-PSBreakpoint** cmdlet disables breakpoints, which assures that they are not hit when the script runs.</span></span>
<span data-ttu-id="7340a-111">您可以使用它來停用所有中斷點，或是藉由送出中斷點物件或中斷點識別碼來指定中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-111">You can use it to disable all breakpoints, or you can specify breakpoints by submitting breakpoint objects or breakpoint IDs.</span></span>

<span data-ttu-id="7340a-112">就技術上來說，這個 Cmdlet 會將中斷點物件的 Enabled 屬性值變更為 False。</span><span class="sxs-lookup"><span data-stu-id="7340a-112">Technically, this cmdlet changes the value of the Enabled property of a breakpoint object to False.</span></span>
<span data-ttu-id="7340a-113">如果要重新啟用中斷點，請使用 Enable-PSBreakpoint Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7340a-113">To re-enable a breakpoint, use the Enable-PSBreakpoint cmdlet.</span></span>
<span data-ttu-id="7340a-114">使用 Set-PSBreakpoint Cmdlet 來建立中斷點時，中斷點預設會處於已啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="7340a-114">Breakpoints are enabled by default when you create them by using the Set-PSBreakpoint cmdlet.</span></span>

<span data-ttu-id="7340a-115">中斷點是指令碼中的暫時停止執行點，用來讓您檢查指令碼中的指示。</span><span class="sxs-lookup"><span data-stu-id="7340a-115">A breakpoint is a point in a script where execution stops temporarily so that you can examine the instructions in the script.</span></span>
<span data-ttu-id="7340a-116">**>disable-psbreakpoint** 是針對將 PowerShell 腳本進行偵錯工具設計的數個 Cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="7340a-116">**Disable-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="7340a-117">如需 PowerShell 偵錯工具的詳細資訊，請參閱 about_Debuggers。</span><span class="sxs-lookup"><span data-stu-id="7340a-117">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="7340a-118">範例</span><span class="sxs-lookup"><span data-stu-id="7340a-118">EXAMPLES</span></span>

### <span data-ttu-id="7340a-119">範例1：設定中斷點並停用它</span><span class="sxs-lookup"><span data-stu-id="7340a-119">Example 1: Set a breakpoint and disable it</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

<span data-ttu-id="7340a-120">這些命令會停用新建的中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-120">These commands disable a newly-created breakpoint.</span></span>

<span data-ttu-id="7340a-121">第一個命令會使用 Set-PSBreakpoint Cmdlet，在 Sample.ps1 腳本中的 *Name* 變數上建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the *Name* variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="7340a-122">然後，它會將中斷點物件儲存在 $B 變數中。</span><span class="sxs-lookup"><span data-stu-id="7340a-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="7340a-123">第二個命令使用 **>disable-psbreakpoint** Cmdlet 來停用新的中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-123">The second command uses the **Disable-PSBreakpoint** cmdlet to disable the new breakpoint.</span></span>
<span data-ttu-id="7340a-124">它使用管線運算子 (|) 將 $B 中的中斷點物件傳送至 **>disable-psbreakpoint** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7340a-124">It uses a pipeline operator (|) to send the breakpoint object in $B to the **Disable-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="7340a-125">這項命令的結果，$B 中中斷點物件的 Enabled 屬性值為 False。</span><span class="sxs-lookup"><span data-stu-id="7340a-125">As a result of this command, the value of the Enabled property of the breakpoint object in $B is False.</span></span>

### <span data-ttu-id="7340a-126">範例2：停用中斷點</span><span class="sxs-lookup"><span data-stu-id="7340a-126">Example 2: Disable a breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Id 0
```

<span data-ttu-id="7340a-127">此命令停用具有中斷點識別碼 0 的中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-127">This command disables the breakpoint with breakpoint ID 0.</span></span>

### <span data-ttu-id="7340a-128">範例3：建立已停用的中斷點</span><span class="sxs-lookup"><span data-stu-id="7340a-128">Example 3: Create a disabled breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

<span data-ttu-id="7340a-129">此命令建立新的中斷點，在您啟用之前它會是停用的。</span><span class="sxs-lookup"><span data-stu-id="7340a-129">This command creates a new breakpoint that is disabled until you enable it.</span></span>

<span data-ttu-id="7340a-130">它會使用 **>disable-psbreakpoint** Cmdlet 來停用中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-130">It uses the **Disable-PSBreakpoint** cmdlet to disable the breakpoint.</span></span>
<span data-ttu-id="7340a-131">*中斷點* 參數的值是設定新中斷點、產生中斷點物件，並將物件儲存在 $B 變數中的 Set-PSBreakpoint 命令。</span><span class="sxs-lookup"><span data-stu-id="7340a-131">The value of the *Breakpoint* parameter is a Set-PSBreakpoint command that sets a new breakpoint, generates a breakpoint object, and saves the object in the $B variable.</span></span>

<span data-ttu-id="7340a-132">以物件為其值的 Cmdlet 參數可接受包含物件的變數，或是取得或產生物件的命令。</span><span class="sxs-lookup"><span data-stu-id="7340a-132">Cmdlet parameters that take objects as their values can accept a variable that contains the object or a command that gets or generates the object.</span></span>
<span data-ttu-id="7340a-133">在此情況下，由於 **>disable-psbreakpoint** 會產生中斷點物件，因此它可以當做 *中斷點* 參數的值使用。</span><span class="sxs-lookup"><span data-stu-id="7340a-133">In this case, because **Set-PSBreakpoint** generates a breakpoint object, it can be used as the value of the *Breakpoint* parameter.</span></span>

<span data-ttu-id="7340a-134">第二個命令會在 $B 變數的值中顯示中斷點物件。</span><span class="sxs-lookup"><span data-stu-id="7340a-134">The second command displays the breakpoint object in the value of the $B variable.</span></span>

### <span data-ttu-id="7340a-135">範例4：停用目前主控台中的所有中斷點</span><span class="sxs-lookup"><span data-stu-id="7340a-135">Example 4: Disable all breakpoints in the current console</span></span>

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

<span data-ttu-id="7340a-136">此命令停用目前主控台中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-136">This command disables all breakpoints in the current console.</span></span>
<span data-ttu-id="7340a-137">您可以將此命令縮寫為："gbp | dbp"。</span><span class="sxs-lookup"><span data-stu-id="7340a-137">You can abbreviate this command as: "gbp | dbp".</span></span>

## <span data-ttu-id="7340a-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7340a-138">PARAMETERS</span></span>

### <span data-ttu-id="7340a-139">-Breakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-139">-Breakpoint</span></span>

<span data-ttu-id="7340a-140">指定要停用的中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-140">Specifies the breakpoints to disable.</span></span>
<span data-ttu-id="7340a-141">請輸入包含中斷點物件的變數，或可取得中斷點物件的命令，例如 Get-PSBreakpoint 命令。</span><span class="sxs-lookup"><span data-stu-id="7340a-141">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a Get-PSBreakpoint command.</span></span>
<span data-ttu-id="7340a-142">您也可以透過管線將中斷點物件傳送至 **>disable-psbreakpoint** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7340a-142">You can also pipe breakpoint objects to the **Disable-PSBreakpoint** cmdlet.</span></span>

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

### <span data-ttu-id="7340a-143">-Id</span><span class="sxs-lookup"><span data-stu-id="7340a-143">-Id</span></span>

<span data-ttu-id="7340a-144">停用具有指定之中斷點識別碼的中斷點。</span><span class="sxs-lookup"><span data-stu-id="7340a-144">Disables the breakpoints with the specified breakpoint IDs.</span></span>
<span data-ttu-id="7340a-145">請輸入識別碼或包含識別碼的變數。</span><span class="sxs-lookup"><span data-stu-id="7340a-145">Enter the IDs or a variable that contains the IDs.</span></span>
<span data-ttu-id="7340a-146">您無法透過管線將識別碼傳送至 **停用->disable-psbreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="7340a-146">You cannot pipe IDs to **Disable-PSBreakpoint** .</span></span>

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

### <span data-ttu-id="7340a-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7340a-147">-PassThru</span></span>

<span data-ttu-id="7340a-148">傳回代表已啟用之中斷點的物件。</span><span class="sxs-lookup"><span data-stu-id="7340a-148">Returns an object representing the enabled breakpoints.</span></span>
<span data-ttu-id="7340a-149">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="7340a-149">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7340a-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7340a-150">-Confirm</span></span>

<span data-ttu-id="7340a-151">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="7340a-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7340a-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7340a-152">-WhatIf</span></span>

<span data-ttu-id="7340a-153">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="7340a-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7340a-154">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="7340a-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7340a-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7340a-155">CommonParameters</span></span>

<span data-ttu-id="7340a-156">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7340a-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7340a-157">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7340a-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7340a-158">輸入</span><span class="sxs-lookup"><span data-stu-id="7340a-158">INPUTS</span></span>

### <span data-ttu-id="7340a-159">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-159">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="7340a-160">您可以使用管線將中斷點物件傳送至 **停用->disable-psbreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="7340a-160">You can pipe a breakpoint object to **Disable-PSBreakpoint** .</span></span>

## <span data-ttu-id="7340a-161">輸出</span><span class="sxs-lookup"><span data-stu-id="7340a-161">OUTPUTS</span></span>

### <span data-ttu-id="7340a-162">無或 System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-162">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="7340a-163">當您使用 *PassThru* 參數時， **>disable-psbreakpoint** 會傳回代表已停用之中斷點的物件。</span><span class="sxs-lookup"><span data-stu-id="7340a-163">When you use the *PassThru* parameter, **Disable-PSBreakpoint** returns an object that represents the disabled breakpoint.</span></span>
<span data-ttu-id="7340a-164">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="7340a-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7340a-165">注意</span><span class="sxs-lookup"><span data-stu-id="7340a-165">NOTES</span></span>

## <span data-ttu-id="7340a-166">相關連結</span><span class="sxs-lookup"><span data-stu-id="7340a-166">RELATED LINKS</span></span>

[<span data-ttu-id="7340a-167">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-167">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="7340a-168">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-168">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="7340a-169">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="7340a-169">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="7340a-170">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-170">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="7340a-171">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="7340a-171">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
