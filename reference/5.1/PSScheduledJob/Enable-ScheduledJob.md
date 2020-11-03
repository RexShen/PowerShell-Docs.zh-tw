---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203011"
---
# <span data-ttu-id="f0858-103">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-103">Enable-ScheduledJob</span></span>

## <span data-ttu-id="f0858-104">概要</span><span class="sxs-lookup"><span data-stu-id="f0858-104">SYNOPSIS</span></span>
<span data-ttu-id="f0858-105">啟用排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-105">Enables a scheduled job.</span></span>

## <span data-ttu-id="f0858-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0858-106">SYNTAX</span></span>

### <span data-ttu-id="f0858-107">Definition (預設值)</span><span class="sxs-lookup"><span data-stu-id="f0858-107">Definition (Default)</span></span>

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f0858-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="f0858-108">DefinitionId</span></span>

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0858-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="f0858-109">DefinitionName</span></span>

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f0858-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f0858-110">DESCRIPTION</span></span>
<span data-ttu-id="f0858-111">**Enable-ScheduledJob** Cmdlet 會重新啟用已停用的排程工作 (例如使 用Disable-ScheduledJob Cmdlet 停用的排程工作)。</span><span class="sxs-lookup"><span data-stu-id="f0858-111">The **Enable-ScheduledJob** cmdlet re-enables scheduled jobs that are disabled, such as those that are disabled by using the Disable-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="f0858-112">已啟用的工作會在被觸發時自動執行。</span><span class="sxs-lookup"><span data-stu-id="f0858-112">Enabled jobs run automatically when triggered.</span></span>

<span data-ttu-id="f0858-113">若要啟用排程工作， **register-scheduledjob 指令程式** 會將排程工作的 Enabled 屬性設定為 $True。</span><span class="sxs-lookup"><span data-stu-id="f0858-113">To enable a scheduled job, the **Enable-ScheduledJob** cmdlet sets the Enabled property of the scheduled job to $True.</span></span>

<span data-ttu-id="f0858-114">**Enabled-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中其中一個工作排程 Cmdlet 的集合。</span><span class="sxs-lookup"><span data-stu-id="f0858-114">**Enabled-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="f0858-115">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="f0858-115">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="f0858-116">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="f0858-116">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="f0858-117">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f0858-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f0858-118">範例</span><span class="sxs-lookup"><span data-stu-id="f0858-118">EXAMPLES</span></span>

### <span data-ttu-id="f0858-119">範例 1：啟用排程工作</span><span class="sxs-lookup"><span data-stu-id="f0858-119">Example 1: Enable a scheduled job</span></span>

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

<span data-ttu-id="f0858-120">此命令會啟用本機電腦上識別碼為 2 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-120">This command enables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="f0858-121">輸出會顯示命令的效果。</span><span class="sxs-lookup"><span data-stu-id="f0858-121">The output shows the effect of the command.</span></span>

### <span data-ttu-id="f0858-122">範例2：啟用所有排程工作</span><span class="sxs-lookup"><span data-stu-id="f0858-122">Example 2: Enable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

<span data-ttu-id="f0858-123">此命令會啟用本機電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-123">This command enables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="f0858-124">它會使用 Get-ScheduledJob Cmdlet 來取得所有排程工作，並使用 **Enable-ScheduledJob** Cmdlet 來將它們啟用。</span><span class="sxs-lookup"><span data-stu-id="f0858-124">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Enable-ScheduledJob** cmdlet to enable them.</span></span>

<span data-ttu-id="f0858-125">**Enable-ScheduledJob** 不會產生警告或錯誤 (若您啟用已啟用的排程工作)，因此您可以在不指定任何條件的情況下啟用所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-125">**Enable-ScheduledJob** does not generate warnings or errors if you enable a scheduled job that is already enabled, so you can enable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="f0858-126">範例 3：啟用選取的排程工作</span><span class="sxs-lookup"><span data-stu-id="f0858-126">Example 3: Enable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

<span data-ttu-id="f0858-127">此命令會啟用不需要網路連線的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-127">This command enables scheduled jobs that do not require a network connection.</span></span>

<span data-ttu-id="f0858-128">命令會使用 Get-ScheduledJob Cmdlet，來取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-128">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="f0858-129">管線運算子會傳送排程工作至 Get-ScheduledJobOption Cmdlet，此 Cmdlet 會取得每個排程工作的工作選項。</span><span class="sxs-lookup"><span data-stu-id="f0858-129">A pipeline operator sends the scheduled jobs to the Get-ScheduledJobOption cmdlet, which gets the job options of each scheduled job.</span></span>
<span data-ttu-id="f0858-130">每個工作選項物件都具有 JobDefinition 屬性，該屬性包含關聯的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-130">Each job options object has a JobDefinition property that contains the associated scheduled job.</span></span>
<span data-ttu-id="f0858-131">JobDefinition 屬性會被用來完成命令。</span><span class="sxs-lookup"><span data-stu-id="f0858-131">The JobDefinition property is used to complete the command.</span></span>

<span data-ttu-id="f0858-132">命令使用管線運算子 (|) 將工作選項傳送至 Where-Object Cmdlet，它會選取排程工作選項物件，其中 **RunWithoutNetwork** 屬性的值為 True ($true) 。</span><span class="sxs-lookup"><span data-stu-id="f0858-132">The command uses a pipeline operator (|) to send the job options to the Where-Object cmdlet, which selects scheduled job option objects in which the **RunWithoutNetwork** property has a value of True ($true).</span></span>
<span data-ttu-id="f0858-133">另一個管線運算子會將選取的排程工作選項物件傳送至 ForEach-Object Cmdlet，它會使用每個工作選項物件的 JobDefinition 屬性值，在排程工作上執行 **Enable-ScheduledJob** 命令。</span><span class="sxs-lookup"><span data-stu-id="f0858-133">Another pipeline operator sends the selected scheduled job options objects to the ForEach-Object cmdlet which runs an **Enable-ScheduledJob** command on the scheduled job in the value of the JobDefinition property of each job options object.</span></span>

### <span data-ttu-id="f0858-134">範例 4：啟用遠端電腦上的排程工作</span><span class="sxs-lookup"><span data-stu-id="f0858-134">Example 4: Enable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

<span data-ttu-id="f0858-135">此命令會啟用兩部遠端電腦 (Srv01 與 Srv10) 上名稱中包含 "test" 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-135">This command enables scheduled jobs that have "test" in their names on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="f0858-136">此命令會使用 Invoke-Command Cmdlet 在 Srv01 與 Srv10 電腦上執行 **Enable-ScheduledJob** 命令。</span><span class="sxs-lookup"><span data-stu-id="f0858-136">The command uses the Invoke-Command cmdlet to run an **Enable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="f0858-137">此命令使用 *Enable-ScheduledJob* 的 **Name** 參數來啟用每部電腦上的 Inventory 排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-137">The command uses the *Name* parameter of **Enable-ScheduledJob** to enable the Inventory scheduled job on each computer.</span></span>

## <span data-ttu-id="f0858-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0858-138">PARAMETERS</span></span>

### <span data-ttu-id="f0858-139">-Id</span><span class="sxs-lookup"><span data-stu-id="f0858-139">-Id</span></span>
<span data-ttu-id="f0858-140">啟用具有所指定識別碼 (ID) 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-140">Enables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="f0858-141">輸入排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0858-141">Enter the ID of a scheduled job.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0858-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f0858-142">-InputObject</span></span>
<span data-ttu-id="f0858-143">指定要啟用的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-143">Specifies the scheduled job to enable.</span></span>
<span data-ttu-id="f0858-144">輸入包含 **>scheduledjobdefinition** 物件的變數，或輸入可取得 **>scheduledjobdefinition** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="f0858-144">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="f0858-145">您也可以使用管線將 **ScheduledJobDefinition** 物件傳送至 **Enable-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="f0858-145">You can also pipe a **ScheduledJobDefinition** object to **Enable-ScheduledJob** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f0858-146">-Name</span><span class="sxs-lookup"><span data-stu-id="f0858-146">-Name</span></span>
<span data-ttu-id="f0858-147">啟用具有所指定名稱的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-147">Enables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="f0858-148">輸入排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="f0858-148">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="f0858-149">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f0858-149">Wildcards are supported.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0858-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f0858-150">-PassThru</span></span>
<span data-ttu-id="f0858-151">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="f0858-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="f0858-152">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f0858-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f0858-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f0858-153">-Confirm</span></span>
<span data-ttu-id="f0858-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f0858-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f0858-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f0858-155">-WhatIf</span></span>
<span data-ttu-id="f0858-156">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f0858-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f0858-157">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f0858-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f0858-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0858-158">CommonParameters</span></span>
<span data-ttu-id="f0858-159">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f0858-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0858-160">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f0858-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0858-161">輸入</span><span class="sxs-lookup"><span data-stu-id="f0858-161">INPUTS</span></span>

### <span data-ttu-id="f0858-162">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="f0858-162">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="f0858-163">您可以使用管線將排程工作傳送到 **Enable-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="f0858-163">You can pipe a scheduled job to **Enable-ScheduledJob** .</span></span>

## <span data-ttu-id="f0858-164">輸出</span><span class="sxs-lookup"><span data-stu-id="f0858-164">OUTPUTS</span></span>

### <span data-ttu-id="f0858-165">無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="f0858-165">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="f0858-166">若使用 **Passthru** 參數， **Enable-ScheduledJob** 會傳回已啟用的排程工作。</span><span class="sxs-lookup"><span data-stu-id="f0858-166">If you use the **Passthru** parameter, **Enable-ScheduledJob** returns the scheduled job that was enabled.</span></span>
<span data-ttu-id="f0858-167">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f0858-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f0858-168">注意</span><span class="sxs-lookup"><span data-stu-id="f0858-168">NOTES</span></span>

* <span data-ttu-id="f0858-169">**Enable-ScheduledJob** 不會產生警告或錯誤 (若使用它來啟用已啟用的排程工作)。</span><span class="sxs-lookup"><span data-stu-id="f0858-169">**Enable-ScheduledJob** does not generate warnings or errors if you use it to enable a scheduled job that is already enabled.</span></span>

## <span data-ttu-id="f0858-170">相關連結</span><span class="sxs-lookup"><span data-stu-id="f0858-170">RELATED LINKS</span></span>

[<span data-ttu-id="f0858-171">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-171">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="f0858-172">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-172">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="f0858-173">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-173">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="f0858-174">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-174">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="f0858-175">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-175">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="f0858-176">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-176">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="f0858-177">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-177">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="f0858-178">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f0858-178">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="f0858-179">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-179">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="f0858-180">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f0858-180">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="f0858-181">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-181">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="f0858-182">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-182">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="f0858-183">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="f0858-183">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="f0858-184">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-184">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="f0858-185">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="f0858-185">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="f0858-186">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="f0858-186">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
