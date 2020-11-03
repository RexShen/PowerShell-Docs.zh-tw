---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 4efa22e8f2a7339e381d92270c1b127054c219cb
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2020
ms.locfileid: "93206288"
---
# <span data-ttu-id="d8ce4-103">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-103">Stop-Process</span></span>

## <span data-ttu-id="d8ce4-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8ce4-104">SYNOPSIS</span></span>
<span data-ttu-id="d8ce4-105">停止一或多個執行中的處理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-105">Stops one or more running processes.</span></span>

## <span data-ttu-id="d8ce4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8ce4-106">SYNTAX</span></span>

### <span data-ttu-id="d8ce4-107">Id (預設值)</span><span class="sxs-lookup"><span data-stu-id="d8ce4-107">Id (Default)</span></span>

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d8ce4-108">Name</span><span class="sxs-lookup"><span data-stu-id="d8ce4-108">Name</span></span>

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d8ce4-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="d8ce4-109">InputObject</span></span>

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d8ce4-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8ce4-110">DESCRIPTION</span></span>

<span data-ttu-id="d8ce4-111">**停止進程指令程式** 會停止一或多個正在執行的進程。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-111">The **Stop-Process** cmdlet stops one or more running processes.</span></span>
<span data-ttu-id="d8ce4-112">您可以依處理常式名稱或處理序識別碼 (PID) 來指定處理常式，或將處理常式物件傳遞至 **停止進程** 。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-112">You can specify a process by process name or process ID (PID), or pass a process object to **Stop-Process** .</span></span>
<span data-ttu-id="d8ce4-113">**停止進程** 只能在本機電腦上執行的進程上運作。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-113">**Stop-Process** works only on processes running on the local computer.</span></span>

<span data-ttu-id="d8ce4-114">在 Windows Vista 和更新版本的 Windows 作業系統上，若要停止不是目前使用者擁有的處理常式，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-114">On Windows Vista and later versions of the Windows operating system, to stop a process that is not owned by the current user, you must start PowerShell by using the Run as administrator option.</span></span>
<span data-ttu-id="d8ce4-115">此外，除非您指定 *Confirm* 參數，否則系統不會提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-115">Also, you are not prompted for confirmation unless you specify the *Confirm* parameter.</span></span>

## <span data-ttu-id="d8ce4-116">範例</span><span class="sxs-lookup"><span data-stu-id="d8ce4-116">EXAMPLES</span></span>

### <span data-ttu-id="d8ce4-117">範例1：停止進程的所有實例</span><span class="sxs-lookup"><span data-stu-id="d8ce4-117">Example 1: Stop all instances of a process</span></span>

```
PS C:\> Stop-Process -Name "notepad"
```

<span data-ttu-id="d8ce4-118">此命令會停止電腦上記事本處理程序的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-118">This command stops all instances of the Notepad process on the computer.</span></span>
<span data-ttu-id="d8ce4-119">記事本的每個實例會在自己的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-119">Each instance of Notepad runs in its own process.</span></span>
<span data-ttu-id="d8ce4-120">它會使用 *Name* 參數來指定處理常式，這些處理常式全都具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-120">It uses the *Name* parameter to specify the processes, all of which have the same name.</span></span>
<span data-ttu-id="d8ce4-121">如果您要使用 *Id* 參數來停止相同的處理常式，則必須列出每個 [記事本] 實例的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-121">If you were to use the *Id* parameter to stop the same processes, you would have to list the process IDs of each instance of Notepad.</span></span>

### <span data-ttu-id="d8ce4-122">範例2：停止進程的特定實例</span><span class="sxs-lookup"><span data-stu-id="d8ce4-122">Example 2: Stop a specific instance of a process</span></span>

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

<span data-ttu-id="d8ce4-123">此命令會停止記事本處理程序的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-123">This command stops a particular instance of the Notepad process.</span></span>
<span data-ttu-id="d8ce4-124">它會使用處理程序識別碼 3952 來識別處理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-124">It uses the process ID, 3952, to identify the process.</span></span>
<span data-ttu-id="d8ce4-125">*Confirm* 參數會指示 PowerShell 在停止進程之前提示您。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-125">The *Confirm* parameter directs PowerShell to prompt you before it stops the process.</span></span>
<span data-ttu-id="d8ce4-126">因為提示中包括程式 namein 的識別碼，所以這是最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-126">Because the prompt includes the process namein addition to its ID, this is best practice.</span></span>
<span data-ttu-id="d8ce4-127">*PassThru* 參數會將處理常式物件傳遞給格式器以供顯示。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-127">The *PassThru* parameter passes the process object to the formatter for display.</span></span>
<span data-ttu-id="d8ce4-128">如果沒有這個參數，就不會在 **停止進程** 命令之後顯示。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-128">Without this parameter, there would be no display after a **Stop-Process** command.</span></span>

### <span data-ttu-id="d8ce4-129">範例3：停止進程並偵測到它已停止</span><span class="sxs-lookup"><span data-stu-id="d8ce4-129">Example 3: Stop a process and detect that it has stopped</span></span>

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

<span data-ttu-id="d8ce4-130">這一系列的命令會啟動及停止 Calc 處理常式，然後偵測已經停止的進程。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-130">This series of commands starts and stops the Calc process, and then detects processes that have stopped.</span></span>

<span data-ttu-id="d8ce4-131">第一個命令會啟動計算機的實例。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-131">The first command starts an instance of the calculator.</span></span>

<span data-ttu-id="d8ce4-132">第二個命令使用 **Get 處理** 程式取得代表 Calc 處理常式的物件，然後將它儲存在 $p 變數中。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-132">The second command uses **Get-Process** gets an object that represents the Calc process, and then stores it in the $p variable.</span></span>

<span data-ttu-id="d8ce4-133">第三個命令會停止 Calc 處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-133">The third command stops the Calc process.</span></span>
<span data-ttu-id="d8ce4-134">它會使用 *InputObject* 參數將物件傳送至 **停止進程** 。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-134">It uses the *InputObject* parameter to pass the object to **Stop-Process** .</span></span>

<span data-ttu-id="d8ce4-135">最後一個命令會取得電腦上所有之前在執行中但現在已經停止的處理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-135">The last command gets all of the processes on the computer that were running but that are now stopped.</span></span>
<span data-ttu-id="d8ce4-136">它會使用 **取得處理常式** 來取得電腦上的所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-136">It uses **Get-Process** to get all of the processes on the computer.</span></span>
<span data-ttu-id="d8ce4-137">管線運算子 (|) 將結果傳遞給 Where-Object Cmdlet，其會選取 [ **HasExited** ] 屬性的值 $True 的值。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-137">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the ones where the value of the **HasExited** property is $True.</span></span>
<span data-ttu-id="d8ce4-138">**HasExited** 只是處理常式物件的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-138">**HasExited** is just one property of process objects.</span></span>
<span data-ttu-id="d8ce4-139">若要尋找所有屬性，請輸入 `Get-Process | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-139">To find all the properties, type `Get-Process | Get-Member`.</span></span>

### <span data-ttu-id="d8ce4-140">範例4：停止目前使用者所擁有的進程</span><span class="sxs-lookup"><span data-stu-id="d8ce4-140">Example 4: Stop a process not owned by the current user</span></span>

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

<span data-ttu-id="d8ce4-141">這些命令會顯示使用 *Force* 來停止不是使用者所擁有之處理常式的效果。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-141">These commands show the effect of using *Force* to stop a process that is not owned by the user.</span></span>

<span data-ttu-id="d8ce4-142">第一個命令會使用 **Get 進程** 來取得 Lsass 進程。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-142">The first command uses **Get-Process** to get the Lsass process.</span></span>
<span data-ttu-id="d8ce4-143">管線運算子會將處理常式傳送至 **停止進程** ，以停止進程。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-143">A pipeline operator sends the process to **Stop-Process** to stop it.</span></span>
<span data-ttu-id="d8ce4-144">如範例輸出所示，第一個命令失敗並顯示「拒絕存取」訊息，因為只有電腦上系統管理員群組的成員才能停止此處理程式。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-144">As shown in the sample output, the first command fails with an Access denied message, because this process can be stopped only by a member of the Administrator group on the computer.</span></span>

<span data-ttu-id="d8ce4-145">使用 [以系統管理員身分執行] 選項開啟 PowerShell 並重覆命令時，PowerShell 會提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-145">When PowerShell is opened by using the Run as administrator option, and the command is repeated, PowerShell prompts you for confirmation.</span></span>

<span data-ttu-id="d8ce4-146">第二個命令指定 *Force* 來抑制提示。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-146">The second command specifies *Force* to suppress the prompt.</span></span>
<span data-ttu-id="d8ce4-147">因此，會在不需要確認的情況下停止處理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-147">As a result, the process is stopped without confirmation.</span></span>

## <span data-ttu-id="d8ce4-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8ce4-148">PARAMETERS</span></span>

### <span data-ttu-id="d8ce4-149">-Force</span><span class="sxs-lookup"><span data-stu-id="d8ce4-149">-Force</span></span>

<span data-ttu-id="d8ce4-150">在沒有提示確認的情況下停止指定的處理程序。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-150">Stops the specified processes without prompting for confirmation.</span></span>
<span data-ttu-id="d8ce4-151">依預設， **停止進程** 會提示您確認，然後才會停止目前使用者未擁有的任何處理程式。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-151">By default, **Stop-Process** prompts for confirmation before stopping any process that is not owned by the current user.</span></span>

<span data-ttu-id="d8ce4-152">若要尋找處理常式的擁有者，請使用 `Get-CimInstance` Cmdlet 取得代表進程的 **Win32_Process** 物件，然後使用物件的 **GetOwner** 方法。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-152">To find the owner of a process, use the `Get-CimInstance` cmdlet to get a **Win32_Process** object that represents the process, and then use the **GetOwner** method of the object.</span></span>

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

### <span data-ttu-id="d8ce4-153">-Id</span><span class="sxs-lookup"><span data-stu-id="d8ce4-153">-Id</span></span>

<span data-ttu-id="d8ce4-154">指定要停止之進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-154">Specifies the process IDs of the processes to stop.</span></span>
<span data-ttu-id="d8ce4-155">若要指定多個識別碼，請使用逗號來分隔識別碼。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-155">To specify multiple IDs, use commas to separate the IDs.</span></span>
<span data-ttu-id="d8ce4-156">若要尋找處理程序的 PID，請輸入 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-156">To find the PID of a process, type `Get-Process`.</span></span>

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

### <span data-ttu-id="d8ce4-157">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d8ce4-157">-InputObject</span></span>

<span data-ttu-id="d8ce4-158">指定要停止的處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-158">Specifies the process objects to stop.</span></span>
<span data-ttu-id="d8ce4-159">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-159">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8ce4-160">-Name</span><span class="sxs-lookup"><span data-stu-id="d8ce4-160">-Name</span></span>

<span data-ttu-id="d8ce4-161">指定要停止之處理常式的處理常式名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-161">Specifies the process names of the processes to stop.</span></span>
<span data-ttu-id="d8ce4-162">您可以輸入多個處理常式名稱（以逗號分隔），或使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-162">You can type multiple process names, separated by commas, or use wildcard characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="d8ce4-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d8ce4-163">-PassThru</span></span>

<span data-ttu-id="d8ce4-164">傳回表示進程的物件。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-164">Returns an object that represents the process.</span></span>
<span data-ttu-id="d8ce4-165">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d8ce4-166">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d8ce4-166">-Confirm</span></span>

<span data-ttu-id="d8ce4-167">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-167">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d8ce4-168">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d8ce4-168">-WhatIf</span></span>

<span data-ttu-id="d8ce4-169">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-169">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d8ce4-170">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-170">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d8ce4-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8ce4-171">CommonParameters</span></span>

<span data-ttu-id="d8ce4-172">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8ce4-173">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8ce4-174">輸入</span><span class="sxs-lookup"><span data-stu-id="d8ce4-174">INPUTS</span></span>

### <span data-ttu-id="d8ce4-175">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-175">System.Diagnostics.Process</span></span>

<span data-ttu-id="d8ce4-176">您可以使用管線將處理程序物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-176">You can pipe a process object to this cmdlet.</span></span>

## <span data-ttu-id="d8ce4-177">輸出</span><span class="sxs-lookup"><span data-stu-id="d8ce4-177">OUTPUTS</span></span>

### <span data-ttu-id="d8ce4-178">無，系統診斷。進程</span><span class="sxs-lookup"><span data-stu-id="d8ce4-178">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="d8ce4-179">如果您指定 *PassThru* 參數，此 Cmdlet 會傳回代表已停止進程的 **處理常式** 物件。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-179">This cmdlet returns a **System.Diagnostics.Process** object that represents the stopped process, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="d8ce4-180">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-180">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d8ce4-181">注意</span><span class="sxs-lookup"><span data-stu-id="d8ce4-181">NOTES</span></span>

* <span data-ttu-id="d8ce4-182">您也可以使用內建的別名（ **kill** 和 **spps** ）來參考 **停止進程** 。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-182">You can also refer to **Stop-Process** by its built-in aliases, **kill** and **spps** .</span></span> <span data-ttu-id="d8ce4-183">如需詳細資訊，請參閱 about_Aliases。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-183">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="d8ce4-184">您也可以在 Windows PowerShell 中使用 Windows Management Instrumentation (WMI) **Win32_Process** 物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-184">You can also use the properties and methods of the Windows Management Instrumentation (WMI) **Win32_Process** object in Windows PowerShell.</span></span>
<span data-ttu-id="d8ce4-185">如需詳細資訊，請參閱 `Get-CimInstance` 和 WMI SDK。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-185">For more information, see `Get-CimInstance` and the WMI SDK.</span></span>

* <span data-ttu-id="d8ce4-186">停止處理常式時，請注意，停止處理常式可能會停止相依于進程的處理常式和服務。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-186">When stopping processes, realize that stopping a process can stop process and services that depend on the process.</span></span>
<span data-ttu-id="d8ce4-187">在極端情況下，停止處理程序可能會停止 Windows。</span><span class="sxs-lookup"><span data-stu-id="d8ce4-187">In an extreme case, stopping a process can stop Windows.</span></span>

## <span data-ttu-id="d8ce4-188">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8ce4-188">RELATED LINKS</span></span>

[<span data-ttu-id="d8ce4-189">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-189">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="d8ce4-190">Get-Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-190">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="d8ce4-191">Start-Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-191">Start-Process</span></span>](Start-Process.md)

[<span data-ttu-id="d8ce4-192">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-192">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="d8ce4-193">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="d8ce4-193">Wait-Process</span></span>](Wait-Process.md)
