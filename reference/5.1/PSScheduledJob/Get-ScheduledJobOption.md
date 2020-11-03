---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203000"
---
# <span data-ttu-id="6c3c3-103">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6c3c3-103">Get-ScheduledJobOption</span></span>

## <span data-ttu-id="6c3c3-104">概要</span><span class="sxs-lookup"><span data-stu-id="6c3c3-104">SYNOPSIS</span></span>
<span data-ttu-id="6c3c3-105">取得排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-105">Gets the job options of scheduled jobs.</span></span>

## <span data-ttu-id="6c3c3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c3c3-106">SYNTAX</span></span>

### <span data-ttu-id="6c3c3-107">JobDefinition (預設值)</span><span class="sxs-lookup"><span data-stu-id="6c3c3-107">JobDefinition (Default)</span></span>

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="6c3c3-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="6c3c3-108">JobDefinitionId</span></span>

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="6c3c3-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="6c3c3-109">JobDefinitionName</span></span>

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="6c3c3-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c3c3-110">DESCRIPTION</span></span>
<span data-ttu-id="6c3c3-111">**ScheduledJobOption 指令程式** 會取得排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-111">The **Get-ScheduledJobOption** cmdlet gets the job options of scheduled jobs.</span></span>
<span data-ttu-id="6c3c3-112">您可以使用此命令檢查工作選項，或者以管線傳送工作選項至其他 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-112">You can use this command to examine the job options or to pipe the job options to other cmdlets.</span></span>

<span data-ttu-id="6c3c3-113">工作選項不會獨立儲存至磁碟；它們是排程工作的一部分。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-113">Job options are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="6c3c3-114">若要取得排程工作的工作選項，請指定排程工作。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-114">To get the job options of a scheduled job, specify the scheduled job.</span></span>

<span data-ttu-id="6c3c3-115">使用 **Get-ScheduledJobOption** Cmdlet 的參數來識別排程工作。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-115">Use the parameters of the **Get-ScheduledJobOption** cmdlet to identify the scheduled job.</span></span>
<span data-ttu-id="6c3c3-116">您可以依名稱或識別碼來識別排程工作，或是輸入或將 **register-scheduledjob** 物件（例如 Get-ScheduledJob Cmdlet 所傳回的物件）輸入或輸送至 **ScheduledJobOption** 。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-116">You can identify scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-ScheduledJobOption** .</span></span>

<span data-ttu-id="6c3c3-117">**Get-ScheduledJobOption** 為 Windows PowerShell 內含之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-117">**Get-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="6c3c3-118">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="6c3c3-119">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="6c3c3-120">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6c3c3-121">範例</span><span class="sxs-lookup"><span data-stu-id="6c3c3-121">EXAMPLES</span></span>

### <span data-ttu-id="6c3c3-122">範例 1：取得工作選項</span><span class="sxs-lookup"><span data-stu-id="6c3c3-122">Example 1: Get job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : False

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="6c3c3-123">此命令會取得名稱中有備份之排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-123">This command gets the job options of scheduled jobs that have BackUp in their names.</span></span>
<span data-ttu-id="6c3c3-124">結果顯示 **Get-ScheduledJobOption** 傳回的工作選項物件。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-124">The results show the job options object that **Get-ScheduledJobOption** returned.</span></span>

### <span data-ttu-id="6c3c3-125">範例 2：取得所有工作選項</span><span class="sxs-lookup"><span data-stu-id="6c3c3-125">Example 2: Get all job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

<span data-ttu-id="6c3c3-126">此命令會取得本機電腦上所有排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-126">This command gets the job options of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="6c3c3-127">它會使用 Get-ScheduledJob Cmdlet，來取得本機電腦上的排程工作。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-127">It uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="6c3c3-128">管線運算子 (|) 將排程工作傳送至 **ScheduledJobOption 指令程式** ，以取得每個排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-128">A pipeline operator (|) sends the scheduled jobs to the **Get-ScheduledJobOption** cmdlet, which gets the job options of each scheduled job.</span></span>

### <span data-ttu-id="6c3c3-129">範例 3：取得選取的工作選項</span><span class="sxs-lookup"><span data-stu-id="6c3c3-129">Example 3: Get selected job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

<span data-ttu-id="6c3c3-130">此範例顯示如何使用特定值尋找工作選項物件。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-130">This example shows how to find job options object with particular values.</span></span>

<span data-ttu-id="6c3c3-131">第一個命令會取得工作選項，其中 RunElevated 屬性的值為 $True，而 RunWithoutNetwork 屬性的值為 $False。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-131">The first command gets job options in which the RunElevated property has a value of $True and the RunWithoutNetwork property has a value of $False.</span></span>
<span data-ttu-id="6c3c3-132">輸出會顯示已選取的 **JobOptions** 物件。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-132">The output shows the **JobOptions** object that was selected.</span></span>

### <span data-ttu-id="6c3c3-133">範例 4：使用工作選項來建立新工作</span><span class="sxs-lookup"><span data-stu-id="6c3c3-133">Example 4: Use job options to create a new job</span></span>

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

<span data-ttu-id="6c3c3-134">這個範例示範如何使用 Get-ScheduledJobOption 在新的排程工作中取得的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-134">This example shows how to use the job options that Get-ScheduledJobOption gets in a new scheduled job.</span></span>

<span data-ttu-id="6c3c3-135">第一個命令會使用 **ScheduledJobOption** 來取得 BackupTestLogs 排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-135">The first command uses **Get-ScheduledJobOption** to get the jobs options of the BackupTestLogs scheduled job.</span></span>
<span data-ttu-id="6c3c3-136">命令會將選項儲存於 $Opts 變數中。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-136">The command saves the options in the $Opts variable.</span></span>

<span data-ttu-id="6c3c3-137">第二個命令會使用 Register-ScheduledJob Cmdlet 來建立新的排程工作。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-137">The second command uses Register-ScheduledJob cmdlet to create a new scheduled job.</span></span>
<span data-ttu-id="6c3c3-138">*ScheduledJobOption* 參數的值為 $Opts 變數中的選項物件。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-138">The value of the *ScheduledJobOption* parameter is the options object in the $Opts variable.</span></span>

### <span data-ttu-id="6c3c3-139">範例 5：從遠端電腦取得工作選項</span><span class="sxs-lookup"><span data-stu-id="6c3c3-139">Example 5: Get job options from a remote computer</span></span>

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

<span data-ttu-id="6c3c3-140">此命令會使用 Invoke-Command Cmdlet，來取得 Srv01 電腦上 DataDemon 工作的排程工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-140">This command uses the Invoke-Command cmdlet to get the scheduled job options of the DataDemon job on the Srv01 computer.</span></span>
<span data-ttu-id="6c3c3-141">命令會將選項儲存在 $O 變數中。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-141">The command saves the options in the $O variable.</span></span>

## <span data-ttu-id="6c3c3-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c3c3-142">PARAMETERS</span></span>

### <span data-ttu-id="6c3c3-143">-Id</span><span class="sxs-lookup"><span data-stu-id="6c3c3-143">-Id</span></span>
<span data-ttu-id="6c3c3-144">指定排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-144">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="6c3c3-145">**Get-ScheduledJobOption** 會取得指定排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-145">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>

<span data-ttu-id="6c3c3-146">若要取得本機電腦或遠端電腦上排程工作的識別碼，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-146">To get the identification numbers of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="6c3c3-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6c3c3-147">-InputObject</span></span>
<span data-ttu-id="6c3c3-148">指定排程工作。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-148">Specifies a scheduled job.</span></span>
<span data-ttu-id="6c3c3-149">輸入包含 **ScheduledJob** 物件的變數，或輸入可取得 **ScheduledJob** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-149">Enter a variable that contains a **ScheduledJob** object or type a command or expression that gets a **ScheduledJob** object, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="6c3c3-150">您也可以使用管線傳送 **ScheduledJob** 物件至 **Get-ScheduledJobOption** 。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-150">You can also pipe a **ScheduledJob** object to **Get-ScheduledJobOption** .</span></span>

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

### <span data-ttu-id="6c3c3-151">-Name</span><span class="sxs-lookup"><span data-stu-id="6c3c3-151">-Name</span></span>
<span data-ttu-id="6c3c3-152">指定排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-152">Specifies the names of scheduled jobs.</span></span>
<span data-ttu-id="6c3c3-153">**Get-ScheduledJobOption** 會取得指定排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-153">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>
<span data-ttu-id="6c3c3-154">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-154">Wildcards are supported.</span></span>

<span data-ttu-id="6c3c3-155">若要取得本機電腦或遠端電腦上排程工作的名稱，請使用 Get-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-155">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6c3c3-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c3c3-156">CommonParameters</span></span>
<span data-ttu-id="6c3c3-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c3c3-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6c3c3-159">輸入</span><span class="sxs-lookup"><span data-stu-id="6c3c3-159">INPUTS</span></span>

### <span data-ttu-id="6c3c3-160">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="6c3c3-160">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="6c3c3-161">您可以使用管線將排程工作從 Get-ScheduledJob 傳送至 **Get-ScheduledJobOption** 。</span><span class="sxs-lookup"><span data-stu-id="6c3c3-161">You can pipe a scheduled job from Get-ScheduledJob to **Get-ScheduledJobOption** .</span></span>

## <span data-ttu-id="6c3c3-162">輸出</span><span class="sxs-lookup"><span data-stu-id="6c3c3-162">OUTPUTS</span></span>

### <span data-ttu-id="6c3c3-163">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="6c3c3-163">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="6c3c3-164">注意</span><span class="sxs-lookup"><span data-stu-id="6c3c3-164">NOTES</span></span>

## <span data-ttu-id="6c3c3-165">相關連結</span><span class="sxs-lookup"><span data-stu-id="6c3c3-165">RELATED LINKS</span></span>

[<span data-ttu-id="6c3c3-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="6c3c3-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="6c3c3-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6c3c3-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="6c3c3-169">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="6c3c3-170">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6c3c3-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="6c3c3-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="6c3c3-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6c3c3-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="6c3c3-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6c3c3-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="6c3c3-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="6c3c3-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6c3c3-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="6c3c3-176">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6c3c3-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="6c3c3-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="6c3c3-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6c3c3-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="6c3c3-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6c3c3-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="6c3c3-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6c3c3-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="6c3c3-181">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6c3c3-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
