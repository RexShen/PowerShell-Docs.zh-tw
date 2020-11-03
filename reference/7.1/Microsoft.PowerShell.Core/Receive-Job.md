---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 51cf0abc1a6362122f18812cd90e59a6ca7dc4ab
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204823"
---
# <span data-ttu-id="4945a-103">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-103">Receive-Job</span></span>

## <span data-ttu-id="4945a-104">概要</span><span class="sxs-lookup"><span data-stu-id="4945a-104">SYNOPSIS</span></span>
<span data-ttu-id="4945a-105">取得目前會話中 PowerShell 背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-105">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="4945a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4945a-106">SYNTAX</span></span>

### <span data-ttu-id="4945a-107">Location (預設值)</span><span class="sxs-lookup"><span data-stu-id="4945a-107">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="4945a-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4945a-108">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="4945a-109">工作階段</span><span class="sxs-lookup"><span data-stu-id="4945a-109">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="4945a-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="4945a-110">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="4945a-111">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="4945a-111">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="4945a-112">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="4945a-112">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="4945a-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4945a-113">DESCRIPTION</span></span>

<span data-ttu-id="4945a-114">`Receive-Job`Cmdlet 會取得 PowerShell 背景工作的結果，例如使用 `Start-Job` Cmdlet 或任何 Cmdlet 的 **AsJob** 參數啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-114">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="4945a-115">您可以取得所有工作的結果，或是依據工作的名稱、識別碼、執行個體識別碼、電腦名稱、位置或工作階段，或藉由送出工作物件，來識別工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-115">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="4945a-116">當您啟動 PowerShell 背景工作時，工作會啟動，但是結果不會立即出現。</span><span class="sxs-lookup"><span data-stu-id="4945a-116">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="4945a-117">取而代之的是，命令會傳回代表背景工作的物件。</span><span class="sxs-lookup"><span data-stu-id="4945a-117">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="4945a-118">工作物件包含工作的相關實用資訊，但是不包含結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-118">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="4945a-119">此方法可讓您在工作執行時繼續在會話中工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-119">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="4945a-120">如需有關 PowerShell 中背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="4945a-120">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="4945a-121">此 `Receive-Job` Cmdlet 會取得提交命令時所產生的結果 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="4945a-121">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="4945a-122">如果結果尚未完成，您可以執行其他 `Receive-Job` 命令來取得剩餘的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-122">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="4945a-123">根據預設，在您收到工作結果之後，工作結果就會自系統中刪除，但是您可以使用 **Keep** 參數來儲存結果，以便再次接收這些結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-123">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="4945a-124">若要刪除工作結果，請 `Receive-Job` 再次執行命令，而不要使用 **Keep** 參數、關閉會話，或使用 `Remove-Job` Cmdlet 來刪除會話中的作業。</span><span class="sxs-lookup"><span data-stu-id="4945a-124">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="4945a-125">從 Windows PowerShell 3.0 開始， `Receive-Job` 也會取得自訂工作類型（例如工作流程工作和排程工作的實例）的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-125">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="4945a-126">若要讓 `Receive-Job` 能夠取得自訂工作類型的結果，請 `Receive-Job` 使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入到會話中，再執行命令。</span><span class="sxs-lookup"><span data-stu-id="4945a-126">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="4945a-127">如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。</span><span class="sxs-lookup"><span data-stu-id="4945a-127">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="4945a-128">範例</span><span class="sxs-lookup"><span data-stu-id="4945a-128">EXAMPLES</span></span>

### <span data-ttu-id="4945a-129">範例1：取得特定作業的結果</span><span class="sxs-lookup"><span data-stu-id="4945a-129">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="4945a-130">這些命令會使用的 **Job** 參數 `Receive-Job` 來取得特定工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-130">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="4945a-131">第一個命令會使用來啟動作業 `Start-Job` ，並將工作物件儲存在 `$job` 變數中。</span><span class="sxs-lookup"><span data-stu-id="4945a-131">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="4945a-132">第二個命令會使用 `Receive-Job` Cmdlet 來取得作業的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-132">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="4945a-133">它使用 **Job** 參數來指定工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-133">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="4945a-134">範例2：使用 Keep 參數</span><span class="sxs-lookup"><span data-stu-id="4945a-134">Example 2: Use the Keep parameter</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="4945a-135">此範例會將工作儲存在 `$job` 變數中，然後使用管線將工作傳送至 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4945a-135">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="4945a-136">此 `-Keep` 參數也會用來允許在第一次視圖之後再次取出所有匯總的資料流程資料。</span><span class="sxs-lookup"><span data-stu-id="4945a-136">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="4945a-137">範例3：取得數個背景工作的結果</span><span class="sxs-lookup"><span data-stu-id="4945a-137">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="4945a-138">當您使用的 **AsJob** 參數 `Invoke-Command` 啟動作業時，會在本機電腦上建立工作物件，即使工作是在遠端電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="4945a-138">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="4945a-139">因此，您是使用本機命令來管理工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-139">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="4945a-140">此外，當您使用 **AsJob** 時，PowerShell 會傳回一個工作物件，其中包含每個已啟動工作的子工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-140">Also, when you use **AsJob** , PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="4945a-141">在此情況下，此工作物件包含三個子工作，分別用於每部遠端電腦上的每個工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-141">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### <span data-ttu-id="4945a-142">範例4：取得多部遠端電腦上的背景工作結果</span><span class="sxs-lookup"><span data-stu-id="4945a-142">Example 4: Get results of background jobs on multiple remote computers</span></span>

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

<span data-ttu-id="4945a-143">這個範例示範如何取得在三部遠端電腦上執行之背景工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-143">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="4945a-144">與先前的範例不同的是，使用 `Invoke-Command` 來執行 `Start-Job` 命令實際上會在三部電腦上啟動三個獨立的工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-144">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="4945a-145">因此，此命令傳回了三個工作物件，分別代表在三部不同電腦的本機執行的三個工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-145">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="4945a-146">在最後一個命令中，因為 `$j` 是區域變數，所以腳本區塊會使用 **Using** 範圍修飾符來識別 `$j` 變數。</span><span class="sxs-lookup"><span data-stu-id="4945a-146">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="4945a-147">如需 **Using** 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](./About/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="4945a-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="4945a-148">範例5：存取子作業</span><span class="sxs-lookup"><span data-stu-id="4945a-148">Example 5: Access child jobs</span></span>

<span data-ttu-id="4945a-149">`-Keep`參數會保留作業的匯總資料流程狀態，以便再次查看。</span><span class="sxs-lookup"><span data-stu-id="4945a-149">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="4945a-150">如果沒有這個參數，則會在接收到作業時清除所有匯總的資料流程資料。</span><span class="sxs-lookup"><span data-stu-id="4945a-150">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="4945a-151">如需詳細資訊，請參閱 [about_Job_Details](About/about_Job_Details.md#child-jobs)</span><span class="sxs-lookup"><span data-stu-id="4945a-151">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="4945a-152">匯總的資料流程包含所有子作業的資料流程。</span><span class="sxs-lookup"><span data-stu-id="4945a-152">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="4945a-153">您仍然可以透過工作物件和子工作物件來觸及個別的資料串流。</span><span class="sxs-lookup"><span data-stu-id="4945a-153">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="4945a-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4945a-154">PARAMETERS</span></span>

### <span data-ttu-id="4945a-155">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="4945a-155">-AutoRemoveJob</span></span>

<span data-ttu-id="4945a-156">指出此 Cmdlet 會在傳回工作結果之後刪除工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-156">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="4945a-157">如果工作有更多結果，作業仍會被刪除，但會 `Receive-Job` 顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="4945a-157">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="4945a-158">這個參數只適用於自訂工作類型。</span><span class="sxs-lookup"><span data-stu-id="4945a-158">This parameter works only on custom job types.</span></span>
<span data-ttu-id="4945a-159">它是專為儲存工作的工作類型執行個體或工作階段外的類型 (例如排程工作的執行個體) 而設計。</span><span class="sxs-lookup"><span data-stu-id="4945a-159">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="4945a-160">如果沒有 **Wait** 參數，就不能使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="4945a-160">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="4945a-161">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4945a-161">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="4945a-162">-ComputerName</span></span>

<span data-ttu-id="4945a-163">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4945a-163">Specifies an array of names of computers.</span></span>

<span data-ttu-id="4945a-164">這個參數會從儲存在本機電腦上的工作結果中選取。</span><span class="sxs-lookup"><span data-stu-id="4945a-164">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="4945a-165">它不會取得在遠端電腦上執行之作業的資料。</span><span class="sxs-lookup"><span data-stu-id="4945a-165">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="4945a-166">若要取得儲存在遠端電腦上的工作結果，請使用 `Invoke-Command` Cmdlet `Receive-Job` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="4945a-166">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4945a-167">-Force</span><span class="sxs-lookup"><span data-stu-id="4945a-167">-Force</span></span>

<span data-ttu-id="4945a-168">指出當工作處於已 **暫停** 或已 **中斷** 連線的狀態時，此 Cmdlet 會繼續等候。</span><span class="sxs-lookup"><span data-stu-id="4945a-168">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="4945a-169">根據預設， **Wait** `Receive-Job` 當作業處於下列其中一種狀態時，的 wait 參數會傳回或結束等候：</span><span class="sxs-lookup"><span data-stu-id="4945a-169">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="4945a-170">Completed</span><span class="sxs-lookup"><span data-stu-id="4945a-170">Completed</span></span>
- <span data-ttu-id="4945a-171">失敗</span><span class="sxs-lookup"><span data-stu-id="4945a-171">Failed</span></span>
- <span data-ttu-id="4945a-172">已停止</span><span class="sxs-lookup"><span data-stu-id="4945a-172">Stopped</span></span>
- <span data-ttu-id="4945a-173">暫止</span><span class="sxs-lookup"><span data-stu-id="4945a-173">Suspended</span></span>
- <span data-ttu-id="4945a-174">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="4945a-174">Disconnected.</span></span>

<span data-ttu-id="4945a-175">只有當命令中也使用 **Wait** 參數時， **Force** 參數才有效。</span><span class="sxs-lookup"><span data-stu-id="4945a-175">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="4945a-176">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4945a-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-177">-Id</span><span class="sxs-lookup"><span data-stu-id="4945a-177">-Id</span></span>

<span data-ttu-id="4945a-178">指定識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="4945a-178">Specifies an array of IDs.</span></span>
<span data-ttu-id="4945a-179">此 Cmdlet 會取得具有指定識別碼之工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-179">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="4945a-180">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="4945a-181">與執行個體識別碼相比，它比較容易記住並輸入，但是它只有在目前的工作階段內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4945a-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="4945a-182">您可以輸入一或多個以逗號分隔的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4945a-182">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="4945a-183">若要尋找工作的識別碼，請使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="4945a-183">To find the ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="4945a-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4945a-184">-InstanceId</span></span>

<span data-ttu-id="4945a-185">指定執行階段識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="4945a-185">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="4945a-186">此 Cmdlet 會取得具有指定實例識別碼之工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-186">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="4945a-187">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="4945a-188">若要尋找工作的實例識別碼，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4945a-188">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-189">-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-189">-Job</span></span>

<span data-ttu-id="4945a-190">指定要為其抓取結果的工作。</span><span class="sxs-lookup"><span data-stu-id="4945a-190">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="4945a-191">請輸入包含工作的變數，或輸入可取得工作的命令。</span><span class="sxs-lookup"><span data-stu-id="4945a-191">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="4945a-192">您也可以使用管線將工作物件傳送至 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="4945a-192">You can also pipe a job object to `Receive-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-193">-Keep</span><span class="sxs-lookup"><span data-stu-id="4945a-193">-Keep</span></span>

<span data-ttu-id="4945a-194">指出此 Cmdlet 會將匯總的資料流程資料儲存在系統中，即使在您收到它們之後也是如此。</span><span class="sxs-lookup"><span data-stu-id="4945a-194">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="4945a-195">依預設，會在使用之後清除匯總的資料流程資料 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="4945a-195">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="4945a-196">關閉會話，或使用 Cmdlet 移除作業也會 `Remove-Job` 刪除匯總的資料流程資料。</span><span class="sxs-lookup"><span data-stu-id="4945a-196">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-197">-Location</span><span class="sxs-lookup"><span data-stu-id="4945a-197">-Location</span></span>

<span data-ttu-id="4945a-198">指定位置的陣列。</span><span class="sxs-lookup"><span data-stu-id="4945a-198">Specifies an array of locations.</span></span>
<span data-ttu-id="4945a-199">此 Cmdlet 只會取得指定位置中的工作結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-199">This cmdlet gets only the results of jobs in the specified locations.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-200">-Name</span><span class="sxs-lookup"><span data-stu-id="4945a-200">-Name</span></span>

<span data-ttu-id="4945a-201">指定好記名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="4945a-201">Specifies an array of friendly names.</span></span>
<span data-ttu-id="4945a-202">此 Cmdlet 會取得具有指定之名稱的工作結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-202">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="4945a-203">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4945a-203">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="4945a-204">-NoRecurse</span><span class="sxs-lookup"><span data-stu-id="4945a-204">-NoRecurse</span></span>

<span data-ttu-id="4945a-205">指出此 Cmdlet 只會從指定的工作取得結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-205">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="4945a-206">根據預設， `Receive-Job` 也會取得指定之工作的所有子工作的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-206">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-207">-Session</span><span class="sxs-lookup"><span data-stu-id="4945a-207">-Session</span></span>

<span data-ttu-id="4945a-208">指定會話的陣列。</span><span class="sxs-lookup"><span data-stu-id="4945a-208">Specifies an array of sessions.</span></span>
<span data-ttu-id="4945a-209">此 Cmdlet 會取得在指定的 PowerShell 會話中執行 ( **PSSession** ) 的工作結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-209">This cmdlet gets the results of jobs that were run in the specified PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="4945a-210">輸入包含 **pssession** 的變數，或輸入可取得 **pssession** 的命令，例如 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="4945a-210">Enter a variable that contains the **PSSession** or a command that gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-211">-Wait</span><span class="sxs-lookup"><span data-stu-id="4945a-211">-Wait</span></span>

<span data-ttu-id="4945a-212">指出此 Cmdlet 會抑制命令提示字元，直到收到所有工作結果為止。</span><span class="sxs-lookup"><span data-stu-id="4945a-212">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="4945a-213">根據預設，會 `Receive-Job` 立即傳回可用的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-213">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="4945a-214">**Wait** 參數預設會等到工作處於下列其中一種狀態：</span><span class="sxs-lookup"><span data-stu-id="4945a-214">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="4945a-215">Completed</span><span class="sxs-lookup"><span data-stu-id="4945a-215">Completed</span></span>
- <span data-ttu-id="4945a-216">失敗</span><span class="sxs-lookup"><span data-stu-id="4945a-216">Failed</span></span>
- <span data-ttu-id="4945a-217">已停止</span><span class="sxs-lookup"><span data-stu-id="4945a-217">Stopped</span></span>
- <span data-ttu-id="4945a-218">暫止</span><span class="sxs-lookup"><span data-stu-id="4945a-218">Suspended</span></span>
- <span data-ttu-id="4945a-219">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="4945a-219">Disconnected.</span></span>

<span data-ttu-id="4945a-220">若要指示 **wait** 參數在工作狀態為 [已暫停] 或 [已中斷連線] 時繼續等待，請使用 **Force** 參數搭配 **Wait** 參數。</span><span class="sxs-lookup"><span data-stu-id="4945a-220">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="4945a-221">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4945a-221">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="4945a-222">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="4945a-222">-WriteEvents</span></span>

<span data-ttu-id="4945a-223">指出此 Cmdlet 會在等候工作完成時，回報工作狀態中的變更。</span><span class="sxs-lookup"><span data-stu-id="4945a-223">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="4945a-224">只有當命令中使用了 **Wait** 參數並且省略了 **Keep** 參數時，這個參數才有效。</span><span class="sxs-lookup"><span data-stu-id="4945a-224">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="4945a-225">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4945a-225">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-226">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="4945a-226">-WriteJobInResults</span></span>

<span data-ttu-id="4945a-227">指出此 Cmdlet 會傳回工作物件，後面接著結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-227">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="4945a-228">只有當命令中使用了 **Wait** 參數並且省略了 **Keep** 參數時，這個參數才有效。</span><span class="sxs-lookup"><span data-stu-id="4945a-228">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="4945a-229">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="4945a-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4945a-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4945a-230">CommonParameters</span></span>

<span data-ttu-id="4945a-231">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4945a-231">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4945a-232">如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4945a-232">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4945a-233">輸入</span><span class="sxs-lookup"><span data-stu-id="4945a-233">INPUTS</span></span>

### <span data-ttu-id="4945a-234">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="4945a-234">System.Management.Automation.Job</span></span>

<span data-ttu-id="4945a-235">您可以透過管線將工作物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4945a-235">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="4945a-236">輸出</span><span class="sxs-lookup"><span data-stu-id="4945a-236">OUTPUTS</span></span>

### <span data-ttu-id="4945a-237">PSObject</span><span class="sxs-lookup"><span data-stu-id="4945a-237">PSObject</span></span>

<span data-ttu-id="4945a-238">此 Cmdlet 會傳回工作中命令的結果。</span><span class="sxs-lookup"><span data-stu-id="4945a-238">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="4945a-239">注意</span><span class="sxs-lookup"><span data-stu-id="4945a-239">NOTES</span></span>

## <span data-ttu-id="4945a-240">相關連結</span><span class="sxs-lookup"><span data-stu-id="4945a-240">RELATED LINKS</span></span>

[<span data-ttu-id="4945a-241">Get-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="4945a-242">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4945a-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="4945a-243">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-243">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="4945a-244">Start-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-244">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="4945a-245">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-245">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="4945a-246">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="4945a-246">Wait-Job</span></span>](Wait-Job.md)

