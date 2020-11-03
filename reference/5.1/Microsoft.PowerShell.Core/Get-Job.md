---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202303"
---
# <span data-ttu-id="db5d9-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-103">Get-Job</span></span>

## <span data-ttu-id="db5d9-104">概要</span><span class="sxs-lookup"><span data-stu-id="db5d9-104">SYNOPSIS</span></span>
<span data-ttu-id="db5d9-105">取得目前會話中正在執行的 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="db5d9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="db5d9-106">SYNTAX</span></span>

### <span data-ttu-id="db5d9-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="db5d9-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="db5d9-108">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="db5d9-108">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="db5d9-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="db5d9-109">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="db5d9-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="db5d9-110">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="db5d9-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="db5d9-111">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="db5d9-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="db5d9-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="db5d9-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="db5d9-113">DESCRIPTION</span></span>

<span data-ttu-id="db5d9-114">**Get-Job** Cmdlet 會取得物件，這類物件代表已在目前工作階段中啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span>
<span data-ttu-id="db5d9-115">您可以使用「 **取得作業** 」來取得使用 Start-Job Cmdlet 或使用任何 Cmdlet 之 *AsJob* 參數啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="db5d9-116">如果沒有參數， **取得工作** 命令會取得目前會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="db5d9-117">您可以使用 **Get-Job** 的參數取得特定工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="db5d9-118">**Get-Job** 傳回的工作物件包含關於工作的有用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="db5d9-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span>
<span data-ttu-id="db5d9-119">若要取得結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="db5d9-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="db5d9-120">Windows PowerShell 背景工作是在背景執行的命令，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="db5d9-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span>
<span data-ttu-id="db5d9-121">一般而言，您會使用背景工作來執行複雜的命令，此命令需要很長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="db5d9-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span>
<span data-ttu-id="db5d9-122">如需 Windows PowerShell 中背景工作的詳細資訊，請參閱 about_Jobs。</span><span class="sxs-lookup"><span data-stu-id="db5d9-122">For more information about background jobs in Windows PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="db5d9-123">從 Windows PowerShell 3.0 開始， **Get-Job** Cmdlet 也可取得自訂工作類型 (例如工作流程工作和排程工作的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="db5d9-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="db5d9-124">若要尋找工作的工作類型，可使用工作的 **PSJobTypeName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="db5d9-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="db5d9-125">若要啟用 **Get 工作** 以取得自訂工作類型，請使用 Import-Module Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入會話中，再執行 [ **取得工作** ] 命令。</span><span class="sxs-lookup"><span data-stu-id="db5d9-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="db5d9-126">如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。</span><span class="sxs-lookup"><span data-stu-id="db5d9-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="db5d9-127">範例</span><span class="sxs-lookup"><span data-stu-id="db5d9-127">EXAMPLES</span></span>

### <span data-ttu-id="db5d9-128">範例1：取得在目前會話中啟動的所有背景工作</span><span class="sxs-lookup"><span data-stu-id="db5d9-128">Example 1: Get all background jobs started in the current session</span></span>

```
PS C:\> Get-Job
```

<span data-ttu-id="db5d9-129">這個命令會取得目前工作階段中啟動的所有背景工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="db5d9-130">它不會包含在其他工作階段中建立的工作，即使這類工作是在本機電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="db5d9-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="db5d9-131">範例2：使用實例識別碼停止作業</span><span class="sxs-lookup"><span data-stu-id="db5d9-131">Example 2: Stop a job by using an instance ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

<span data-ttu-id="db5d9-132">這些命令示範如何取得工作的執行個體識別碼，然後使用它來停止工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="db5d9-133">與工作名稱 (這不是唯一的) 不同，執行個體識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="db5d9-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

### <span data-ttu-id="db5d9-134">範例3：取得包含特定命令的工作</span><span class="sxs-lookup"><span data-stu-id="db5d9-134">Example 3: Get jobs that include a specific command</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

<span data-ttu-id="db5d9-135">此命令會取得系統上包含 Get-Process 命令的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-135">This command gets the jobs on the system that include a Get-Process command.</span></span>
<span data-ttu-id="db5d9-136">命令使用 *Get-Job* 的 **Command** 參數限制抓取的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-136">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span>
<span data-ttu-id="db5d9-137">命令使用萬用字元 ( \* ) 來取得命令字串中任何位置包含 **取得處理** 程式命令的作業。</span><span class="sxs-lookup"><span data-stu-id="db5d9-137">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="db5d9-138">範例4：使用管線取得包含特定命令的作業</span><span class="sxs-lookup"><span data-stu-id="db5d9-138">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

<span data-ttu-id="db5d9-139">如同上一個範例中的命令，此命令會取得系統上包含 **Get 進程** 命令的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-139">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span>
<span data-ttu-id="db5d9-140">命令使用管線運算子 (|) 將字串（以引號括住）傳送至「 **取得工作** 」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="db5d9-140">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span>
<span data-ttu-id="db5d9-141">它等同於前一個命令。</span><span class="sxs-lookup"><span data-stu-id="db5d9-141">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="db5d9-142">範例5：取得尚未啟動的工作</span><span class="sxs-lookup"><span data-stu-id="db5d9-142">Example 5: Get jobs that have not been started</span></span>

```
PS C:\> Get-Job -State NotStarted
```

<span data-ttu-id="db5d9-143">這個命令只會取得已建立但尚未啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-143">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="db5d9-144">這包括已排定在未來執行的工作以及尚未排程的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-144">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="db5d9-145">範例6：取得尚未指派名稱的工作</span><span class="sxs-lookup"><span data-stu-id="db5d9-145">Example 6: Get jobs that have not been assigned a name</span></span>

```
PS C:\> Get-Job -Name Job*
```

<span data-ttu-id="db5d9-146">此命令會取得工作名稱以 job 開頭的所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-146">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="db5d9-147">因為 job \<number\> 是作業的預設名稱，所以此命令會取得所有沒有明確指派名稱的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-147">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="db5d9-148">範例7：使用工作物件來代表命令中的工作</span><span class="sxs-lookup"><span data-stu-id="db5d9-148">Example 7: Use a job object to represent the job in a command</span></span>

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="db5d9-149">這個範例示範如何使用 **Get-Job** 取得工作物件，然後示範如何使用該工作物件來代表命令中的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-149">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

### <span data-ttu-id="db5d9-150">範例8：取得所有工作，包括其他方法啟動的作業</span><span class="sxs-lookup"><span data-stu-id="db5d9-150">Example 8: Get all jobs including jobs started by a different method</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="db5d9-151">這個範例示範，即使是使用不同的方法啟動， **Get 工作** Cmdlet 也可以取得在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-151">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

### <span data-ttu-id="db5d9-152">範例9：調查失敗的作業</span><span class="sxs-lookup"><span data-stu-id="db5d9-152">Example 9: Investigate a failed job</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
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

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

<span data-ttu-id="db5d9-153">此命令示範如何使用工作物件，該工作物件會傳回工作物件來調查工作 **失敗的原因** 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-153">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="db5d9-154">它也會示範如何取得每個工作的子工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-154">It also shows how to get the child jobs of each job.</span></span>

### <span data-ttu-id="db5d9-155">範例10：取得篩選的結果</span><span class="sxs-lookup"><span data-stu-id="db5d9-155">Example 10: Get filtered results</span></span>

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="db5d9-156">這個範例示範如何使用 *Filter* 參數取得工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-156">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="db5d9-157">*Filter* 參數 (在 Windows PowerShell 3.0 中引進) 只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-157">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

### <span data-ttu-id="db5d9-158">範例11：取得子作業的相關資訊</span><span class="sxs-lookup"><span data-stu-id="db5d9-158">Example 11: Get information about child jobs</span></span>

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
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

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="db5d9-159">這個範例示範使用 *Get-Job* Cmdlet 的 *IncludeChildJob* 和 **ChildJobState** 參數的效果。</span><span class="sxs-lookup"><span data-stu-id="db5d9-159">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

## <span data-ttu-id="db5d9-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="db5d9-160">PARAMETERS</span></span>

### <span data-ttu-id="db5d9-161">-After</span><span class="sxs-lookup"><span data-stu-id="db5d9-161">-After</span></span>

<span data-ttu-id="db5d9-162">取得在指定日期和時間之後結束的已完成工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-162">Gets completed jobs that ended after the specified date and time.</span></span>
<span data-ttu-id="db5d9-163">輸入 **datetime** 物件，例如 Get-Date Cmdlet 所傳回的物件，或是可轉換成 **DateTime** 物件的字串，例如 `Dec 1, 2012 2:00 AM` 或 `11/06` 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-163">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="db5d9-164">這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-164">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="db5d9-165">它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-165">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="db5d9-166">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="db5d9-166">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="db5d9-167">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-167">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db5d9-168">-Before</span><span class="sxs-lookup"><span data-stu-id="db5d9-168">-Before</span></span>

<span data-ttu-id="db5d9-169">取得在指定日期和時間之前結束的已完成工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-169">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="db5d9-170">輸入 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="db5d9-170">Enter a **DateTime** object.</span></span>

<span data-ttu-id="db5d9-171">這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-171">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="db5d9-172">它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-172">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="db5d9-173">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="db5d9-173">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="db5d9-174">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db5d9-175">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="db5d9-175">-ChildJobState</span></span>

<span data-ttu-id="db5d9-176">只取得具有指定狀態的子工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-176">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="db5d9-177">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="db5d9-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="db5d9-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="db5d9-178">NotStarted</span></span>
- <span data-ttu-id="db5d9-179">執行中</span><span class="sxs-lookup"><span data-stu-id="db5d9-179">Running</span></span>
- <span data-ttu-id="db5d9-180">Completed</span><span class="sxs-lookup"><span data-stu-id="db5d9-180">Completed</span></span>
- <span data-ttu-id="db5d9-181">失敗</span><span class="sxs-lookup"><span data-stu-id="db5d9-181">Failed</span></span>
- <span data-ttu-id="db5d9-182">已停止</span><span class="sxs-lookup"><span data-stu-id="db5d9-182">Stopped</span></span>
- <span data-ttu-id="db5d9-183">封鎖</span><span class="sxs-lookup"><span data-stu-id="db5d9-183">Blocked</span></span>
- <span data-ttu-id="db5d9-184">暫止</span><span class="sxs-lookup"><span data-stu-id="db5d9-184">Suspended</span></span>
- <span data-ttu-id="db5d9-185">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="db5d9-185">Disconnected</span></span>
- <span data-ttu-id="db5d9-186">Suspending</span><span class="sxs-lookup"><span data-stu-id="db5d9-186">Suspending</span></span>
- <span data-ttu-id="db5d9-187">停止中</span><span class="sxs-lookup"><span data-stu-id="db5d9-187">Stopping</span></span>

<span data-ttu-id="db5d9-188">根據預設， **Get-Job** 無法取得子工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-188">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="db5d9-189">藉由使用 *IncludeChildJob* 參數， **取得工作會取得** 所有子工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-189">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="db5d9-190">如果您使用 *ChildJobState* 參數， *IncludeChildJob* 參數就沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="db5d9-190">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="db5d9-191">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db5d9-192">-Command</span><span class="sxs-lookup"><span data-stu-id="db5d9-192">-Command</span></span>

<span data-ttu-id="db5d9-193">將命令陣列指定為字串。</span><span class="sxs-lookup"><span data-stu-id="db5d9-193">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="db5d9-194">此 Cmdlet 會取得包含指定命令的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-194">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="db5d9-195">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-195">The default is all jobs.</span></span>
<span data-ttu-id="db5d9-196">您可以使用萬用字元來指定命令模式。</span><span class="sxs-lookup"><span data-stu-id="db5d9-196">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="db5d9-197">-Filter</span><span class="sxs-lookup"><span data-stu-id="db5d9-197">-Filter</span></span>

<span data-ttu-id="db5d9-198">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="db5d9-198">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="db5d9-199">此 Cmdlet 會取得符合所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-199">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="db5d9-200">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="db5d9-200">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="db5d9-201">這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-201">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="db5d9-202">它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-202">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="db5d9-203">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="db5d9-203">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="db5d9-204">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="db5d9-205">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="db5d9-205">-HasMoreData</span></span>

<span data-ttu-id="db5d9-206">指出此 Cmdlet 是否只會取得具有指定之 **HasMoreData** 屬性值的作業。</span><span class="sxs-lookup"><span data-stu-id="db5d9-206">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="db5d9-207">**HasMoreData** 屬性會指出是否已在目前工作階段中收到所有的工作結果。</span><span class="sxs-lookup"><span data-stu-id="db5d9-207">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="db5d9-208">若要取得具有更多結果的工作，請指定 $True 的值。</span><span class="sxs-lookup"><span data-stu-id="db5d9-208">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="db5d9-209">若要取得沒有其他結果的工作，請指定 $False 的值。</span><span class="sxs-lookup"><span data-stu-id="db5d9-209">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="db5d9-210">若要取得作業的結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="db5d9-210">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="db5d9-211">當您使用 **Receive-Job** Cmdlet 時，它會從記憶體內部的會話特定儲存體中刪除它傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="db5d9-211">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span>
<span data-ttu-id="db5d9-212">當它傳回目前會話中的所有工作結果時，它會將工作的 **HasMoreData** 屬性值設定為 $False) ，以指出它在目前的會話中沒有其他作業的結果。</span><span class="sxs-lookup"><span data-stu-id="db5d9-212">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span>
<span data-ttu-id="db5d9-213">使用 *Receive-Job* 的 **Keep** 參數，來防止 **Receive-Job** 刪除結果以及變更 **HasMoreData** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="db5d9-213">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="db5d9-214">如需詳細資訊，請鍵入 `Get-Help Receive-Job`。</span><span class="sxs-lookup"><span data-stu-id="db5d9-214">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="db5d9-215">**HasMoreData** 屬性是目前工作階段特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="db5d9-215">The **HasMoreData** property is specific to the current session.</span></span>
<span data-ttu-id="db5d9-216">如果自訂工作類型的結果儲存在會話外部，例如將工作結果儲存在磁片上的排程工作類型，您可以在不同的會話中使用 **Receive 作業指令程式** ，以再次取得工作結果，即使 **HasMoreData** 的值為 $False。</span><span class="sxs-lookup"><span data-stu-id="db5d9-216">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span>
<span data-ttu-id="db5d9-217">如需詳細資訊，請參閱自訂工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="db5d9-217">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="db5d9-218">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-218">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db5d9-219">-Id</span><span class="sxs-lookup"><span data-stu-id="db5d9-219">-Id</span></span>

<span data-ttu-id="db5d9-220">指定此 Cmdlet 取得之作業的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="db5d9-220">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="db5d9-221">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-221">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="db5d9-222">它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="db5d9-222">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="db5d9-223">您可以輸入一或多個以逗號分隔的識別碼。</span><span class="sxs-lookup"><span data-stu-id="db5d9-223">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="db5d9-224">若要尋找作業的識別碼，請輸入 `Get-Job` 但不使用參數。</span><span class="sxs-lookup"><span data-stu-id="db5d9-224">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="db5d9-225">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="db5d9-225">-IncludeChildJob</span></span>

<span data-ttu-id="db5d9-226">指出除了父作業之外，此 Cmdlet 會傳回子工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-226">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="db5d9-227">此參數特別適用于調查工作流程工作，其中的 **Get 作業** 會傳回容器父工作和作業失敗，因為失敗的原因會儲存于子工作的屬性中。</span><span class="sxs-lookup"><span data-stu-id="db5d9-227">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="db5d9-228">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db5d9-229">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="db5d9-229">-InstanceId</span></span>

<span data-ttu-id="db5d9-230">指定此 Cmdlet 取得之作業的實例識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="db5d9-230">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="db5d9-231">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-231">The default is all jobs.</span></span>

<span data-ttu-id="db5d9-232">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-232">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="db5d9-233">若要尋找工作的執行個體識別碼，請使用 **Get-Job** 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-233">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="db5d9-234">-Name</span><span class="sxs-lookup"><span data-stu-id="db5d9-234">-Name</span></span>

<span data-ttu-id="db5d9-235">指定此 Cmdlet 取得之作業的實例易記名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="db5d9-235">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="db5d9-236">輸入工作名稱，或使用萬用字元來輸入工作名稱模式。</span><span class="sxs-lookup"><span data-stu-id="db5d9-236">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="db5d9-237">根據預設， **Get-Job** 會取得目前工作階段中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-237">By default, **Get-Job** gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="db5d9-238">-Newest</span><span class="sxs-lookup"><span data-stu-id="db5d9-238">-Newest</span></span>

<span data-ttu-id="db5d9-239">指定要取得的作業數。</span><span class="sxs-lookup"><span data-stu-id="db5d9-239">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="db5d9-240">此 Cmdlet 會取得最近結束的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-240">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="db5d9-241">*Newest* 參數不會依結束時間順序排序或傳回最新的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-241">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="db5d9-242">若要排序輸出，請使用 Sort-Object Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="db5d9-242">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="db5d9-243">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="db5d9-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="db5d9-244">-State</span><span class="sxs-lookup"><span data-stu-id="db5d9-244">-State</span></span>

<span data-ttu-id="db5d9-245">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="db5d9-245">Specifies a job state.</span></span>
<span data-ttu-id="db5d9-246">此 Cmdlet 只會取得處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-246">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="db5d9-247">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="db5d9-247">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="db5d9-248">NotStarted</span><span class="sxs-lookup"><span data-stu-id="db5d9-248">NotStarted</span></span>
- <span data-ttu-id="db5d9-249">執行中</span><span class="sxs-lookup"><span data-stu-id="db5d9-249">Running</span></span>
- <span data-ttu-id="db5d9-250">Completed</span><span class="sxs-lookup"><span data-stu-id="db5d9-250">Completed</span></span>
- <span data-ttu-id="db5d9-251">失敗</span><span class="sxs-lookup"><span data-stu-id="db5d9-251">Failed</span></span>
- <span data-ttu-id="db5d9-252">已停止</span><span class="sxs-lookup"><span data-stu-id="db5d9-252">Stopped</span></span>
- <span data-ttu-id="db5d9-253">封鎖</span><span class="sxs-lookup"><span data-stu-id="db5d9-253">Blocked</span></span>
- <span data-ttu-id="db5d9-254">暫止</span><span class="sxs-lookup"><span data-stu-id="db5d9-254">Suspended</span></span>
- <span data-ttu-id="db5d9-255">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="db5d9-255">Disconnected</span></span>
- <span data-ttu-id="db5d9-256">Suspending</span><span class="sxs-lookup"><span data-stu-id="db5d9-256">Suspending</span></span>
- <span data-ttu-id="db5d9-257">停止中</span><span class="sxs-lookup"><span data-stu-id="db5d9-257">Stopping</span></span>

<span data-ttu-id="db5d9-258">根據預設， **Get-Job** 會取得目前工作階段中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-258">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="db5d9-259">如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-259">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="db5d9-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="db5d9-260">CommonParameters</span></span>

<span data-ttu-id="db5d9-261">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="db5d9-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="db5d9-262">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="db5d9-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="db5d9-263">輸入</span><span class="sxs-lookup"><span data-stu-id="db5d9-263">INPUTS</span></span>

### <span data-ttu-id="db5d9-264">無</span><span class="sxs-lookup"><span data-stu-id="db5d9-264">None</span></span>

<span data-ttu-id="db5d9-265">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="db5d9-265">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="db5d9-266">輸出</span><span class="sxs-lookup"><span data-stu-id="db5d9-266">OUTPUTS</span></span>

### <span data-ttu-id="db5d9-267">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="db5d9-267">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="db5d9-268">此 Cmdlet 會傳回代表會話中之作業的物件。</span><span class="sxs-lookup"><span data-stu-id="db5d9-268">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="db5d9-269">注意</span><span class="sxs-lookup"><span data-stu-id="db5d9-269">NOTES</span></span>

* <span data-ttu-id="db5d9-270">工作的 **PSJobTypeName** 屬性會指出工作的工作類型。</span><span class="sxs-lookup"><span data-stu-id="db5d9-270">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="db5d9-271">屬性值是由工作類型作者所決定。</span><span class="sxs-lookup"><span data-stu-id="db5d9-271">The property value is determined by the job type author.</span></span> <span data-ttu-id="db5d9-272">下列清單顯示常見的工作類型。</span><span class="sxs-lookup"><span data-stu-id="db5d9-272">The following list shows common job types.</span></span>

  - <span data-ttu-id="db5d9-273">**BackgroundJob** 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-273">**BackgroundJob** .</span></span>
<span data-ttu-id="db5d9-274">使用 **啟動工作** 啟動的本機作業。</span><span class="sxs-lookup"><span data-stu-id="db5d9-274">Local job started by using **Start-Job** .</span></span>

  - <span data-ttu-id="db5d9-275">**RemoteJob** 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-275">**RemoteJob** .</span></span>
<span data-ttu-id="db5d9-276">使用 Invoke-Command Cmdlet 的 *AsJob* 參數在 **PSSession** 中啟動作業。</span><span class="sxs-lookup"><span data-stu-id="db5d9-276">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="db5d9-277">**PSWorkflowJob** 。</span><span class="sxs-lookup"><span data-stu-id="db5d9-277">**PSWorkflowJob** .</span></span>
<span data-ttu-id="db5d9-278">使用工作流程 *AsJob* 一般參數啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="db5d9-278">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="db5d9-279">相關連結</span><span class="sxs-lookup"><span data-stu-id="db5d9-279">RELATED LINKS</span></span>

[<span data-ttu-id="db5d9-280">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="db5d9-280">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="db5d9-281">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-281">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="db5d9-282">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-282">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="db5d9-283">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-283">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="db5d9-284">Start-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-284">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="db5d9-285">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-285">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="db5d9-286">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-286">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="db5d9-287">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="db5d9-287">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="db5d9-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="db5d9-288">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="db5d9-289">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="db5d9-289">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="db5d9-290">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="db5d9-290">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="db5d9-291">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="db5d9-291">about_Scheduled_Jobs</span></span>](../PSScheduledJob/About/about_Scheduled_Jobs.md)
