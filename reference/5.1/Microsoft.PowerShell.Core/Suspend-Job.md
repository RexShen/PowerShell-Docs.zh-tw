---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388459"
---
# <span data-ttu-id="0645c-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-103">Suspend-Job</span></span>

## <span data-ttu-id="0645c-104">概要</span><span class="sxs-lookup"><span data-stu-id="0645c-104">SYNOPSIS</span></span>
<span data-ttu-id="0645c-105">暫時停止工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="0645c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0645c-106">SYNTAX</span></span>

### <span data-ttu-id="0645c-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="0645c-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0645c-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="0645c-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0645c-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="0645c-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0645c-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="0645c-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0645c-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="0645c-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0645c-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="0645c-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0645c-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0645c-113">DESCRIPTION</span></span>

<span data-ttu-id="0645c-114">此 `Suspend-Job` Cmdlet 會暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-114">The `Suspend-Job` cmdlet suspends workflow jobs.</span></span> <span data-ttu-id="0645c-115">暫止表示暫時中斷或暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span> <span data-ttu-id="0645c-116">此 Cmdlet 可讓正在執行工作流程的使用者暫停工作流程。</span><span class="sxs-lookup"><span data-stu-id="0645c-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span> <span data-ttu-id="0645c-117">它會補充暫止工作流程 https://go.microsoft.com/fwlink/?LinkId=267141 活動，此活動是工作流程中暫停工作流程的命令。</span><span class="sxs-lookup"><span data-stu-id="0645c-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="0645c-118">此 `Suspend-Job` Cmdlet 只適用于工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-118">The `Suspend-Job` cmdlet works only on workflow jobs.</span></span> <span data-ttu-id="0645c-119">它無法在標準背景工作（例如使用 Cmdlet 啟動的背景工作）上運作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="0645c-119">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="0645c-120">若要識別工作流程工作，請尋找工作之 PSJobTypeName 屬性中 **PSWorkflowJob** 的值。</span><span class="sxs-lookup"><span data-stu-id="0645c-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="0645c-121">若要判斷特定的自訂工作類型是否支援 `Suspend-Job` Cmdlet，請參閱自訂工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="0645c-121">To determine whether a particular custom job type supports the `Suspend-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="0645c-122">當您暫停工作流程工作時，工作流程工作會執行至下一個檢查點，接著暫停，然後立即傳回工作流程工作物件。</span><span class="sxs-lookup"><span data-stu-id="0645c-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span> <span data-ttu-id="0645c-123">若要在取得作業之前等候暫停完成，請使用或 Cmdlet 的 **wait** 參數 `Suspend-Job` `Wait-Job` 。</span><span class="sxs-lookup"><span data-stu-id="0645c-123">To wait for the suspension to complete before getting the job, use the **Wait** parameter of `Suspend-Job` or the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="0645c-124">當工作流程工作暫停時，工作的 **State** 屬性值會被擱置。</span><span class="sxs-lookup"><span data-stu-id="0645c-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="0645c-125">是否能夠正確暫停需依賴檢查點。</span><span class="sxs-lookup"><span data-stu-id="0645c-125">Suspending correctly relies on checkpoints.</span></span> <span data-ttu-id="0645c-126">目前的工作狀態、中繼資料及輸出會儲存在檢查點中，因此工作流程工作可以在不遺失狀態或資料的情況下繼續。</span><span class="sxs-lookup"><span data-stu-id="0645c-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span> <span data-ttu-id="0645c-127">如果工作流程工作沒有檢查點，就無法正確地暫停。</span><span class="sxs-lookup"><span data-stu-id="0645c-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span> <span data-ttu-id="0645c-128">若要新增檢查點至您正在執行的工作流程，請使用 **PSPersist** 工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="0645c-128">To add checkpoints to a workflow that you are running, use the **PSPersist** workflow common parameter.</span></span> <span data-ttu-id="0645c-129">您可以使用 **Force** 參數立即暫停任何工作流程工作，並暫停沒有檢查點的工作流程工作，但動作可能會導致狀態和資料遺失。</span><span class="sxs-lookup"><span data-stu-id="0645c-129">You can use the **Force** parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="0645c-130">在自訂工作類型（例如工作流程工作）上使用 Job Cmdlet 之前 ( **PSWorkflowJob** ) 匯入支援自訂工作類型的模組，方法是使用 `Import-Module` Cmdlet 或使用或使用模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0645c-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the `Import-Module` cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="0645c-131">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="0645c-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="0645c-132">範例</span><span class="sxs-lookup"><span data-stu-id="0645c-132">EXAMPLES</span></span>

### <span data-ttu-id="0645c-133">範例1：依名稱暫止工作流程工作</span><span class="sxs-lookup"><span data-stu-id="0645c-133">Example 1: Suspend a workflow job by name</span></span>

<span data-ttu-id="0645c-134">此範例顯示如何暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-134">This example shows how to suspend a workflow job.</span></span>

<span data-ttu-id="0645c-135">第一個命令會建立 `Get-SystemLog` 工作流程。</span><span class="sxs-lookup"><span data-stu-id="0645c-135">The first command creates the `Get-SystemLog` workflow.</span></span> <span data-ttu-id="0645c-136">工作流程會使用 `CheckPoint-Workflow` 活動來定義工作流程中的檢查點。</span><span class="sxs-lookup"><span data-stu-id="0645c-136">The workflow uses the `CheckPoint-Workflow` activity to define a checkpoint in the workflow.</span></span>

<span data-ttu-id="0645c-137">第二個命令會使用所有工作流程通用的 **AsJob** 參數，以背景工作的 `Get-SystemLog` 形式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="0645c-137">The second command uses the **AsJob** parameter that is common to all workflows to run the `Get-SystemLog` workflow as a background job.</span></span> <span data-ttu-id="0645c-138">命令會使用 **JobName** 工作流程一般參數，指定工作流程工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="0645c-138">The command uses the **JobName** workflow common parameter to specify a friendly name for the workflow job.</span></span>

<span data-ttu-id="0645c-139">第三個命令會使用 `Get-Job` Cmdlet 來取得 `Get-SystemLogJob` 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-139">The third command uses the `Get-Job` cmdlet to get the `Get-SystemLogJob` workflow job.</span></span> <span data-ttu-id="0645c-140">輸出顯示 **PSJobTypeName** 屬性的值為 PSWorkflowJob。</span><span class="sxs-lookup"><span data-stu-id="0645c-140">The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.</span></span>

<span data-ttu-id="0645c-141">第四個命令會使用 `Suspend-Job` Cmdlet 來暫停 `Get-SystemLogJob` 作業。</span><span class="sxs-lookup"><span data-stu-id="0645c-141">The fourth command uses the `Suspend-Job` cmdlet to suspend the `Get-SystemLogJob` job.</span></span> <span data-ttu-id="0645c-142">工作會執行至檢查點，然後暫停。</span><span class="sxs-lookup"><span data-stu-id="0645c-142">The job runs to the checkpoint and then suspends.</span></span>

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### <span data-ttu-id="0645c-143">範例2：暫停和繼續工作流程工作</span><span class="sxs-lookup"><span data-stu-id="0645c-143">Example 2: Suspend and resume a workflow job</span></span>

<span data-ttu-id="0645c-144">此範例顯示如何暫停及繼續工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-144">This example shows how to suspend and resume a workflow job.</span></span>

<span data-ttu-id="0645c-145">第一個命令會暫停 LogWorkflowJob 工作。此命令會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="0645c-145">The first command suspends the LogWorkflowJob job.The command returns immediately.</span></span> <span data-ttu-id="0645c-146">輸出顯示工作流程工作仍在執行中，即使它已暫止也一樣。</span><span class="sxs-lookup"><span data-stu-id="0645c-146">The output shows that the workflow job is still running, even though it is being suspended.</span></span>

<span data-ttu-id="0645c-147">第二個命令會使用 `Get-Job` Cmdlet 來取得 LogWorkflowJob 工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-147">The second command uses the `Get-Job` cmdlet to get the LogWorkflowJob job.</span></span> <span data-ttu-id="0645c-148">輸出會顯示已順利暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-148">The output shows that the workflow job suspended successfully.</span></span>

<span data-ttu-id="0645c-149">第三個命令 `Get-Job` 會使用 Cmdlet 來取得 LogWorkflowJob 作業，並使用 `Resume-Job` Cmdlet 來繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0645c-149">The third command uses the `Get-Job` cmdlet to get the LogWorkflowJob job and the `Resume-Job` cmdlet to resume it.</span></span> <span data-ttu-id="0645c-150">輸出會顯示已順利繼續工作流程工作並且現在正在執行。</span><span class="sxs-lookup"><span data-stu-id="0645c-150">The output shows that the workflow job resumed successfully and is now running.</span></span>

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### <span data-ttu-id="0645c-151">範例3：暫停遠端電腦上的工作流程工作</span><span class="sxs-lookup"><span data-stu-id="0645c-151">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="0645c-152">此命令會使用 `Invoke-Command` Cmdlet 來暫停 Srv01 遠端電腦上的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-152">This command uses the `Invoke-Command` cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span> <span data-ttu-id="0645c-153">**篩選** 參數的值是指定 CustomID 值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="0645c-153">The value of the **Filter** parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="0645c-154">此 **CustomID** 為工作中繼資料 ( **PSPrivateMetadata** )。</span><span class="sxs-lookup"><span data-stu-id="0645c-154">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="0645c-155">範例4：等候工作流程工作暫停</span><span class="sxs-lookup"><span data-stu-id="0645c-155">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="0645c-156">此命令會暫停 VersionCheck 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-156">This command suspends the VersionCheck workflow job.</span></span> <span data-ttu-id="0645c-157">命令會使用 **Wait** 參數以等待工作流程工作暫停。</span><span class="sxs-lookup"><span data-stu-id="0645c-157">The command uses the **Wait** parameter to wait until the workflow job is suspended.</span></span> <span data-ttu-id="0645c-158">當工作流程工作執行至下一個檢查點並暫停時，命令就會完成並傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="0645c-158">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="0645c-159">範例5：強制工作流程工作暫停</span><span class="sxs-lookup"><span data-stu-id="0645c-159">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="0645c-160">此命令會強制暫停 Maintenance 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-160">This command suspends the Maintenance workflow job forcibly.</span></span> <span data-ttu-id="0645c-161">維護作業沒有檢查點。</span><span class="sxs-lookup"><span data-stu-id="0645c-161">The Maintenance job does not have checkpoints.</span></span> <span data-ttu-id="0645c-162">無法正確地暫停，而且可能無法正確地繼續。</span><span class="sxs-lookup"><span data-stu-id="0645c-162">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="0645c-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0645c-163">PARAMETERS</span></span>

### <span data-ttu-id="0645c-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="0645c-164">-Filter</span></span>

<span data-ttu-id="0645c-165">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="0645c-165">Specifies a hash table of conditions.</span></span> <span data-ttu-id="0645c-166">此 Cmdlet 會暫停滿足所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-166">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="0645c-167">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="0645c-167">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="0645c-168">-Force</span><span class="sxs-lookup"><span data-stu-id="0645c-168">-Force</span></span>

<span data-ttu-id="0645c-169">立即暫停工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-169">Suspends the workflow job immediately.</span></span> <span data-ttu-id="0645c-170">這個動作可能會導致狀態與資料遺失。</span><span class="sxs-lookup"><span data-stu-id="0645c-170">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="0645c-171">依預設， `Suspend-Job` 會讓工作流程工作執行至下一個檢查點，然後暫停它。</span><span class="sxs-lookup"><span data-stu-id="0645c-171">By default, `Suspend-Job` lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="0645c-172">您也可以使用此參數來暫停沒有檢查點的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-172">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

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

### <span data-ttu-id="0645c-173">-Id</span><span class="sxs-lookup"><span data-stu-id="0645c-173">-Id</span></span>

<span data-ttu-id="0645c-174">指定此 Cmdlet 所暫停之作業的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0645c-174">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="0645c-175">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-175">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="0645c-176">它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0645c-176">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="0645c-177">您可以輸入一個或多個識別碼，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="0645c-177">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="0645c-178">若要尋找工作的識別碼，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0645c-178">To find the ID of a job, use the `Get-Job` cmdlet.</span></span>

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

### <span data-ttu-id="0645c-179">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="0645c-179">-InstanceId</span></span>

<span data-ttu-id="0645c-180">指定此 Cmdlet 所暫停之作業的實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="0645c-180">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="0645c-181">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-181">The default is all jobs.</span></span>

<span data-ttu-id="0645c-182">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-182">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="0645c-183">若要尋找工作的實例識別碼，請使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="0645c-183">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="0645c-184">-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-184">-Job</span></span>

<span data-ttu-id="0645c-185">指定此 Cmdlet 停止的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-185">Specifies the workflow jobs that this cmdlet stops.</span></span> <span data-ttu-id="0645c-186">輸入包含工作流程工作的變數，或輸入可取得工作流程工作的命令。</span><span class="sxs-lookup"><span data-stu-id="0645c-186">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span> <span data-ttu-id="0645c-187">您也可以透過管線將工作流程作業傳送至 `Suspend-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0645c-187">You can also pipe workflow jobs to the `Suspend-Job` cmdlet.</span></span>

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

### <span data-ttu-id="0645c-188">-Name</span><span class="sxs-lookup"><span data-stu-id="0645c-188">-Name</span></span>

<span data-ttu-id="0645c-189">指定此 Cmdlet 所暫止之作業的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="0645c-189">Specifies friendly names of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="0645c-190">輸入一或多個工作流程工作名稱。</span><span class="sxs-lookup"><span data-stu-id="0645c-190">Enter one or more workflow job names.</span></span>
<span data-ttu-id="0645c-191">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="0645c-191">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="0645c-192">-State</span><span class="sxs-lookup"><span data-stu-id="0645c-192">-State</span></span>

<span data-ttu-id="0645c-193">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="0645c-193">Specifies a job state.</span></span> <span data-ttu-id="0645c-194">此 Cmdlet 只停止處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-194">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="0645c-195">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="0645c-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0645c-196">NotStarted</span><span class="sxs-lookup"><span data-stu-id="0645c-196">NotStarted</span></span>
- <span data-ttu-id="0645c-197">執行中</span><span class="sxs-lookup"><span data-stu-id="0645c-197">Running</span></span>
- <span data-ttu-id="0645c-198">Completed</span><span class="sxs-lookup"><span data-stu-id="0645c-198">Completed</span></span>
- <span data-ttu-id="0645c-199">失敗</span><span class="sxs-lookup"><span data-stu-id="0645c-199">Failed</span></span>
- <span data-ttu-id="0645c-200">已停止</span><span class="sxs-lookup"><span data-stu-id="0645c-200">Stopped</span></span>
- <span data-ttu-id="0645c-201">封鎖</span><span class="sxs-lookup"><span data-stu-id="0645c-201">Blocked</span></span>
- <span data-ttu-id="0645c-202">暫止</span><span class="sxs-lookup"><span data-stu-id="0645c-202">Suspended</span></span>
- <span data-ttu-id="0645c-203">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="0645c-203">Disconnected</span></span>
- <span data-ttu-id="0645c-204">Suspending</span><span class="sxs-lookup"><span data-stu-id="0645c-204">Suspending</span></span>
- <span data-ttu-id="0645c-205">停止中</span><span class="sxs-lookup"><span data-stu-id="0645c-205">Stopping</span></span>

<span data-ttu-id="0645c-206">`Suspend-Job` 只暫停處於執行 **中狀態的** 工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-206">`Suspend-Job` suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="0645c-207">如需有關工作狀態的詳細資訊，請參閱 [JobState 列舉](/dotnet/api/system.management.automation.jobstate)。</span><span class="sxs-lookup"><span data-stu-id="0645c-207">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="0645c-208">-Wait</span><span class="sxs-lookup"><span data-stu-id="0645c-208">-Wait</span></span>

<span data-ttu-id="0645c-209">指出此 Cmdlet 會抑制命令提示字元，直到工作流程工作處於暫停狀態。</span><span class="sxs-lookup"><span data-stu-id="0645c-209">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span> <span data-ttu-id="0645c-210">根據預設， `Suspend-Job` 會立即傳回，即使工作流程工作尚未處於暫停狀態也一樣。</span><span class="sxs-lookup"><span data-stu-id="0645c-210">By default, `Suspend-Job` returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="0645c-211">**Wait** 參數相當於將 `Suspend-Job` 命令輸送至 `Wait-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0645c-211">The **Wait** parameter is equivalent to piping a `Suspend-Job` command to the `Wait-Job` cmdlet.</span></span>

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

### <span data-ttu-id="0645c-212">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0645c-212">-Confirm</span></span>

<span data-ttu-id="0645c-213">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="0645c-213">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0645c-214">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0645c-214">-WhatIf</span></span>

<span data-ttu-id="0645c-215">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="0645c-215">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0645c-216">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="0645c-216">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0645c-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0645c-217">CommonParameters</span></span>

<span data-ttu-id="0645c-218">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0645c-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0645c-219">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0645c-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0645c-220">輸入</span><span class="sxs-lookup"><span data-stu-id="0645c-220">INPUTS</span></span>

### <span data-ttu-id="0645c-221">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="0645c-221">System.Management.Automation.Job</span></span>

<span data-ttu-id="0645c-222">您可以透過管道將所有類型的作業傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0645c-222">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="0645c-223">但是，如果 `Suspend-Job` 取得不支援之類型的作業，則會傳回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="0645c-223">However, if `Suspend-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="0645c-224">輸出</span><span class="sxs-lookup"><span data-stu-id="0645c-224">OUTPUTS</span></span>

### <span data-ttu-id="0645c-225">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="0645c-225">System.Management.Automation.Job</span></span>
<span data-ttu-id="0645c-226">此 Cmdlet 會傳回它所暫停的工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-226">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="0645c-227">注意</span><span class="sxs-lookup"><span data-stu-id="0645c-227">NOTES</span></span>

- <span data-ttu-id="0645c-228">用於儲存暫停工作的機制與位置可能會視工作類型不同而改變。</span><span class="sxs-lookup"><span data-stu-id="0645c-228">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="0645c-229">例如，暫停的工作流程工作是預設儲存在一般檔案存放區，但是也可以儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0645c-229">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
- <span data-ttu-id="0645c-230">如果您提交不是處於執行中狀態的工作流程工作，則會 `Suspend-Job` 顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="0645c-230">If you submit a workflow job that is not in the Running state, `Suspend-Job` displays a warning message.</span></span> <span data-ttu-id="0645c-231">若要隱藏警告，請使用 **WarningAction** 一般參數搭配 SilentlyContinue 的值。</span><span class="sxs-lookup"><span data-stu-id="0645c-231">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="0645c-232">如果作業不是支援暫止的型別，則會傳回 `Suspend-Job` 終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="0645c-232">If a job is not of a type that supports suspending, `Suspend-Job` returns a terminating error.</span></span>

- <span data-ttu-id="0645c-233">若要尋找已暫止的工作流程工作（包括此 Cmdlet 所暫停的工作），請使用 Cmdlet 的 **State** 參數 `Get-Job` 來取得處於暫停狀態的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="0645c-233">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get workflow jobs in the Suspended state.</span></span>
- <span data-ttu-id="0645c-234">部分工作類型具有可防止 Windows PowerShell 暫停工作的選項或屬性。</span><span class="sxs-lookup"><span data-stu-id="0645c-234">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="0645c-235">如果嘗試暫停工作失敗，請確認工作選項與屬性是否允許暫停。</span><span class="sxs-lookup"><span data-stu-id="0645c-235">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="0645c-236">相關連結</span><span class="sxs-lookup"><span data-stu-id="0645c-236">RELATED LINKS</span></span>

[<span data-ttu-id="0645c-237">Get-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-237">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="0645c-238">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-238">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="0645c-239">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-239">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="0645c-240">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-240">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="0645c-241">Start-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-241">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="0645c-242">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-242">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="0645c-243">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-243">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="0645c-244">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="0645c-244">Wait-Job</span></span>](Wait-Job.md)
