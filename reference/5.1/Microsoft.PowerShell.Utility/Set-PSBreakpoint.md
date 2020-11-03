---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5968c51f04199d59d3514cdc85ba3f15d02475a4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203139"
---
# <span data-ttu-id="cb5b1-103">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cb5b1-103">Set-PSBreakpoint</span></span>

## <span data-ttu-id="cb5b1-104">概要</span><span class="sxs-lookup"><span data-stu-id="cb5b1-104">SYNOPSIS</span></span>
<span data-ttu-id="cb5b1-105">在行、命令或變數上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-105">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="cb5b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cb5b1-106">SYNTAX</span></span>

### <span data-ttu-id="cb5b1-107">Line (預設值)</span><span class="sxs-lookup"><span data-stu-id="cb5b1-107">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="cb5b1-108">Command</span><span class="sxs-lookup"><span data-stu-id="cb5b1-108">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="cb5b1-109">變數</span><span class="sxs-lookup"><span data-stu-id="cb5b1-109">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="cb5b1-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb5b1-110">DESCRIPTION</span></span>

<span data-ttu-id="cb5b1-111">Cmdlet 會在 `Set-PSBreakpoint` 腳本中或在目前會話中執行的任何命令中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-111">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="cb5b1-112">在另一個中斷點停止時，您可以使用，在 `Set-PSBreakpoint` 執行腳本或執行命令之前，或在調試期間設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-112">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="cb5b1-113">`Set-PSBreakpoint` 無法在遠端電腦上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-113">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="cb5b1-114">若要在遠端電腦上執行指令碼偵錯，請將指令碼複製到本機電腦，然後在本機偵錯。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-114">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="cb5b1-115">每個 `Set-PSBreakpoint` 命令都會建立下列三種中斷點類型的其中一種：</span><span class="sxs-lookup"><span data-stu-id="cb5b1-115">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="cb5b1-116">行中斷點：在特定行和資料行座標上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-116">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="cb5b1-117">命令中斷點-在命令和函式上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-117">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="cb5b1-118">變數中斷點-在變數上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-118">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="cb5b1-119">您可以在單一命令中的多行、命令或變數上設定中斷點 `Set-PSBreakpoint` ，但每個 `Set-PSBreakpoint` 命令只會設定一種類型的中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-119">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="cb5b1-120">PowerShell 會在中斷點暫時停止執行，並將控制權交給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-120">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="cb5b1-121">命令提示字元會變更為 `DBG\>` ，而且會有一組偵錯工具命令可供使用。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-121">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="cb5b1-122">不過，您可以使用 **Action** 參數來指定替代回應，例如中斷點的條件或執行其他工作（例如記錄或診斷）的指示。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-122">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="cb5b1-123">此 `Set-PSBreakpoint` Cmdlet 是專為偵測 PowerShell 腳本而設計的數個 Cmdlet 之一。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-123">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="cb5b1-124">如需 PowerShell 偵錯工具的詳細資訊，請參閱 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-124">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="cb5b1-125">範例</span><span class="sxs-lookup"><span data-stu-id="cb5b1-125">EXAMPLES</span></span>

### <span data-ttu-id="cb5b1-126">範例1：在行上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-126">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="cb5b1-127">此範例會在 Sample.ps1 腳本中的第5行設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-127">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="cb5b1-128">當腳本執行時，會在執行第5行之前立即停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-128">When the script runs, execution stops immediately before line 5 would execute.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="cb5b1-129">當您以行號設定新的中斷點時，此 `Set-PSBreakpoint` Cmdlet 會產生行中斷點物件 ( **System.management.automation.linebreakpoint** ) ，其中包含中斷點識別碼和計數。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-129">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object ( **System.Management.Automation.LineBreakpoint** ) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="cb5b1-130">範例2：在函式上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-130">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="cb5b1-131">此範例會在 Sample.ps1 Cmdlet 的函式上建立命令中斷點 `Increment` 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-131">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="cb5b1-132">在每次呼叫指定函式之前，指令碼就會停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-132">The script stops executing immediately before each call to the specified function.</span></span>

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="cb5b1-133">結果就是一個命令中斷點物件。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-133">The result is a command breakpoint object.</span></span> <span data-ttu-id="cb5b1-134">在腳本執行之前， **擊中數** 屬性的值為0。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-134">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="cb5b1-135">範例3：在變數上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-135">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="cb5b1-136">這個範例會在 Sample.ps1 腳本的 **伺服器** 變數上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-136">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="cb5b1-137">它會使用值為 **ReadWrite** 的 **Mode** 參數，在讀取變數的值且剛好在值變更之前停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-137">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="cb5b1-138">範例4：在以指定文字開頭的每個命令上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-138">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="cb5b1-139">這個範例會在 Sample.ps1 腳本中的每個命令上設定一個中斷點，其開頭為 "write" （例如） `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-139">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="cb5b1-140">範例5：根據變數的值設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-140">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="cb5b1-141">此範例 `DiskTest` 只會在變數的值大於2時，才會在 Test.ps1 腳本的函式中停止執行 `$Disk` 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-141">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="cb5b1-142">**動作** 的值是腳本區塊，會測試函式中的變數值 `$Disk` 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-142">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="cb5b1-143">`break`如果符合條件，此動作會使用關鍵字來停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-143">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="cb5b1-144">替代 (和預設) **繼續** 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-144">The alternative (and the default) is **Continue** .</span></span>

### <span data-ttu-id="cb5b1-145">範例6：在函式上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-145">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="cb5b1-146">此範例會在函數上設定中斷點 `CheckLog` 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-146">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="cb5b1-147">因為命令並未指定指令碼，所以會在於目前工作階段中執行的任何項目上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-147">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="cb5b1-148">偵錯工具會在呼叫函式時中斷，而不是在宣告時中斷。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-148">The debugger breaks when the function is called, not when it is declared.</span></span>

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### <span data-ttu-id="cb5b1-149">範例7：在多行上設定中斷點</span><span class="sxs-lookup"><span data-stu-id="cb5b1-149">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="cb5b1-150">此範例會在 Sample.ps1 腳本中設定三個行中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-150">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="cb5b1-151">它會在指令碼中每一指定行上的欄位 2 位置設定一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-151">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="cb5b1-152">**Action** 參數中指定的動作會套用至所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-152">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## <span data-ttu-id="cb5b1-153">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cb5b1-153">PARAMETERS</span></span>

### <span data-ttu-id="cb5b1-154">-Action</span><span class="sxs-lookup"><span data-stu-id="cb5b1-154">-Action</span></span>

<span data-ttu-id="cb5b1-155">指定在每個中斷點執行的命令，而非中斷。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-155">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="cb5b1-156">輸入包含命令的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-156">Enter a script block that contains the commands.</span></span> <span data-ttu-id="cb5b1-157">您可以使用此參數設定條件式中斷點或執行其他工作，例如測試或記錄。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-157">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="cb5b1-158">如果省略此參數或未指定任何動作，就會在中斷點停止執行並啟動偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-158">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="cb5b1-159">使用 **action** 參數時，action 腳本區塊會在每個中斷點執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-159">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="cb5b1-160">除非指令碼區塊包含 Break 關鍵字，否則不會停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-160">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="cb5b1-161">如果您在指令碼區塊中使用 Continue 關鍵字，就會繼續執行到下一個中斷點為止。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-161">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="cb5b1-162">如需詳細資訊，請參閱 [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md)、 [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)和 [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-162">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb5b1-163">-Column</span><span class="sxs-lookup"><span data-stu-id="cb5b1-163">-Column</span></span>

<span data-ttu-id="cb5b1-164">指定指令碼檔案中，執行將停止之欄位的欄位編號。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-164">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="cb5b1-165">請只輸入一個欄位編號。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-165">Enter only one column number.</span></span> <span data-ttu-id="cb5b1-166">預設值為欄位 1。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-166">The default is column 1.</span></span>

<span data-ttu-id="cb5b1-167">資料行值會與 **Line** 參數的值搭配使用，以指定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-167">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="cb5b1-168">如果 **Line** 參數指定多行， **column** 參數會在每個指定行上的指定資料行上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-168">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="cb5b1-169">PowerShell 會在包含指定行和資料行位置之字元的語句或運算式之前停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-169">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="cb5b1-170">欄位是從左上角邊界處從欄位編號 1 (不是 0) 開始計算。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-170">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="cb5b1-171">如果您指定指令碼中不存在的欄位，系統並不會宣告錯誤，但中斷點永遠不會執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-171">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb5b1-172">-Command</span><span class="sxs-lookup"><span data-stu-id="cb5b1-172">-Command</span></span>

<span data-ttu-id="cb5b1-173">設定命令中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-173">Sets a command breakpoint.</span></span> <span data-ttu-id="cb5b1-174">輸入 Cmdlet 名稱，例如 `Get-Process` 或函數名稱。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-174">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="cb5b1-175">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-175">Wildcards are permitted.</span></span>

<span data-ttu-id="cb5b1-176">執行會在每個命令的每個執行個體執行之前停止。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-176">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="cb5b1-177">如果命令是函式，執行就會在每次呼叫函式時，以及在 BEGIN、PROCESS 及 END 區段中停止。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-177">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="cb5b1-178">-Line</span><span class="sxs-lookup"><span data-stu-id="cb5b1-178">-Line</span></span>

<span data-ttu-id="cb5b1-179">在指令碼中設定行中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-179">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="cb5b1-180">輸入一個或多個行編號，並使用逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-180">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="cb5b1-181">PowerShell 會在每個指定行開始執行語句之前立即停止。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-181">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="cb5b1-182">行是從指令碼檔案左上角邊界從行編號 1 (不是 0) 開始計算。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-182">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="cb5b1-183">如果您指定了空白行，執行就會在下一個非空白行之前停止。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-183">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="cb5b1-184">如果行超出範圍，就永遠不會命中中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-184">If the line is out of range, the breakpoint is never hit.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb5b1-185">-Mode</span><span class="sxs-lookup"><span data-stu-id="cb5b1-185">-Mode</span></span>

<span data-ttu-id="cb5b1-186">指定觸發變數中斷點的存取模式。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-186">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="cb5b1-187">預設值為 **Write** 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-187">The default is **Write** .</span></span>

<span data-ttu-id="cb5b1-188">只有當命令中使用 **Variable** 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-188">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="cb5b1-189">此模式適用於命令中設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-189">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="cb5b1-190">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="cb5b1-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cb5b1-191">在將新值寫入變數之前，立即進行 **寫入** -停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-191">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="cb5b1-192">讀取-在讀取變數時執行 **讀取** ，也就是在存取它的值時，要指派、顯示或使用這些變數的值。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-192">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="cb5b1-193">在讀取模式中，變數的值變更時不會停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-193">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="cb5b1-194">**ReadWrite** -在讀取或寫入變數時停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-194">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb5b1-195">-Script</span><span class="sxs-lookup"><span data-stu-id="cb5b1-195">-Script</span></span>

<span data-ttu-id="cb5b1-196">指定此 Cmdlet 在中設定中斷點的指令檔陣列。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-196">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="cb5b1-197">輸入一個或多個指令碼檔案的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-197">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="cb5b1-198">如果檔案是在目前的目錄中，您可以省略路徑。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-198">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="cb5b1-199">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-199">Wildcards are permitted.</span></span>

<span data-ttu-id="cb5b1-200">根據預設，會在於目前工作階段中執行的任何命令上設定變數中斷點與命令中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-200">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="cb5b1-201">只有設定行中斷點時才需要此參數。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-201">This parameter is required only when setting a line breakpoint.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb5b1-202">-Variable</span><span class="sxs-lookup"><span data-stu-id="cb5b1-202">-Variable</span></span>

<span data-ttu-id="cb5b1-203">指定此 Cmdlet 在上設定中斷點的變數陣列。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-203">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="cb5b1-204">輸入以逗號分隔的變數清單，而不使用貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-204">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="cb5b1-205">使用 **mode** 參數來判斷觸發中斷點的存取模式。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-205">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="cb5b1-206">預設模式 (Write) 會在將新值寫入變數之前停止執行。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-206">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cb5b1-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cb5b1-207">CommonParameters</span></span>

<span data-ttu-id="cb5b1-208">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cb5b1-209">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cb5b1-210">輸入</span><span class="sxs-lookup"><span data-stu-id="cb5b1-210">INPUTS</span></span>

### <span data-ttu-id="cb5b1-211">無</span><span class="sxs-lookup"><span data-stu-id="cb5b1-211">None</span></span>
<span data-ttu-id="cb5b1-212">您無法透過管道傳送輸入 `Set-PSBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-212">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="cb5b1-213">輸出</span><span class="sxs-lookup"><span data-stu-id="cb5b1-213">OUTPUTS</span></span>

### <span data-ttu-id="cb5b1-214">中斷點物件 (System.Management.Automation.LineBreakpoint、System.Management.Automation.VariableBreakpoint、System.Management.Automation.CommandBreakpoint)</span><span class="sxs-lookup"><span data-stu-id="cb5b1-214">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="cb5b1-215">`Set-PSBreakpoint` 傳回物件，表示它所設定的每一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-215">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="cb5b1-216">注意</span><span class="sxs-lookup"><span data-stu-id="cb5b1-216">NOTES</span></span>

- <span data-ttu-id="cb5b1-217">`Set-PSBreakpoint` 無法在遠端電腦上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-217">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="cb5b1-218">若要在遠端電腦上執行指令碼偵錯，請將指令碼複製到本機電腦，然後在本機偵錯。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-218">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="cb5b1-219">當您在一個以上的行、命令或變數上設定中斷點時，會 `Set-PSBreakpoint` 為每個專案產生中斷點物件。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-219">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="cb5b1-220">在命令提示字元設定函式或變數的中斷點時，您可以在建立函式或變數之前或之後設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="cb5b1-220">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="cb5b1-221">相關連結</span><span class="sxs-lookup"><span data-stu-id="cb5b1-221">RELATED LINKS</span></span>

[<span data-ttu-id="cb5b1-222">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cb5b1-222">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="cb5b1-223">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cb5b1-223">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="cb5b1-224">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cb5b1-224">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="cb5b1-225">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="cb5b1-225">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="cb5b1-226">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cb5b1-226">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)
