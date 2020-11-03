---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: c130feac876ff812a854d52961ba3141ba341af0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204612"
---
# <span data-ttu-id="40459-103">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-103">Get-PSBreakpoint</span></span>

## <span data-ttu-id="40459-104">概要</span><span class="sxs-lookup"><span data-stu-id="40459-104">SYNOPSIS</span></span>
<span data-ttu-id="40459-105">取得目前工作階段中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-105">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="40459-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="40459-106">SYNTAX</span></span>

### <span data-ttu-id="40459-107">Script (預設值)</span><span class="sxs-lookup"><span data-stu-id="40459-107">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="40459-108">變數</span><span class="sxs-lookup"><span data-stu-id="40459-108">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="40459-109">Command</span><span class="sxs-lookup"><span data-stu-id="40459-109">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="40459-110">類型</span><span class="sxs-lookup"><span data-stu-id="40459-110">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="40459-111">Id</span><span class="sxs-lookup"><span data-stu-id="40459-111">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="40459-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="40459-112">DESCRIPTION</span></span>

<span data-ttu-id="40459-113">**>disable-psbreakpoint 指令程式** 會取得在目前會話中設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-113">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="40459-114">您可以使用 Cmdlet 參數以取得特定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-114">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="40459-115">中斷點是命令或指令碼中的暫時停止執行點，用來讓您檢查指示。</span><span class="sxs-lookup"><span data-stu-id="40459-115">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="40459-116">**>disable-psbreakpoint** 是數個設計用來對 PowerShell 腳本和命令進行偵錯工具的 Cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="40459-116">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="40459-117">如需 PowerShell 偵錯工具的詳細資訊，請參閱 about_Debuggers。</span><span class="sxs-lookup"><span data-stu-id="40459-117">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="40459-118">範例</span><span class="sxs-lookup"><span data-stu-id="40459-118">EXAMPLES</span></span>

### <span data-ttu-id="40459-119">範例1：取得所有腳本和函式的所有中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-119">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="40459-120">此命令會取得在目前工作階段中之所有指令碼和函式上設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-120">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="40459-121">範例2：依識別碼取得中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-121">Example 2: Get breakpoints by ID</span></span>

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="40459-122">此命令會取得具有中斷點識別碼 2 的中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-122">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="40459-123">範例3：使用管線將識別碼傳送至 Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-123">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="40459-124">這些命令會顯示如何使用管線將中斷點識別碼傳送至 **>disable-psbreakpoint** ，以取得中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-124">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint** .</span></span>

<span data-ttu-id="40459-125">第一個命令會使用 Set-PSBreakpoint Cmdlet 在 Sample.ps1 指令碼中的 Increment 函式建立中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-125">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="40459-126">它會將中斷點物件儲存在 $B 變數中。</span><span class="sxs-lookup"><span data-stu-id="40459-126">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="40459-127">第二個命令使用點運算子 (. ) 取得 $B 變數中中斷點物件的 Id 屬性。</span><span class="sxs-lookup"><span data-stu-id="40459-127">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="40459-128">它使用管線運算子 (|) 將識別碼傳送至 **>disable-psbreakpoint** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40459-128">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="40459-129">因此， **>disable-psbreakpoint** 會取得具有指定識別碼的中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-129">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="40459-130">範例4：在指定的指令檔中取得中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-130">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="40459-131">此命令會取得 Sample.ps1 和 SupportScript.ps1 檔案中的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-131">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="40459-132">此命令不會取得其他腳本或會話中的函數所設定的其他中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-132">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="40459-133">範例5：在指定的 Cmdlet 中取得中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-133">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="40459-134">此命令會取得設定在 Sample.ps1 檔案之 Read-Host 或 Write-Host 命令上的所有命令中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-134">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="40459-135">範例6：在指定的檔案中取得命令中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-135">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="40459-136">此命令會取得 Sample.ps1 檔案中的所有命令中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-136">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="40459-137">範例7：依變數取得中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-137">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="40459-138">此命令會取得在目前會話中的 $Index 和 $Swap 變數上設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-138">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="40459-139">範例8：取得檔案中的所有行和變數中斷點</span><span class="sxs-lookup"><span data-stu-id="40459-139">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="40459-140">此命令會取得 Sample.ps1 指令碼中的所有行和變數中斷點。</span><span class="sxs-lookup"><span data-stu-id="40459-140">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="40459-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="40459-141">PARAMETERS</span></span>

### <span data-ttu-id="40459-142">-Command</span><span class="sxs-lookup"><span data-stu-id="40459-142">-Command</span></span>

<span data-ttu-id="40459-143">指定在指定的命令名稱上設定的命令中斷點陣列。</span><span class="sxs-lookup"><span data-stu-id="40459-143">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="40459-144">輸入命令名稱，例如 Cmdlet 或函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="40459-144">Enter the command names, such as the name of a cmdlet or function.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40459-145">-Id</span><span class="sxs-lookup"><span data-stu-id="40459-145">-Id</span></span>

<span data-ttu-id="40459-146">指定此 Cmdlet 取得的中斷點識別碼。</span><span class="sxs-lookup"><span data-stu-id="40459-146">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="40459-147">以逗號分隔的清單方式輸入識別碼。</span><span class="sxs-lookup"><span data-stu-id="40459-147">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="40459-148">您也可以透過管線將中斷點識別碼傳送至 **>disable-psbreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="40459-148">You can also pipe breakpoint IDs to **Get-PSBreakpoint** .</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40459-149">-Script</span><span class="sxs-lookup"><span data-stu-id="40459-149">-Script</span></span>

<span data-ttu-id="40459-150">指定包含中斷點之腳本的陣列。</span><span class="sxs-lookup"><span data-stu-id="40459-150">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="40459-151">輸入 (選用) 的路徑，以及一或多個腳本檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="40459-151">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="40459-152">若省略路徑，則預設位置為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="40459-152">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40459-153">-Type</span><span class="sxs-lookup"><span data-stu-id="40459-153">-Type</span></span>

<span data-ttu-id="40459-154">指定此 Cmdlet 取得之中斷點類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="40459-154">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="40459-155">輸入一個或多個類型。</span><span class="sxs-lookup"><span data-stu-id="40459-155">Enter one or more types.</span></span>
<span data-ttu-id="40459-156">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="40459-156">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="40459-157">線條</span><span class="sxs-lookup"><span data-stu-id="40459-157">Line</span></span>
- <span data-ttu-id="40459-158">Command</span><span class="sxs-lookup"><span data-stu-id="40459-158">Command</span></span>
- <span data-ttu-id="40459-159">變數</span><span class="sxs-lookup"><span data-stu-id="40459-159">Variable</span></span>

<span data-ttu-id="40459-160">您也可以透過管線將中斷點類型傳送至 **>disable-psbreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="40459-160">You can also pipe breakpoint types to **Get-PSBreakPoint** .</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="40459-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="40459-161">-Variable</span></span>

<span data-ttu-id="40459-162">指定在指定的變數名稱上設定的變數中斷點陣列。</span><span class="sxs-lookup"><span data-stu-id="40459-162">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="40459-163">輸入不含貨幣符號的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="40459-163">Enter the variable names without dollar signs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40459-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40459-164">CommonParameters</span></span>

<span data-ttu-id="40459-165">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="40459-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40459-166">如需詳細資訊，請參閱 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="40459-166">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40459-167">輸入</span><span class="sxs-lookup"><span data-stu-id="40459-167">INPUTS</span></span>

### <span data-ttu-id="40459-168">System.Int32、Microsoft.PowerShell.Commands.BreakpointType</span><span class="sxs-lookup"><span data-stu-id="40459-168">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="40459-169">您可以透過管線將中斷點識別碼和中斷點類型傳送至 **>disable-psbreakpoint** 。</span><span class="sxs-lookup"><span data-stu-id="40459-169">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint** .</span></span>

## <span data-ttu-id="40459-170">輸出</span><span class="sxs-lookup"><span data-stu-id="40459-170">OUTPUTS</span></span>

### <span data-ttu-id="40459-171">System.Management.Automation.Breakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-171">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="40459-172">**>disable-psbreakpoint** 會傳回代表會話中中斷點的物件。</span><span class="sxs-lookup"><span data-stu-id="40459-172">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="40459-173">注意</span><span class="sxs-lookup"><span data-stu-id="40459-173">NOTES</span></span>

* <span data-ttu-id="40459-174">您可以使用 **>disable-psbreakpoint** 或其別名 "gbp"。</span><span class="sxs-lookup"><span data-stu-id="40459-174">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="40459-175">相關連結</span><span class="sxs-lookup"><span data-stu-id="40459-175">RELATED LINKS</span></span>

[<span data-ttu-id="40459-176">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-176">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="40459-177">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-177">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="40459-178">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="40459-178">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="40459-179">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-179">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="40459-180">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="40459-180">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
