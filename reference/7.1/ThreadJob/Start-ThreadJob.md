---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: bced2b87c3843833414ebfd189d003e83af9718f
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96777742"
---
# <span data-ttu-id="c75b3-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="c75b3-102">Start-ThreadJob</span></span>

## <span data-ttu-id="c75b3-103">概要</span><span class="sxs-lookup"><span data-stu-id="c75b3-103">SYNOPSIS</span></span>
<span data-ttu-id="c75b3-104">建立與 Cmdlet 類似的背景工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="c75b3-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="c75b3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c75b3-105">SYNTAX</span></span>

### <span data-ttu-id="c75b3-106">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="c75b3-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### <span data-ttu-id="c75b3-107">FilePath</span><span class="sxs-lookup"><span data-stu-id="c75b3-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## <span data-ttu-id="c75b3-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c75b3-108">DESCRIPTION</span></span>

<span data-ttu-id="c75b3-109">`Start-ThreadJob` 建立與 Cmdlet 類似的背景工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="c75b3-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="c75b3-110">主要差異在於建立的工作會在本機進程內的不同執行緒中執行。</span><span class="sxs-lookup"><span data-stu-id="c75b3-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="c75b3-111">根據預設，工作會使用啟動作業之呼叫端的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="c75b3-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="c75b3-112">此 Cmdlet 也支援 **ThrottleLimit** 參數，以限制一次執行的作業數目。</span><span class="sxs-lookup"><span data-stu-id="c75b3-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="c75b3-113">當作業啟動時，會將它們排入佇列，並等候目前的作業數目降至低於節流限制。</span><span class="sxs-lookup"><span data-stu-id="c75b3-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="c75b3-114">範例</span><span class="sxs-lookup"><span data-stu-id="c75b3-114">EXAMPLES</span></span>

### <span data-ttu-id="c75b3-115">範例 1-建立執行緒限制為2的背景工作</span><span class="sxs-lookup"><span data-stu-id="c75b3-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### <span data-ttu-id="c75b3-116">範例 2-比較 Start-Job 和 Start-ThreadJob 的效能</span><span class="sxs-lookup"><span data-stu-id="c75b3-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="c75b3-117">這個範例會顯示與之間的差異 `Start-Job` `Start-ThreadJob` 。</span><span class="sxs-lookup"><span data-stu-id="c75b3-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="c75b3-118">作業會執行 `Start-Sleep` Cmdlet 1 秒。</span><span class="sxs-lookup"><span data-stu-id="c75b3-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="c75b3-119">由於工作會以平行方式執行，因此總執行時間大約是1秒，再加上建立作業所需的任何時間。</span><span class="sxs-lookup"><span data-stu-id="c75b3-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

<span data-ttu-id="c75b3-120">在減去1秒的執行時間之後，您會看到 `Start-Job` 大約需要4.8 秒的時間來建立五個作業。</span><span class="sxs-lookup"><span data-stu-id="c75b3-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="c75b3-121">`Start-ThreadJob` 有8倍的速度，大約需要0.6 秒來建立五個作業。</span><span class="sxs-lookup"><span data-stu-id="c75b3-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="c75b3-122">您的環境中可能會有不同的結果，但相對改進應該相同。</span><span class="sxs-lookup"><span data-stu-id="c75b3-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="c75b3-123">範例 3-使用 InputObject 建立作業</span><span class="sxs-lookup"><span data-stu-id="c75b3-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="c75b3-124">在此範例中，腳本區塊會使用 `$input` 變數來接收來自 **InputObject** 參數的輸入。</span><span class="sxs-lookup"><span data-stu-id="c75b3-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="c75b3-125">這也可以藉由將物件輸送至來完成 `Start-ThreadJob` 。</span><span class="sxs-lookup"><span data-stu-id="c75b3-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### <span data-ttu-id="c75b3-126">範例 4-將工作輸出串流至父主機</span><span class="sxs-lookup"><span data-stu-id="c75b3-126">Example 4 - Stream job output to parent host</span></span>

<span data-ttu-id="c75b3-127">使用 **StreamingHost** 參數，您可以告知作業將所有主機輸出導向至特定的主機。</span><span class="sxs-lookup"><span data-stu-id="c75b3-127">Using the **StreamingHost** parameter you can tell a job to direct all host output to a specific host.</span></span> <span data-ttu-id="c75b3-128">如果沒有這個參數，輸出就會移至作業資料流程集合，而且在您收到作業的輸出之前，不會出現在主機主控台中。</span><span class="sxs-lookup"><span data-stu-id="c75b3-128">Without this parameter the output goes to the job data stream collection and doesn't appear in a host console until you receive the output from the job.</span></span>

<span data-ttu-id="c75b3-129">在此範例中，會 `Start-ThreadJob` 使用自動變數將目前的主機傳遞給 `$Host` 。</span><span class="sxs-lookup"><span data-stu-id="c75b3-129">For this example, the current host is passed to `Start-ThreadJob` using the `$Host` automatic variable.</span></span>

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

<span data-ttu-id="c75b3-130">請注意，顯示的提示 `Read-Host` 會顯示，而且您可以輸入輸入。</span><span class="sxs-lookup"><span data-stu-id="c75b3-130">Notice that the prompt from `Read-Host` is displayed and you are able to type input.</span></span> <span data-ttu-id="c75b3-131">然後會顯示來自的訊息 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="c75b3-131">Then, the message from `Write-Warning` is displayed.</span></span> <span data-ttu-id="c75b3-132">Cmdlet 會傳回 `Receive-Job` 作業的所有輸出。</span><span class="sxs-lookup"><span data-stu-id="c75b3-132">The `Receive-Job` cmdlet returns all the output from the job.</span></span>

## <span data-ttu-id="c75b3-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c75b3-133">PARAMETERS</span></span>

### <span data-ttu-id="c75b3-134">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="c75b3-134">-ArgumentList</span></span>

<span data-ttu-id="c75b3-135">針對 **FilePath** 或 **ScriptBlock** 參數所指定的腳本，指定引數或參數值的陣列。</span><span class="sxs-lookup"><span data-stu-id="c75b3-135">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="c75b3-136">**ArgumentList** 必須是命令列上的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="c75b3-136">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="c75b3-137">參數名稱後面的所有值都是引數清單中的解讀值。</span><span class="sxs-lookup"><span data-stu-id="c75b3-137">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75b3-138">-FilePath</span><span class="sxs-lookup"><span data-stu-id="c75b3-138">-FilePath</span></span>

<span data-ttu-id="c75b3-139">指定要以背景工作的形式執行的指令檔。</span><span class="sxs-lookup"><span data-stu-id="c75b3-139">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="c75b3-140">輸入腳本的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="c75b3-140">Enter the path and filename of the script.</span></span> <span data-ttu-id="c75b3-141">腳本必須位於本機電腦或本機電腦可以存取的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c75b3-141">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="c75b3-142">當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換為腳本區塊，並以背景工作的形式執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="c75b3-142">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75b3-143">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="c75b3-143">-InitializationScript</span></span>

<span data-ttu-id="c75b3-144">指定要在工作開始之前執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c75b3-144">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="c75b3-145">以大括弧括住命令 (`{}`) 來建立腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="c75b3-145">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="c75b3-146">使用這個參數來準備執行工作的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c75b3-146">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="c75b3-147">例如，您可以使用它將函式和模組新增至會話。</span><span class="sxs-lookup"><span data-stu-id="c75b3-147">For example, you can use it to add functions and modules to the session.</span></span>

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

### <span data-ttu-id="c75b3-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c75b3-148">-InputObject</span></span>

<span data-ttu-id="c75b3-149">指定用來做為腳本區塊輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="c75b3-149">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="c75b3-150">它也允許管線輸入。</span><span class="sxs-lookup"><span data-stu-id="c75b3-150">It also allows for pipeline input.</span></span> <span data-ttu-id="c75b3-151">使用 `$input` 腳本區塊中的自動變數來存取輸入物件。</span><span class="sxs-lookup"><span data-stu-id="c75b3-151">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

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

### <span data-ttu-id="c75b3-152">-Name</span><span class="sxs-lookup"><span data-stu-id="c75b3-152">-Name</span></span>

<span data-ttu-id="c75b3-153">指定新工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="c75b3-153">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="c75b3-154">您可以使用此名稱來識別其他工作 Cmdlet 的作業，例如 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c75b3-154">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="c75b3-155">預設的易記名稱是 "Job #"，其中 "#" 是每項作業的遞增序號。</span><span class="sxs-lookup"><span data-stu-id="c75b3-155">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75b3-156">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="c75b3-156">-ScriptBlock</span></span>

<span data-ttu-id="c75b3-157">指定要在背景工作執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c75b3-157">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="c75b3-158">以大括弧括住命令 (`{}`) 來建立腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="c75b3-158">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="c75b3-159">使用 `$Input` 自動變數來存取 **InputObject** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c75b3-159">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="c75b3-160">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="c75b3-160">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75b3-161">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="c75b3-161">-StreamingHost</span></span>

<span data-ttu-id="c75b3-162">此參數提供安全線程的方式，讓 `Write-Host` 輸出直接移至傳遞的 **PSHost** 物件中。</span><span class="sxs-lookup"><span data-stu-id="c75b3-162">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="c75b3-163">如果沒有它，輸出就會 `Write-Host` 移至作業資訊資料流程集合，而且在作業執行完成之後，才會出現在主機主控台中。</span><span class="sxs-lookup"><span data-stu-id="c75b3-163">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75b3-164">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="c75b3-164">-ThrottleLimit</span></span>

<span data-ttu-id="c75b3-165">此參數會限制一次執行的作業數目。</span><span class="sxs-lookup"><span data-stu-id="c75b3-165">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="c75b3-166">當作業啟動時，會將它們排入佇列，並等候執行緒集區中的執行緒可執行作業。</span><span class="sxs-lookup"><span data-stu-id="c75b3-166">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="c75b3-167">預設限制為5個執行緒。</span><span class="sxs-lookup"><span data-stu-id="c75b3-167">The default limit is 5 threads.</span></span>

<span data-ttu-id="c75b3-168">執行緒集區大小對 PowerShell 會話而言是全域的。</span><span class="sxs-lookup"><span data-stu-id="c75b3-168">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="c75b3-169">在一個呼叫中指定 **ThrottleLimit** ，就會在相同的會話中設定後續呼叫的限制。</span><span class="sxs-lookup"><span data-stu-id="c75b3-169">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c75b3-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c75b3-170">CommonParameters</span></span>

<span data-ttu-id="c75b3-171">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c75b3-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c75b3-172">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c75b3-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c75b3-173">輸入</span><span class="sxs-lookup"><span data-stu-id="c75b3-173">INPUTS</span></span>

### <span data-ttu-id="c75b3-174">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="c75b3-174">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="c75b3-175">輸出</span><span class="sxs-lookup"><span data-stu-id="c75b3-175">OUTPUTS</span></span>

### <span data-ttu-id="c75b3-176">ThreadJob.ThreadJob</span><span class="sxs-lookup"><span data-stu-id="c75b3-176">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="c75b3-177">注意</span><span class="sxs-lookup"><span data-stu-id="c75b3-177">NOTES</span></span>

## <span data-ttu-id="c75b3-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="c75b3-178">RELATED LINKS</span></span>

[<span data-ttu-id="c75b3-179">Start-Job</span><span class="sxs-lookup"><span data-stu-id="c75b3-179">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="c75b3-180">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="c75b3-180">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="c75b3-181">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="c75b3-181">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)
