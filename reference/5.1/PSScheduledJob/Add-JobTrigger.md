---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203035"
---
# <span data-ttu-id="c25e9-103">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-103">Add-JobTrigger</span></span>

## <span data-ttu-id="c25e9-104">概要</span><span class="sxs-lookup"><span data-stu-id="c25e9-104">SYNOPSIS</span></span>
<span data-ttu-id="c25e9-105">新增工作觸發程序至排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-105">Adds job triggers to scheduled jobs.</span></span>

## <span data-ttu-id="c25e9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c25e9-106">SYNTAX</span></span>

### <span data-ttu-id="c25e9-107">JobDefinition (預設值)</span><span class="sxs-lookup"><span data-stu-id="c25e9-107">JobDefinition (Default)</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### <span data-ttu-id="c25e9-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c25e9-108">JobDefinitionId</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="c25e9-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="c25e9-109">JobDefinitionName</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="c25e9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c25e9-110">DESCRIPTION</span></span>
<span data-ttu-id="c25e9-111">**Add-JobTrigger** Cmdlet 會新增工作觸發程序至排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-111">The **Add-JobTrigger** cmdlet adds job triggers to scheduled jobs.</span></span>
<span data-ttu-id="c25e9-112">您可以使用它來新增多個觸發程序至多個排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-112">You can use it to add multiple triggers to multiple scheduled jobs.</span></span>

<span data-ttu-id="c25e9-113">工作觸發程式會以一次性或週期性排程啟動排程工作，或在事件發生時啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-113">A job trigger starts a scheduled job on a one-time or recurring schedule or when an event occurs.</span></span>

<span data-ttu-id="c25e9-114">使用 **Add-JobTrigger** 的 *Trigger* 參數來識別要新增的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c25e9-114">Use the *Trigger* parameter of **Add-JobTrigger** to identify the job triggers to add.</span></span>
<span data-ttu-id="c25e9-115">使用 **Add-JobTrigger** 的 *Name* 、 *ID* 或 *InputObject* 參數來識別要新增觸發程序的排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-115">Use the *Name* , *ID* , or *InputObject* parameters of **Add-JobTrigger** to identify the scheduled job to which the triggers are added.</span></span>

<span data-ttu-id="c25e9-116">若要針對 *Trigger* 參數的值建立工作觸發程序，請使用 New-JobTrigger Cmdlet 或使用雜湊表來指定工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c25e9-116">To create job triggers for the value of the *Trigger* parameter, use the New-JobTrigger cmdlet or use a hash table to specify the job trigger.</span></span>

<span data-ttu-id="c25e9-117">**Add-JobTrigger** 為 Windows PowerShell 所包含 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="c25e9-117">**Add-JobTrigger** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="c25e9-118">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="c25e9-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="c25e9-119">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="c25e9-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="c25e9-120">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c25e9-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c25e9-121">範例</span><span class="sxs-lookup"><span data-stu-id="c25e9-121">EXAMPLES</span></span>

### <span data-ttu-id="c25e9-122">範例 1：新增工作觸發程序至排程工作</span><span class="sxs-lookup"><span data-stu-id="c25e9-122">Example 1: Add a job trigger to a scheduled job</span></span>

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

<span data-ttu-id="c25e9-123">這些命令會新增 Daily 工作觸發程序至 TestJob 排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-123">These commands add the Daily job trigger to the TestJob scheduled job.</span></span>

<span data-ttu-id="c25e9-124">第一個命令會使用 New-JobTrigger Cmdlet 來建立工作觸發程序，此工作觸發程序會在每天上午 3 點啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-124">The first command uses the New-JobTrigger cmdlet to create a job trigger that starts a scheduled job every day at 3:00 a.m.</span></span>
<span data-ttu-id="c25e9-125">此命令會將工作觸發程序儲存於 $Daily 變數中。</span><span class="sxs-lookup"><span data-stu-id="c25e9-125">The command saves the job trigger in the $Daily variable.</span></span>

<span data-ttu-id="c25e9-126">第二個命令使用 **Add-JobTrigger** Cmdlet 將 $Startup 變數中的工作觸發程序新增至 TestJob 排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-126">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in the $Startup variable to the TestJob scheduled job.</span></span>

### <span data-ttu-id="c25e9-127">範例2：將工作觸發程式新增至數個排程工作</span><span class="sxs-lookup"><span data-stu-id="c25e9-127">Example 2: Add a job trigger to several scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

<span data-ttu-id="c25e9-128">此命令會新增 AtStartup 工作觸發程序至本機電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-128">This command adds an AtStartup job trigger to all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="c25e9-129">它會使用 Get-ScheduledJob 來取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-129">It uses the Get-ScheduledJob to get all of the scheduled jobs on the computer.</span></span>
<span data-ttu-id="c25e9-130">它會使用管線運算子 (|) 傳送工作至 **Add-JobTrigger** Cmdlet，此 Cmdlet 會新增工作觸發程序至每個排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-130">It uses a pipeline operator (|) to send the jobs to the **Add-JobTrigger** cmdlet, which adds the job trigger to each of the scheduled jobs.</span></span>
<span data-ttu-id="c25e9-131">*Trigger* 參數的值是 New-JobTrigger 命令，此命令會建立 AtStartup 工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c25e9-131">The value of the *Trigger* parameter is a New-JobTrigger command that creates the AtStartup job trigger.</span></span>

### <span data-ttu-id="c25e9-132">範例 3：複製工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="c25e9-132">Example 3: Copy a job trigger</span></span>

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

<span data-ttu-id="c25e9-133">這些命令會從 BackupArchives 排程工作複製工作觸發程序，並將它新增到 TestBackup 與 BackupLogs 排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-133">These commands copy the job trigger from the BackupArchives scheduled job and add it to the TestBackup and BackupLogs scheduled jobs.</span></span>

<span data-ttu-id="c25e9-134">第一個命令會使用 Get-JobTrigger Cmdlet，來取得 BackupArchives 排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c25e9-134">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the BackupArchives scheduled job.</span></span>
<span data-ttu-id="c25e9-135">命令會將觸發程序儲存於 $t 變數中。</span><span class="sxs-lookup"><span data-stu-id="c25e9-135">The command saves the trigger in the $t variable.</span></span>

<span data-ttu-id="c25e9-136">第二個命令使用 **Add-JobTrigger** Cmdlet 將 $t 中的工作觸發程序新增到 TestBackup 與 BackupLogs 排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-136">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in $t to the TestBackup and BackupLogs scheduled jobs.</span></span>

## <span data-ttu-id="c25e9-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c25e9-137">PARAMETERS</span></span>

### <span data-ttu-id="c25e9-138">-Id</span><span class="sxs-lookup"><span data-stu-id="c25e9-138">-Id</span></span>
<span data-ttu-id="c25e9-139">指定排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c25e9-139">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="c25e9-140">**Add-JobTrigger** 會新增工作觸發程序至指定的排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-140">**Add-JobTrigger** adds the job trigger to the specified scheduled jobs.</span></span>

<span data-ttu-id="c25e9-141">若要取得本機電腦或遠端電腦上排程工作的識別碼，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c25e9-141">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c25e9-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c25e9-142">-InputObject</span></span>
<span data-ttu-id="c25e9-143">指定排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-143">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="c25e9-144">輸入包含 **register-scheduledjob** 物件的變數，或輸入可取得 **register-scheduledjob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="c25e9-144">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="c25e9-145">您也可以使用管線將 **ScheduledJob** 物件傳送至 **Add-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="c25e9-145">You can also pipe **ScheduledJob** objects to **Add-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c25e9-146">-Name</span><span class="sxs-lookup"><span data-stu-id="c25e9-146">-Name</span></span>
<span data-ttu-id="c25e9-147">指定排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="c25e9-147">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="c25e9-148">**Add-JobTrigger** 會新增工作觸發程序至指定的排程工作。</span><span class="sxs-lookup"><span data-stu-id="c25e9-148">**Add-JobTrigger** adds the job triggers to the specified scheduled jobs.</span></span>
<span data-ttu-id="c25e9-149">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c25e9-149">Wildcards are supported.</span></span>

<span data-ttu-id="c25e9-150">若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c25e9-150">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c25e9-151">-Trigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-151">-Trigger</span></span>
<span data-ttu-id="c25e9-152">指定要新增的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c25e9-152">Specifies the job triggers to add.</span></span>
<span data-ttu-id="c25e9-153">輸入指定工作觸發程序的雜湊表或包含 **ScheduledJobTrigger** 物件的變數，或輸入可取得 **ScheduledJobTrigger** 物件的命令或運算式，例如 Get-JobTrigger 命令。</span><span class="sxs-lookup"><span data-stu-id="c25e9-153">Enter a hash table that specifies job triggers or a variable that contains **ScheduledJobTrigger** objects, or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="c25e9-154">您也可以使用管線將 **ScheduledJobTrigger** 物件傳送至 **Add-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="c25e9-154">You can also pipe **ScheduledJobTrigger** objects to **Add-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c25e9-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c25e9-155">CommonParameters</span></span>
<span data-ttu-id="c25e9-156">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c25e9-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c25e9-157">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c25e9-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c25e9-158">輸入</span><span class="sxs-lookup"><span data-stu-id="c25e9-158">INPUTS</span></span>

### <span data-ttu-id="c25e9-159">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger、Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="c25e9-159">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger, Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="c25e9-160">您可以使用管線傳送工作觸發程序或排程工作至 **Add-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="c25e9-160">You can pipe job triggers or scheduled jobs to **Add-JobTrigger** .</span></span>

## <span data-ttu-id="c25e9-161">輸出</span><span class="sxs-lookup"><span data-stu-id="c25e9-161">OUTPUTS</span></span>

### <span data-ttu-id="c25e9-162">無</span><span class="sxs-lookup"><span data-stu-id="c25e9-162">None</span></span>
<span data-ttu-id="c25e9-163">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c25e9-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="c25e9-164">注意</span><span class="sxs-lookup"><span data-stu-id="c25e9-164">NOTES</span></span>

## <span data-ttu-id="c25e9-165">相關連結</span><span class="sxs-lookup"><span data-stu-id="c25e9-165">RELATED LINKS</span></span>

[<span data-ttu-id="c25e9-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="c25e9-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="c25e9-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c25e9-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="c25e9-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="c25e9-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c25e9-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="c25e9-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="c25e9-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c25e9-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="c25e9-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c25e9-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="c25e9-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="c25e9-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c25e9-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="c25e9-176">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c25e9-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="c25e9-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="c25e9-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c25e9-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="c25e9-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c25e9-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="c25e9-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c25e9-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="c25e9-181">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c25e9-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
