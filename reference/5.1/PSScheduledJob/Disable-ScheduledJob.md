---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203024"
---
# <span data-ttu-id="36dc6-103">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-103">Disable-ScheduledJob</span></span>

## <span data-ttu-id="36dc6-104">概要</span><span class="sxs-lookup"><span data-stu-id="36dc6-104">SYNOPSIS</span></span>
<span data-ttu-id="36dc6-105">停用排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-105">Disables a scheduled job.</span></span>

## <span data-ttu-id="36dc6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36dc6-106">SYNTAX</span></span>

### <span data-ttu-id="36dc6-107">Definition (預設值)</span><span class="sxs-lookup"><span data-stu-id="36dc6-107">Definition (Default)</span></span>

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="36dc6-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="36dc6-108">DefinitionId</span></span>

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36dc6-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="36dc6-109">DefinitionName</span></span>

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="36dc6-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="36dc6-110">DESCRIPTION</span></span>
<span data-ttu-id="36dc6-111">**Disable-ScheduledJob** Cmdlet 會暫時停用排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-111">The **Disable-ScheduledJob** cmdlet temporarily disables scheduled jobs.</span></span>
<span data-ttu-id="36dc6-112">停用會保留所有工作屬性，而且不會停用工作觸發程序，但會防止排程工作在被觸發時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="36dc6-112">Disabling preserves all job properties and does not disable the job triggers, but it prevents the scheduled jobs from starting automatically when triggered.</span></span>
<span data-ttu-id="36dc6-113">您可以使用 Start-Job Cmdlet 來啟動已停用的排程工作，或使用已停用的排程工作做為範本。</span><span class="sxs-lookup"><span data-stu-id="36dc6-113">You can start a disabled scheduled job by using the Start-Job cmdlet or use a disabled scheduled job as a template.</span></span>

<span data-ttu-id="36dc6-114">為停用排程工作， **Disable-ScheduledJob** Cmdlet 會將排程工作的 **Enabled** 屬性設定為 False ($false)。</span><span class="sxs-lookup"><span data-stu-id="36dc6-114">To disable a scheduled job, the **Disable-ScheduledJob** cmdlet sets the **Enabled** property of the scheduled job to False ($false).</span></span>
<span data-ttu-id="36dc6-115">若要重新啟用排程工作，請使用 Enable-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="36dc6-115">To re-enable the scheduled job, use the Enable-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="36dc6-116">**Disable-ScheduledJob** 為 Windows PowerShell 內含之 **PSScheduledJob** 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="36dc6-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="36dc6-117">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="36dc6-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="36dc6-118">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="36dc6-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="36dc6-119">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="36dc6-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="36dc6-120">範例</span><span class="sxs-lookup"><span data-stu-id="36dc6-120">EXAMPLES</span></span>

### <span data-ttu-id="36dc6-121">範例 1：停用排程工作</span><span class="sxs-lookup"><span data-stu-id="36dc6-121">Example 1: Disable a scheduled job</span></span>

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

<span data-ttu-id="36dc6-122">此命令會停用本機電腦上識別碼為 2 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-122">This command disables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="36dc6-123">輸出會顯示命令的效果。</span><span class="sxs-lookup"><span data-stu-id="36dc6-123">The output shows the effect of the command.</span></span>

### <span data-ttu-id="36dc6-124">範例 2：停用所有排程工作</span><span class="sxs-lookup"><span data-stu-id="36dc6-124">Example 2: Disable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

<span data-ttu-id="36dc6-125">此命令會停用本機電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-125">This command disables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="36dc6-126">它會使用 Get-ScheduledJob Cmdlet 來取得所有排程工作，並使用 **Disable-ScheduledJob** Cmdlet 來停用它們。</span><span class="sxs-lookup"><span data-stu-id="36dc6-126">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Disable-ScheduledJob** cmdlet to disable them.</span></span>

<span data-ttu-id="36dc6-127">您可以使用 Enable-ScheduledJob Cmdlet 來重新啟用排程工作，並使用 Start-Job Cmdlet 來執行已停用的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-127">You can re-enable scheduled job by using the Enable-ScheduledJob cmdlet and run a disabled scheduled job by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="36dc6-128">**Disable-ScheduledJob** 不會產生警告或錯誤 (若您停用已經停用的排程工作)，因此您可以在不指定任何條件的情況下停用所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-128">**Disable-ScheduledJob** does not generate warnings or errors if you disable a scheduled job that is already disabled, so you can disable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="36dc6-129">範例 3：停用選取的排程工作</span><span class="sxs-lookup"><span data-stu-id="36dc6-129">Example 3: Disable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

<span data-ttu-id="36dc6-130">此命令會停用不包含認證的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-130">This command disables scheduled job do not include a credential.</span></span>
<span data-ttu-id="36dc6-131">不包含認證的工作是以建立工作之使用者的權限執行。</span><span class="sxs-lookup"><span data-stu-id="36dc6-131">Jobs without credentials run with the permission of the user who created them.</span></span>

<span data-ttu-id="36dc6-132">命令會使用 Get-ScheduledJob Cmdlet，來取得電腦上的所有排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-132">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="36dc6-133">管線運算子會將排程工作傳送到 Where-Object Cmdlet，此 Cmdlet 會選取沒有認證的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-133">A pipeline operator sends the scheduled jobs to the Where-Object cmdlet, which selects scheduled jobs that do not have credentials.</span></span>
<span data-ttu-id="36dc6-134">此命令使用 Not (!) 運算子並參照排程工作的 Credential 屬性。</span><span class="sxs-lookup"><span data-stu-id="36dc6-134">The command uses the not (!) operator and references the Credential property of the scheduled job.</span></span>
<span data-ttu-id="36dc6-135">另一個管線運算子會將選取的排程工作傳送到 **Disable-ScheduledJob** Cmdlet，此 Cmdlet 會將排程工作停用。</span><span class="sxs-lookup"><span data-stu-id="36dc6-135">Another pipeline operator sends the selected scheduled jobs to the **Disable-ScheduledJob** cmdlet, which disables them.</span></span>

### <span data-ttu-id="36dc6-136">範例 4：停用遠端電腦上的排程工作</span><span class="sxs-lookup"><span data-stu-id="36dc6-136">Example 4: Disable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

<span data-ttu-id="36dc6-137">此命令會停用兩部遠端電腦 (Srv01 與 Srv10) 上的 TestJob 排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-137">This command disables the TestJob scheduled job on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="36dc6-138">此命令會使用 Invoke-Command Cmdlet，在 Srv01 與 Srv10 電腦上執行 **Disable-ScheduledJob** 命令。</span><span class="sxs-lookup"><span data-stu-id="36dc6-138">The command uses the Invoke-Command cmdlet to run a **Disable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="36dc6-139">此命令會使用 *Disable-ScheduledJob* 的 **Name** 參數來選取每部電腦上的 TestJob 排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-139">The command uses the *Name* parameter of **Disable-ScheduledJob** to select the TestJob scheduled job on each computer.</span></span>

### <span data-ttu-id="36dc6-140">範例 5：依全域識別碼停用排程工作</span><span class="sxs-lookup"><span data-stu-id="36dc6-140">Example 5: Disable a scheduled job by its global ID</span></span>

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

<span data-ttu-id="36dc6-141">此範例顯示如何使用全域識別碼來停用排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-141">This examples shows how to disable a scheduled job by using its global identifier.</span></span>
<span data-ttu-id="36dc6-142">排程工作的 GlobalID 屬性值是唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="36dc6-142">The value of the GlobalID property of a scheduled job is a unique identifier (GUID).</span></span>
<span data-ttu-id="36dc6-143">需要進行精確處理 (例如，當您想要停用多部電腦上的排程工作) 時，請使用 GlobalID 值。</span><span class="sxs-lookup"><span data-stu-id="36dc6-143">Use the GlobalID value when precision is required, such as when you are disabling scheduled jobs on multiple computers.</span></span>

## <span data-ttu-id="36dc6-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36dc6-144">PARAMETERS</span></span>

### <span data-ttu-id="36dc6-145">-Id</span><span class="sxs-lookup"><span data-stu-id="36dc6-145">-Id</span></span>
<span data-ttu-id="36dc6-146">停用具有所指定識別碼 (ID) 的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-146">Disables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="36dc6-147">輸入排程工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="36dc6-147">Enter the ID of a scheduled job.</span></span>

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

### <span data-ttu-id="36dc6-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="36dc6-148">-InputObject</span></span>
<span data-ttu-id="36dc6-149">指定要停用的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-149">Specifies the scheduled job to be disabled.</span></span>
<span data-ttu-id="36dc6-150">輸入包含 **ScheduledJobDefinition** 物件的變數，或輸入可取得 **ScheduledJobDefinition** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="36dc6-150">Enter a variable that contains  **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="36dc6-151">您也可以使用管線將 **ScheduledJobDefinition** 物件傳送至 **Disable-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="36dc6-151">You can also pipe a **ScheduledJobDefinition** object to **Disable-ScheduledJob** .</span></span>

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

### <span data-ttu-id="36dc6-152">-Name</span><span class="sxs-lookup"><span data-stu-id="36dc6-152">-Name</span></span>
<span data-ttu-id="36dc6-153">停用具有所指定名稱的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-153">Disables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="36dc6-154">輸入排程工作的名稱。</span><span class="sxs-lookup"><span data-stu-id="36dc6-154">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="36dc6-155">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="36dc6-155">Wildcards are supported.</span></span>

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

### <span data-ttu-id="36dc6-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="36dc6-156">-PassThru</span></span>
<span data-ttu-id="36dc6-157">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="36dc6-157">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="36dc6-158">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="36dc6-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="36dc6-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="36dc6-159">-Confirm</span></span>
<span data-ttu-id="36dc6-160">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="36dc6-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="36dc6-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="36dc6-161">-WhatIf</span></span>
<span data-ttu-id="36dc6-162">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="36dc6-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="36dc6-163">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="36dc6-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="36dc6-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36dc6-164">CommonParameters</span></span>
<span data-ttu-id="36dc6-165">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="36dc6-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36dc6-166">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="36dc6-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36dc6-167">輸入</span><span class="sxs-lookup"><span data-stu-id="36dc6-167">INPUTS</span></span>

### <span data-ttu-id="36dc6-168">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="36dc6-168">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="36dc6-169">您可以使用管線將排程工作傳送到 **Disable-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="36dc6-169">You can pipe a scheduled job to **Disable-ScheduledJob** .</span></span>

## <span data-ttu-id="36dc6-170">輸出</span><span class="sxs-lookup"><span data-stu-id="36dc6-170">OUTPUTS</span></span>

### <span data-ttu-id="36dc6-171">無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="36dc6-171">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="36dc6-172">若使用 **Passthru** 參數， **Disable-ScheduledJob** 會傳回已停用的排程工作。</span><span class="sxs-lookup"><span data-stu-id="36dc6-172">If you use the **Passthru** parameter, **Disable-ScheduledJob** returns the scheduled job that was disabled.</span></span>
<span data-ttu-id="36dc6-173">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="36dc6-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="36dc6-174">注意</span><span class="sxs-lookup"><span data-stu-id="36dc6-174">NOTES</span></span>

* <span data-ttu-id="36dc6-175">若您使用 **Disable-ScheduledJob** 來停用已經停用的排程工作，它就不會產生警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="36dc6-175">**Disable-ScheduledJob** does not generate warnings or errors if you use it to disable a scheduled job that is already disabled.</span></span>

## <span data-ttu-id="36dc6-176">相關連結</span><span class="sxs-lookup"><span data-stu-id="36dc6-176">RELATED LINKS</span></span>

[<span data-ttu-id="36dc6-177">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-177">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="36dc6-178">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-178">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="36dc6-179">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-179">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="36dc6-180">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-180">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="36dc6-181">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-181">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="36dc6-182">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-182">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="36dc6-183">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-183">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="36dc6-184">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="36dc6-184">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="36dc6-185">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-185">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="36dc6-186">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="36dc6-186">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="36dc6-187">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-187">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="36dc6-188">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-188">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="36dc6-189">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="36dc6-189">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="36dc6-190">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-190">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="36dc6-191">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="36dc6-191">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="36dc6-192">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="36dc6-192">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
