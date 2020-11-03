---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202648"
---
# <span data-ttu-id="b3f32-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-103">Suspend-Job</span></span>

## <span data-ttu-id="b3f32-104">概要</span><span class="sxs-lookup"><span data-stu-id="b3f32-104">SYNOPSIS</span></span>
<span data-ttu-id="b3f32-105">暫時停止工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="b3f32-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b3f32-106">SYNTAX</span></span>

### <span data-ttu-id="b3f32-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="b3f32-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b3f32-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="b3f32-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b3f32-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="b3f32-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b3f32-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="b3f32-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b3f32-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="b3f32-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b3f32-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="b3f32-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b3f32-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b3f32-113">DESCRIPTION</span></span>
<span data-ttu-id="b3f32-114">**暫** 止工作 Cmdlet 會暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-114">The **Suspend-Job** cmdlet suspends workflow jobs.</span></span>
<span data-ttu-id="b3f32-115">暫止表示暫時中斷或暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span>
<span data-ttu-id="b3f32-116">此 Cmdlet 可讓正在執行工作流程的使用者暫停工作流程。</span><span class="sxs-lookup"><span data-stu-id="b3f32-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span>
<span data-ttu-id="b3f32-117">它會補充暫止工作流程 https://go.microsoft.com/fwlink/?LinkId=267141 活動，此活動是工作流程中暫停工作流程的命令。</span><span class="sxs-lookup"><span data-stu-id="b3f32-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="b3f32-118">**Suspend-Job** Cmdlet 只能在工作流程工作上使用。</span><span class="sxs-lookup"><span data-stu-id="b3f32-118">The **Suspend-Job** cmdlet works only on workflow jobs.</span></span>
<span data-ttu-id="b3f32-119">它無法在標準背景工作（例如使用 Start-Job Cmdlet 啟動的背景工作）上運作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-119">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="b3f32-120">若要識別工作流程工作，請尋找工作之 PSJobTypeName 屬性中 **PSWorkflowJob** 的值。</span><span class="sxs-lookup"><span data-stu-id="b3f32-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="b3f32-121">若要判斷特定自訂工作類型是否支援 **Suspend-Job** Cmdlet，請參閱自訂工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="b3f32-121">To determine whether a particular custom job type supports the **Suspend-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="b3f32-122">當您暫停工作流程工作時，工作流程工作會執行至下一個檢查點，接著暫停，然後立即傳回工作流程工作物件。</span><span class="sxs-lookup"><span data-stu-id="b3f32-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span>
<span data-ttu-id="b3f32-123">若要在取得作業之前等候暫停完成，請使用 **暫止工作** 的 *wait* 參數或 Wait-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3f32-123">To wait for the suspension to complete before getting the job, use the *Wait* parameter of **Suspend-Job** or the Wait-Job cmdlet.</span></span>
<span data-ttu-id="b3f32-124">當工作流程工作暫停時，工作的 **State** 屬性值會被擱置。</span><span class="sxs-lookup"><span data-stu-id="b3f32-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="b3f32-125">是否能夠正確暫停需依賴檢查點。</span><span class="sxs-lookup"><span data-stu-id="b3f32-125">Suspending correctly relies on checkpoints.</span></span>
<span data-ttu-id="b3f32-126">目前的工作狀態、中繼資料及輸出會儲存在檢查點中，因此工作流程工作可以在不遺失狀態或資料的情況下繼續。</span><span class="sxs-lookup"><span data-stu-id="b3f32-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span>
<span data-ttu-id="b3f32-127">如果工作流程工作沒有檢查點，就無法正確地暫停。</span><span class="sxs-lookup"><span data-stu-id="b3f32-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span>
<span data-ttu-id="b3f32-128">若要新增檢查點至您正在執行的工作流程，請使用 *PSPersist* 工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="b3f32-128">To add checkpoints to a workflow that you are running, use the *PSPersist* workflow common parameter.</span></span>
<span data-ttu-id="b3f32-129">您可以使用 *Force* 參數立即暫停任何工作流程工作，並暫停沒有檢查點的工作流程工作，但動作可能會導致狀態和資料遺失。</span><span class="sxs-lookup"><span data-stu-id="b3f32-129">You can use the *Force* parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="b3f32-130">在自訂工作類型上使用 Job Cmdlet 之前（例如工作流程工作） ( **PSWorkflowJob** ) 匯入支援自訂工作類型的模組，方法是使用 Import-Module Cmdlet，或使用或使用模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3f32-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the Import-Module cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="b3f32-131">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b3f32-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b3f32-132">範例</span><span class="sxs-lookup"><span data-stu-id="b3f32-132">EXAMPLES</span></span>

### <span data-ttu-id="b3f32-133">範例1：依名稱暫止工作流程工作</span><span class="sxs-lookup"><span data-stu-id="b3f32-133">Example 1: Suspend a workflow job by name</span></span>

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

<span data-ttu-id="b3f32-134">此範例顯示如何暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-134">This example shows how to suspend a workflow job.</span></span>

### <span data-ttu-id="b3f32-135">範例2：暫停和繼續工作流程工作</span><span class="sxs-lookup"><span data-stu-id="b3f32-135">Example 2: Suspend and resume a workflow job</span></span>

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

<span data-ttu-id="b3f32-136">此範例顯示如何暫停及繼續工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-136">This example shows how to suspend and resume a workflow job.</span></span>

### <span data-ttu-id="b3f32-137">範例3：暫停遠端電腦上的工作流程工作</span><span class="sxs-lookup"><span data-stu-id="b3f32-137">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="b3f32-138">此命令會使用 Invoke-Command Cmdlet 來暫停 Srv01 遠端電腦上的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-138">This command uses the Invoke-Command cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span>
<span data-ttu-id="b3f32-139">*篩選* 參數的值是指定 CustomID 值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b3f32-139">The value of the *Filter* parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="b3f32-140">此 **CustomID** 為工作中繼資料 ( **PSPrivateMetadata** )。</span><span class="sxs-lookup"><span data-stu-id="b3f32-140">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="b3f32-141">範例4：等候工作流程工作暫停</span><span class="sxs-lookup"><span data-stu-id="b3f32-141">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="b3f32-142">此命令會暫停 VersionCheck 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-142">This command suspends the VersionCheck workflow job.</span></span>
<span data-ttu-id="b3f32-143">命令會使用 *Wait* 參數以等待工作流程工作暫停。</span><span class="sxs-lookup"><span data-stu-id="b3f32-143">The command uses the *Wait* parameter to wait until the workflow job is suspended.</span></span>
<span data-ttu-id="b3f32-144">當工作流程工作執行至下一個檢查點並暫停時，命令就會完成並傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="b3f32-144">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="b3f32-145">範例5：強制工作流程工作暫停</span><span class="sxs-lookup"><span data-stu-id="b3f32-145">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="b3f32-146">此命令會強制暫停 Maintenance 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-146">This command suspends the Maintenance workflow job forcibly.</span></span>
<span data-ttu-id="b3f32-147">維護作業沒有檢查點。</span><span class="sxs-lookup"><span data-stu-id="b3f32-147">The Maintenance job does not have checkpoints.</span></span>
<span data-ttu-id="b3f32-148">無法正確地暫停，而且可能無法正確地繼續。</span><span class="sxs-lookup"><span data-stu-id="b3f32-148">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="b3f32-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b3f32-149">PARAMETERS</span></span>

### <span data-ttu-id="b3f32-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="b3f32-150">-Filter</span></span>
<span data-ttu-id="b3f32-151">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b3f32-151">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="b3f32-152">此 Cmdlet 會暫停滿足所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-152">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="b3f32-153">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="b3f32-153">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="b3f32-154">-Force</span><span class="sxs-lookup"><span data-stu-id="b3f32-154">-Force</span></span>
<span data-ttu-id="b3f32-155">立即暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-155">Suspends the workflow job immediately.</span></span>
<span data-ttu-id="b3f32-156">這個動作可能會導致狀態與資料遺失。</span><span class="sxs-lookup"><span data-stu-id="b3f32-156">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="b3f32-157">依照預設， **Suspend-Job** 會讓工作流程工作執行到下一個檢查點，然後暫停工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-157">By default, **Suspend-Job** lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="b3f32-158">您也可以使用此參數來暫停沒有檢查點的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-158">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3f32-159">-Id</span><span class="sxs-lookup"><span data-stu-id="b3f32-159">-Id</span></span>
<span data-ttu-id="b3f32-160">指定此 Cmdlet 所暫停之作業的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b3f32-160">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="b3f32-161">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-161">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="b3f32-162">它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="b3f32-162">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="b3f32-163">您可以輸入一個或多個識別碼，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="b3f32-163">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="b3f32-164">若要尋找工作的識別碼，請使用 Get-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3f32-164">To find the ID of a job, use the Get-Job cmdlet.</span></span>

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

### <span data-ttu-id="b3f32-165">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="b3f32-165">-InstanceId</span></span>
<span data-ttu-id="b3f32-166">指定此 Cmdlet 所暫停之作業的實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="b3f32-166">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="b3f32-167">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-167">The default is all jobs.</span></span>

<span data-ttu-id="b3f32-168">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-168">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="b3f32-169">若要尋找工作的執行個體識別碼，請使用 **Get-Job** 。</span><span class="sxs-lookup"><span data-stu-id="b3f32-169">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="b3f32-170">-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-170">-Job</span></span>
<span data-ttu-id="b3f32-171">指定此 Cmdlet 停止的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-171">Specifies the workflow jobs that this cmdlet stops.</span></span>
<span data-ttu-id="b3f32-172">輸入包含工作流程工作的變數，或輸入可取得工作流程工作的命令。</span><span class="sxs-lookup"><span data-stu-id="b3f32-172">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span>
<span data-ttu-id="b3f32-173">您也可以使用管線將工作流程工作傳送至 **Suspend-Job** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3f32-173">You can also pipe workflow jobs to the **Suspend-Job** cmdlet.</span></span>

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

### <span data-ttu-id="b3f32-174">-Name</span><span class="sxs-lookup"><span data-stu-id="b3f32-174">-Name</span></span>
<span data-ttu-id="b3f32-175">指定此 Cmdlet 所暫止之作業的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b3f32-175">Specifies friendly names of jobs that this cmdlet suspends.</span></span>
<span data-ttu-id="b3f32-176">輸入一或多個工作流程工作名稱。</span><span class="sxs-lookup"><span data-stu-id="b3f32-176">Enter one or more workflow job names.</span></span>
<span data-ttu-id="b3f32-177">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b3f32-177">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="b3f32-178">-State</span><span class="sxs-lookup"><span data-stu-id="b3f32-178">-State</span></span>
<span data-ttu-id="b3f32-179">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="b3f32-179">Specifies a job state.</span></span>
<span data-ttu-id="b3f32-180">此 Cmdlet 只停止處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-180">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="b3f32-181">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="b3f32-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b3f32-182">NotStarted</span><span class="sxs-lookup"><span data-stu-id="b3f32-182">NotStarted</span></span>
- <span data-ttu-id="b3f32-183">執行中</span><span class="sxs-lookup"><span data-stu-id="b3f32-183">Running</span></span>
- <span data-ttu-id="b3f32-184">Completed</span><span class="sxs-lookup"><span data-stu-id="b3f32-184">Completed</span></span>
- <span data-ttu-id="b3f32-185">失敗</span><span class="sxs-lookup"><span data-stu-id="b3f32-185">Failed</span></span>
- <span data-ttu-id="b3f32-186">已停止</span><span class="sxs-lookup"><span data-stu-id="b3f32-186">Stopped</span></span>
- <span data-ttu-id="b3f32-187">封鎖</span><span class="sxs-lookup"><span data-stu-id="b3f32-187">Blocked</span></span>
- <span data-ttu-id="b3f32-188">暫止</span><span class="sxs-lookup"><span data-stu-id="b3f32-188">Suspended</span></span>
- <span data-ttu-id="b3f32-189">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="b3f32-189">Disconnected</span></span>
- <span data-ttu-id="b3f32-190">Suspending</span><span class="sxs-lookup"><span data-stu-id="b3f32-190">Suspending</span></span>
- <span data-ttu-id="b3f32-191">停止中</span><span class="sxs-lookup"><span data-stu-id="b3f32-191">Stopping</span></span>

<span data-ttu-id="b3f32-192">**暫** 止工作只會暫停處於執行中 **狀態的** 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-192">**Suspend-Job** suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="b3f32-193">如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。</span><span class="sxs-lookup"><span data-stu-id="b3f32-193">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="b3f32-194">-Wait</span><span class="sxs-lookup"><span data-stu-id="b3f32-194">-Wait</span></span>
<span data-ttu-id="b3f32-195">指出此 Cmdlet 會抑制命令提示字元，直到工作流程工作處於暫停狀態。</span><span class="sxs-lookup"><span data-stu-id="b3f32-195">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span>
<span data-ttu-id="b3f32-196">根據預設，即使工作流程工作尚未處於暫停狀態， **暫止工作** 也會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="b3f32-196">By default, **Suspend-Job** returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="b3f32-197">*Wait* 參數相當於將 **暫止工作** 命令輸送至 **等候工作** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3f32-197">The *Wait* parameter is equivalent to piping a **Suspend-Job** command to the **Wait-Job** cmdlet.</span></span>

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

### <span data-ttu-id="b3f32-198">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b3f32-198">-Confirm</span></span>
<span data-ttu-id="b3f32-199">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b3f32-199">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b3f32-200">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b3f32-200">-WhatIf</span></span>
<span data-ttu-id="b3f32-201">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b3f32-201">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b3f32-202">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b3f32-202">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b3f32-203">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3f32-203">CommonParameters</span></span>
<span data-ttu-id="b3f32-204">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b3f32-204">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b3f32-205">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b3f32-205">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b3f32-206">輸入</span><span class="sxs-lookup"><span data-stu-id="b3f32-206">INPUTS</span></span>

### <span data-ttu-id="b3f32-207">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-207">System.Management.Automation.Job</span></span>
<span data-ttu-id="b3f32-208">您可以透過管道將所有類型的作業傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3f32-208">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="b3f32-209">但是，如果 **暫止工作** 取得不支援之類型的作業，則會傳回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3f32-209">However, if **Suspend-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="b3f32-210">輸出</span><span class="sxs-lookup"><span data-stu-id="b3f32-210">OUTPUTS</span></span>

### <span data-ttu-id="b3f32-211">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-211">System.Management.Automation.Job</span></span>
<span data-ttu-id="b3f32-212">此 Cmdlet 會傳回它所暫停的工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-212">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="b3f32-213">注意</span><span class="sxs-lookup"><span data-stu-id="b3f32-213">NOTES</span></span>

* <span data-ttu-id="b3f32-214">用於儲存暫停工作的機制與位置可能會視工作類型不同而改變。</span><span class="sxs-lookup"><span data-stu-id="b3f32-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="b3f32-215">例如，暫停的工作流程工作是預設儲存在一般檔案存放區，但是也可以儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="b3f32-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
* <span data-ttu-id="b3f32-216">如果您送出狀態不是 Running 的工作流程工作， **Suspend-Job** 會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b3f32-216">If you submit a workflow job that is not in the Running state, **Suspend-Job** displays a warning message.</span></span> <span data-ttu-id="b3f32-217">若要隱藏警告，請使用 *WarningAction* 一般參數搭配 SilentlyContinue 的值。</span><span class="sxs-lookup"><span data-stu-id="b3f32-217">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="b3f32-218">如果作業不是支援暫止的型別，則 **暫止工作** 會傳回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3f32-218">If a job is not of a type that supports suspending, **Suspend-Job** returns a terminating error.</span></span>

* <span data-ttu-id="b3f32-219">若要尋找已暫止的工作流程工作（包括此 Cmdlet 所暫停的工作），請使用「 **取得** 工作」 Cmdlet 的 *State* 參數來取得處於「已暫停」狀態的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="b3f32-219">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get workflow jobs in the Suspended state.</span></span>
* <span data-ttu-id="b3f32-220">部分工作類型具有可防止 Windows PowerShell 暫停工作的選項或屬性。</span><span class="sxs-lookup"><span data-stu-id="b3f32-220">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="b3f32-221">如果嘗試暫停工作失敗，請確認工作選項與屬性是否允許暫停。</span><span class="sxs-lookup"><span data-stu-id="b3f32-221">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="b3f32-222">相關連結</span><span class="sxs-lookup"><span data-stu-id="b3f32-222">RELATED LINKS</span></span>

[<span data-ttu-id="b3f32-223">Get-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-223">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="b3f32-224">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-224">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="b3f32-225">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-225">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="b3f32-226">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-226">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="b3f32-227">Start-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-227">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="b3f32-228">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-228">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="b3f32-229">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-229">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="b3f32-230">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="b3f32-230">Wait-Job</span></span>](Wait-Job.md)
