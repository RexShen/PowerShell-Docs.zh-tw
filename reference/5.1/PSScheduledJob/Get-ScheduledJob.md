---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203004"
---
# <span data-ttu-id="b3d6c-103">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-103">Get-ScheduledJob</span></span>

## <span data-ttu-id="b3d6c-104">概要</span><span class="sxs-lookup"><span data-stu-id="b3d6c-104">SYNOPSIS</span></span>
<span data-ttu-id="b3d6c-105">取得本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-105">Gets scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="b3d6c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b3d6c-106">SYNTAX</span></span>

### <span data-ttu-id="b3d6c-107">DefinitionId (預設值)</span><span class="sxs-lookup"><span data-stu-id="b3d6c-107">DefinitionId (Default)</span></span>

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="b3d6c-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="b3d6c-108">DefinitionName</span></span>

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="b3d6c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b3d6c-109">DESCRIPTION</span></span>
<span data-ttu-id="b3d6c-110">**Get-ScheduledJob** Cmdlet 會取得本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-110">The **Get-ScheduledJob** cmdlet gets scheduled jobs on the local computer.</span></span>
<span data-ttu-id="b3d6c-111">**Get-ScheduledJob** 只會取得目前使用者使用 Register-ScheduledJob Cmdlet 所建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-111">**Get-ScheduledJob** gets only scheduled jobs that are created by the current user using the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="b3d6c-112">雖然使用 **Register-ScheduledJob** Cmdlet 建立的工作會出現在 [工作排程器] 中， **Get-ScheduledJob** 只會取得排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-112">Although jobs that are created by using the **Register-ScheduledJob** cmdlet appear in Task Scheduler, **Get-ScheduledJob** gets only scheduled jobs.</span></span>
<span data-ttu-id="b3d6c-113">它不會取得在 [工作排程器] 中建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-113">It does not get scheduled tasks created in Task Scheduler.</span></span>

<span data-ttu-id="b3d6c-114">若未指定參數， **Get-ScheduledJob** 會取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-114">Without parameters, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="b3d6c-115">您可以使用 **Get-ScheduledJob** 的參數依識別碼或名稱取得排程工作，並檢查這些排程工作或使用管線將這些排程工作傳送至其他 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-115">You can use the parameters of **Get-ScheduledJob** to get scheduled jobs by ID or name and examine them or pipe them to other cmdlets.</span></span>

<span data-ttu-id="b3d6c-116">**Get-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-116">**Get-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="b3d6c-117">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="b3d6c-118">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="b3d6c-119">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b3d6c-120">範例</span><span class="sxs-lookup"><span data-stu-id="b3d6c-120">EXAMPLES</span></span>

### <span data-ttu-id="b3d6c-121">範例 1：取得所有排程工作</span><span class="sxs-lookup"><span data-stu-id="b3d6c-121">Example 1: Get all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob
```

<span data-ttu-id="b3d6c-122">此命令會取得本機電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-122">This command gets all scheduled jobs on the local computer.</span></span>

### <span data-ttu-id="b3d6c-123">範例 2：依名稱取得排程工作</span><span class="sxs-lookup"><span data-stu-id="b3d6c-123">Example 2: Get scheduled jobs by name</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

<span data-ttu-id="b3d6c-124">此命令會取得電腦上名稱包含 Backup 或 Archive 的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-124">This command gets all scheduled jobs on the computer that have names that include Backup or Archive.</span></span>
<span data-ttu-id="b3d6c-125">此命令格式可讓您搜尋特定工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-125">This command format lets you search for particular jobs.</span></span>

### <span data-ttu-id="b3d6c-126">範例 3：取得遠端電腦上的排程工作</span><span class="sxs-lookup"><span data-stu-id="b3d6c-126">Example 3: Get scheduled jobs on remote computers</span></span>

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

<span data-ttu-id="b3d6c-127">此命令會取得 Servers.txt 檔案中所列之遠端電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-127">This command gets all scheduled jobs on the computers that are listed in the Servers.txt file.</span></span>
<span data-ttu-id="b3d6c-128">此命令會使用 Invoke-Command Cmdlet，在每部電腦上執行 **Get-ScheduleJob** 命令。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-128">The command uses the Invoke-Command cmdlet to run a **Get-ScheduleJob** command on each computer.</span></span>

### <span data-ttu-id="b3d6c-129">範例 4：使用管線以將排程工作傳送至其他 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3d6c-129">Example 4: Pipe scheduled jobs to other cmdlets</span></span>

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

<span data-ttu-id="b3d6c-130">此命令會取得 DailyBackup 與 WeeklyBackup 排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-130">This command gets the job triggers of the DailyBackup and WeeklyBackup scheduled jobs.</span></span>
<span data-ttu-id="b3d6c-131">它會使用 **Get-ScheduledJob** Cmdlet 來取得排程工作，以及使用 Get-JobTrigger Cmdlet 來取得排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-131">It uses the **Get-ScheduledJob** cmdlet to get the scheduled jobs and the Get-JobTrigger cmdlet to get the job triggers of the scheduled jobs.</span></span>

## <span data-ttu-id="b3d6c-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b3d6c-132">PARAMETERS</span></span>

### <span data-ttu-id="b3d6c-133">-Id</span><span class="sxs-lookup"><span data-stu-id="b3d6c-133">-Id</span></span>
<span data-ttu-id="b3d6c-134">只取得具有所指定識別碼 (ID) 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-134">Gets only the scheduled jobs with the specified identification number (ID).</span></span>
<span data-ttu-id="b3d6c-135">輸入電腦上之排程工作的一或多個識別碼。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-135">Enter one or more IDs of scheduled jobs on the computer.</span></span>
<span data-ttu-id="b3d6c-136">根據預設值， **Get-ScheduledJob** 會取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-136">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3d6c-137">-Name</span><span class="sxs-lookup"><span data-stu-id="b3d6c-137">-Name</span></span>
<span data-ttu-id="b3d6c-138">只取得具有所指定名稱的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-138">Gets only the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="b3d6c-139">輸入電腦上之排程工作的一或多個名稱。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-139">Enter one or more names of scheduled jobs on the computer.</span></span>
<span data-ttu-id="b3d6c-140">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-140">Wildcards are supported.</span></span>
<span data-ttu-id="b3d6c-141">根據預設值， **Get-ScheduledJob** 會取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-141">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b3d6c-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b3d6c-142">CommonParameters</span></span>
<span data-ttu-id="b3d6c-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b3d6c-144">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b3d6c-145">輸入</span><span class="sxs-lookup"><span data-stu-id="b3d6c-145">INPUTS</span></span>

### <span data-ttu-id="b3d6c-146">無</span><span class="sxs-lookup"><span data-stu-id="b3d6c-146">None</span></span>
<span data-ttu-id="b3d6c-147">您無法使用管線將輸入傳送至 **Get-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-147">You cannot pipe input to **Get-ScheduledJob** .</span></span>

## <span data-ttu-id="b3d6c-148">輸出</span><span class="sxs-lookup"><span data-stu-id="b3d6c-148">OUTPUTS</span></span>

### <span data-ttu-id="b3d6c-149">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="b3d6c-149">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="b3d6c-150">注意</span><span class="sxs-lookup"><span data-stu-id="b3d6c-150">NOTES</span></span>

* <span data-ttu-id="b3d6c-151">每個排程工作都是儲存在本機電腦之 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-151">Each scheduled job is saved in a subdirectory of the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the local computer.</span></span> <span data-ttu-id="b3d6c-152">該子目錄是依排程工作名稱命名，而且包含排程工作的 XML 檔案與其執行記錄。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-152">The subdirectory is named for the scheduled job and contains the XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="b3d6c-153">如需有關磁碟上之排程工作的詳細資訊，請參閱 about_Scheduled_Jobs_Advanced。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-153">For more information about scheduled jobs on disk, see about_Scheduled_Jobs_Advanced.</span></span>
* <span data-ttu-id="b3d6c-154">您在 Windows PowerShell 中建立的排程工作會出現在 [工作排程器] 的 [工作排程器程式庫\Microsoft\Windows\PowerShell\ScheduledJobs] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-154">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs folder.</span></span> <span data-ttu-id="b3d6c-155">您可以使用 [工作排程器] 來檢視及編輯排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-155">You can use Task Scheduler to view and edit the scheduled job.</span></span>
* <span data-ttu-id="b3d6c-156">您可以使用 [工作排程器]、SchTasks.exe 命令列工具或「工作排程器」Cmdlet 來管理使用「排程工作」Cmdlet 建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-156">You can use Task Scheduler, the SchTasks.exe command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="b3d6c-157">不過，您無法使用「排程工作」Cmdlet 來管理您在 [工作排程器] 中建立的工作。</span><span class="sxs-lookup"><span data-stu-id="b3d6c-157">However, you cannot use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

## <span data-ttu-id="b3d6c-158">相關連結</span><span class="sxs-lookup"><span data-stu-id="b3d6c-158">RELATED LINKS</span></span>

[<span data-ttu-id="b3d6c-159">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-159">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="b3d6c-160">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-160">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="b3d6c-161">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-161">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="b3d6c-162">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-162">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="b3d6c-163">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-163">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="b3d6c-164">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-164">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="b3d6c-165">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-165">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="b3d6c-166">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b3d6c-166">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="b3d6c-167">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-167">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="b3d6c-168">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b3d6c-168">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="b3d6c-169">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-169">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="b3d6c-170">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-170">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="b3d6c-171">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b3d6c-171">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="b3d6c-172">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-172">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="b3d6c-173">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b3d6c-173">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="b3d6c-174">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b3d6c-174">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
