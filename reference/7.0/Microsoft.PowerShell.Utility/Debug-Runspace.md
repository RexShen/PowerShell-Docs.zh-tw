---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 1f347afe89ed63d64e8a8156b7259509800d5d24
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201331"
---
# <span data-ttu-id="f32dc-103">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="f32dc-103">Debug-Runspace</span></span>

## <span data-ttu-id="f32dc-104">概要</span><span class="sxs-lookup"><span data-stu-id="f32dc-104">SYNOPSIS</span></span>
<span data-ttu-id="f32dc-105">啟動具有運行空間的互動式偵錯工具會話。</span><span class="sxs-lookup"><span data-stu-id="f32dc-105">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="f32dc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f32dc-106">SYNTAX</span></span>

### <span data-ttu-id="f32dc-107">RunspaceParameterSet (預設) </span><span class="sxs-lookup"><span data-stu-id="f32dc-107">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f32dc-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f32dc-108">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f32dc-109">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f32dc-109">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f32dc-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f32dc-110">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f32dc-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f32dc-111">DESCRIPTION</span></span>

<span data-ttu-id="f32dc-112">`Debug-Runspace`Cmdlet 會啟動具有本機或遠端使用中運行空間的互動式偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f32dc-112">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="f32dc-113">您可以尋找您想要先執行的運行時， `Get-Process` 尋找與 PowerShell 相關聯的進程，然後 `Enter-PSHostProcess` 使用 **id** 參數中指定的處理序識別碼來附加至進程，然後 `Get-Runspace` 列出 PowerShell 主機進程內的執行程式。</span><span class="sxs-lookup"><span data-stu-id="f32dc-113">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="f32dc-114">當您選取要進行偵錯工具的執行時間時，如果執行時間目前正在執行命令或腳本，或腳本已在中斷點停止，則 PowerShell 會開啟該執行時間的遠端偵錯程式會話。</span><span class="sxs-lookup"><span data-stu-id="f32dc-114">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="f32dc-115">您可以用相同的方式，以調試遠端會話腳本的相同方式來偵測運行空間腳本。</span><span class="sxs-lookup"><span data-stu-id="f32dc-115">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="f32dc-116">如果您是執行進程之電腦的系統管理員，或您正在執行要進行偵錯工具的腳本，您只能附加至 PowerShell 主機進程。</span><span class="sxs-lookup"><span data-stu-id="f32dc-116">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="f32dc-117">此外，您無法輸入正在執行目前 PowerShell 會話的主機進程。</span><span class="sxs-lookup"><span data-stu-id="f32dc-117">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="f32dc-118">您只能輸入正在執行不同 PowerShell 會話的主機進程。</span><span class="sxs-lookup"><span data-stu-id="f32dc-118">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="f32dc-119">範例</span><span class="sxs-lookup"><span data-stu-id="f32dc-119">EXAMPLES</span></span>

### <span data-ttu-id="f32dc-120">範例1： Debug remote 運行空間</span><span class="sxs-lookup"><span data-stu-id="f32dc-120">Example 1: Debug a remote runspace</span></span>

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

<span data-ttu-id="f32dc-121">在此範例中，您會對在遠端電腦上開啟的運行空間進行 WS10TestServer 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f32dc-121">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="f32dc-122">在命令的第一行中，您會在 `Get-Process` 遠端電腦上執行，並篩選 Windows PowerShell 的主機進程。</span><span class="sxs-lookup"><span data-stu-id="f32dc-122">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="f32dc-123">在此範例中，您想要將處理序識別碼1152（Windows PowerShell ISE 的主機進程）進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f32dc-123">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="f32dc-124">在第二個命令中，您會執行 `Enter-PSSession` 以開啟 WS10TestServer 上的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="f32dc-124">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="f32dc-125">在第三個命令中，藉由執行來附加至遠端伺服器上執行的 Windows PowerShell ISE 主機進程， `Enter-PSHostProcess` 並指定您在第一個命令1152中取得之主機進程的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f32dc-125">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="f32dc-126">在第四個命令中，您可以藉由執行來列出處理序識別碼為1152的可用執行空間 `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="f32dc-126">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="f32dc-127">您會記下忙碌的運行空間的識別碼：它正在執行您想要進行偵錯工具的腳本。</span><span class="sxs-lookup"><span data-stu-id="f32dc-127">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="f32dc-128">在最後一個命令中，您會藉由新增 Id 參數，開始將執行腳本的已開啟執行時間（藉由執行 `Debug-Runspace` ，並依識別碼（2）識別 **Id** 執行時間）進行 TestWFVar1.ps1 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f32dc-128">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="f32dc-129">因為腳本中有一個中斷點，偵錯工具會開啟。</span><span class="sxs-lookup"><span data-stu-id="f32dc-129">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="f32dc-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f32dc-130">PARAMETERS</span></span>

### <span data-ttu-id="f32dc-131">-Id</span><span class="sxs-lookup"><span data-stu-id="f32dc-131">-Id</span></span>

<span data-ttu-id="f32dc-132">指定運行空間的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f32dc-132">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="f32dc-133">您可以執行 `Get-Runspace` 以顯示運行時識別碼。</span><span class="sxs-lookup"><span data-stu-id="f32dc-133">You can run `Get-Runspace` to show runspace IDs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f32dc-134">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f32dc-134">-InstanceId</span></span>

<span data-ttu-id="f32dc-135">依實例識別碼指定運行空間，這是您可以藉由執行來顯示的 GUID `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="f32dc-135">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f32dc-136">-Name</span><span class="sxs-lookup"><span data-stu-id="f32dc-136">-Name</span></span>

<span data-ttu-id="f32dc-137">依名稱指定運行時。</span><span class="sxs-lookup"><span data-stu-id="f32dc-137">Specifies a runspace by its name.</span></span> <span data-ttu-id="f32dc-138">您可以執行 `Get-Runspace` 以顯示執行空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="f32dc-138">You can run `Get-Runspace` to show the names of runspaces.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f32dc-139">-運行時</span><span class="sxs-lookup"><span data-stu-id="f32dc-139">-Runspace</span></span>

<span data-ttu-id="f32dc-140">指定運行時物件。</span><span class="sxs-lookup"><span data-stu-id="f32dc-140">Specifies a runspace object.</span></span> <span data-ttu-id="f32dc-141">為此參數提供值最簡單的方式，就是指定包含已篩選命令之結果的變數 `Get-Runspace` 。</span><span class="sxs-lookup"><span data-stu-id="f32dc-141">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f32dc-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f32dc-142">-Confirm</span></span>

<span data-ttu-id="f32dc-143">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f32dc-143">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f32dc-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f32dc-144">-WhatIf</span></span>

<span data-ttu-id="f32dc-145">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f32dc-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f32dc-146">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f32dc-146">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f32dc-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f32dc-147">CommonParameters</span></span>

<span data-ttu-id="f32dc-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f32dc-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f32dc-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f32dc-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f32dc-150">輸入</span><span class="sxs-lookup"><span data-stu-id="f32dc-150">INPUTS</span></span>

### <span data-ttu-id="f32dc-151">系統管理。運行空間</span><span class="sxs-lookup"><span data-stu-id="f32dc-151">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="f32dc-152">您可以使用管線將命令的結果傳送 `Get-Runspace` 至 **Debug-運行空間。**</span><span class="sxs-lookup"><span data-stu-id="f32dc-152">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="f32dc-153">輸出</span><span class="sxs-lookup"><span data-stu-id="f32dc-153">OUTPUTS</span></span>

## <span data-ttu-id="f32dc-154">注意</span><span class="sxs-lookup"><span data-stu-id="f32dc-154">NOTES</span></span>

<span data-ttu-id="f32dc-155">`Debug-Runspace` 適用于處於開啟狀態的工作空間。</span><span class="sxs-lookup"><span data-stu-id="f32dc-155">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="f32dc-156">如果運行時狀態從 [開啟] 變更為另一個狀態，則會自動從執行清單中移除該執行空間。</span><span class="sxs-lookup"><span data-stu-id="f32dc-156">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="f32dc-157">只有當運行空間符合下列準則時，才會將它新增至執行清單。</span><span class="sxs-lookup"><span data-stu-id="f32dc-157">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="f32dc-158">如果是來自 Invoke 命令，則為。也就是說，它有 `Invoke-Command` GUID 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f32dc-158">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="f32dc-159">如果來自 `Debug-Runspace` ，也就是它有 `Debug-Runspace` GUID 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f32dc-159">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="f32dc-160">如果是來自 PowerShell 工作流程，而且其工作流程工作識別碼與目前作用中的偵錯工具工作流程工作識別碼相同。</span><span class="sxs-lookup"><span data-stu-id="f32dc-160">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="f32dc-161">相關連結</span><span class="sxs-lookup"><span data-stu-id="f32dc-161">RELATED LINKS</span></span>

[<span data-ttu-id="f32dc-162">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="f32dc-162">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="f32dc-163">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="f32dc-163">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="f32dc-164">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="f32dc-164">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="f32dc-165">Get-Process</span><span class="sxs-lookup"><span data-stu-id="f32dc-165">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="f32dc-166">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f32dc-166">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="f32dc-167">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="f32dc-167">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)
