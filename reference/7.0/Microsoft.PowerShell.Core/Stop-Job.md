---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 77982029240727ff5c7c90866d1a67cf7cae794d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391301"
---
# <span data-ttu-id="12ad6-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-103">Stop-Job</span></span>

## <span data-ttu-id="12ad6-104">概要</span><span class="sxs-lookup"><span data-stu-id="12ad6-104">SYNOPSIS</span></span>
<span data-ttu-id="12ad6-105">停止 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="12ad6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12ad6-106">SYNTAX</span></span>

### <span data-ttu-id="12ad6-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="12ad6-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12ad6-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="12ad6-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12ad6-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="12ad6-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12ad6-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="12ad6-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12ad6-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="12ad6-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12ad6-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="12ad6-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12ad6-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="12ad6-113">DESCRIPTION</span></span>

<span data-ttu-id="12ad6-114">此 `Stop-Job` Cmdlet 會停止進行中的 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-114">The `Stop-Job` cmdlet stops PowerShell background jobs that are in progress.</span></span> <span data-ttu-id="12ad6-115">您可以使用這個 Cmdlet 來停止所有工作，或根據其名稱、識別碼、實例識別碼或狀態來停止選取的工作，或將工作物件傳遞給 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="12ad6-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to `Stop-Job`.</span></span>

<span data-ttu-id="12ad6-116">您可以使用 `Stop-Job` 來停止背景工作，例如使用 `Start-Job` Cmdlet 或任何 Cmdlet 的 **AsJob** 參數啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-116">You can use `Stop-Job` to stop background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span> <span data-ttu-id="12ad6-117">當您停止背景工作時，PowerShell 會完成該工作佇列中所有擱置中的工作，然後結束該工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span> <span data-ttu-id="12ad6-118">在送出這個命令之後，就不會再新增任何新工作到佇列中。</span><span class="sxs-lookup"><span data-stu-id="12ad6-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="12ad6-119">此 Cmdlet 不會刪除背景工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-119">This cmdlet does not delete background jobs.</span></span> <span data-ttu-id="12ad6-120">若要刪除作業，請使用 `Remove-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12ad6-120">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="12ad6-121">從 Windows PowerShell 3.0 開始， `Stop-Job` 也會停止自訂工作類型，例如工作流程工作和排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="12ad6-121">Starting in Windows PowerShell 3.0, `Stop-Job` also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="12ad6-122">若要啟用 `Stop-Job` 以自訂工作類型停止作業，請 `Stop-Job` 使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入會話中，再執行命令。</span><span class="sxs-lookup"><span data-stu-id="12ad6-122">To enable `Stop-Job` to stop a job with custom job type, import the module that supports the custom job type into the session before you run a `Stop-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="12ad6-123">如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。</span><span class="sxs-lookup"><span data-stu-id="12ad6-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="12ad6-124">範例</span><span class="sxs-lookup"><span data-stu-id="12ad6-124">EXAMPLES</span></span>

### <span data-ttu-id="12ad6-125">範例 1︰使用 Invoke-Command 停止遠端電腦上的工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="12ad6-126">此範例示範如何使用指令 `Stop-Job` 程式來停止在遠端電腦上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="12ad6-126">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="12ad6-127">因為作業是使用 `Invoke-Command` Cmdlet `Start-Job` 從遠端執行命令來啟動，所以會將工作物件儲存在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="12ad6-127">Because the job was started by using the `Invoke-Command` cmdlet to run a `Start-Job` command remotely, the job object is stored on the remote computer.</span></span> <span data-ttu-id="12ad6-128">您必須使用另一個 `Invoke-Command` 命令 `Stop-Job` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="12ad6-128">You must use another `Invoke-Command` command to run a `Stop-Job` command remotely.</span></span> <span data-ttu-id="12ad6-129">如需有關遠端背景工作的詳細資訊，請參閱 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="12ad6-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="12ad6-130">第一個命令會在 Server01 電腦上建立 ( **PSSession** ) 的 PowerShell 會話，然後將會話物件儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="12ad6-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the `$s` variable.</span></span> <span data-ttu-id="12ad6-131">命令使用網域系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="12ad6-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="12ad6-132">第二個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="12ad6-132">The second command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the session.</span></span> <span data-ttu-id="12ad6-133">工作中的命令取得 System 事件記錄檔中的所有事件。</span><span class="sxs-lookup"><span data-stu-id="12ad6-133">The command in the job gets all of the events in the System event log.</span></span> <span data-ttu-id="12ad6-134">產生的工作物件會儲存在 `$j` 變數中。</span><span class="sxs-lookup"><span data-stu-id="12ad6-134">The resulting job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="12ad6-135">第三個命令停止工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-135">The third command stops the job.</span></span> <span data-ttu-id="12ad6-136">它會使用 `Invoke-Command` Cmdlet 在 `Stop-Job` Server01 上的 **PSSession** 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="12ad6-136">It uses the `Invoke-Command` cmdlet to run a `Stop-Job` command in the **PSSession** on Server01.</span></span> <span data-ttu-id="12ad6-137">由於工作物件是儲存在 `$j` 本機電腦上的變數中，因此命令會使用 Using 範圍修飾符來識別 `$j` 為本機變數。</span><span class="sxs-lookup"><span data-stu-id="12ad6-137">Because the job objects are stored in `$j`, which is a variable on the local computer, the command uses the Using scope modifier to identify `$j` as a local variable.</span></span>
<span data-ttu-id="12ad6-138">如需 Using 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](about/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="12ad6-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="12ad6-139">當命令完成時，會停止工作，且中 **PSSession** 的 PSSession `$s` 可供使用。</span><span class="sxs-lookup"><span data-stu-id="12ad6-139">When the command finishes, the job is stopped and the **PSSession** in `$s` is available for use.</span></span>

### <span data-ttu-id="12ad6-140">範例 2︰停止背景工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="12ad6-141">此命令停止 Job1 背景工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="12ad6-142">範例 3︰停止幾個背景工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="12ad6-143">此命令停止三個工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-143">This command stops three jobs.</span></span>
<span data-ttu-id="12ad6-144">它會依其識別碼來識別它們。</span><span class="sxs-lookup"><span data-stu-id="12ad6-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="12ad6-145">範例 4︰停止所有背景工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="12ad6-146">此命令停止目前工作階段中的所有背景工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="12ad6-147">範例 5︰停止所有已封鎖的背景工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="12ad6-148">此命令停止所有已封鎖的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="12ad6-149">範例 6︰使用執行個體識別碼停止工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-149">Example 6: Stop a job by using an instance ID</span></span>

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

<span data-ttu-id="12ad6-150">這些命令示範如何根據工作的執行個體識別碼來停止工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="12ad6-151">第一個命令會使用 `Get-Job` Cmdlet 取得目前會話中的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-151">The first command uses the `Get-Job` cmdlet to get the jobs in the current session.</span></span> <span data-ttu-id="12ad6-152">此命令會使用管線運算子 (`|`) 將作業傳送至 `Format-Table` 命令，該命令會顯示每個工作的指定屬性資料表。</span><span class="sxs-lookup"><span data-stu-id="12ad6-152">The command uses a pipeline operator (`|`) to send the jobs to a `Format-Table` command, which displays a table of the specified properties of each job.</span></span> <span data-ttu-id="12ad6-153">此表格包含每個工作的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="12ad6-153">The table includes the Instance ID of each job.</span></span> <span data-ttu-id="12ad6-154">它使用計算的屬性來顯示工作狀態。</span><span class="sxs-lookup"><span data-stu-id="12ad6-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="12ad6-155">第二個命令使用 `Stop-Job` 具有 **InstanceID** 參數的命令，以停止選取的作業。</span><span class="sxs-lookup"><span data-stu-id="12ad6-155">The second command uses a `Stop-Job` command that has the **InstanceID** parameter to stop a selected job.</span></span>

### <span data-ttu-id="12ad6-156">範例 7︰停止遠端電腦上的工作</span><span class="sxs-lookup"><span data-stu-id="12ad6-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="12ad6-157">此範例示範如何使用指令 `Stop-Job` 程式來停止在遠端電腦上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="12ad6-157">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="12ad6-158">因為作業是使用指令程式的 **AsJob** 參數來啟動 `Invoke-Command` ，所以即使工作是在遠端電腦上執行，工作物件仍位於本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="12ad6-158">Because the job was started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span> <span data-ttu-id="12ad6-159">因此，您可以使用本機 `Stop-Job` 命令來停止工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-159">Therefore, you can use a local `Stop-Job` command to stop the job.</span></span>

<span data-ttu-id="12ad6-160">第一個命令會使用 `Invoke-Command` Cmdlet 在 Server01 電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-160">The first command uses the `Invoke-Command` cmdlet to start a background job on the Server01 computer.</span></span> <span data-ttu-id="12ad6-161">命令使用 **AsJob** 參數將遠端命令當作背景工作來執行。</span><span class="sxs-lookup"><span data-stu-id="12ad6-161">The command uses the **AsJob** parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="12ad6-162">此命令會傳回工作物件，此物件與 Cmdlet 所傳回的工作物件相同 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="12ad6-162">This command returns a job object, which is the same job object that the `Start-Job` cmdlet returns.</span></span>
<span data-ttu-id="12ad6-163">此命令會將工作物件儲存在 `$j` 變數中。</span><span class="sxs-lookup"><span data-stu-id="12ad6-163">The command saves the job object in the `$j` variable.</span></span>

<span data-ttu-id="12ad6-164">第二個命令會使用管線運算子，將變數中的工作傳送 `$j` 至 `Stop-Job` 。</span><span class="sxs-lookup"><span data-stu-id="12ad6-164">The second command uses a pipeline operator to send the job in the `$j` variable to `Stop-Job`.</span></span> <span data-ttu-id="12ad6-165">此命令會使用 **PassThru** 參數來指示傳回 `Stop-Job` 工作物件。</span><span class="sxs-lookup"><span data-stu-id="12ad6-165">The command uses the **PassThru** parameter to direct `Stop-Job` to return a job object.</span></span> <span data-ttu-id="12ad6-166">工作物件顯示會確認工作的狀態為 Stopped。</span><span class="sxs-lookup"><span data-stu-id="12ad6-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="12ad6-167">如需有關遠端背景工作的詳細資訊，請參閱 about_Remote_Jobs。</span><span class="sxs-lookup"><span data-stu-id="12ad6-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="12ad6-168">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12ad6-168">PARAMETERS</span></span>

### <span data-ttu-id="12ad6-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="12ad6-169">-Filter</span></span>

<span data-ttu-id="12ad6-170">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12ad6-170">Specifies a hash table of conditions.</span></span> <span data-ttu-id="12ad6-171">此 Cmdlet 會停止符合所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="12ad6-172">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="12ad6-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="12ad6-173">這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="12ad6-174">它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="12ad6-174">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="12ad6-175">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="12ad6-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="12ad6-176">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="12ad6-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="12ad6-177">-Id</span><span class="sxs-lookup"><span data-stu-id="12ad6-177">-Id</span></span>

<span data-ttu-id="12ad6-178">指定此 Cmdlet 停止之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="12ad6-178">Specifies the IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="12ad6-179">預設為目前工作階段中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="12ad6-180">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-180">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="12ad6-181">與執行個體識別碼相比，它比較容易記住並輸入，但是它只有在目前的工作階段內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="12ad6-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="12ad6-182">您可以輸入一個或多個識別碼，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="12ad6-182">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="12ad6-183">若要尋找工作的識別碼，請輸入 `Get-Job`。</span><span class="sxs-lookup"><span data-stu-id="12ad6-183">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12ad6-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="12ad6-184">-InstanceId</span></span>

<span data-ttu-id="12ad6-185">指定此 Cmdlet 停止之工作的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="12ad6-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="12ad6-186">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-186">The default is all jobs.</span></span>

<span data-ttu-id="12ad6-187">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="12ad6-188">若要尋找工作的實例識別碼，請使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="12ad6-188">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12ad6-189">-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-189">-Job</span></span>

<span data-ttu-id="12ad6-190">指定此 Cmdlet 停止的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-190">Specifies the jobs that this cmdlet stops.</span></span> <span data-ttu-id="12ad6-191">輸入包含工作的變數，或輸入可取得工作的命令。</span><span class="sxs-lookup"><span data-stu-id="12ad6-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="12ad6-192">您也可以使用管線運算子將作業提交至 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12ad6-192">You can also use a pipeline operator to submit jobs to the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="12ad6-193">預設 `Stop-Job` 會刪除在目前會話中啟動的所有工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-193">By default, `Stop-Job` deletes all jobs that were started in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="12ad6-194">-Name</span><span class="sxs-lookup"><span data-stu-id="12ad6-194">-Name</span></span>

<span data-ttu-id="12ad6-195">指定此 Cmdlet 停止之工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="12ad6-195">Specifies friendly names of jobs that this cmdlet stops.</span></span> <span data-ttu-id="12ad6-196">請以逗號分隔的清單方式輸入工作名稱，或使用萬用字元 (\*) 來輸入工作名稱模式。</span><span class="sxs-lookup"><span data-stu-id="12ad6-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span> <span data-ttu-id="12ad6-197">預設會 `Stop-Job` 停止在目前會話中建立的所有作業。</span><span class="sxs-lookup"><span data-stu-id="12ad6-197">By default, `Stop-Job` stops all jobs created in the current session.</span></span>

<span data-ttu-id="12ad6-198">由於易記名稱不保證是唯一的，因此請在依名稱停止工作時使用 **WhatIf** 和 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="12ad6-198">Because the friendly name is not guaranteed to be unique, use the **WhatIf** and **Confirm** parameters when stopping jobs by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="12ad6-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12ad6-199">-PassThru</span></span>

<span data-ttu-id="12ad6-200">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="12ad6-200">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="12ad6-201">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="12ad6-201">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="12ad6-202">-State</span><span class="sxs-lookup"><span data-stu-id="12ad6-202">-State</span></span>

<span data-ttu-id="12ad6-203">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="12ad6-203">Specifies a job state.</span></span> <span data-ttu-id="12ad6-204">此 Cmdlet 只停止處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="12ad6-204">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="12ad6-205">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="12ad6-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="12ad6-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="12ad6-206">NotStarted</span></span>
- <span data-ttu-id="12ad6-207">執行中</span><span class="sxs-lookup"><span data-stu-id="12ad6-207">Running</span></span>
- <span data-ttu-id="12ad6-208">Completed</span><span class="sxs-lookup"><span data-stu-id="12ad6-208">Completed</span></span>
- <span data-ttu-id="12ad6-209">失敗</span><span class="sxs-lookup"><span data-stu-id="12ad6-209">Failed</span></span>
- <span data-ttu-id="12ad6-210">已停止</span><span class="sxs-lookup"><span data-stu-id="12ad6-210">Stopped</span></span>
- <span data-ttu-id="12ad6-211">封鎖</span><span class="sxs-lookup"><span data-stu-id="12ad6-211">Blocked</span></span>
- <span data-ttu-id="12ad6-212">暫止</span><span class="sxs-lookup"><span data-stu-id="12ad6-212">Suspended</span></span>
- <span data-ttu-id="12ad6-213">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="12ad6-213">Disconnected</span></span>
- <span data-ttu-id="12ad6-214">Suspending</span><span class="sxs-lookup"><span data-stu-id="12ad6-214">Suspending</span></span>
- <span data-ttu-id="12ad6-215">停止中</span><span class="sxs-lookup"><span data-stu-id="12ad6-215">Stopping</span></span>

<span data-ttu-id="12ad6-216">如需有關工作狀態的詳細資訊，請參閱 [JobState 列舉](/dotnet/api/system.management.automation.jobstate)。</span><span class="sxs-lookup"><span data-stu-id="12ad6-216">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="12ad6-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12ad6-217">-Confirm</span></span>

<span data-ttu-id="12ad6-218">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="12ad6-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="12ad6-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12ad6-219">-WhatIf</span></span>

<span data-ttu-id="12ad6-220">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="12ad6-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="12ad6-221">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="12ad6-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="12ad6-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12ad6-222">CommonParameters</span></span>

<span data-ttu-id="12ad6-223">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="12ad6-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12ad6-224">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="12ad6-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12ad6-225">輸入</span><span class="sxs-lookup"><span data-stu-id="12ad6-225">INPUTS</span></span>

### <span data-ttu-id="12ad6-226">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="12ad6-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="12ad6-227">您可以使用管線將工作物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="12ad6-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="12ad6-228">輸出</span><span class="sxs-lookup"><span data-stu-id="12ad6-228">OUTPUTS</span></span>

### <span data-ttu-id="12ad6-229">無、System.Management.Automation.PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="12ad6-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="12ad6-230">如果您指定 **PassThru** 參數，此 Cmdlet 會傳回工作物件。</span><span class="sxs-lookup"><span data-stu-id="12ad6-230">This cmdlet returns a job object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="12ad6-231">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="12ad6-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="12ad6-232">注意</span><span class="sxs-lookup"><span data-stu-id="12ad6-232">NOTES</span></span>

## <span data-ttu-id="12ad6-233">相關連結</span><span class="sxs-lookup"><span data-stu-id="12ad6-233">RELATED LINKS</span></span>

[<span data-ttu-id="12ad6-234">Get-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="12ad6-235">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="12ad6-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="12ad6-236">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="12ad6-237">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="12ad6-238">Start-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-238">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="12ad6-239">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="12ad6-239">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="12ad6-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="12ad6-240">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="12ad6-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="12ad6-241">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="12ad6-242">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="12ad6-242">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="12ad6-243">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="12ad6-243">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="12ad6-244">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="12ad6-244">about_Scopes</span></span>](About/about_scopes.md)
