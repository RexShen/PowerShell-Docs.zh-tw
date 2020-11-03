---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: d61f1efc613b7628585e5090b9fad8d90333a291
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203812"
---
# <span data-ttu-id="3050c-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="3050c-103">Get-Job</span></span>

## <span data-ttu-id="3050c-104">概要</span><span class="sxs-lookup"><span data-stu-id="3050c-104">SYNOPSIS</span></span>
<span data-ttu-id="3050c-105">取得目前會話中正在執行的 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="3050c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3050c-106">SYNTAX</span></span>

### <span data-ttu-id="3050c-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="3050c-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="3050c-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3050c-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="3050c-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3050c-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3050c-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="3050c-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="3050c-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="3050c-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3050c-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="3050c-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="3050c-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3050c-113">DESCRIPTION</span></span>

<span data-ttu-id="3050c-114">**Get-Job** Cmdlet 會取得物件，這類物件代表已在目前工作階段中啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="3050c-115">您可以使用「 **取得作業** 」來取得使用 Start-Job Cmdlet 或使用任何 Cmdlet 之 *AsJob* 參數啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="3050c-116">如果沒有參數， **取得工作** 命令會取得目前會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="3050c-117">您可以使用 **Get-Job** 的參數取得特定工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="3050c-118">**Get-Job** 傳回的工作物件包含關於工作的有用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="3050c-119">若要取得結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3050c-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="3050c-120">PowerShell 背景工作是在背景執行的命令，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="3050c-120">A PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="3050c-121">一般而言，您會使用背景工作來執行複雜的命令，此命令需要很長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="3050c-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="3050c-122">如需有關 PowerShell 中背景工作的詳細資訊，請參閱 about_Jobs。</span><span class="sxs-lookup"><span data-stu-id="3050c-122">For more information about background jobs in PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="3050c-123">從 Windows PowerShell 3.0 開始， **Get-Job** Cmdlet 也可取得自訂工作類型 (例如工作流程工作和排程工作的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="3050c-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="3050c-124">若要尋找工作的工作類型，可使用工作的 **PSJobTypeName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3050c-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="3050c-125">若要啟用 **Get 工作** 以取得自訂工作類型，請使用 Import-Module Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入會話中，再執行 [ **取得工作** ] 命令。</span><span class="sxs-lookup"><span data-stu-id="3050c-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="3050c-126">如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。</span><span class="sxs-lookup"><span data-stu-id="3050c-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="3050c-127">範例</span><span class="sxs-lookup"><span data-stu-id="3050c-127">EXAMPLES</span></span>

### <span data-ttu-id="3050c-128">範例1：取得在目前會話中啟動的所有背景工作</span><span class="sxs-lookup"><span data-stu-id="3050c-128">Example 1: Get all background jobs started in the current session</span></span>

```powershell
Get-Job
```

<span data-ttu-id="3050c-129">這個命令會取得目前工作階段中啟動的所有背景工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="3050c-130">它不會包含在其他工作階段中建立的工作，即使這類工作是在本機電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="3050c-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="3050c-131">範例2：使用實例識別碼停止作業</span><span class="sxs-lookup"><span data-stu-id="3050c-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="3050c-132">這些命令示範如何取得工作的執行個體識別碼，然後使用它來停止工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="3050c-133">與工作名稱 (這不是唯一的) 不同，執行個體識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3050c-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

<span data-ttu-id="3050c-134">第一個命令使用 **Get-Job** Cmdlet 取得工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-134">The first command uses the **Get-Job** cmdlet to get a job.</span></span> <span data-ttu-id="3050c-135">它會使用 *Name* 參數來識別工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-135">It uses the *Name* parameter to identify the job.</span></span> <span data-ttu-id="3050c-136">命令將 **Get-Job** 傳回的工作物件儲存於 $j 變數中。</span><span class="sxs-lookup"><span data-stu-id="3050c-136">The command stores the job object that **Get-Job** returns in the $j variable.</span></span> <span data-ttu-id="3050c-137">在這個範例中，只有一個具有指定名稱的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-137">In this example, there is only one job with the specified name.</span></span>

<span data-ttu-id="3050c-138">第二個命令在 $j 變數中取得物件的 **InstanceId** 屬性，並將它儲存於 $ID 變數中。</span><span class="sxs-lookup"><span data-stu-id="3050c-138">The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.</span></span>

<span data-ttu-id="3050c-139">第三個命令顯示 $ID 變數的值。</span><span class="sxs-lookup"><span data-stu-id="3050c-139">The third command displays the value of the $ID variable.</span></span>

<span data-ttu-id="3050c-140">第四個命令使用 Stop-Job Cmdlet 來停止工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-140">The fourth command uses Stop-Job cmdlet to stop the job.</span></span> <span data-ttu-id="3050c-141">它使用 *InstanceId* 參數來識別工作，並使用 $ID 變數來代表工作的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="3050c-141">It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.</span></span>

### <span data-ttu-id="3050c-142">範例3：取得包含特定命令的工作</span><span class="sxs-lookup"><span data-stu-id="3050c-142">Example 3: Get jobs that include a specific command</span></span>

```powershell
Get-Job -Command "*get-process*"
```

<span data-ttu-id="3050c-143">此命令會取得系統上包含 Get-Process 命令的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-143">This command gets the jobs on the system that include a Get-Process command.</span></span> <span data-ttu-id="3050c-144">命令使用 *Get-Job* 的 **Command** 參數限制抓取的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-144">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span> <span data-ttu-id="3050c-145">命令使用萬用字元 ( \* ) 來取得命令字串中任何位置包含 **取得處理** 程式命令的作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-145">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="3050c-146">範例4：使用管線取得包含特定命令的作業</span><span class="sxs-lookup"><span data-stu-id="3050c-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```powershell
"*get-process*" | Get-Job
```

<span data-ttu-id="3050c-147">如同上一個範例中的命令，此命令會取得系統上包含 **Get 進程** 命令的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-147">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span> <span data-ttu-id="3050c-148">命令使用管線運算子 (|) 將字串（以引號括住）傳送至「 **取得工作** 」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3050c-148">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span> <span data-ttu-id="3050c-149">它等同於前一個命令。</span><span class="sxs-lookup"><span data-stu-id="3050c-149">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="3050c-150">範例5：取得尚未啟動的工作</span><span class="sxs-lookup"><span data-stu-id="3050c-150">Example 5: Get jobs that have not been started</span></span>

```powershell
Get-Job -State NotStarted
```

<span data-ttu-id="3050c-151">這個命令只會取得已建立但尚未啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-151">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="3050c-152">這包括已排定在未來執行的工作以及尚未排程的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="3050c-153">範例6：取得尚未指派名稱的工作</span><span class="sxs-lookup"><span data-stu-id="3050c-153">Example 6: Get jobs that have not been assigned a name</span></span>

```powershell
Get-Job -Name Job*
```

<span data-ttu-id="3050c-154">此命令會取得工作名稱以 job 開頭的所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-154">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="3050c-155">因為 job \<number\> 是作業的預設名稱，所以此命令會取得所有沒有明確指派名稱的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-155">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="3050c-156">範例7：使用工作物件來代表命令中的工作</span><span class="sxs-lookup"><span data-stu-id="3050c-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="3050c-157">這個範例示範如何使用 **Get-Job** 取得工作物件，然後示範如何使用該工作物件來代表命令中的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-157">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="3050c-158">第一個命令會使用 **啟動工作** 指令程式來啟動在本機電腦上執行 **取得處理** 程式命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-158">The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer.</span></span> <span data-ttu-id="3050c-159">命令使用 *Start-Job* 的 **Name** 參數，為工作指派好記名稱。</span><span class="sxs-lookup"><span data-stu-id="3050c-159">The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.</span></span>

<span data-ttu-id="3050c-160">第二個命令使用 Get-Job 取得工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-160">The second command uses Get-Job to get the job.</span></span> <span data-ttu-id="3050c-161">它使用 *Get-Job* 的 **Name** 參數識別工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-161">It uses the *Name* parameter of **Get-Job** to identify the job.</span></span> <span data-ttu-id="3050c-162">命令會將產生的工作物件儲存於 $j 變數中。</span><span class="sxs-lookup"><span data-stu-id="3050c-162">The command saves the resulting job object in the $j variable.</span></span>

<span data-ttu-id="3050c-163">第三個命令顯示 $j 變數中工作物件的值。</span><span class="sxs-lookup"><span data-stu-id="3050c-163">The third command displays the value of the job object in the $j variable.</span></span> <span data-ttu-id="3050c-164">**State** 屬性的值顯示作業已完成。</span><span class="sxs-lookup"><span data-stu-id="3050c-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="3050c-165">**HasMoreData** 屬性的值顯示有來自尚未抓取之工作的可用結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span>

<span data-ttu-id="3050c-166">第四個命令 **會使用接收工作** Cmdlet 來取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-166">The fourth command uses the **Receive-Job** cmdlet to get the results of the job.</span></span> <span data-ttu-id="3050c-167">它使用 $j 變數中的工作物件來代表工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-167">It uses the job object in the $j variable to represent the job.</span></span> <span data-ttu-id="3050c-168">您也可以使用管線運算子將工作物件傳送至 **接收工作** 。</span><span class="sxs-lookup"><span data-stu-id="3050c-168">You can also use a pipeline operator to send a job object to **Receive-Job** .</span></span>

### <span data-ttu-id="3050c-169">範例8：取得所有工作，包括其他方法啟動的作業</span><span class="sxs-lookup"><span data-stu-id="3050c-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="3050c-170">這個範例示範，即使是使用不同的方法啟動， **Get 工作** Cmdlet 也可以取得在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-170">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="3050c-171">第一個命令使用 **啟動工作** Cmdlet 在本機電腦上啟動作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-171">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span>

<span data-ttu-id="3050c-172">第二個命令會使用 **調用命令** Cmdlet 的 *AsJob* 參數，在 S1 電腦上啟動工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-172">The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="3050c-173">即使工作中的命令是在遠端電腦上執行，還是會在本機電腦上建立工作物件，因此您可以使用本機命令來管理工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span>

<span data-ttu-id="3050c-174">第三個命令使用 **Invoke-Command** Cmdlet，在 S2 電腦上執行 **Start-Job** 命令。</span><span class="sxs-lookup"><span data-stu-id="3050c-174">The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer.</span></span> <span data-ttu-id="3050c-175">使用這個方法時，會在遠端電腦上建立工作物件，因此您可以使用遠端命令來管理作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span>

<span data-ttu-id="3050c-176">第四個命令使用 **Get-Job** 取得儲存於本機電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-176">The fourth command uses **Get-Job** to get the jobs stored on the local computer.</span></span> <span data-ttu-id="3050c-177">Windows PowerShell 3.0 中引進之作業的 **PSJobTypeName** 屬性，顯示使用 **啟動工作** Cmdlet 啟動的本機工作是背景工作，而使用 **Invoke 命令** Cmdlet 在遠端會話中啟動的作業是遠端作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.</span></span>

<span data-ttu-id="3050c-178">第五個命令使用 **Invoke 命令** 在 S2 電腦上執行「 **取得工作** 」命令。範例輸出會顯示 Get-Job 命令的結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-178">The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command.</span></span> <span data-ttu-id="3050c-179">在 S2 電腦上，工作顯示為本機工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="3050c-180">電腦名稱稱是 localhost，而工作類型是背景工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-180">The computer name is localhost and the job type is a background job.</span></span>

<span data-ttu-id="3050c-181">如需有關如何在遠端電腦上執行背景工作的詳細資訊，請參閱 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="3050c-181">For more information about how to run background jobs on remote computers, see about_Remote_Jobs.</span></span>

### <span data-ttu-id="3050c-182">範例9：調查失敗的作業</span><span class="sxs-lookup"><span data-stu-id="3050c-182">Example 9: Investigate a failed job</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

<span data-ttu-id="3050c-183">此命令示範如何使用工作物件，該工作物件會傳回工作物件來調查工作 **失敗的原因** 。</span><span class="sxs-lookup"><span data-stu-id="3050c-183">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="3050c-184">它也會示範如何取得每個工作的子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-184">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="3050c-185">第一個命令使用 **啟動工作** Cmdlet 在本機電腦上啟動作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-185">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="3050c-186">**Start-Job** 傳回的工作物件顯示工作失敗。</span><span class="sxs-lookup"><span data-stu-id="3050c-186">The job object that **Start-Job** returns shows that the job failed.</span></span> <span data-ttu-id="3050c-187">**State** 屬性的值為 Failed。</span><span class="sxs-lookup"><span data-stu-id="3050c-187">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="3050c-188">第二個命令使用 **Get-Job** Cmdlet 取得工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-188">The second command uses the **Get-Job** cmdlet to get the job.</span></span> <span data-ttu-id="3050c-189">命令使用點方法，取得物件的 **JobStateInfo** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="3050c-189">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="3050c-190">它會使用管線運算子將 **JobStateInfo** 屬性中的物件傳送至 Format-List Cmdlet，此 Cmdlet 會將物件的所有屬性格式化 ( \* ) 在清單中。 **格式清單** 命令的結果顯示作業的 **Reason** 屬性值是空白的。</span><span class="sxs-lookup"><span data-stu-id="3050c-190">It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (\*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="3050c-191">第三個命令會進一步調查。</span><span class="sxs-lookup"><span data-stu-id="3050c-191">The third command investigates more.</span></span> <span data-ttu-id="3050c-192">它會使用「 **取得工作** 」命令來取得工作，然後使用管線運算子將整個工作物件傳送至 **格式清單** Cmdlet，此 Cmdlet 會將工作的所有屬性顯示在清單中。工作物件中所有屬性的顯示會顯示作業包含名為 Job2 的子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-192">It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="3050c-193">第四個命令使用 **Get-Job** ，取得代表 Job2 子工作的工作物件。</span><span class="sxs-lookup"><span data-stu-id="3050c-193">The fourth command uses **Get-Job** to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="3050c-194">這是命令實際於其中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-194">This is the job in which the command actually ran.</span></span> <span data-ttu-id="3050c-195">它會使用點方法來取得 **JobStateInfo** 屬性的 **Reason** 屬性。結果顯示作業因為拒絕存取錯誤而失敗。</span><span class="sxs-lookup"><span data-stu-id="3050c-195">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="3050c-196">在此情況下，使用者在啟動 PowerShell 時忘記使用 [以系統管理員身分執行] 選項。因為背景工作會使用 PowerShell 的遠端功能，所以必須將電腦設定為遠端執行作業，即使是在本機電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-196">In this case, the user forgot to use the Run as administrator option when starting PowerShell.Because background jobs use the remoting features of PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.</span></span>

### <span data-ttu-id="3050c-197">範例10：取得篩選的結果</span><span class="sxs-lookup"><span data-stu-id="3050c-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="3050c-198">這個範例示範如何使用 *Filter* 參數取得工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-198">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="3050c-199">*Filter* 參數 (在 Windows PowerShell 3.0 中引進) 只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-199">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="3050c-200">第一個命令會使用 **Workflow** 關鍵字來建立 WFProcess 工作流程。</span><span class="sxs-lookup"><span data-stu-id="3050c-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span>

<span data-ttu-id="3050c-201">第二個命令會使用 WFProcess 工作流程的 *AsJob* 參數，以背景工作的形式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="3050c-201">The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="3050c-202">它使用工作流程的 *JobName* 參數指定工作的名稱，以及使用工作流程的 *PSPrivateMetadata* 參數指定自訂識別碼。</span><span class="sxs-lookup"><span data-stu-id="3050c-202">It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.</span></span>

<span data-ttu-id="3050c-203">第三個命令使用 *Get-Job* 的 **Filter** 參數，利用 *PSPrivateMetadata* 參數中指定的自訂識別碼來取得工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-203">The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.</span></span>

### <span data-ttu-id="3050c-204">範例11：取得子作業的相關資訊</span><span class="sxs-lookup"><span data-stu-id="3050c-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="3050c-205">這個範例示範使用 *Get-Job* Cmdlet 的 *IncludeChildJob* 和 **ChildJobState** 參數的效果。</span><span class="sxs-lookup"><span data-stu-id="3050c-205">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="3050c-206">第一個命令取得目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="3050c-207">輸出包含背景工作、遠端工作，以及已排程工作的數個執行個體。</span><span class="sxs-lookup"><span data-stu-id="3050c-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="3050c-208">遠端工作 (Job4) 似乎已失敗。</span><span class="sxs-lookup"><span data-stu-id="3050c-208">The remote job, Job4, appears to have failed.</span></span>

<span data-ttu-id="3050c-209">第二個命令使用 *Get-Job* 的 **IncludeChildJob** 參數。</span><span class="sxs-lookup"><span data-stu-id="3050c-209">The second command uses the *IncludeChildJob* parameter of **Get-Job** .</span></span> <span data-ttu-id="3050c-210">輸出會加入所有具有子工作的工作的子工作。在此情況下，修改後的輸出會顯示只有 Job4 的 Job5 子工作失敗。</span><span class="sxs-lookup"><span data-stu-id="3050c-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span>

<span data-ttu-id="3050c-211">第三個命令使用 *ChildJobState* 參數，其值為 failed。輸出會包含所有父工作，以及只有失敗的子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-211">The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span>

<span data-ttu-id="3050c-212">第四個命令會使用作業的 **JobStateInfo** 屬性及其 **Reason** 屬性，來探索 Job5 失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="3050c-212">The fourth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

## <span data-ttu-id="3050c-213">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3050c-213">PARAMETERS</span></span>

### <span data-ttu-id="3050c-214">-After</span><span class="sxs-lookup"><span data-stu-id="3050c-214">-After</span></span>

<span data-ttu-id="3050c-215">取得在指定日期和時間之後結束的已完成工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-215">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="3050c-216">輸入 **datetime** 物件，例如 Get-Date Cmdlet 所傳回的物件，或是可轉換成 **DateTime** 物件的字串，例如 `Dec 1, 2012 2:00 AM` 或 `11/06` 。</span><span class="sxs-lookup"><span data-stu-id="3050c-216">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="3050c-217">這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-217">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="3050c-218">它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-218">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="3050c-219">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="3050c-219">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3050c-220">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-221">-Before</span><span class="sxs-lookup"><span data-stu-id="3050c-221">-Before</span></span>

<span data-ttu-id="3050c-222">取得在指定日期和時間之前結束的已完成工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-222">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="3050c-223">輸入 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="3050c-223">Enter a **DateTime** object.</span></span>

<span data-ttu-id="3050c-224">這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-224">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="3050c-225">它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-225">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="3050c-226">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="3050c-226">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3050c-227">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-228">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="3050c-228">-ChildJobState</span></span>

<span data-ttu-id="3050c-229">只取得具有指定狀態的子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-229">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="3050c-230">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="3050c-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3050c-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="3050c-231">NotStarted</span></span>
- <span data-ttu-id="3050c-232">執行中</span><span class="sxs-lookup"><span data-stu-id="3050c-232">Running</span></span>
- <span data-ttu-id="3050c-233">Completed</span><span class="sxs-lookup"><span data-stu-id="3050c-233">Completed</span></span>
- <span data-ttu-id="3050c-234">失敗</span><span class="sxs-lookup"><span data-stu-id="3050c-234">Failed</span></span>
- <span data-ttu-id="3050c-235">已停止</span><span class="sxs-lookup"><span data-stu-id="3050c-235">Stopped</span></span>
- <span data-ttu-id="3050c-236">封鎖</span><span class="sxs-lookup"><span data-stu-id="3050c-236">Blocked</span></span>
- <span data-ttu-id="3050c-237">暫止</span><span class="sxs-lookup"><span data-stu-id="3050c-237">Suspended</span></span>
- <span data-ttu-id="3050c-238">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="3050c-238">Disconnected</span></span>
- <span data-ttu-id="3050c-239">Suspending</span><span class="sxs-lookup"><span data-stu-id="3050c-239">Suspending</span></span>
- <span data-ttu-id="3050c-240">停止中</span><span class="sxs-lookup"><span data-stu-id="3050c-240">Stopping</span></span>

<span data-ttu-id="3050c-241">根據預設， **Get-Job** 無法取得子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-241">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="3050c-242">藉由使用 *IncludeChildJob* 參數， **取得工作會取得** 所有子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-242">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="3050c-243">如果您使用 *ChildJobState* 參數， *IncludeChildJob* 參數就沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="3050c-243">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="3050c-244">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-245">-Command</span><span class="sxs-lookup"><span data-stu-id="3050c-245">-Command</span></span>

<span data-ttu-id="3050c-246">將命令陣列指定為字串。</span><span class="sxs-lookup"><span data-stu-id="3050c-246">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="3050c-247">此 Cmdlet 會取得包含指定命令的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-247">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="3050c-248">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-248">The default is all jobs.</span></span>
<span data-ttu-id="3050c-249">您可以使用萬用字元來指定命令模式。</span><span class="sxs-lookup"><span data-stu-id="3050c-249">You can use wildcard characters to specify a command pattern.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="3050c-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="3050c-250">-Filter</span></span>

<span data-ttu-id="3050c-251">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="3050c-251">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="3050c-252">此 Cmdlet 會取得符合所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-252">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="3050c-253">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="3050c-253">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="3050c-254">這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-254">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="3050c-255">它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-255">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="3050c-256">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="3050c-256">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3050c-257">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3050c-258">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="3050c-258">-HasMoreData</span></span>

<span data-ttu-id="3050c-259">指出此 Cmdlet 是否只會取得具有指定之 **HasMoreData** 屬性值的作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-259">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="3050c-260">**HasMoreData** 屬性會指出是否已在目前工作階段中收到所有的工作結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-260">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="3050c-261">若要取得具有更多結果的工作，請指定 $True 的值。</span><span class="sxs-lookup"><span data-stu-id="3050c-261">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="3050c-262">若要取得沒有其他結果的工作，請指定 $False 的值。</span><span class="sxs-lookup"><span data-stu-id="3050c-262">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="3050c-263">若要取得作業的結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3050c-263">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="3050c-264">當您使用 **Receive-Job** Cmdlet 時，它會從記憶體內部的會話特定儲存體中刪除它傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-264">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="3050c-265">當它傳回目前會話中的所有工作結果時，它會將工作的 **HasMoreData** 屬性值設定為 $False) ，以指出它在目前的會話中沒有其他作業的結果。</span><span class="sxs-lookup"><span data-stu-id="3050c-265">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="3050c-266">使用 *Receive-Job* 的 **Keep** 參數，來防止 **Receive-Job** 刪除結果以及變更 **HasMoreData** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="3050c-266">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span> <span data-ttu-id="3050c-267">如需詳細資訊，請鍵入 `Get-Help Receive-Job`。</span><span class="sxs-lookup"><span data-stu-id="3050c-267">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="3050c-268">**HasMoreData** 屬性是目前工作階段特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="3050c-268">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="3050c-269">如果自訂工作類型的結果儲存在會話外部，例如將工作結果儲存在磁片上的排程工作類型，您可以在不同的會話中使用 **Receive 作業指令程式** ，以再次取得工作結果，即使 **HasMoreData** 的值為 $False。</span><span class="sxs-lookup"><span data-stu-id="3050c-269">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span> <span data-ttu-id="3050c-270">如需詳細資訊，請參閱自訂工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="3050c-270">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="3050c-271">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-272">-Id</span><span class="sxs-lookup"><span data-stu-id="3050c-272">-Id</span></span>

<span data-ttu-id="3050c-273">指定此 Cmdlet 取得之作業的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="3050c-273">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="3050c-274">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-274">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="3050c-275">它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3050c-275">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="3050c-276">您可以輸入一或多個以逗號分隔的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3050c-276">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="3050c-277">若要尋找作業的識別碼，請輸入 `Get-Job` 但不使用參數。</span><span class="sxs-lookup"><span data-stu-id="3050c-277">To find the ID of a job, type `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-278">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="3050c-278">-IncludeChildJob</span></span>

<span data-ttu-id="3050c-279">指出除了父作業之外，此 Cmdlet 會傳回子工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-279">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="3050c-280">此參數特別適用于調查工作流程工作，其中的 **Get 作業** 會傳回容器父工作和作業失敗，因為失敗的原因會儲存于子工作的屬性中。</span><span class="sxs-lookup"><span data-stu-id="3050c-280">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="3050c-281">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-282">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="3050c-282">-InstanceId</span></span>

<span data-ttu-id="3050c-283">指定此 Cmdlet 取得之作業的實例識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="3050c-283">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="3050c-284">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-284">The default is all jobs.</span></span>

<span data-ttu-id="3050c-285">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-285">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="3050c-286">若要尋找工作的執行個體識別碼，請使用 **Get-Job** 。</span><span class="sxs-lookup"><span data-stu-id="3050c-286">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="3050c-287">-Name</span><span class="sxs-lookup"><span data-stu-id="3050c-287">-Name</span></span>

<span data-ttu-id="3050c-288">指定此 Cmdlet 取得之作業的實例易記名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="3050c-288">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="3050c-289">輸入工作名稱，或使用萬用字元來輸入工作名稱模式。</span><span class="sxs-lookup"><span data-stu-id="3050c-289">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="3050c-290">根據預設， **Get-Job** 會取得目前工作階段中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-290">By default, **Get-Job** gets all jobs in the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="3050c-291">-Newest</span><span class="sxs-lookup"><span data-stu-id="3050c-291">-Newest</span></span>

<span data-ttu-id="3050c-292">指定要取得的作業數。</span><span class="sxs-lookup"><span data-stu-id="3050c-292">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="3050c-293">此 Cmdlet 會取得最近結束的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-293">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="3050c-294">*Newest* 參數不會依結束時間順序排序或傳回最新的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-294">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="3050c-295">若要排序輸出，請使用 Sort-Object Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3050c-295">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="3050c-296">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="3050c-296">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3050c-297">-State</span><span class="sxs-lookup"><span data-stu-id="3050c-297">-State</span></span>

<span data-ttu-id="3050c-298">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="3050c-298">Specifies a job state.</span></span>
<span data-ttu-id="3050c-299">此 Cmdlet 只會取得處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-299">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="3050c-300">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="3050c-300">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3050c-301">NotStarted</span><span class="sxs-lookup"><span data-stu-id="3050c-301">NotStarted</span></span>
- <span data-ttu-id="3050c-302">執行中</span><span class="sxs-lookup"><span data-stu-id="3050c-302">Running</span></span>
- <span data-ttu-id="3050c-303">Completed</span><span class="sxs-lookup"><span data-stu-id="3050c-303">Completed</span></span>
- <span data-ttu-id="3050c-304">失敗</span><span class="sxs-lookup"><span data-stu-id="3050c-304">Failed</span></span>
- <span data-ttu-id="3050c-305">已停止</span><span class="sxs-lookup"><span data-stu-id="3050c-305">Stopped</span></span>
- <span data-ttu-id="3050c-306">封鎖</span><span class="sxs-lookup"><span data-stu-id="3050c-306">Blocked</span></span>
- <span data-ttu-id="3050c-307">暫止</span><span class="sxs-lookup"><span data-stu-id="3050c-307">Suspended</span></span>
- <span data-ttu-id="3050c-308">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="3050c-308">Disconnected</span></span>
- <span data-ttu-id="3050c-309">Suspending</span><span class="sxs-lookup"><span data-stu-id="3050c-309">Suspending</span></span>
- <span data-ttu-id="3050c-310">停止中</span><span class="sxs-lookup"><span data-stu-id="3050c-310">Stopping</span></span>

<span data-ttu-id="3050c-311">根據預設， **Get-Job** 會取得目前工作階段中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="3050c-311">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="3050c-312">如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。</span><span class="sxs-lookup"><span data-stu-id="3050c-312">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="3050c-313">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3050c-313">CommonParameters</span></span>

<span data-ttu-id="3050c-314">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3050c-314">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3050c-315">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3050c-315">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3050c-316">輸入</span><span class="sxs-lookup"><span data-stu-id="3050c-316">INPUTS</span></span>

### <span data-ttu-id="3050c-317">無</span><span class="sxs-lookup"><span data-stu-id="3050c-317">None</span></span>

<span data-ttu-id="3050c-318">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3050c-318">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3050c-319">輸出</span><span class="sxs-lookup"><span data-stu-id="3050c-319">OUTPUTS</span></span>

### <span data-ttu-id="3050c-320">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="3050c-320">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="3050c-321">此 Cmdlet 會傳回代表會話中之作業的物件。</span><span class="sxs-lookup"><span data-stu-id="3050c-321">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="3050c-322">注意</span><span class="sxs-lookup"><span data-stu-id="3050c-322">NOTES</span></span>

* <span data-ttu-id="3050c-323">工作的 **PSJobTypeName** 屬性會指出工作的工作類型。</span><span class="sxs-lookup"><span data-stu-id="3050c-323">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="3050c-324">屬性值是由工作類型作者所決定。</span><span class="sxs-lookup"><span data-stu-id="3050c-324">The property value is determined by the job type author.</span></span> <span data-ttu-id="3050c-325">下列清單顯示常見的工作類型。</span><span class="sxs-lookup"><span data-stu-id="3050c-325">The following list shows common job types.</span></span>

  - <span data-ttu-id="3050c-326">**BackgroundJob** 。</span><span class="sxs-lookup"><span data-stu-id="3050c-326">**BackgroundJob** .</span></span>
<span data-ttu-id="3050c-327">使用 **啟動工作** 啟動的本機作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-327">Local job started by using **Start-Job** .</span></span>

  - <span data-ttu-id="3050c-328">**RemoteJob** 。</span><span class="sxs-lookup"><span data-stu-id="3050c-328">**RemoteJob** .</span></span>
<span data-ttu-id="3050c-329">使用 Invoke-Command Cmdlet 的 *AsJob* 參數在 **PSSession** 中啟動作業。</span><span class="sxs-lookup"><span data-stu-id="3050c-329">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

## <span data-ttu-id="3050c-330">相關連結</span><span class="sxs-lookup"><span data-stu-id="3050c-330">RELATED LINKS</span></span>

[<span data-ttu-id="3050c-331">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3050c-331">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3050c-332">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="3050c-332">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="3050c-333">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="3050c-333">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="3050c-334">Start-Job</span><span class="sxs-lookup"><span data-stu-id="3050c-334">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="3050c-335">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="3050c-335">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="3050c-336">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3050c-336">Wait-Job</span></span>](Wait-Job.md)
