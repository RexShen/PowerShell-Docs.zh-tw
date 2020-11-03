---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202995"
---
# <span data-ttu-id="f2ab8-103">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-103">Register-ScheduledJob</span></span>

## <span data-ttu-id="f2ab8-104">概要</span><span class="sxs-lookup"><span data-stu-id="f2ab8-104">SYNOPSIS</span></span>
<span data-ttu-id="f2ab8-105">建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-105">Creates a scheduled job.</span></span>

## <span data-ttu-id="f2ab8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2ab8-106">SYNTAX</span></span>

### <span data-ttu-id="f2ab8-107">ScriptBlock (預設值)</span><span class="sxs-lookup"><span data-stu-id="f2ab8-107">ScriptBlock (Default)</span></span>

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2ab8-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="f2ab8-108">FilePath</span></span>

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f2ab8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f2ab8-109">DESCRIPTION</span></span>

<span data-ttu-id="f2ab8-110">`Register-ScheduledJob`Cmdlet 會在本機電腦上建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-110">The `Register-ScheduledJob` cmdlet creates scheduled jobs on the local computer.</span></span>

<span data-ttu-id="f2ab8-111">排程工作是一種 Windows PowerShell 背景工作，可以在單次或週期性排程上自動啟動。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-111">A scheduled job is a Windows PowerShell background job that can be started automatically on a one-time or recurring schedule.</span></span> <span data-ttu-id="f2ab8-112">排程的工作會儲存在磁片上，並在工作排程器中註冊。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-112">Scheduled jobs are stored on disk and registered in Task Scheduler.</span></span>
<span data-ttu-id="f2ab8-113">您可以在工作排程器中管理工作，也可以使用 Windows PowerShell 中的排程工作 Cmdlet 來管理作業。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-113">The jobs can be managed in Task Scheduler or by using the Scheduled Job cmdlets in Windows PowerShell.</span></span>

<span data-ttu-id="f2ab8-114">當排程工作啟動時，它會建立排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-114">When a scheduled job starts, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="f2ab8-115">排程工作執行個體類似 Windows PowerShell 背景工作，但排程工作的結果會儲存在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-115">Scheduled job instances are identical to Windows PowerShell background jobs, except that the results are saved on disk.</span></span> <span data-ttu-id="f2ab8-116">使用工作 Cmdlet （例如 `Start-Job` 、和） `Get-Job` `Receive-Job` 來啟動、查看和取得工作實例的結果。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-116">Use the Job cmdlets, such as `Start-Job`, `Get-Job`, and `Receive-Job` to start, view, and get the results of the job instances.</span></span>

<span data-ttu-id="f2ab8-117">用 `Register-ScheduledJob` 來建立新的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-117">Use `Register-ScheduledJob` to create a new scheduled job.</span></span> <span data-ttu-id="f2ab8-118">若要指定排程工作執行的命令，請使用 **ScriptBlock** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-118">To specify the commands that the scheduled job runs, use the **ScriptBlock** parameter.</span></span> <span data-ttu-id="f2ab8-119">若要指定工作執行的腳本，請使用 **FilePath** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-119">To specify a script that the job runs, use the **FilePath** parameter.</span></span>

<span data-ttu-id="f2ab8-120">Windows PowerShell 排程工作會使用工作排程器用於排程工作的相同工作觸發程式和工作選項。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-120">Windows PowerShell-scheduled jobs use the same job triggers and job options that Task Scheduler uses for scheduled tasks.</span></span>

<span data-ttu-id="f2ab8-121">的 **觸發** 程式參數 `Register-ScheduledJob` 會加入一個或多個工作觸發程式，以啟動作業。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-121">The **Trigger** parameter of `Register-ScheduledJob` adds one or more job triggers that start the job.</span></span> <span data-ttu-id="f2ab8-122">**觸發** 程式參數是選擇性的，因此您可以在建立排程工作時新增觸發程式、稍後新增工作觸發程式、新增 **RunNow** 參數以立即啟動工作、使用 `Start-Job` Cmdlet 隨時啟動作業，或將 untriggered 排程工作儲存為其他作業的範本。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-122">The **Trigger** parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the **RunNow** parameter to start the job immediately, use the `Start-Job` cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="f2ab8-123">**Options** 參數可讓您自訂排程工作的選項設定。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-123">The **Options** parameter lets you customize the options settings for the scheduled job.</span></span> <span data-ttu-id="f2ab8-124">**Options** 參數是選擇性的，因此您可以在建立排程工作時設定工作選項，或隨時變更工作選項。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-124">The **Options** parameter is optional, so you can set job options when you create the scheduled job or change them at any time.</span></span> <span data-ttu-id="f2ab8-125">因為工作選項設定可能會使得排程工作無法如預期般執行，因此請務必謹慎檢閱及設定工作選項。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-125">Because job option settings can prevent the scheduled job from running, review the job options and set them carefully.</span></span>

<span data-ttu-id="f2ab8-126">`Register-ScheduledJob` 是 **PSScheduledJob** 模組中包含在 Windows PowerShell 中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-126">`Register-ScheduledJob` is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="f2ab8-127">如需排程工作的詳細資訊，請參閱 **PSScheduledJob** 課程模組中的相關文章。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-127">For more information about Scheduled Jobs, see the About articles in the **PSScheduledJob** module.</span></span>
<span data-ttu-id="f2ab8-128">匯入 **PSScheduledJob** 模組，然後輸入： `Get-Help about_Scheduled*` 或查看 [about_Scheduled_Jobs](./about/about_scheduled_jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-128">Import the **PSScheduledJob** module and then type: `Get-Help about_Scheduled*` or see [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span></span>

<span data-ttu-id="f2ab8-129">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-129">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f2ab8-130">範例</span><span class="sxs-lookup"><span data-stu-id="f2ab8-130">EXAMPLES</span></span>

### <span data-ttu-id="f2ab8-131">範例1：建立排程工作</span><span class="sxs-lookup"><span data-stu-id="f2ab8-131">Example 1: Create a scheduled job</span></span>

<span data-ttu-id="f2ab8-132">此範例會在本機電腦上建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-132">This example creates a scheduled job on the local computer.</span></span>

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

<span data-ttu-id="f2ab8-133">`Register-ScheduledJob` 使用 **Name** 參數來建立封存 **-腳本** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-133">`Register-ScheduledJob` uses the **Name** parameter to create the **Archive-Scripts** scheduled job.</span></span>
<span data-ttu-id="f2ab8-134">**ScriptBlock** 參數會執行 `Get-ChildItem` ，以 `$home` 遞迴方式搜尋目錄中的檔案 `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-134">The **ScriptBlock** parameter runs `Get-ChildItem` that searches the `$home` directory recursively for `.ps1` files.</span></span> <span data-ttu-id="f2ab8-135">`Copy-Item`Cmdlet 會將檔案複製到 **目的地** 參數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-135">The `Copy-Item` cmdlet copies the files to a directory specified by the **Destination** parameter.</span></span>

<span data-ttu-id="f2ab8-136">因為排程工作不包含觸發程式，所以它不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-136">Because the scheduled job doesn't contain a trigger, it's not started automatically.</span></span> <span data-ttu-id="f2ab8-137">您可以使用新增工作觸發 `Add-JobTrigger` 程式、使用指令 `Start-Job` 程式依需求啟動作業，或使用排程工作做為其他排程工作的範本。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-137">You can add job triggers with `Add-JobTrigger`, use the `Start-Job` cmdlet to start the job on demand, or use the scheduled job as a template for other scheduled jobs.</span></span>

### <span data-ttu-id="f2ab8-138">範例2：建立具有觸發程式和自訂選項的排程工作</span><span class="sxs-lookup"><span data-stu-id="f2ab8-138">Example 2: Create a scheduled job with triggers and custom options</span></span>

<span data-ttu-id="f2ab8-139">此範例顯示如何建立具有工作觸發程序與自訂工作選項的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-139">This example shows how to create a scheduled job that has a job trigger and custom job options.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

<span data-ttu-id="f2ab8-140">`$O`變數會儲存 Cmdlet 所建立的工作選項物件 `New-ScheduledJobOption` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-140">The `$O` variable stores the job option object that the `New-ScheduledJobOption` cmdlet created.</span></span> <span data-ttu-id="f2ab8-141">選項會啟動排程工作，即使電腦未閒置，也會喚醒電腦以執行工作（如有必要），並允許工作的多個實例在數列中執行。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-141">The options start the scheduled job even if the computer isn't idle, wakes the computer to run the job, if necessary, and allows multiple instances of the job to run in a series.</span></span>

<span data-ttu-id="f2ab8-142">`$T`變數會儲存 Cmdlet 的結果 `New-JobTrigger` 來建立工作觸發程式，以在下午9:00 點啟動作業。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-142">The `$T` variable stores the result from the `New-JobTrigger` cmdlet to create job trigger that starts a job every other Monday at 9:00 PM.</span></span>

<span data-ttu-id="f2ab8-143">`$path`變數會儲存腳本檔案的路徑 `UpdateVersion.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-143">The `$path` variable stores the path to the `UpdateVersion.ps1` script file.</span></span>

<span data-ttu-id="f2ab8-144">`Register-ScheduledJob` 使用 **Name** 參數來建立 **UpdateVersion** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-144">`Register-ScheduledJob` uses the **Name** paramter to create the **UpdateVersion** scheduled job.</span></span>
<span data-ttu-id="f2ab8-145">**FilePath** 參數會使用 `$path` 來指定工作執行的腳本。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-145">The **FilePath** parameter uses `$path` to specify the script that the job runs.</span></span> <span data-ttu-id="f2ab8-146">**ScheduledJobOption** 參數會使用中儲存的工作選項 `$O` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-146">The **ScheduledJobOption** parameter uses the job options stored in `$O`.</span></span> <span data-ttu-id="f2ab8-147">**觸發** 程式參數會使用儲存在中的工作觸發程式 `$T` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-147">The **Trigger** parameter uses the job triggers stored in `$T`.</span></span>

### <span data-ttu-id="f2ab8-148">範例3：使用雜湊表來指定觸發程式和排程工作選項</span><span class="sxs-lookup"><span data-stu-id="f2ab8-148">Example 3: Use hash tables to specify a trigger and scheduled job options</span></span>

<span data-ttu-id="f2ab8-149">此範例的效果與範例2中的命令相同。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-149">This example has the same effect as the command in Example 2.</span></span> <span data-ttu-id="f2ab8-150">它會使用雜湊表來指定 **觸發** 程式和 **ScheduledJobOption** 參數的值，以建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-150">It creates a scheduled job, using hash tables to specify the values of the **Trigger** and **ScheduledJobOption** parameters.</span></span> <span data-ttu-id="f2ab8-151">`$O` `$T` 範例2中定義的和變數會以雜湊表取代。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-151">The `$O` and `$T`variables defined in Example 2 are replaced with hash tables.</span></span>

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### <span data-ttu-id="f2ab8-152">範例4：在遠端電腦上建立排程工作</span><span class="sxs-lookup"><span data-stu-id="f2ab8-152">Example 4: Create scheduled jobs on remote computers</span></span>

<span data-ttu-id="f2ab8-153">在此範例中，會在多部遠端電腦上建立 **EnergyData** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-153">In this example, the **EnergyData** scheduled job is created on multiple remote computers.</span></span> <span data-ttu-id="f2ab8-154">排程工作會執行腳本來收集原始資料，並將它儲存在遠端電腦上執行中的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-154">The scheduled job runs a script that gathers raw data and saves it in a running log on the remote computer.</span></span>

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

<span data-ttu-id="f2ab8-155">此 `$Cred` 變數會在具有建立排程工作之許可權的使用者的 **PSCredential** 物件中儲存認證。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-155">The `$Cred` variable stores credentials in a **PSCredential** object for a user with permissions to create scheduled jobs.</span></span> <span data-ttu-id="f2ab8-156">`$O`變數會儲存以建立的工作選項 `New-ScheduledJobOption` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-156">The `$O` variable stores the job options created with `New-ScheduledJobOption`.</span></span> <span data-ttu-id="f2ab8-157">`$T`變數會儲存以建立的工作觸發程式 `New-JobTrigger` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-157">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="f2ab8-158">此 `Invoke-Command` Cmdlet 會使用 **ComputerName** 參數來取得檔案中的伺服器名稱清單 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-158">The `Invoke-Command` cmdlet uses the **ComputerName** parameter to get a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="f2ab8-159">**Credential** 參數會取得儲存在中的認證物件 `$Cred` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-159">The **Credential** parameter gets the credential object stored in `$Cred`.</span></span>
<span data-ttu-id="f2ab8-160">**ScriptBlock** 參數會在檔案 `Register-ScheduledJob` 中的電腦上執行命令 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-160">The **ScriptBlock** parameter runs a `Register-ScheduledJob` command on the computers in the `Servers.txt` file.</span></span>

<span data-ttu-id="f2ab8-161">的參數 `Register-ScheduledJob` 是由定義 `$params` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-161">The parameters for `Register-ScheduledJob` are defined by `$params`.</span></span> <span data-ttu-id="f2ab8-162">**Name** 參數會指定在每部遠端電腦上將作業命名為 **EnergyData** 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-162">The **Name** parameters specifies the job is named **Get-EnergyData** on each remote computer.</span></span> <span data-ttu-id="f2ab8-163">**FilePath** 提供腳本的位置 `EnergyData.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-163">**FilePath** provides the location of the `EnergyData.ps1` script.</span></span> <span data-ttu-id="f2ab8-164">腳本位於可供所有參與電腦使用的檔案伺服器上。作業會依照中的工作觸發程式所指定的排程執行 `$T` ，以及中的工作選項 `$O` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-164">The script is located on a file server that is available to all participating computers.The job runs on the schedule specified by the job triggers in `$T` and the job options in `$O`.</span></span>

<span data-ttu-id="f2ab8-165">此 `Register-ScheduledJob @params` 命令會使用腳本區塊中的參數建立排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-165">The `Register-ScheduledJob @params` command creates the scheduled job with the parameters from the script block.</span></span>

### <span data-ttu-id="f2ab8-166">範例5：建立在遠端電腦上執行腳本的排程工作</span><span class="sxs-lookup"><span data-stu-id="f2ab8-166">Example 5: Create a scheduled job that runs a script on remote computers</span></span>

<span data-ttu-id="f2ab8-167">此範例會在本機電腦上建立 **CollectEnergyData** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-167">This example creates the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="f2ab8-168">作業會在多部遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-168">The job runs on multiple remote computers.</span></span>

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

<span data-ttu-id="f2ab8-169">`$Admin`變數會儲存具有在 **PSCredential** 物件中執行命令之許可權的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-169">The `$Admin` variable stores credentials for a user with permissions to run the commands in a **PSCredential** object.</span></span> <span data-ttu-id="f2ab8-170">`$T`變數會儲存以建立的工作觸發程式 `New-JobTrigger` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-170">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="f2ab8-171">此 `Register-ScheduledJob` Cmdlet 會使用 **Name** 參數在本機電腦上建立 **CollectEnergyData** 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-171">The `Register-ScheduledJob` cmdlet uses the **Name** parameter to create the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="f2ab8-172">**Trigger** 參數會指定中的工作觸發程式 `$T` ，而 **MaxResultCount** 參數會將儲存的結果數目增加到99。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-172">The **Trigger** parameter specifies the job triggers in `$T` and the **MaxResultCount** parameter increases the number of saved results to 99.</span></span>

<span data-ttu-id="f2ab8-173">**ScriptBlock** 參數會定義的 `Invoke-Command` 參數 `$params` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-173">The **ScriptBlock** parameter defines the `Invoke-Command` parameters with `$params`.</span></span> <span data-ttu-id="f2ab8-174">**AsJob** 參數會在本機電腦上建立背景工作物件，即使腳本是在 `Energydata.ps1` 遠端電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-174">The **AsJob** parameter creates the background job object on the local computer, even though the `Energydata.ps1` script runs on the remote computers.</span></span> <span data-ttu-id="f2ab8-175">**ComputerName** 參數會從檔案取得伺服器名稱的清單 `Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-175">The **ComputerName** parameter gets a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="f2ab8-176">**Credential** 參數指定有權在遠端電腦上執行腳本的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-176">The **Credential** parameter specifies a user account that has permission to run scripts on the remote computers.</span></span> <span data-ttu-id="f2ab8-177">而且， **驗證** 參數會指定 **CredSSP** 的值來允許委派的認證。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-177">And, the **Authentication** parameter specifies a value of **CredSSP** to allow delegated credentials.</span></span>

<span data-ttu-id="f2ab8-178">會 `Invoke-Command @params` 以腳本區塊中的參數執行命令。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-178">The `Invoke-Command @params` runs the command with the parameters from the script block.</span></span>

## <span data-ttu-id="f2ab8-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2ab8-179">PARAMETERS</span></span>

### <span data-ttu-id="f2ab8-180">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="f2ab8-180">-ArgumentList</span></span>

<span data-ttu-id="f2ab8-181">指定由 **FilePath** 參數所指定之指令碼的參數值，或指定由 **ScriptBlock** 參數所指定之命令的參數值。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-181">Specifies values for the parameters of the script that is specified by the **FilePath** parameter or for the command that is specified by the **ScriptBlock** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-182">-Authentication</span><span class="sxs-lookup"><span data-stu-id="f2ab8-182">-Authentication</span></span>

<span data-ttu-id="f2ab8-183">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-183">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="f2ab8-184">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-184">The default value is Default.</span></span>

<span data-ttu-id="f2ab8-185">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f2ab8-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f2ab8-186">預設</span><span class="sxs-lookup"><span data-stu-id="f2ab8-186">Default</span></span>
- <span data-ttu-id="f2ab8-187">基本</span><span class="sxs-lookup"><span data-stu-id="f2ab8-187">Basic</span></span>
- <span data-ttu-id="f2ab8-188">Credssp</span><span class="sxs-lookup"><span data-stu-id="f2ab8-188">Credssp</span></span>
- <span data-ttu-id="f2ab8-189">Digest</span><span class="sxs-lookup"><span data-stu-id="f2ab8-189">Digest</span></span>
- <span data-ttu-id="f2ab8-190">Kerberos</span><span class="sxs-lookup"><span data-stu-id="f2ab8-190">Kerberos</span></span>
- <span data-ttu-id="f2ab8-191">交涉</span><span class="sxs-lookup"><span data-stu-id="f2ab8-191">Negotiate</span></span>
- <span data-ttu-id="f2ab8-192">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="f2ab8-192">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="f2ab8-193">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-193">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="f2ab8-194">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性服務提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-194">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="f2ab8-195">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="f2ab8-196">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f2ab8-197">-Confirm</span></span>

<span data-ttu-id="f2ab8-198">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-198">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f2ab8-199">-Credential</span><span class="sxs-lookup"><span data-stu-id="f2ab8-199">-Credential</span></span>

<span data-ttu-id="f2ab8-200">指定具有執行排程工作之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-200">Specifies a user account that has permission to run the scheduled job.</span></span> <span data-ttu-id="f2ab8-201">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-201">The default is the current user.</span></span>

<span data-ttu-id="f2ab8-202">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 中的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-202">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f2ab8-203">如果您只輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-203">If you enter only a user name, you're prompted for a password.</span></span>

<span data-ttu-id="f2ab8-204">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-204">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f2ab8-205">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-205">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-206">-FilePath</span><span class="sxs-lookup"><span data-stu-id="f2ab8-206">-FilePath</span></span>

<span data-ttu-id="f2ab8-207">指定排程工作所執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-207">Specifies a script that the scheduled job runs.</span></span> <span data-ttu-id="f2ab8-208">輸入 `.ps1` 本機電腦上的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-208">Enter the path to a `.ps1` file on the local computer.</span></span> <span data-ttu-id="f2ab8-209">若要指定指令碼參數的預設值，請使用 **ArgumentList** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-209">To specify default values for the script parameters, use the **ArgumentList** parameter.</span></span>
<span data-ttu-id="f2ab8-210">每個 `Register-ScheduledJob` 命令都必須使用 **ScriptBlock** 或 **FilePath** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-210">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-211">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="f2ab8-211">-InitializationScript</span></span>

<span data-ttu-id="f2ab8-212">指定 () 之 Windows PowerShell 腳本的完整路徑 `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-212">Specifies the fully qualified path to a Windows PowerShell script (`.ps1`).</span></span> <span data-ttu-id="f2ab8-213">初始化指令碼會在執行 **ScriptBlock** 參數所指定的命令或 **FilePath** 參數所指定的指令碼之前，在針對背景工作所建立的工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-213">The initialization script runs in the session that is created for the background job before the commands that are specified by the **ScriptBlock** parameter or the script that is specified by the **FilePath** parameter.</span></span> <span data-ttu-id="f2ab8-214">您可以使用初始化指令碼來設定工作階段，例如新增檔案/函式/別名、建立目錄，或檢查先決條件。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-214">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="f2ab8-215">若要指定會執行主要工作命令的指令碼，請使用 **FilePath** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-215">To specify a script that runs the primary job commands, use the **FilePath** parameter.</span></span>

<span data-ttu-id="f2ab8-216">如果初始化腳本產生錯誤（即使是非終止錯誤），則排程工作的目前實例不會執行，且其狀態會是 [ **失敗** ]。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-216">If the initialization script generates an error, even a non-terminating error, the current instance of the scheduled job doesn't run and its status is **Failed** .</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-217">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="f2ab8-217">-MaxResultCount</span></span>

<span data-ttu-id="f2ab8-218">指定要為排程工作保留幾個工作結果項目。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-218">Specifies how many job result entries are maintained for the scheduled job.</span></span> <span data-ttu-id="f2ab8-219">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-219">The default value is 32.</span></span>

<span data-ttu-id="f2ab8-220">Windows PowerShell 會將每個觸發之排程工作執行個體的執行記錄與結果儲存在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-220">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span> <span data-ttu-id="f2ab8-221">此參數的值決定針對此排程工作儲存的工作執行個體結果數目。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-221">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span> <span data-ttu-id="f2ab8-222">當工作執行個體數目超過此值時，Windows PowerShell 會刪除最舊的工作執行個體結果，以便挪出空間儲存最新工作執行個體結果。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-222">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="f2ab8-223">作業執行歷程記錄和工作結果會儲存在 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span><span class="sxs-lookup"><span data-stu-id="f2ab8-223">The job execution history and job results are saved in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span></span>
<span data-ttu-id="f2ab8-224">在其上建立作業的電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-224">directories on the computer on which the job is created.</span></span> <span data-ttu-id="f2ab8-225">若要查看執行歷程記錄，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-225">To see the execution history, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="f2ab8-226">若要取得工作結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-226">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="f2ab8-227">**MaxResultCount** 參數會設定排程工作之 ExecutionHistoryLength 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-227">The **MaxResultCount** parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="f2ab8-228">若要刪除目前的執行歷程記錄和工作結果，請使用 Cmdlet 的 **ClearExecutionHistory** 參數 `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-228">To delete the current execution history and job results, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-229">-Name</span><span class="sxs-lookup"><span data-stu-id="f2ab8-229">-Name</span></span>

<span data-ttu-id="f2ab8-230">指定排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-230">Specifies a name for the scheduled job.</span></span> <span data-ttu-id="f2ab8-231">此名稱也會用於所有已啟動的排程工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-231">The name is also used for all started instances of the scheduled job.</span></span> <span data-ttu-id="f2ab8-232">此名稱在電腦上必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-232">The name must be unique on the computer.</span></span> <span data-ttu-id="f2ab8-233">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-233">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-234">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="f2ab8-234">-RunAs32</span></span>

<span data-ttu-id="f2ab8-235">在 32 位元處理程序中執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-235">Runs the scheduled job in a 32-bit process.</span></span>

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

### <span data-ttu-id="f2ab8-236">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="f2ab8-236">-RunEvery</span></span>

<span data-ttu-id="f2ab8-237">用來指定執行作業的頻率。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-237">Used to specify how often to run the job.</span></span> <span data-ttu-id="f2ab8-238">例如，使用此選項可每隔15分鐘執行一次作業。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-238">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-239">-RunNow</span><span class="sxs-lookup"><span data-stu-id="f2ab8-239">-RunNow</span></span>

<span data-ttu-id="f2ab8-240">在執行 Cmdlet 之後立即啟動作業 `Register-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-240">Starts a job immediately, as soon as the `Register-ScheduledJob` cmdlet is run.</span></span> <span data-ttu-id="f2ab8-241">此參數可讓您不需要觸發工作排程器在註冊後立即執行 Windows PowerShell 腳本，也不需要使用者建立指定開始日期和時間的觸發程式。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-241">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and doesn't require users to create a trigger that specifies a starting date and time.</span></span>

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

### <span data-ttu-id="f2ab8-242">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f2ab8-242">-ScheduledJobOption</span></span>

<span data-ttu-id="f2ab8-243">設定排程工作的選項。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-243">Sets options for the scheduled job.</span></span> <span data-ttu-id="f2ab8-244">輸入 **ScheduledJobOptions** 物件，例如使用 Cmdlet 建立的物件 `New-ScheduledJobOption` ，或雜湊表值。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-244">Enter a **ScheduledJobOptions** object, such as one that you create by using the `New-ScheduledJobOption` cmdlet, or a hash table value.</span></span>

<span data-ttu-id="f2ab8-245">您可以在註冊排程工作時設定排程工作的選項，或使用 `Set-ScheduledJobOption` 或 `Set-ScheduledJob` Cmdlet 來變更選項。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-245">You can set options for a scheduled job when you register the schedule job or use the `Set-ScheduledJobOption` or `Set-ScheduledJob` cmdlets to change the options.</span></span>

<span data-ttu-id="f2ab8-246">許多選項與其預設值會決定排程工作是否會執行以及執行時間。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-246">Many of the options and their default values determine whether and when a scheduled job runs.</span></span> <span data-ttu-id="f2ab8-247">排定工作之前，請務必檢閱這些選項。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-247">Be sure to review these options before scheduling a job.</span></span> <span data-ttu-id="f2ab8-248">如需排程工作選項的描述（包括預設值），請參閱 `New-ScheduledJobOption` 。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-248">For a description of the scheduled job options, including the default values, see `New-ScheduledJobOption`.</span></span>

<span data-ttu-id="f2ab8-249">若要提交雜湊表，請使用下列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-249">To submit a hash table, use the following keys.</span></span> <span data-ttu-id="f2ab8-250">在下列雜湊表中，索引鍵隨著其預設值顯示。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-250">In the following hash table, the keys are shown with their default values.</span></span>

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-251">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="f2ab8-251">-ScriptBlock</span></span>

<span data-ttu-id="f2ab8-252">指定排程工作執行的命令。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-252">Specifies the commands that the scheduled job runs.</span></span> <span data-ttu-id="f2ab8-253">以大括弧括住命令 (`{}`) 來建立腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-253">Enclose the commands in curly braces (`{}`) to create a script block.</span></span> <span data-ttu-id="f2ab8-254">若要指定命令參數的預設值，請使用 **ArgumentList** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-254">To specify default values for command parameters, use the **ArgumentList** parameter.</span></span>

<span data-ttu-id="f2ab8-255">每個 `Register-ScheduledJob` 命令都必須使用 **ScriptBlock** 或 **FilePath** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-255">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-256">-Trigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-256">-Trigger</span></span>

<span data-ttu-id="f2ab8-257">指定排程工作的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-257">Specifies the triggers for the scheduled job.</span></span> <span data-ttu-id="f2ab8-258">輸入一或多個 **>scheduledjobtrigger** 物件，例如 Cmdlet 傳回的物件 `New-JobTrigger` ，或工作觸發程式索引鍵和值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-258">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the `New-JobTrigger` cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="f2ab8-259">工作觸發程式會啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-259">A job trigger starts the schedule job.</span></span> <span data-ttu-id="f2ab8-260">觸發程序可以指定一次性或週期性排程工作或事件 (例如當使用者登入時或 Windows 啟動時)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-260">The trigger can specify a one-time or recurring scheduled or an event, such as when a user logs on or Windows starts.</span></span>

<span data-ttu-id="f2ab8-261">**Trigger** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-261">The **Trigger** parameter is optional.</span></span> <span data-ttu-id="f2ab8-262">您可以在建立排程工作時新增觸發程式、使用 `Add-JobTrigger` 、 `Set-JobTrigger` 或 `Set-ScheduledJob` Cmdlet 稍後新增或變更工作觸發程式，或使用 `Start-Job` Cmdlet 來立即啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-262">You can add a trigger when you create the scheduled job, use the `Add-JobTrigger`, `Set-JobTrigger`, or `Set-ScheduledJob` cmdlets to add or change job triggers later, or use the `Start-Job` cmdlet to start the scheduled job immediately.</span></span> <span data-ttu-id="f2ab8-263">您也可以建立及維護沒有觸發程序且做為範本的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-263">You can also create and maintain a scheduled job without a trigger that is used as a template.</span></span>

<span data-ttu-id="f2ab8-264">若要提交雜湊表，請使用下列索引鍵：</span><span class="sxs-lookup"><span data-stu-id="f2ab8-264">To submit a hash table, use the following keys:</span></span>

- <span data-ttu-id="f2ab8-265">**頻率** ：每日、每週、AtStartup、AtLogon</span><span class="sxs-lookup"><span data-stu-id="f2ab8-265">**Frequency** : Daily, Weekly, AtStartup, AtLogon</span></span>
- <span data-ttu-id="f2ab8-266">**At** ：任何有效的時間字串</span><span class="sxs-lookup"><span data-stu-id="f2ab8-266">**At** : Any valid time string</span></span>
- <span data-ttu-id="f2ab8-267">**DaysOfWeek** -日期名稱的任何組合</span><span class="sxs-lookup"><span data-stu-id="f2ab8-267">**DaysOfWeek** - Any combination of day names</span></span>
- <span data-ttu-id="f2ab8-268">**間隔** -任何有效的頻率間隔</span><span class="sxs-lookup"><span data-stu-id="f2ab8-268">**Interval** - Any valid frequency interval</span></span>
- <span data-ttu-id="f2ab8-269">**RandomDelay** ：任何有效的 timespan 字串</span><span class="sxs-lookup"><span data-stu-id="f2ab8-269">**RandomDelay** : Any valid timespan string</span></span>
- <span data-ttu-id="f2ab8-270">**使用者** ：任何有效的使用者。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-270">**User** : Any valid user.</span></span> <span data-ttu-id="f2ab8-271">只能搭配 AtLogon 頻率值使用</span><span class="sxs-lookup"><span data-stu-id="f2ab8-271">Used only with the AtLogon frequency value</span></span>

<span data-ttu-id="f2ab8-272">例如：</span><span class="sxs-lookup"><span data-stu-id="f2ab8-272">For example:</span></span>

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2ab8-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f2ab8-273">-WhatIf</span></span>

<span data-ttu-id="f2ab8-274">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-274">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f2ab8-275">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-275">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="f2ab8-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2ab8-276">CommonParameters</span></span>

<span data-ttu-id="f2ab8-277">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2ab8-278">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2ab8-279">輸入</span><span class="sxs-lookup"><span data-stu-id="f2ab8-279">INPUTS</span></span>

### <span data-ttu-id="f2ab8-280">無</span><span class="sxs-lookup"><span data-stu-id="f2ab8-280">None</span></span>

<span data-ttu-id="f2ab8-281">您無法將輸入向下傳送到此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-281">You can't send input down the pipeline to this cmdlet.</span></span>

## <span data-ttu-id="f2ab8-282">輸出</span><span class="sxs-lookup"><span data-stu-id="f2ab8-282">OUTPUTS</span></span>

### <span data-ttu-id="f2ab8-283">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="f2ab8-283">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="f2ab8-284">注意</span><span class="sxs-lookup"><span data-stu-id="f2ab8-284">NOTES</span></span>

<span data-ttu-id="f2ab8-285">每個排程工作都是儲存在 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` 本機電腦上目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-285">Each scheduled job is saved in a subdirectory of the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span>
<span data-ttu-id="f2ab8-286">子目錄是針對排程工作命名，而且包含排程工作的 XML 檔案，以及其執行歷程記錄的記錄。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-286">The subdirectory is named for the scheduled job and contains an XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="f2ab8-287">如需有關磁片上之排程工作的詳細資訊，請參閱 [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-287">For more information about scheduled jobs on disk, see [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span></span>

<span data-ttu-id="f2ab8-288">您在 Windows PowerShell 中建立的排程工作會顯示在工作排程器的工作排程器 `Library\Microsoft\Windows\PowerShell\ScheduledJobs` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-288">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler `Library\Microsoft\Windows\PowerShell\ScheduledJobs` folder.</span></span> <span data-ttu-id="f2ab8-289">您可以使用 [工作排程器] 來檢視及編輯排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-289">You can use Task Scheduler to view and edit the scheduled job.</span></span>

<span data-ttu-id="f2ab8-290">您可以使用工作排程器、 **schtasks.exe** 命令列工具和工作排程器 Cmdlet 來管理您使用排程工作 Cmdlet 建立的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-290">You can use Task Scheduler, the **schtasks.exe** command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="f2ab8-291">不過，您無法使用「排程工作」 Cmdlet 來管理您在工作排程器中建立的工作。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-291">However, you can't use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

<span data-ttu-id="f2ab8-292">若排程工作命令失敗，Windows PowerShell 會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-292">If a scheduled job command fails, Windows PowerShell returns an error message.</span></span> <span data-ttu-id="f2ab8-293">但是，如果工作排程器嘗試執行作業失敗，則無法 Windows PowerShell 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-293">However, if the job fails when Task Scheduler tries to run it, the error isn't available to Windows PowerShell.</span></span>

<span data-ttu-id="f2ab8-294">如果排程工作未執行，請使用下列方法找出原因：</span><span class="sxs-lookup"><span data-stu-id="f2ab8-294">If a scheduled job doesn't run, use the following methods to find the reason:</span></span>

- <span data-ttu-id="f2ab8-295">確認工作觸發程式已正確設定。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-295">Verify that the job trigger is set properly.</span></span>
  - <span data-ttu-id="f2ab8-296">確認已滿足工作選項中設定的條件。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-296">Verify that the conditions set in the job options are satisfied.</span></span>
- <span data-ttu-id="f2ab8-297">確認執行作業的使用者帳戶具有執行作業中命令或腳本的許可權。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-297">Verify that the user account under which the job runs has permission to run the commands or scripts in the job.</span></span>
- <span data-ttu-id="f2ab8-298">檢查工作排程器歷程記錄是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-298">Check the Task Scheduler history for errors.</span></span>
- <span data-ttu-id="f2ab8-299">檢查工作排程器事件記錄檔中是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-299">Check the Task Scheduler event log for errors.</span></span>

<span data-ttu-id="f2ab8-300">如需詳細資訊，請參閱 [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="f2ab8-300">For more information, see [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span></span>

## <span data-ttu-id="f2ab8-301">相關連結</span><span class="sxs-lookup"><span data-stu-id="f2ab8-301">RELATED LINKS</span></span>

[<span data-ttu-id="f2ab8-302">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-302">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="f2ab8-303">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-303">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="f2ab8-304">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-304">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="f2ab8-305">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-305">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="f2ab8-306">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-306">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="f2ab8-307">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-307">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="f2ab8-308">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-308">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="f2ab8-309">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f2ab8-309">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="f2ab8-310">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-310">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="f2ab8-311">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f2ab8-311">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="f2ab8-312">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-312">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="f2ab8-313">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-313">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="f2ab8-314">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f2ab8-314">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="f2ab8-315">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-315">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="f2ab8-316">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f2ab8-316">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="f2ab8-317">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f2ab8-317">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
