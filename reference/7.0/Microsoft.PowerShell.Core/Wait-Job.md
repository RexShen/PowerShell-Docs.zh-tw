---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 2eeacf8703dbe0f662d0b26d405c605d21c2b84e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390349"
---
# <span data-ttu-id="7a789-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-103">Wait-Job</span></span>

## <span data-ttu-id="7a789-104">概要</span><span class="sxs-lookup"><span data-stu-id="7a789-104">SYNOPSIS</span></span>
<span data-ttu-id="7a789-105">抑制命令提示字元，直到會話中正在執行的其中一個或所有 PowerShell 背景工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="7a789-105">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="7a789-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a789-106">SYNTAX</span></span>

### <span data-ttu-id="7a789-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="7a789-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="7a789-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="7a789-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="7a789-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="7a789-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="7a789-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="7a789-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="7a789-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="7a789-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="7a789-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="7a789-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="7a789-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7a789-113">DESCRIPTION</span></span>

<span data-ttu-id="7a789-114">`Wait-Job`Cmdlet 會等候 PowerShell 背景工作完成，然後才會顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7a789-114">The `Wait-Job` cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span> <span data-ttu-id="7a789-115">您可以等到任一背景工作完成，或等到所有背景工作都完成，而且可以設定工作的最長等待時間。</span><span class="sxs-lookup"><span data-stu-id="7a789-115">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="7a789-116">當工作中的命令完成時，會 `Wait-Job` 顯示命令提示字元並傳回工作物件，讓您可以使用管線將它傳送至另一個命令。</span><span class="sxs-lookup"><span data-stu-id="7a789-116">When the commands in the job are complete, `Wait-Job` displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="7a789-117">您可以使用 `Wait-Job` Cmdlet 來等候背景工作，例如使用 `Start-Job` Cmdlet 或 Cmdlet 的 **AsJob** 參數啟動的工作 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-117">You can use `Wait-Job` cmdlet to wait for background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="7a789-118">如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](./about/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="7a789-118">For more information about Windows PowerShell background jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="7a789-119">從 Windows PowerShell 3.0 開始，此 `Wait-Job` Cmdlet 也會等待自訂工作類型，例如工作流程工作和排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="7a789-119">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="7a789-120">若要讓 `Wait-Job` 等待特定類型的工作，請 `Get-Job` 使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入會話中，再執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a789-120">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="7a789-121">如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。</span><span class="sxs-lookup"><span data-stu-id="7a789-121">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="7a789-122">範例</span><span class="sxs-lookup"><span data-stu-id="7a789-122">EXAMPLES</span></span>

### <span data-ttu-id="7a789-123">範例1：等候所有作業</span><span class="sxs-lookup"><span data-stu-id="7a789-123">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="7a789-124">此命令會等待會話中執行的所有背景工作完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-124">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="7a789-125">範例2：使用 Start-Job 等候遠端電腦上啟動的工作</span><span class="sxs-lookup"><span data-stu-id="7a789-125">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="7a789-126">此範例示範如何使用指令程式搭配使用 `Wait-Job` Cmdlet 在遠端電腦上啟動的作業 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-126">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="7a789-127">`Start-Job`和 `Wait-Job` 命令都使用 Cmdlet 提交至遠端電腦 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-127">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="7a789-128">這個範例 `Wait-Job` 會使用來判斷 `Get-Date` 在三部不同電腦上以背景工作方式執行的命令是否已完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-128">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="7a789-129">第一個命令會在三部遠端電腦上 ( **PSSession** ) 建立 Windows PowerShell 會話，並將它們儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-129">The first command creates a Windows PowerShell session ( **PSSession** ) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="7a789-130">第二個命令會使用在中的 `Invoke-Command` `Start-Job` 三個會話中執行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-130">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="7a789-131">所有的工作都命名為 Date1。</span><span class="sxs-lookup"><span data-stu-id="7a789-131">All of the jobs are named Date1.</span></span>

<span data-ttu-id="7a789-132">第三個命令會使用 `Invoke-Command` 來執行 `Wait-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-132">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="7a789-133">此命令會等待每一部電腦上的 Date1 工作完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-133">This command waits for the Date1 jobs on each computer to finish.</span></span> <span data-ttu-id="7a789-134">它會將產生的集合 (陣列) 在變數中的工作物件 `$done` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-134">It stores the resulting collection (array) of job objects in the `$done` variable.</span></span>

<span data-ttu-id="7a789-135">第四個命令使用變數中工作物件陣列的 **Count** 屬性 `$done` 來判斷已完成的作業數目。</span><span class="sxs-lookup"><span data-stu-id="7a789-135">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="7a789-136">範例3：判斷第一個背景工作完成的時間</span><span class="sxs-lookup"><span data-stu-id="7a789-136">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="7a789-137">這個範例會使用的 **Any** 參數 `Wait-Job` ，來判斷在目前的會話中執行的多個背景工作的第一個作業完成的時間。</span><span class="sxs-lookup"><span data-stu-id="7a789-137">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many background jobs running in the current session are completed.</span></span> <span data-ttu-id="7a789-138">它也會示範如何使用指令 `Wait-Job` 程式來等候遠端工作完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-138">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="7a789-139">第一個命令會在 Machines.txt 檔案中列出的每一部電腦上建立 **pssession** ，並將 **pssession** 物件儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-139">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="7a789-140">此命令會使用 `Get-Content` Cmdlet 來取得檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="7a789-140">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="7a789-141">此 `Get-Content` 命令會以括弧括住，以確保它會在命令之前執行 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-141">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="7a789-142">第二個命令會在變數中儲存 `Get-EventLog` 命令字串（以引號括住） `$c` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-142">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="7a789-143">第三個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在的每個會話中執行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-143">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="7a789-144">此 `Start-Job` 命令會啟動在 `Get-EventLog` 變數中執行命令的背景工作 `$c` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-144">The `Start-Job` command starts a background job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="7a789-145">此命令會使用 **Using** 範圍修飾符來指出 `$c` 變數是在本機電腦上定義。</span><span class="sxs-lookup"><span data-stu-id="7a789-145">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="7a789-146">**Using** 範圍修飾符是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="7a789-146">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="7a789-147">如需 **Using** 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](./about/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="7a789-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="7a789-148">第四個命令會使用在 `Invoke-Command` `Wait-Job` 會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="7a789-148">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="7a789-149">它會使用 **Any** 參數來等候，直到遠端電腦上的第一個工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="7a789-149">It uses the **Any** parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="7a789-150">範例4：設定遠端電腦上作業的等候時間</span><span class="sxs-lookup"><span data-stu-id="7a789-150">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="7a789-151">這個範例會示範如何使用的 **Timeout** 參數 `Wait-Job` ，為遠端電腦上執行的作業設定最長等候時間。</span><span class="sxs-lookup"><span data-stu-id="7a789-151">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="7a789-152">第一個命令會在三部遠端電腦上建立 **PSSession** (Server01、Server02 和 Server03) ，然後將 **pssession** 物件儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-152">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="7a789-153">第二個命令會使用在 `Invoke-Command` `Start-Job` 中的每個 **PSSession** 物件中執行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-153">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="7a789-154">它會將產生的工作物件儲存在 `$jobs` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-154">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="7a789-155">第三個命令會使用在中的 `Invoke-Command` `Wait-Job` 每個會話中執行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-155">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="7a789-156">此 `Wait-Job` 命令會判斷所有命令是否已在30秒內完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-156">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="7a789-157">它會使用值為30的 **Timeout** 參數來建立最長等待時間，然後將命令的結果儲存在 `$done` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-157">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="7a789-158">在本例中，30 秒之後，只有 Server02 電腦上的命令已完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-158">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="7a789-159">`Wait-Job` 結束等待、顯示命令提示字元，然後傳回代表已完成作業的物件。</span><span class="sxs-lookup"><span data-stu-id="7a789-159">`Wait-Job` ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="7a789-160">`$done`變數包含代表在 Server02 上執行之工作的工作物件。</span><span class="sxs-lookup"><span data-stu-id="7a789-160">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="7a789-161">範例5：等候數個作業的其中一個完成</span><span class="sxs-lookup"><span data-stu-id="7a789-161">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="7a789-162">此命令會依識別碼來識別三個工作，並等到其中任何一個工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="7a789-162">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="7a789-163">第一個作業完成時，會傳回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7a789-163">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="7a789-164">範例6：等候一段時間，然後允許作業在背景中繼續</span><span class="sxs-lookup"><span data-stu-id="7a789-164">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="7a789-165">此命令會等候120秒 (兩) 分鐘的時間，DailyLog 作業才會完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-165">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="7a789-166">如果作業未在接下來的兩分鐘內完成，則會傳回命令提示字元，而工作會繼續在背景執行。</span><span class="sxs-lookup"><span data-stu-id="7a789-166">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="7a789-167">範例7：依名稱等候工作</span><span class="sxs-lookup"><span data-stu-id="7a789-167">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="7a789-168">此命令使用工作名稱來識別要等待的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-168">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="7a789-169">範例8：等候本機電腦上的工作以 Start-Job 啟動</span><span class="sxs-lookup"><span data-stu-id="7a789-169">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="7a789-170">此範例示範如何使用指令程式搭配在 `Wait-Job` 本機電腦上啟動的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-170">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="7a789-171">這些命令啟動可取得上週新增或更新之 Windows PowerShell 指令檔的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-171">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="7a789-172">第一個命令會使用在 `Start-Job` 本機電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-172">The first command uses `Start-Job` to start a background job on the local computer.</span></span> <span data-ttu-id="7a789-173">作業會執行 `Get-ChildItem` 命令，以取得在上一周新增或更新的所有檔案，其副檔名為 ps1。</span><span class="sxs-lookup"><span data-stu-id="7a789-173">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="7a789-174">第三個命令 `Wait-Job` 會使用來等候工作完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-174">The third command uses `Wait-Job` to wait until the job is completed.</span></span> <span data-ttu-id="7a789-175">當作業完成時，此命令會顯示工作物件，其中包含作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7a789-175">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="7a789-176">範例9：使用 Invoke-Command 等候遠端電腦上啟動的工作</span><span class="sxs-lookup"><span data-stu-id="7a789-176">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="7a789-177">這個範例示範如何使用的 `Wait-Job` **AsJob** 參數，在遠端電腦上使用來執行工作 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-177">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="7a789-178">使用 **AsJob** 時，會在本機電腦上建立工作，而即使工作是在遠端電腦上執行，也會將結果自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="7a789-178">When using **AsJob** , the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="7a789-179">此範例 `Wait-Job` 會使用來判斷在 `Get-Process` 三部遠端電腦上的會話中執行的命令是否已完成。</span><span class="sxs-lookup"><span data-stu-id="7a789-179">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="7a789-180">第一個命令會在三部電腦上建立 **PSSession** 物件，並將它們儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-180">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="7a789-181">第二個命令會使用在中的 `Invoke-Command` `Get-Process` 三個會話中執行 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-181">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="7a789-182">此命令會使用 **AsJob** 參數，以非同步方式以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="7a789-182">The command uses the **AsJob** parameter to run the command asynchronously as a background job.</span></span> <span data-ttu-id="7a789-183">命令會傳回工作物件，就像使用啟動的工作一樣， `Start-Job` 工作物件也會儲存在 `$j` 變數中。</span><span class="sxs-lookup"><span data-stu-id="7a789-183">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="7a789-184">第三個命令使用管線運算子 (`|`) 將工作物件傳送 `$j` 至 `Wait-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a789-184">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="7a789-185">`Invoke-Command`在此情況下不需要命令，因為作業位於本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="7a789-185">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="7a789-186">範例10：等候具有識別碼的作業</span><span class="sxs-lookup"><span data-stu-id="7a789-186">Example 10: Wait for a job that has an ID</span></span>

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

<span data-ttu-id="7a789-187">此命令等待 ID 值為 1 的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-187">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="7a789-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a789-188">PARAMETERS</span></span>

### <span data-ttu-id="7a789-189">-Any</span><span class="sxs-lookup"><span data-stu-id="7a789-189">-Any</span></span>

<span data-ttu-id="7a789-190">指出當任何作業完成時，此 Cmdlet 會顯示命令提示字元，並傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="7a789-190">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span> <span data-ttu-id="7a789-191">根據預設， `Wait-Job` 會等到所有指定的工作都完成後，才會顯示提示。</span><span class="sxs-lookup"><span data-stu-id="7a789-191">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="7a789-192">-Filter</span><span class="sxs-lookup"><span data-stu-id="7a789-192">-Filter</span></span>

<span data-ttu-id="7a789-193">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="7a789-193">Specifies a hash table of conditions.</span></span> <span data-ttu-id="7a789-194">此 Cmdlet 會等候符合雜湊表中所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-194">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="7a789-195">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="7a789-195">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="7a789-196">這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-196">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="7a789-197">它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-197">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="7a789-198">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="7a789-198">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="7a789-199">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="7a789-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-200">-Force</span><span class="sxs-lookup"><span data-stu-id="7a789-200">-Force</span></span>

<span data-ttu-id="7a789-201">指出此 Cmdlet 會繼續等待處於暫停或已中斷線上狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-201">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="7a789-202">根據預設， `Wait-Job` 當作業處於下列其中一個狀態時，會傳回或結束等候：</span><span class="sxs-lookup"><span data-stu-id="7a789-202">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="7a789-203">Completed</span><span class="sxs-lookup"><span data-stu-id="7a789-203">Completed</span></span>
- <span data-ttu-id="7a789-204">失敗</span><span class="sxs-lookup"><span data-stu-id="7a789-204">Failed</span></span>
- <span data-ttu-id="7a789-205">已停止</span><span class="sxs-lookup"><span data-stu-id="7a789-205">Stopped</span></span>
- <span data-ttu-id="7a789-206">暫止</span><span class="sxs-lookup"><span data-stu-id="7a789-206">Suspended</span></span>
- <span data-ttu-id="7a789-207">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="7a789-207">Disconnected</span></span>

<span data-ttu-id="7a789-208">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="7a789-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="7a789-209">-Id</span><span class="sxs-lookup"><span data-stu-id="7a789-209">-Id</span></span>

<span data-ttu-id="7a789-210">指定此 Cmdlet 等候之作業的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="7a789-210">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="7a789-211">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-211">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="7a789-212">與執行個體識別碼相比，它比較容易記住並輸入，但是它只有在目前的工作階段內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7a789-212">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="7a789-213">您可以輸入一個或多個識別碼，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="7a789-213">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="7a789-214">若要尋找工作的識別碼，請輸入 `Get-Job`。</span><span class="sxs-lookup"><span data-stu-id="7a789-214">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-215">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="7a789-215">-InstanceId</span></span>

<span data-ttu-id="7a789-216">指定此 Cmdlet 等候之作業的實例識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="7a789-216">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="7a789-217">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-217">The default is all jobs.</span></span>

<span data-ttu-id="7a789-218">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-218">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="7a789-219">若要尋找工作的實例識別碼，請使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-219">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-220">-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-220">-Job</span></span>

<span data-ttu-id="7a789-221">指定此 Cmdlet 等候的作業。</span><span class="sxs-lookup"><span data-stu-id="7a789-221">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="7a789-222">輸入包含工作物件的變數，或輸入可取得工作物件的命令。</span><span class="sxs-lookup"><span data-stu-id="7a789-222">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="7a789-223">您也可以使用管線運算子將工作物件傳送至 `Wait-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a789-223">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="7a789-224">根據預設，會 `Wait-Job` 等候目前會話中建立的所有作業。</span><span class="sxs-lookup"><span data-stu-id="7a789-224">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-225">-Name</span><span class="sxs-lookup"><span data-stu-id="7a789-225">-Name</span></span>

<span data-ttu-id="7a789-226">指定此 Cmdlet 等候之作業的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7a789-226">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-227">-State</span><span class="sxs-lookup"><span data-stu-id="7a789-227">-State</span></span>

<span data-ttu-id="7a789-228">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="7a789-228">Specifies a job state.</span></span> <span data-ttu-id="7a789-229">此 Cmdlet 只會等待處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="7a789-229">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="7a789-230">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="7a789-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7a789-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="7a789-231">NotStarted</span></span>
- <span data-ttu-id="7a789-232">執行中</span><span class="sxs-lookup"><span data-stu-id="7a789-232">Running</span></span>
- <span data-ttu-id="7a789-233">Completed</span><span class="sxs-lookup"><span data-stu-id="7a789-233">Completed</span></span>
- <span data-ttu-id="7a789-234">失敗</span><span class="sxs-lookup"><span data-stu-id="7a789-234">Failed</span></span>
- <span data-ttu-id="7a789-235">已停止</span><span class="sxs-lookup"><span data-stu-id="7a789-235">Stopped</span></span>
- <span data-ttu-id="7a789-236">封鎖</span><span class="sxs-lookup"><span data-stu-id="7a789-236">Blocked</span></span>
- <span data-ttu-id="7a789-237">暫止</span><span class="sxs-lookup"><span data-stu-id="7a789-237">Suspended</span></span>
- <span data-ttu-id="7a789-238">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="7a789-238">Disconnected</span></span>
- <span data-ttu-id="7a789-239">Suspending</span><span class="sxs-lookup"><span data-stu-id="7a789-239">Suspending</span></span>
- <span data-ttu-id="7a789-240">停止中</span><span class="sxs-lookup"><span data-stu-id="7a789-240">Stopping</span></span>

<span data-ttu-id="7a789-241">如需有關工作狀態的詳細資訊，請參閱 [JobState 列舉](/dotnet/api/system.management.automation.jobstate)。</span><span class="sxs-lookup"><span data-stu-id="7a789-241">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-242">-Timeout</span><span class="sxs-lookup"><span data-stu-id="7a789-242">-Timeout</span></span>

<span data-ttu-id="7a789-243">指定每個背景工作的最長等候時間（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="7a789-243">Specifies the maximum wait time for each background job, in seconds.</span></span> <span data-ttu-id="7a789-244">預設值-1 表示 Cmdlet 會等候，直到工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="7a789-244">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="7a789-245">當您提交 `Wait-Job` 命令（而不是命令）時，就會開始計時 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="7a789-245">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="7a789-246">如果超過這個時間，即使工作仍在執行，也會結束等待並返回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7a789-246">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span> <span data-ttu-id="7a789-247">此命令不會顯示任何錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7a789-247">The command does not display any error message.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a789-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a789-248">CommonParameters</span></span>

<span data-ttu-id="7a789-249">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7a789-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a789-250">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7a789-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a789-251">輸入</span><span class="sxs-lookup"><span data-stu-id="7a789-251">INPUTS</span></span>

### <span data-ttu-id="7a789-252">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="7a789-252">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="7a789-253">您可以使用管線將工作物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7a789-253">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="7a789-254">輸出</span><span class="sxs-lookup"><span data-stu-id="7a789-254">OUTPUTS</span></span>

### <span data-ttu-id="7a789-255">System.Management.Automation.PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="7a789-255">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="7a789-256">此 Cmdlet 會傳回代表已完成之工作的工作物件。</span><span class="sxs-lookup"><span data-stu-id="7a789-256">This cmdlet returns job objects that represent the completed jobs.</span></span> <span data-ttu-id="7a789-257">如果因為超過 **Timeout** 參數的值而結束等候，則 `Wait-Job` 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="7a789-257">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="7a789-258">注意</span><span class="sxs-lookup"><span data-stu-id="7a789-258">NOTES</span></span>

<span data-ttu-id="7a789-259">根據預設， `Wait-Job` 當作業處於下列其中一個狀態時，會傳回或結束等候：</span><span class="sxs-lookup"><span data-stu-id="7a789-259">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="7a789-260">Completed</span><span class="sxs-lookup"><span data-stu-id="7a789-260">Completed</span></span>
- <span data-ttu-id="7a789-261">失敗</span><span class="sxs-lookup"><span data-stu-id="7a789-261">Failed</span></span>
- <span data-ttu-id="7a789-262">已停止</span><span class="sxs-lookup"><span data-stu-id="7a789-262">Stopped</span></span>
- <span data-ttu-id="7a789-263">暫止</span><span class="sxs-lookup"><span data-stu-id="7a789-263">Suspended</span></span>
- <span data-ttu-id="7a789-264">中斷連線以 `Wait-Job` 繼續等候已暫止和已中斷連線的作業，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="7a789-264">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="7a789-265">相關連結</span><span class="sxs-lookup"><span data-stu-id="7a789-265">RELATED LINKS</span></span>

[<span data-ttu-id="7a789-266">Get-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-266">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="7a789-267">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="7a789-267">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="7a789-268">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-268">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="7a789-269">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-269">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="7a789-270">Start-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-270">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="7a789-271">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="7a789-271">Stop-Job</span></span>](Stop-Job.md)
