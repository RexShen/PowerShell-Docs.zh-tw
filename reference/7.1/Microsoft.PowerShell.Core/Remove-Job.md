---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: b65e990c8d03858705b167bd1712ab6fde305a82
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204799"
---
# <span data-ttu-id="cf3df-103">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-103">Remove-Job</span></span>

## <span data-ttu-id="cf3df-104">概要</span><span class="sxs-lookup"><span data-stu-id="cf3df-104">SYNOPSIS</span></span>
<span data-ttu-id="cf3df-105">刪除 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-105">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="cf3df-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf3df-106">SYNTAX</span></span>

### <span data-ttu-id="cf3df-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="cf3df-107">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cf3df-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="cf3df-108">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cf3df-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="cf3df-109">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cf3df-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="cf3df-110">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cf3df-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="cf3df-111">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cf3df-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="cf3df-112">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cf3df-113">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="cf3df-113">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cf3df-114">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cf3df-114">DESCRIPTION</span></span>

<span data-ttu-id="cf3df-115">此 `Remove-Job` Cmdlet 會刪除 Cmdlet 或 Cmdlet 所啟動的 PowerShell 背景工作， `Start-Job` 例如 `Invoke-Command` 支援 **AsJob** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf3df-115">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="cf3df-116">您可以使用 `Remove-Job` 刪除所有作業，或刪除選取的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-116">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="cf3df-117">作業是由其 **名稱** 、 **識別碼** 、 **實例識別碼** 、 **命令** 或 **狀態** 來識別。</span><span class="sxs-lookup"><span data-stu-id="cf3df-117">The jobs are identified by their **Name** , **ID** , **Instance ID** , **Command** , or **State** .</span></span> <span data-ttu-id="cf3df-118">或者，您可以將工作物件向下傳送至 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-118">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="cf3df-119">如果沒有參數或參數值， `Remove-Job` 就不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="cf3df-119">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="cf3df-120">從 PowerShell 3.0 開始， `Remove-Job` 可以刪除自訂工作類型，例如排程工作和工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-120">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="cf3df-121">例如， `Remove-Job` 刪除排程工作、磁片上排程工作的所有實例，以及所有觸發之工作實例的結果。</span><span class="sxs-lookup"><span data-stu-id="cf3df-121">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="cf3df-122">如果您嘗試刪除執行中的作業，就 `Remove-Job` 會失敗。</span><span class="sxs-lookup"><span data-stu-id="cf3df-122">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="cf3df-123">使用 `Stop-Job` Cmdlet 來停止執行中的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-123">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="cf3df-124">或者，使用 `Remove-Job` With **Force** 參數來刪除執行中的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-124">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="cf3df-125">作業會保留在全域工作快取中，直到您移除背景工作或關閉 PowerShell 會話為止。</span><span class="sxs-lookup"><span data-stu-id="cf3df-125">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="cf3df-126">範例</span><span class="sxs-lookup"><span data-stu-id="cf3df-126">EXAMPLES</span></span>

### <span data-ttu-id="cf3df-127">範例1：使用其名稱刪除作業</span><span class="sxs-lookup"><span data-stu-id="cf3df-127">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="cf3df-128">此範例會使用變數和管線來依名稱刪除工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-128">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="cf3df-129">`Get-Job` 使用 **Name** 參數來指定作業 **BatchJob** 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-129">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob** .</span></span> <span data-ttu-id="cf3df-130">工作物件會儲存在變數中 `$batch` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-130">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="cf3df-131">中的物件 `$batch` 會向下傳送到管線 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-131">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="cf3df-132">替代方法是使用 **工作** 參數，例如 `Remove-Job -Job $batch` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-132">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="cf3df-133">範例2：刪除會話中的所有工作</span><span class="sxs-lookup"><span data-stu-id="cf3df-133">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="cf3df-134">在此範例中，會刪除目前 PowerShell 會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-134">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="cf3df-135">`Get-Job` 取得目前 PowerShell 會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-135">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="cf3df-136">工作物件會向下傳送到管線 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-136">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="cf3df-137">範例3：刪除 NotStarted 作業</span><span class="sxs-lookup"><span data-stu-id="cf3df-137">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="cf3df-138">此範例會從目前未啟動的 PowerShell 會話中刪除所有作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-138">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="cf3df-139">`Remove-Job` 使用 **State** 參數指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="cf3df-139">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="cf3df-140">範例4：使用易記名稱刪除作業</span><span class="sxs-lookup"><span data-stu-id="cf3df-140">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="cf3df-141">此範例會從目前會話中刪除以 \* batch \* \* 結尾的易記名稱，包括正在執行的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-141">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="cf3df-142">`Remove-Job` 使用 **name** 參數來指定工作名稱模式。</span><span class="sxs-lookup"><span data-stu-id="cf3df-142">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="cf3df-143">此模式包含星號 (`*`) 萬用字元來尋找以 **批次** 結尾的所有工作名稱。</span><span class="sxs-lookup"><span data-stu-id="cf3df-143">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch** .</span></span> <span data-ttu-id="cf3df-144">**Force** 參數會刪除執行中的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-144">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="cf3df-145">範例5：刪除 Invoke-Command 所建立的作業</span><span class="sxs-lookup"><span data-stu-id="cf3df-145">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="cf3df-146">此範例會使用 AsJob 參數，移除在遠端電腦上啟動的工作 `Invoke-Command` 。 **AsJob**</span><span class="sxs-lookup"><span data-stu-id="cf3df-146">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="cf3df-147">因為此範例使用 **AsJob** 參數，所以會在本機電腦上建立工作物件。</span><span class="sxs-lookup"><span data-stu-id="cf3df-147">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="cf3df-148">但是，工作會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="cf3df-148">But, the job runs on a remote computer.</span></span> <span data-ttu-id="cf3df-149">因此，您是使用本機命令來管理工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-149">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="cf3df-150">`Invoke-Command` 在 **Server01** 電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-150">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="cf3df-151">**AsJob** 參數會將 **ScriptBlock** 以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="cf3df-151">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="cf3df-152">工作物件會儲存在變數中 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-152">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="cf3df-153">`$job`變數物件會向下傳送到管線 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-153">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="cf3df-154">範例6：刪除 Invoke-Command 和 Start-Job 所建立的作業</span><span class="sxs-lookup"><span data-stu-id="cf3df-154">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="cf3df-155">這個範例示範如何在使用執行的遠端電腦上移除作業 `Invoke-Command` `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-155">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="cf3df-156">系統會在遠端電腦上建立工作物件，並使用遠端命令來管理作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-156">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="cf3df-157">執行遠端命令時，需要持續性連接 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-157">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="cf3df-158">`New-PSSession`建立 **Server01** 電腦的 **PSSession** （持續連線）。</span><span class="sxs-lookup"><span data-stu-id="cf3df-158">`New-PSSession` creates a **PSSession** , a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="cf3df-159">連接會儲存在變數中 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-159">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="cf3df-160">`Invoke-Command` 連接到儲存在中的會話 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-160">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="cf3df-161">**ScriptBlock** 會使用 `Start-Job` 來啟動遠端作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-161">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="cf3df-162">作業會執行 `Get-Process` 命令，並使用 **Name** 參數來指定易記的作業名稱 **>myjob** 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-162">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob** .</span></span>

<span data-ttu-id="cf3df-163">`Invoke-Command` 使用 `$S` 會話並執行 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-163">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="cf3df-164">**Name** 參數指定刪除名為 **>myjob** 的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-164">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="cf3df-165">範例7：使用其 InstanceId 來刪除作業</span><span class="sxs-lookup"><span data-stu-id="cf3df-165">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="cf3df-166">此範例會根據其 **InstanceId** 來移除作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-166">This example removes a job based on its **InstanceId** .</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="cf3df-167">`Start-Job` 啟動背景工作，並將工作物件儲存在變數中 `$job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-167">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="cf3df-168">中的物件 `$job` 會向下傳送到管線 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-168">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="cf3df-169">**Property** 參數使用星號 (`*`) 來指定所有物件的屬性都會顯示在清單中。</span><span class="sxs-lookup"><span data-stu-id="cf3df-169">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="cf3df-170">`Remove-Job` 使用 **InstanceId** 參數指定要刪除的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-170">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="cf3df-171">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf3df-171">PARAMETERS</span></span>

### <span data-ttu-id="cf3df-172">-Command</span><span class="sxs-lookup"><span data-stu-id="cf3df-172">-Command</span></span>

<span data-ttu-id="cf3df-173">刪除命令中包含指定字詞的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-173">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="cf3df-174">您可以輸入逗點分隔的陣列。</span><span class="sxs-lookup"><span data-stu-id="cf3df-174">You can enter a comma-separated array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cf3df-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cf3df-175">-Confirm</span></span>

<span data-ttu-id="cf3df-176">在執行之前提示您確認 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-176">Prompts you for confirmation before `Remove-Job` is run.</span></span>

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

### <span data-ttu-id="cf3df-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="cf3df-177">-Filter</span></span>

<span data-ttu-id="cf3df-178">刪除符合在相關聯雜湊表中建立之所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-178">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="cf3df-179">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cf3df-179">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="cf3df-180">這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-180">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="cf3df-181">它無法在標準背景工作上運作，例如使用所建立的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-181">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="cf3df-182">此參數在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cf3df-182">This parameter is introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cf3df-183">-Force</span><span class="sxs-lookup"><span data-stu-id="cf3df-183">-Force</span></span>

<span data-ttu-id="cf3df-184">刪除作業，即使作業的狀態為 [ **正在** 執行]。</span><span class="sxs-lookup"><span data-stu-id="cf3df-184">Deletes a job even if the job's state is **Running** .</span></span> <span data-ttu-id="cf3df-185">如果未指定 **Force** 參數，則 `Remove-Job` 不會刪除執行中的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-185">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cf3df-186">-Id</span><span class="sxs-lookup"><span data-stu-id="cf3df-186">-Id</span></span>

<span data-ttu-id="cf3df-187">刪除具有指定 **識別碼** 的背景工作。您可以輸入逗點分隔的陣列。</span><span class="sxs-lookup"><span data-stu-id="cf3df-187">Deletes background jobs with the specified **Id** . You can enter a comma-separated array.</span></span> <span data-ttu-id="cf3df-188">作業的 **識別碼** 是唯一的整數，用來識別目前會話中的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-188">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="cf3df-189">若要尋找作業的 **識別碼** ，請使用 `Get-Job` 不含參數的。</span><span class="sxs-lookup"><span data-stu-id="cf3df-189">To find a job's **Id** , use `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="cf3df-190">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="cf3df-190">-InstanceId</span></span>

<span data-ttu-id="cf3df-191">刪除具有指定 **InstanceId** 的作業。</span><span class="sxs-lookup"><span data-stu-id="cf3df-191">Deletes jobs with the specified **InstanceId** .</span></span> <span data-ttu-id="cf3df-192">您可以輸入逗點分隔的陣列。</span><span class="sxs-lookup"><span data-stu-id="cf3df-192">You can enter a comma-separated array.</span></span> <span data-ttu-id="cf3df-193">**InstanceId** 是識別作業的唯一 GUID。</span><span class="sxs-lookup"><span data-stu-id="cf3df-193">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="cf3df-194">若要尋找作業的 **InstanceId** ，請使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-194">To find a job's **InstanceId** , use `Get-Job`.</span></span>

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

### <span data-ttu-id="cf3df-195">-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-195">-Job</span></span>

<span data-ttu-id="cf3df-196">指定要刪除的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-196">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="cf3df-197">輸入包含工作的變數，或輸入可取得工作的命令。</span><span class="sxs-lookup"><span data-stu-id="cf3df-197">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="cf3df-198">您可以輸入逗點分隔的陣列。</span><span class="sxs-lookup"><span data-stu-id="cf3df-198">You can enter a comma-separated array.</span></span>

<span data-ttu-id="cf3df-199">您可以將管線中的工作物件傳送至 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-199">You can send job objects down the pipeline to `Remove-Job`.</span></span>

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

### <span data-ttu-id="cf3df-200">-Name</span><span class="sxs-lookup"><span data-stu-id="cf3df-200">-Name</span></span>

<span data-ttu-id="cf3df-201">只刪除具有指定易記名稱的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-201">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="cf3df-202">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf3df-202">Wildcards are permitted.</span></span> <span data-ttu-id="cf3df-203">您可以輸入逗點分隔的陣列。</span><span class="sxs-lookup"><span data-stu-id="cf3df-203">You can enter a comma-separated array.</span></span>

<span data-ttu-id="cf3df-204">工作的易記名稱不保證是唯一的，即使在 PowerShell 會話內也是如此。</span><span class="sxs-lookup"><span data-stu-id="cf3df-204">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="cf3df-205">當您依名稱刪除檔案時，請使用 **WhatIf** 和 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf3df-205">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

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

### <span data-ttu-id="cf3df-206">-State</span><span class="sxs-lookup"><span data-stu-id="cf3df-206">-State</span></span>

<span data-ttu-id="cf3df-207">只刪除具有指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="cf3df-207">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="cf3df-208">若要刪除狀態為 [ **正在** 執行] 的工作，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="cf3df-208">To delete jobs with a state of **Running** , use the **Force** parameter.</span></span>

<span data-ttu-id="cf3df-209">接受的值：</span><span class="sxs-lookup"><span data-stu-id="cf3df-209">Accepted values:</span></span>

- <span data-ttu-id="cf3df-210">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cf3df-210">AtBreakpoint</span></span>
- <span data-ttu-id="cf3df-211">封鎖</span><span class="sxs-lookup"><span data-stu-id="cf3df-211">Blocked</span></span>
- <span data-ttu-id="cf3df-212">已完成</span><span class="sxs-lookup"><span data-stu-id="cf3df-212">Completed</span></span>
- <span data-ttu-id="cf3df-213">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="cf3df-213">Disconnected</span></span>
- <span data-ttu-id="cf3df-214">失敗</span><span class="sxs-lookup"><span data-stu-id="cf3df-214">Failed</span></span>
- <span data-ttu-id="cf3df-215">NotStarted</span><span class="sxs-lookup"><span data-stu-id="cf3df-215">NotStarted</span></span>
- <span data-ttu-id="cf3df-216">執行中</span><span class="sxs-lookup"><span data-stu-id="cf3df-216">Running</span></span>
- <span data-ttu-id="cf3df-217">已停止</span><span class="sxs-lookup"><span data-stu-id="cf3df-217">Stopped</span></span>
- <span data-ttu-id="cf3df-218">停止中</span><span class="sxs-lookup"><span data-stu-id="cf3df-218">Stopping</span></span>
- <span data-ttu-id="cf3df-219">暫止</span><span class="sxs-lookup"><span data-stu-id="cf3df-219">Suspended</span></span>
- <span data-ttu-id="cf3df-220">Suspending</span><span class="sxs-lookup"><span data-stu-id="cf3df-220">Suspending</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cf3df-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cf3df-221">-WhatIf</span></span>

<span data-ttu-id="cf3df-222">顯示執行時所發生 `Remove-Job` 的情況。</span><span class="sxs-lookup"><span data-stu-id="cf3df-222">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="cf3df-223">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf3df-223">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="cf3df-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf3df-224">CommonParameters</span></span>

<span data-ttu-id="cf3df-225">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cf3df-225">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf3df-226">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cf3df-226">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf3df-227">輸入</span><span class="sxs-lookup"><span data-stu-id="cf3df-227">INPUTS</span></span>

### <span data-ttu-id="cf3df-228">System.Management.Automation.Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-228">System.Management.Automation.Job</span></span>

<span data-ttu-id="cf3df-229">您可以將管線下的工作物件傳送至 `Remove-Job` 。</span><span class="sxs-lookup"><span data-stu-id="cf3df-229">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="cf3df-230">輸出</span><span class="sxs-lookup"><span data-stu-id="cf3df-230">OUTPUTS</span></span>

### <span data-ttu-id="cf3df-231">無</span><span class="sxs-lookup"><span data-stu-id="cf3df-231">None</span></span>

<span data-ttu-id="cf3df-232">`Remove-Job` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cf3df-232">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="cf3df-233">注意</span><span class="sxs-lookup"><span data-stu-id="cf3df-233">NOTES</span></span>

<span data-ttu-id="cf3df-234">PowerShell 作業會建立新的處理常式。</span><span class="sxs-lookup"><span data-stu-id="cf3df-234">A PowerShell job creates a new process.</span></span> <span data-ttu-id="cf3df-235">當作業完成時，進程便會結束。</span><span class="sxs-lookup"><span data-stu-id="cf3df-235">When the job completes, the process exits.</span></span> <span data-ttu-id="cf3df-236">當 `Remove-Job` 執行時，會移除作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="cf3df-236">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="cf3df-237">如果作業在完成前停止，而且其進程尚未結束，則會強制終止進程。</span><span class="sxs-lookup"><span data-stu-id="cf3df-237">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="cf3df-238">相關連結</span><span class="sxs-lookup"><span data-stu-id="cf3df-238">RELATED LINKS</span></span>

[<span data-ttu-id="cf3df-239">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="cf3df-239">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="cf3df-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="cf3df-240">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="cf3df-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="cf3df-241">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="cf3df-242">Get-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-242">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="cf3df-243">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="cf3df-243">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="cf3df-244">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-244">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="cf3df-245">Start-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-245">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="cf3df-246">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-246">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="cf3df-247">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="cf3df-247">Wait-Job</span></span>](Wait-Job.md)

