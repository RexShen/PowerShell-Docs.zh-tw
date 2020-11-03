---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202675"
---
# <span data-ttu-id="bf6ba-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-103">Resume-Job</span></span>

## <span data-ttu-id="bf6ba-104">概要</span><span class="sxs-lookup"><span data-stu-id="bf6ba-104">SYNOPSIS</span></span>
<span data-ttu-id="bf6ba-105">重新啟動暫停的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="bf6ba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf6ba-106">SYNTAX</span></span>

### <span data-ttu-id="bf6ba-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="bf6ba-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf6ba-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="bf6ba-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf6ba-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="bf6ba-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf6ba-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="bf6ba-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf6ba-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="bf6ba-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf6ba-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="bf6ba-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bf6ba-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bf6ba-113">DESCRIPTION</span></span>
<span data-ttu-id="bf6ba-114">**Resume** 工作 Cmdlet 會繼續已暫停的工作流程工作，例如使用 Suspend-Job Cmdlet 或 About_Suspend 工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-114">The **Resume-Job** cmdlet resumes a workflow job that was suspended, such as by using the Suspend-Job cmdlet or the about_Suspend-Workflow activity.</span></span>
<span data-ttu-id="bf6ba-115">當工作流程工作繼續時，工作引擎會從儲存的資源（例如檢查點）重建狀態、中繼資料和輸出。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span>
<span data-ttu-id="bf6ba-116">作業會在沒有任何狀態或資料遺失的情況下重新開機。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="bf6ba-117">工作狀態會從 **Suspended** 變更為 **Running** 。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-117">The job state is changed from **Suspended** to **Running** .</span></span>

<span data-ttu-id="bf6ba-118">使用 **Resume 工作** 的參數，依名稱、識別碼、實例識別碼選取工作，或使用管線將工作物件（例如 Get-Job Cmdlet 所傳回的工作物件）選取為 **繼續作業** 。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-118">Use the parameters of **Resume-Job** to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the Get-Job cmdlet, to **Resume-Job** .</span></span>
<span data-ttu-id="bf6ba-119">您也可以使用屬性篩選來選取要繼續的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="bf6ba-120">依照預設， **Resume-Job** 會立即傳回，即使所有工作可能尚未繼續。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-120">By default, **Resume-Job** returns immediately, even though all jobs might not yet be resumed.</span></span>
<span data-ttu-id="bf6ba-121">若要防止在指定工作繼續之前顯示命令提示字元，請使用 *Wait* 參數。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-121">To suppress the command prompt until all specified jobs are resumed, use the *Wait* parameter.</span></span>

<span data-ttu-id="bf6ba-122">**Resume-Job** Cmdlet 只能使用於自訂工作類型，例如工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-122">The **Resume-Job** cmdlet works only on custom job types, such as workflow jobs.</span></span>
<span data-ttu-id="bf6ba-123">它無法在標準背景工作（例如使用 Start-Job Cmdlet 啟動的背景工作）上運作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-123">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>
<span data-ttu-id="bf6ba-124">如果您送出不受支援類型的工作， **Resume-Job** 會產生終止錯誤並停止執行。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-124">If you submit a job of an unsupported type, **Resume-Job** generates a terminating error and stops running.</span></span>

<span data-ttu-id="bf6ba-125">若要識別工作流程工作，請尋找工作之 **PSJobTypeName** 屬性中 **PSWorkflowJob** 的值。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="bf6ba-126">若要判斷特定的自訂工作類型是否支援 **Resume 工作** Cmdlet，請參閱自訂工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-126">To determine whether a particular custom job type supports the **Resume-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="bf6ba-127">在自訂工作類型上使用 Job Cmdlet 之前，請使用 Import-Module Cmdlet 或取得或使用模組中的 Cmdlet，匯入支援自訂工作類型的模組。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the Import-Module cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="bf6ba-128">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bf6ba-129">範例</span><span class="sxs-lookup"><span data-stu-id="bf6ba-129">EXAMPLES</span></span>

### <span data-ttu-id="bf6ba-130">範例1：依識別碼繼續工作</span><span class="sxs-lookup"><span data-stu-id="bf6ba-130">Example 1: Resume a job by ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

<span data-ttu-id="bf6ba-131">此範例中的命令會確認工作是否為暫停的工作流程工作，然後繼續該工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span>

### <span data-ttu-id="bf6ba-132">範例2：依名稱繼續工作</span><span class="sxs-lookup"><span data-stu-id="bf6ba-132">Example 2: Resume a job by name</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

<span data-ttu-id="bf6ba-133">此命令使用 *Name* 參數繼續本機電腦上的數個工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-133">This command uses the *Name* parameter to resume several workflow jobs on the local computer.</span></span>

### <span data-ttu-id="bf6ba-134">範例3：使用自訂屬性值</span><span class="sxs-lookup"><span data-stu-id="bf6ba-134">Example 3: Use custom property values</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

<span data-ttu-id="bf6ba-135">此命令使用自訂屬性的值來識別工作流程工作以繼續工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-135">This command uses the value of a custom property to identify the workflow job to resume.</span></span>
<span data-ttu-id="bf6ba-136">它會使用 *Filter* 參數依工作流程工作的 **CustomID** 屬性識別工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-136">It uses the *Filter* parameter to identify the workflow job by its **CustomID** property.</span></span>
<span data-ttu-id="bf6ba-137">它也會使用 *State* 參數先確認工作流程工作已經暫停，然後再嘗試繼續工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-137">It also uses the *State* parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

### <span data-ttu-id="bf6ba-138">範例4：繼續遠端電腦上所有已暫停的工作</span><span class="sxs-lookup"><span data-stu-id="bf6ba-138">Example 4: Resume all suspended jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="bf6ba-139">此命令會繼續 Srv01 遠端電腦上所有已暫停的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-139">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

<span data-ttu-id="bf6ba-140">命令使用 Invoke-Command Cmdlet 在 Srv01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-140">The command uses the Invoke-Command cmdlet to run a command on the Srv01 computer.</span></span>
<span data-ttu-id="bf6ba-141">遠端命令會使用「 **取得工作** 」 Cmdlet 的 *State* 參數來取得電腦上所有已暫停的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-141">The remote command uses the *State* parameter of the **Get-Job** cmdlet to get all suspended jobs on the computer.</span></span>
<span data-ttu-id="bf6ba-142">管線運算子 (|) 會將已暫停工作傳送至 **Resume-Job** Cmdlet，以繼續工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-142">A pipeline operator (|) sends the suspended jobs to the **Resume-Job** cmdlet, which resumes them.</span></span>

### <span data-ttu-id="bf6ba-143">範例5：等候工作繼續</span><span class="sxs-lookup"><span data-stu-id="bf6ba-143">Example 5: Wait for jobs to resume</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

<span data-ttu-id="bf6ba-144">此命令會使用 *Wait* 參數 **，直接在所有指定的工作** 都繼續之後才傳回。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-144">This command uses the *Wait* parameter to direct **Resume-Job** to return only after all specified jobs are resumed.</span></span>
<span data-ttu-id="bf6ba-145">在假設指令碼繼續之前會先繼續工作的指令碼中， *Wait* 參數特別有用。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-145">The *Wait* parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

### <span data-ttu-id="bf6ba-146">範例6：繼續暫停本身的工作流程</span><span class="sxs-lookup"><span data-stu-id="bf6ba-146">Example 6: Resume a workflow that suspends itself</span></span>

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

<span data-ttu-id="bf6ba-147">Resume 工作指令 **程式** 可讓您繼續使用 **暫停工作流程** 活動暫停的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-147">The **Resume-Job** cmdlet lets you resume a workflow job that was suspend by using the **Suspend-Workflow** activity.</span></span>
<span data-ttu-id="bf6ba-148">此活動會從工作流程內暫停工作流程。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-148">This activity suspends a workflow from within a workflow.</span></span>
<span data-ttu-id="bf6ba-149">它只在工作流程中有效。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-149">It is valid only in workflows.</span></span>

<span data-ttu-id="bf6ba-150">如需 Suspend-Workflow 的相關資訊，請參閱 about_Suspend-Workflow。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-150">For information about the Suspend-Workflow, see about_Suspend-Workflow.</span></span>

## <span data-ttu-id="bf6ba-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf6ba-151">PARAMETERS</span></span>

### <span data-ttu-id="bf6ba-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="bf6ba-152">-Filter</span></span>
<span data-ttu-id="bf6ba-153">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-153">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="bf6ba-154">此 Cmdlet 會繼續符合雜湊表中所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-154">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="bf6ba-155">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-155">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="bf6ba-156">-Id</span><span class="sxs-lookup"><span data-stu-id="bf6ba-156">-Id</span></span>
<span data-ttu-id="bf6ba-157">針對此 Cmdlet 繼續的作業指定識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-157">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="bf6ba-158">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-158">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="bf6ba-159">它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-159">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="bf6ba-160">您可以輸入一個或多個識別碼，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-160">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="bf6ba-161">若要尋找作業的識別碼，請執行 **Get 作業** 。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-161">To find the ID of a job, run **Get-Job** .</span></span>

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

### <span data-ttu-id="bf6ba-162">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="bf6ba-162">-InstanceId</span></span>
<span data-ttu-id="bf6ba-163">指定此 Cmdlet 繼續之作業的實例識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-163">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="bf6ba-164">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-164">The default is all jobs.</span></span>

<span data-ttu-id="bf6ba-165">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-165">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="bf6ba-166">若要尋找工作的實例識別碼，請執行 **Get 作業** 。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-166">To find the instance ID of a job, run **Get-Job** .</span></span>

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

### <span data-ttu-id="bf6ba-167">-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-167">-Job</span></span>
<span data-ttu-id="bf6ba-168">指定要繼續的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-168">Specifies the jobs to be resumed.</span></span>
<span data-ttu-id="bf6ba-169">輸入包含工作的變數，或輸入可取得工作的命令。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-169">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="bf6ba-170">您也可以使用管線將工作傳送至 **Resume-Job** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-170">You can also pipe jobs to the **Resume-Job** cmdlet.</span></span>

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

### <span data-ttu-id="bf6ba-171">-Name</span><span class="sxs-lookup"><span data-stu-id="bf6ba-171">-Name</span></span>
<span data-ttu-id="bf6ba-172">指定此 Cmdlet 所繼續之作業的易記名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-172">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="bf6ba-173">輸入一或多個工作名稱。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-173">Enter one or more job names.</span></span>
<span data-ttu-id="bf6ba-174">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-174">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="bf6ba-175">-State</span><span class="sxs-lookup"><span data-stu-id="bf6ba-175">-State</span></span>
<span data-ttu-id="bf6ba-176">指定要繼續之作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-176">Specifies the state of jobs to resume.</span></span>
<span data-ttu-id="bf6ba-177">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="bf6ba-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bf6ba-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="bf6ba-178">NotStarted</span></span>
- <span data-ttu-id="bf6ba-179">執行中</span><span class="sxs-lookup"><span data-stu-id="bf6ba-179">Running</span></span>
- <span data-ttu-id="bf6ba-180">Completed</span><span class="sxs-lookup"><span data-stu-id="bf6ba-180">Completed</span></span>
- <span data-ttu-id="bf6ba-181">失敗</span><span class="sxs-lookup"><span data-stu-id="bf6ba-181">Failed</span></span>
- <span data-ttu-id="bf6ba-182">已停止</span><span class="sxs-lookup"><span data-stu-id="bf6ba-182">Stopped</span></span>
- <span data-ttu-id="bf6ba-183">封鎖</span><span class="sxs-lookup"><span data-stu-id="bf6ba-183">Blocked</span></span>
- <span data-ttu-id="bf6ba-184">暫止</span><span class="sxs-lookup"><span data-stu-id="bf6ba-184">Suspended</span></span>
- <span data-ttu-id="bf6ba-185">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="bf6ba-185">Disconnected</span></span>
- <span data-ttu-id="bf6ba-186">Suspending</span><span class="sxs-lookup"><span data-stu-id="bf6ba-186">Suspending</span></span>
- <span data-ttu-id="bf6ba-187">停止中</span><span class="sxs-lookup"><span data-stu-id="bf6ba-187">Stopping</span></span>

<span data-ttu-id="bf6ba-188">此 Cmdlet 只會恢復處於 **暫停** 狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-188">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="bf6ba-189">如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-189">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="bf6ba-190">-Wait</span><span class="sxs-lookup"><span data-stu-id="bf6ba-190">-Wait</span></span>
<span data-ttu-id="bf6ba-191">指出此 Cmdlet 會抑制命令提示字元，直到重新開機所有工作結果為止。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-191">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span>
<span data-ttu-id="bf6ba-192">根據預設，此 Cmdlet 會立即傳回可用的結果。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-192">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="bf6ba-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bf6ba-193">-Confirm</span></span>
<span data-ttu-id="bf6ba-194">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bf6ba-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bf6ba-195">-WhatIf</span></span>
<span data-ttu-id="bf6ba-196">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bf6ba-197">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bf6ba-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf6ba-198">CommonParameters</span></span>
<span data-ttu-id="bf6ba-199">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf6ba-200">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf6ba-201">輸入</span><span class="sxs-lookup"><span data-stu-id="bf6ba-201">INPUTS</span></span>

### <span data-ttu-id="bf6ba-202">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-202">System.Management.Automation.Job</span></span>
<span data-ttu-id="bf6ba-203">您可以透過管道將所有類型的作業傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-203">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="bf6ba-204">如果 **繼續作業** 取得不支援之類型的作業，則會傳回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-204">If **Resume-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="bf6ba-205">輸出</span><span class="sxs-lookup"><span data-stu-id="bf6ba-205">OUTPUTS</span></span>

### <span data-ttu-id="bf6ba-206">無，系統管理。作業</span><span class="sxs-lookup"><span data-stu-id="bf6ba-206">None, System.Management.Automation.Job</span></span>
<span data-ttu-id="bf6ba-207">如果您使用 *PassThru* 參數，此 Cmdlet 會傳回它嘗試繼續的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-207">This cmdlet returns the jobs that it tries to resume, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="bf6ba-208">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="bf6ba-209">注意</span><span class="sxs-lookup"><span data-stu-id="bf6ba-209">NOTES</span></span>

* <span data-ttu-id="bf6ba-210">**Resume-工作** 只能繼續已暫停的工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-210">**Resume-Job** can only resume jobs that are suspended.</span></span> <span data-ttu-id="bf6ba-211">如果您送出狀態不同的工作， **Resume-Job** 會在工作上執行繼續操作，但是會產生警告以通知您無法繼續該工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-211">If you submit a job in a different state, **Resume-Job** runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="bf6ba-212">若要隱藏警告，請使用 *WarningAction* 一般參數搭配 SilentlyContinue 的值。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-212">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>
* <span data-ttu-id="bf6ba-213">如果作業不是支援繼續的型別，例如工作流程工作 ( **PSWorkflowJob** ) ，則 **Resume 作業** 會傳回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-213">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), **Resume-Job** returns a terminating error.</span></span>
* <span data-ttu-id="bf6ba-214">用於儲存暫停工作的機制與位置可能會視工作類型不同而改變。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="bf6ba-215">例如，暫停的工作流程工作是預設儲存在一般檔案存放區，但是也可以儲存在 SQL 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
* <span data-ttu-id="bf6ba-216">當您繼續工作時，工作狀態會從 **Suspended** 變更為 **Running** 。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-216">When you resume a job, the job state changes from **Suspended** to **Running** .</span></span> <span data-ttu-id="bf6ba-217">若要尋找正在執行的作業（包括此 Cmdlet 所繼續的工作），請使用「 **取得工作** 」 Cmdlet 的 *State* 參數來取得處於執行中 **狀態的** 工作。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-217">To find the jobs that are running, including those that were resumed by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get jobs in the **Running** state.</span></span>
* <span data-ttu-id="bf6ba-218">部分工作類型具有可防止 Windows PowerShell 暫停工作的選項或屬性。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-218">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="bf6ba-219">如果嘗試暫停工作失敗，請確認工作選項與屬性是否允許暫停。</span><span class="sxs-lookup"><span data-stu-id="bf6ba-219">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="bf6ba-220">相關連結</span><span class="sxs-lookup"><span data-stu-id="bf6ba-220">RELATED LINKS</span></span>

[<span data-ttu-id="bf6ba-221">Get-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-221">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="bf6ba-222">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-222">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="bf6ba-223">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-223">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="bf6ba-224">Start-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-224">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="bf6ba-225">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-225">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="bf6ba-226">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-226">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="bf6ba-227">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="bf6ba-227">Wait-Job</span></span>](Wait-Job.md)
