---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203007"
---
# <span data-ttu-id="b8730-103">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-103">Get-JobTrigger</span></span>

## <span data-ttu-id="b8730-104">概要</span><span class="sxs-lookup"><span data-stu-id="b8730-104">SYNOPSIS</span></span>
<span data-ttu-id="b8730-105">取得排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-105">Gets the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="b8730-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8730-106">SYNTAX</span></span>

### <span data-ttu-id="b8730-107">JobDefinition (預設值)</span><span class="sxs-lookup"><span data-stu-id="b8730-107">JobDefinition (Default)</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="b8730-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b8730-108">JobDefinitionId</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="b8730-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="b8730-109">JobDefinitionName</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="b8730-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b8730-110">DESCRIPTION</span></span>
<span data-ttu-id="b8730-111">**Get-JobTrigger** Cmdlet 會取得排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-111">The **Get-JobTrigger** cmdlet gets the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="b8730-112">您可以使用此命令檢查工作觸發程序，或者以管線傳送工作觸發程序至其他 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8730-112">You can use this command to examine the job triggers or to pipe the job triggers to other cmdlets.</span></span>

<span data-ttu-id="b8730-113">工作觸發程式會定義用於啟動排程工作的週期性排程或條件。</span><span class="sxs-lookup"><span data-stu-id="b8730-113">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="b8730-114">工作觸發程序不會獨立儲存至磁碟；它們是排程工作的一部分。</span><span class="sxs-lookup"><span data-stu-id="b8730-114">Job triggers are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="b8730-115">若要取得工作觸發程序，請指定觸發程序啟動的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b8730-115">To get a job trigger, specify the scheduled job that the trigger starts.</span></span>

<span data-ttu-id="b8730-116">使用 **Get-JobTrigger** Cmdlet 的參數來識別排程工作。</span><span class="sxs-lookup"><span data-stu-id="b8730-116">Use the parameters of the **Get-JobTrigger** cmdlet to identify the scheduled jobs.</span></span>
<span data-ttu-id="b8730-117">您可以依名稱或識別碼來識別排程工作，或是輸入或將 **register-scheduledjob** 物件（例如 Get-ScheduledJob Cmdlet 所傳回的物件）輸入或輸送至 **enable-jobtrigger** 。</span><span class="sxs-lookup"><span data-stu-id="b8730-117">You can identify the scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-JobTrigger** .</span></span>

<span data-ttu-id="b8730-118">**Get-JobTrigger** 為 Windows PowerShell 所包含 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="b8730-118">**Get-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="b8730-119">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="b8730-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="b8730-120">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="b8730-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="b8730-121">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b8730-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b8730-122">範例</span><span class="sxs-lookup"><span data-stu-id="b8730-122">EXAMPLES</span></span>

### <span data-ttu-id="b8730-123">範例 1：依排程工作名稱取得工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="b8730-123">Example 1: Get a job trigger by scheduled job name</span></span>

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

<span data-ttu-id="b8730-124">此命令會使用 Enable-jobtrigger 的 *Name* 參數來取得 BackupJob 排程工作的工作觸發 **程式** 。</span><span class="sxs-lookup"><span data-stu-id="b8730-124">The command uses the *Name* parameter of **Get-JobTrigger** to get the job triggers of the BackupJob scheduled job.</span></span>

### <span data-ttu-id="b8730-125">範例 2：依識別碼取得工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="b8730-125">Example 2: Get a job trigger by ID</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

<span data-ttu-id="b8730-126">此範例會使用 Enable-jobtrigger 的 *ID* 參數來取得排程工作的工作觸發 **程式** 。</span><span class="sxs-lookup"><span data-stu-id="b8730-126">The example uses the *ID* parameter of **Get-JobTrigger** to get the job triggers of a scheduled job.</span></span>

### <span data-ttu-id="b8730-127">範例 3：使用管線傳送工作來取得工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="b8730-127">Example 3: Get job triggers by piping a job</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

<span data-ttu-id="b8730-128">此命令會取得在其名稱中有備份或封存之所有工作的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="b8730-128">This command gets the job triggers of all jobs that have Backup or Archive in their names.</span></span>

### <span data-ttu-id="b8730-129">範例 4：取得遠端電腦上工作的工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="b8730-129">Example 4: Get the job trigger of a job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

<span data-ttu-id="b8730-130">此命令會取得遠端電腦上之排程工作的兩個工作觸發程序的其中一個。</span><span class="sxs-lookup"><span data-stu-id="b8730-130">This command gets one of the two job triggers of a scheduled job on a remote computer.</span></span>

<span data-ttu-id="b8730-131">此命令會使用 Invoke-Command Cmdlet，在 Server01 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="b8730-131">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>
<span data-ttu-id="b8730-132">其會使用 Get-ScheduledJob Cmdlet 來取得 Backup 排程工作，並使用管線將它傳送至 **Get-JobTrigger** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8730-132">It uses the Get-ScheduledJob cmdlet to get the Backup scheduled job, which it pipes to the **Get-JobTrigger** cmdlet.</span></span>
<span data-ttu-id="b8730-133">它使用 *TriggerID* 參數來只取得第二個觸發程式。</span><span class="sxs-lookup"><span data-stu-id="b8730-133">It uses the *TriggerID* parameter to get only the second trigger.</span></span>

### <span data-ttu-id="b8730-134">範例 5：取得所有工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="b8730-134">Example 5: Get all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

<span data-ttu-id="b8730-135">此命令會取得本機電腦上所有排程工作的所有工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-135">This command gets all job triggers of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="b8730-136">此命令會使用 Get-ScheduledJob 來取得本機電腦上的排程工作，並使用管線將它們傳送至 **Get-JobTrigger** ，其會取得每個排程工作的工作觸發程序 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="b8730-136">The command uses the Get-ScheduledJob to get the scheduled jobs on the local computer and pipes them to **Get-JobTrigger** , which gets the job trigger of each scheduled job (if any).</span></span>

<span data-ttu-id="b8730-137">若要將排程工作的名稱加入至工作觸發程式顯示，此命令會使用 Format-Table Cmdlet 的計算屬性功能。</span><span class="sxs-lookup"><span data-stu-id="b8730-137">To add the name of the scheduled job to the job trigger display, the command uses the calculated property feature of the Format-Table cmdlet.</span></span>
<span data-ttu-id="b8730-138">除了預設顯示的工作觸發程式屬性之外，此命令還會建立新的 Register-scheduledjob 屬性，以顯示排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8730-138">In addition to the job trigger properties that are displayed by default, the command creates a new ScheduledJob property that displays the name of the scheduled job.</span></span>

### <span data-ttu-id="b8730-139">範例 6：取得排程工作的工作觸發程序屬性</span><span class="sxs-lookup"><span data-stu-id="b8730-139">Example 6: Get the job trigger property of a scheduled job</span></span>

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

<span data-ttu-id="b8730-140">排程工作的工作觸發程序是儲存在工作的 JobTriggers 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b8730-140">The job triggers of a scheduled job are stored in the JobTriggers property of the job.</span></span>
<span data-ttu-id="b8730-141">此範例顯示使用 **enable-jobtrigger 指令程式** 來取得工作觸發程式的替代方案。</span><span class="sxs-lookup"><span data-stu-id="b8730-141">This example shows alternatives to using the **Get-JobTrigger** cmdlet to get job triggers.</span></span>
<span data-ttu-id="b8730-142">結果類似使用 **Get-JobTrigger** Cmdlet，且技巧可交換使用。</span><span class="sxs-lookup"><span data-stu-id="b8730-142">The results are identical to using the **Get-JobTrigger** cmdlet and the techniques can be used interchangeably.</span></span>

### <span data-ttu-id="b8730-143">範例 7：比較工作觸發程序</span><span class="sxs-lookup"><span data-stu-id="b8730-143">Example 7: Compare job triggers</span></span>

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

<span data-ttu-id="b8730-144">此範例顯示如何比較兩個排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-144">This example shows how to compare the job triggers of two scheduled jobs.</span></span>

## <span data-ttu-id="b8730-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8730-145">PARAMETERS</span></span>

### <span data-ttu-id="b8730-146">-Id</span><span class="sxs-lookup"><span data-stu-id="b8730-146">-Id</span></span>
<span data-ttu-id="b8730-147">指定排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b8730-147">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="b8730-148">**Get-JobTrigger** 會取得指定排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-148">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>

<span data-ttu-id="b8730-149">若要取得本機電腦或遠端電腦上排程工作的識別碼，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8730-149">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8730-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b8730-150">-InputObject</span></span>
<span data-ttu-id="b8730-151">指定排程工作。</span><span class="sxs-lookup"><span data-stu-id="b8730-151">Specifies a scheduled job.</span></span>
<span data-ttu-id="b8730-152">輸入包含 **ScheduledJob** 物件的變數，或輸入可取得 **ScheduledJob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="b8730-152">Enter a variable that contains  **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="b8730-153">您也可以使用管線將 **ScheduledJob** 物件傳送至 **Get-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="b8730-153">You can also pipe **ScheduledJob** objects to **Get-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8730-154">-Name</span><span class="sxs-lookup"><span data-stu-id="b8730-154">-Name</span></span>
<span data-ttu-id="b8730-155">指定排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8730-155">Specifies the name of a scheduled job.</span></span>
<span data-ttu-id="b8730-156">**Get-JobTrigger** 會取得指定排程工作的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-156">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>
<span data-ttu-id="b8730-157">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b8730-157">Wildcards are supported.</span></span>

<span data-ttu-id="b8730-158">若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8730-158">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8730-159">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="b8730-159">-TriggerId</span></span>
<span data-ttu-id="b8730-160">取得指定的工作觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b8730-160">Gets the specified job triggers.</span></span>
<span data-ttu-id="b8730-161">輸入排程工作之一或多個工作觸發程序的觸發程序識別碼。</span><span class="sxs-lookup"><span data-stu-id="b8730-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="b8730-162">當由 *Name* 、 *ID* 或 *InputObject* 參數指定的排程工作有多個工作觸發程序時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="b8730-162">Use this parameter when the scheduled job that is specified by the *Name* , *ID* , or *InputObject* parameters has multiple job triggers.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8730-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8730-163">CommonParameters</span></span>
<span data-ttu-id="b8730-164">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b8730-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8730-165">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b8730-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8730-166">輸入</span><span class="sxs-lookup"><span data-stu-id="b8730-166">INPUTS</span></span>

### <span data-ttu-id="b8730-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="b8730-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="b8730-168">您可以使用管線將排程工作從 Get-ScheduledJob 傳送至 **Get-JobTrigger** 。</span><span class="sxs-lookup"><span data-stu-id="b8730-168">You can pipe a scheduled job from Get-ScheduledJob to **Get-JobTrigger** .</span></span>

## <span data-ttu-id="b8730-169">輸出</span><span class="sxs-lookup"><span data-stu-id="b8730-169">OUTPUTS</span></span>

### <span data-ttu-id="b8730-170">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-170">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="b8730-171">注意</span><span class="sxs-lookup"><span data-stu-id="b8730-171">NOTES</span></span>

## <span data-ttu-id="b8730-172">相關連結</span><span class="sxs-lookup"><span data-stu-id="b8730-172">RELATED LINKS</span></span>

[<span data-ttu-id="b8730-173">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-173">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="b8730-174">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-174">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="b8730-175">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b8730-175">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="b8730-176">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-176">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="b8730-177">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b8730-177">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="b8730-178">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-178">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="b8730-179">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b8730-179">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="b8730-180">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b8730-180">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="b8730-181">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-181">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="b8730-182">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b8730-182">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="b8730-183">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b8730-183">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="b8730-184">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-184">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="b8730-185">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="b8730-185">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="b8730-186">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b8730-186">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="b8730-187">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="b8730-187">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="b8730-188">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="b8730-188">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
