---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 905f3522a071fdd3f59d020b734c689a59e68a63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205127"
---
# <span data-ttu-id="30c00-103">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="30c00-103">Debug-Process</span></span>

## <span data-ttu-id="30c00-104">概要</span><span class="sxs-lookup"><span data-stu-id="30c00-104">SYNOPSIS</span></span>
<span data-ttu-id="30c00-105">偵錯本機電腦上執行的一或多個處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-105">Debugs one or more processes running on the local computer.</span></span>

## <span data-ttu-id="30c00-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30c00-106">SYNTAX</span></span>

### <span data-ttu-id="30c00-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="30c00-107">Name (Default)</span></span>

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="30c00-108">Id</span><span class="sxs-lookup"><span data-stu-id="30c00-108">Id</span></span>

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="30c00-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="30c00-109">InputObject</span></span>

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="30c00-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="30c00-110">DESCRIPTION</span></span>

<span data-ttu-id="30c00-111">**調試** 程式 Cmdlet 會將偵錯工具附加到本機電腦上的一或多個執行中處理常式。</span><span class="sxs-lookup"><span data-stu-id="30c00-111">The **Debug-Process** cmdlet attaches a debugger to one or more running processes on a local computer.</span></span>
<span data-ttu-id="30c00-112">您可以依處理程序名稱或處理程序識別碼 (PID) 來指定處理程序，或使用管線將處理程序物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c00-112">You can specify the processes by their process name or process ID (PID), or you can pipe process objects to this cmdlet.</span></span>

<span data-ttu-id="30c00-113">此 Cmdlet 會附加目前針對該處理程序註冊的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="30c00-113">This cmdlet attaches the debugger that is currently registered for the process.</span></span>
<span data-ttu-id="30c00-114">開始使用這個 Cmdlet 之前，請先確認已下載並正確設定偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="30c00-114">Before using this cmdlet, verify that a debugger is downloaded and correctly configured.</span></span>

## <span data-ttu-id="30c00-115">範例</span><span class="sxs-lookup"><span data-stu-id="30c00-115">EXAMPLES</span></span>

### <span data-ttu-id="30c00-116">範例 1︰將偵錯工具附加到電腦上的處理程序</span><span class="sxs-lookup"><span data-stu-id="30c00-116">Example 1: Attach a debugger to a process on the computer</span></span>

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

<span data-ttu-id="30c00-117">此命令將偵錯工具附加到電腦上的 PowerShell 處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-117">This command attaches a debugger to the PowerShell process on the computer.</span></span>

### <span data-ttu-id="30c00-118">範例 2︰將偵錯工具附加到以指定字串開頭的所有處理程序</span><span class="sxs-lookup"><span data-stu-id="30c00-118">Example 2: Attach a debugger to all processes that begin with the specified string</span></span>

```
PS C:\> Debug-Process -Name "SQL*"
```

<span data-ttu-id="30c00-119">此命令會將偵錯工具附加到名稱開頭為 SQL 的所有處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-119">This command attaches a debugger to all processes that have names that begin with SQL.</span></span>

### <span data-ttu-id="30c00-120">範例 3︰將偵錯工具附加到多個處理程序</span><span class="sxs-lookup"><span data-stu-id="30c00-120">Example 3: Attach a debugger to multiple processes</span></span>

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

<span data-ttu-id="30c00-121">此命令將偵錯工具附加到 Winlogon、Explorer 及 Outlook 處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-121">This command attaches a debugger to the Winlogon, Explorer, and Outlook processes.</span></span>

### <span data-ttu-id="30c00-122">範例 4︰將偵錯工具附加到多個處理程序識別碼</span><span class="sxs-lookup"><span data-stu-id="30c00-122">Example 4: Attach a debugger to multiple process IDs</span></span>

```
PS C:\> Debug-Process -Id 1132, 2028
```

<span data-ttu-id="30c00-123">此命令將偵錯工具附加到處理程序識別碼為 1132 和 2028 的處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-123">This command attaches a debugger to the processes that have process IDs 1132 and 2028.</span></span>

### <span data-ttu-id="30c00-124">範例 5︰使用 Get-Process 取得處理程序，然後將偵錯工具附加到其中</span><span class="sxs-lookup"><span data-stu-id="30c00-124">Example 5: Use Get-Process to get a process then attach a debugger to it</span></span>

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

<span data-ttu-id="30c00-125">此命令將偵錯工具附加到電腦上的 PowerShell 處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-125">This command attaches a debugger to the PowerShell processes on the computer.</span></span>
<span data-ttu-id="30c00-126">它會使用 **取得程式** Cmdlet 取得電腦上的 PowerShell 處理常式，並使用管線運算子 (|) 將進程傳送至 **Debug 進程** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c00-126">It uses the **Get-Process** cmdlet to get the PowerShell processes on the computer, and it uses a pipeline operator (|) to send the processes to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="30c00-127">若要指定特定的 PowerShell 處理常式，請使用 **Get 進程** 的 ID 參數。</span><span class="sxs-lookup"><span data-stu-id="30c00-127">To specify a particular PowerShell process, use the ID parameter of **Get-Process** .</span></span>

### <span data-ttu-id="30c00-128">範例 6︰將偵錯工具附加到本機電腦上目前的處理程序</span><span class="sxs-lookup"><span data-stu-id="30c00-128">Example 6: Attach a debugger to a current process on the local computer</span></span>

```
PS C:\> $PID | Debug-Process
```

<span data-ttu-id="30c00-129">此命令將偵錯工具附加到電腦上目前的 PowerShell 處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-129">This command attaches a debugger to the current PowerShell processes on the computer.</span></span>

<span data-ttu-id="30c00-130">此命令會使用 $PID 自動變數，其中包含目前 PowerShell 進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="30c00-130">The command uses the $PID automatic variable, which contains the process ID of the current PowerShell process.</span></span>
<span data-ttu-id="30c00-131">然後，它會使用管線運算子 (|) 將處理序識別碼傳送至 **Debug 進程** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c00-131">Then, it uses a pipeline operator (|) to send the process ID to the **Debug-Process** cmdlet.</span></span>

<span data-ttu-id="30c00-132">如需 $PID 自動變數的詳細資訊，請參閱 about_Automatic_Variables。</span><span class="sxs-lookup"><span data-stu-id="30c00-132">For more information about the $PID automatic variable, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="30c00-133">範例7：將偵錯工具附加至使用 InputObject 參數的進程</span><span class="sxs-lookup"><span data-stu-id="30c00-133">Example 7: Attach a debugger to a process that uses the InputObject parameter</span></span>

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

<span data-ttu-id="30c00-134">此命令將偵錯工具附加到本機電腦上的 PowerShell 處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-134">This command attaches a debugger to the PowerShell processes on the local computer.</span></span>

<span data-ttu-id="30c00-135">第一個命令會使用 **取得程式** Cmdlet 取得電腦上的 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="30c00-135">The first command uses the **Get-Process** cmdlet to get the PowerShell processes on the computer.</span></span>
<span data-ttu-id="30c00-136">它會將產生的處理程序物件儲存在 $P 變數中。</span><span class="sxs-lookup"><span data-stu-id="30c00-136">It saves the resulting process object in the variable named $P.</span></span>

<span data-ttu-id="30c00-137">第二個命令會使用 **Debug-Process** 的 *InputObject* 參數，來提交 $P 變數中的處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="30c00-137">The second command uses the *InputObject* parameter of the **Debug-Process** cmdlet to submit the process object in the $P variable.</span></span>

## <span data-ttu-id="30c00-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="30c00-138">PARAMETERS</span></span>

### <span data-ttu-id="30c00-139">-Id</span><span class="sxs-lookup"><span data-stu-id="30c00-139">-Id</span></span>

<span data-ttu-id="30c00-140">指定要進行偵錯之處理程序的處理程序識別碼。</span><span class="sxs-lookup"><span data-stu-id="30c00-140">Specifies the process IDs of the processes to be debugged.</span></span>
<span data-ttu-id="30c00-141">*Id* 參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="30c00-141">The *Id* parameter name is optional.</span></span>

<span data-ttu-id="30c00-142">若要尋找處理程序的處理程序識別碼，請輸入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="30c00-142">To find the process ID of a process, type `Get-Process`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30c00-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="30c00-143">-InputObject</span></span>

<span data-ttu-id="30c00-144">指定代表要進行偵錯之處理程序的處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="30c00-144">Specifies the process objects that represent processes to be debugged.</span></span>
<span data-ttu-id="30c00-145">輸入包含處理程序物件的變數，或輸入可取得處理程序物件的命令，例如 Get-Process Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c00-145">Enter a variable that contains the process objects or a command that gets the process objects, such as the Get-Process cmdlet.</span></span>
<span data-ttu-id="30c00-146">您也可以使用管線將處理程序物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c00-146">You can also pipe process objects to this cmdlet.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="30c00-147">-Name</span><span class="sxs-lookup"><span data-stu-id="30c00-147">-Name</span></span>

<span data-ttu-id="30c00-148">指定要進行偵錯之處理程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="30c00-148">Specifies the names of the processes to be debugged.</span></span>
<span data-ttu-id="30c00-149">如果有多個處理程序具有相同的名稱，此 Cmdlet 會將偵錯工具附加到具有該名稱的所有處理程序。</span><span class="sxs-lookup"><span data-stu-id="30c00-149">If there is more than one process with the same name, this cmdlet attaches a debugger to all processes with that name.</span></span>
<span data-ttu-id="30c00-150">*Name* 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="30c00-150">The *Name* parameter is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30c00-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="30c00-151">-Confirm</span></span>

<span data-ttu-id="30c00-152">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="30c00-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="30c00-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="30c00-153">-WhatIf</span></span>

<span data-ttu-id="30c00-154">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="30c00-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="30c00-155">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="30c00-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="30c00-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30c00-156">CommonParameters</span></span>

<span data-ttu-id="30c00-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="30c00-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30c00-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="30c00-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30c00-159">輸入</span><span class="sxs-lookup"><span data-stu-id="30c00-159">INPUTS</span></span>

### <span data-ttu-id="30c00-160">System.Int32、System.Diagnostics.Process、System.String</span><span class="sxs-lookup"><span data-stu-id="30c00-160">System.Int32, System.Diagnostics.Process, System.String</span></span>

<span data-ttu-id="30c00-161">您可以使用管線將處理程序識別碼 (Int32)、處理程序物件 (System.Diagnostics.Process) 或處理程序名稱 (String) 傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="30c00-161">You can pipe a process ID (Int32), a process object (System.Diagnostics.Process), or a process name (String) to this cmdlet.</span></span>

## <span data-ttu-id="30c00-162">輸出</span><span class="sxs-lookup"><span data-stu-id="30c00-162">OUTPUTS</span></span>

### <span data-ttu-id="30c00-163">無</span><span class="sxs-lookup"><span data-stu-id="30c00-163">None</span></span>

<span data-ttu-id="30c00-164">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="30c00-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="30c00-165">注意</span><span class="sxs-lookup"><span data-stu-id="30c00-165">NOTES</span></span>

* <span data-ttu-id="30c00-166">此 Cmdlet 會使用 Windows Management Instrumentation (WMI) Win32_Process 類別的 AttachDebugger 方法。</span><span class="sxs-lookup"><span data-stu-id="30c00-166">This cmdlet uses the AttachDebugger method of the Windows Management Instrumentation (WMI) Win32_Process class.</span></span> <span data-ttu-id="30c00-167">如需此方法的詳細資訊，請參閱 MSDN library 中的 [AttachDebugger 方法](https://go.microsoft.com/fwlink/?LinkId=143640) 。</span><span class="sxs-lookup"><span data-stu-id="30c00-167">For more information about this method, see [AttachDebugger method](https://go.microsoft.com/fwlink/?LinkId=143640) in the MSDN library.</span></span>

## <span data-ttu-id="30c00-168">相關連結</span><span class="sxs-lookup"><span data-stu-id="30c00-168">RELATED LINKS</span></span>

[<span data-ttu-id="30c00-169">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="30c00-169">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="30c00-170">Get-Process</span><span class="sxs-lookup"><span data-stu-id="30c00-170">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="30c00-171">Start-Process</span><span class="sxs-lookup"><span data-stu-id="30c00-171">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="30c00-172">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="30c00-172">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="30c00-173">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="30c00-173">Wait-Process</span></span>](Wait-Process.md)

