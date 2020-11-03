---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: d36d15194ce1d4a48a59ad8bb8621b3c9c1a74ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202343"
---
# <span data-ttu-id="f72eb-103">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-103">Debug-Job</span></span>

## <span data-ttu-id="f72eb-104">概要</span><span class="sxs-lookup"><span data-stu-id="f72eb-104">SYNOPSIS</span></span>
<span data-ttu-id="f72eb-105">對執行中的背景、遠端或 Windows PowerShell 工作流程工作進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f72eb-105">Debugs a running background, remote, or Windows PowerShell Workflow job.</span></span>

## <span data-ttu-id="f72eb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f72eb-106">SYNTAX</span></span>

### <span data-ttu-id="f72eb-107">JobParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="f72eb-107">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f72eb-108">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72eb-108">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f72eb-109">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72eb-109">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f72eb-110">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72eb-110">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f72eb-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f72eb-111">DESCRIPTION</span></span>
<span data-ttu-id="f72eb-112">**Debug-Job** Cmdlet 可讓您對在工作內執行的指令碼進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f72eb-112">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="f72eb-113">此 Cmdlet 專門設計來對 Windows PowerShell 工作流程工作、背景工作，以及在遠端工作階段中執行的工作進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f72eb-113">The cmdlet is designed to debug Windows PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="f72eb-114">**Debug-Job** 接受以執行中的工作物件、名稱、識別碼或執行個體識別碼做為輸入，並在執行的指令碼上啟動偵錯工作階段。</span><span class="sxs-lookup"><span data-stu-id="f72eb-114">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="f72eb-115">偵錯工具 **quit** 命令會停止工作和正在執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f72eb-115">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="f72eb-116">從 Windows PowerShell 5.0 開始， **exit** 命令會中斷偵錯工具，並允許工作繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f72eb-116">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="f72eb-117">範例</span><span class="sxs-lookup"><span data-stu-id="f72eb-117">EXAMPLES</span></span>

### <span data-ttu-id="f72eb-118">範例 1：依工作識別碼對工作進行偵錯</span><span class="sxs-lookup"><span data-stu-id="f72eb-118">Example 1: Debug a job by job ID</span></span>

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

<span data-ttu-id="f72eb-119">此命令會中斷識別碼為 3 的執行中工作。</span><span class="sxs-lookup"><span data-stu-id="f72eb-119">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="f72eb-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f72eb-120">PARAMETERS</span></span>

### <span data-ttu-id="f72eb-121">-Id</span><span class="sxs-lookup"><span data-stu-id="f72eb-121">-Id</span></span>
<span data-ttu-id="f72eb-122">指定執行中工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f72eb-122">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="f72eb-123">若要取得工作的識別碼，請執行 Get-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72eb-123">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72eb-124">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f72eb-124">-InstanceId</span></span>
<span data-ttu-id="f72eb-125">指定執行中工作的執行個體識別碼 GUID。</span><span class="sxs-lookup"><span data-stu-id="f72eb-125">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="f72eb-126">若要取得工作的 *InstanceId* ，請執行 **Get-Job** Cmdlet，將結果使用管道傳送到 **Format-** \* Cmdlet，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="f72eb-126">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** \* cmdlet, as shown in the following example:</span></span>

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72eb-127">-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-127">-Job</span></span>
<span data-ttu-id="f72eb-128">指定執行中的工作物件。</span><span class="sxs-lookup"><span data-stu-id="f72eb-128">Specifies a running job object.</span></span>
<span data-ttu-id="f72eb-129">使用此參數最簡單的方式，是將 **Get-Job** 命令 (傳回您要進行偵錯的執行中工作) 的結果儲存在變數中，然後將變數指定為此參數的值。</span><span class="sxs-lookup"><span data-stu-id="f72eb-129">The simplest way to use this parameter is to save the results of a **Get-Job** command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f72eb-130">-Name</span><span class="sxs-lookup"><span data-stu-id="f72eb-130">-Name</span></span>
<span data-ttu-id="f72eb-131">依工作的好記名稱指定工作。</span><span class="sxs-lookup"><span data-stu-id="f72eb-131">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="f72eb-132">當您啟動工作時，您可以在 Cmdlet (例如 Invoke-Command 和 Start-Job) 中加入 *JobName* 參數指定工作名稱。</span><span class="sxs-lookup"><span data-stu-id="f72eb-132">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72eb-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f72eb-133">-Confirm</span></span>
<span data-ttu-id="f72eb-134">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f72eb-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f72eb-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f72eb-135">-WhatIf</span></span>
<span data-ttu-id="f72eb-136">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f72eb-136">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f72eb-137">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f72eb-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f72eb-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f72eb-138">CommonParameters</span></span>
<span data-ttu-id="f72eb-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f72eb-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f72eb-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f72eb-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f72eb-141">輸入</span><span class="sxs-lookup"><span data-stu-id="f72eb-141">INPUTS</span></span>

### <span data-ttu-id="f72eb-142">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="f72eb-142">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="f72eb-143">輸出</span><span class="sxs-lookup"><span data-stu-id="f72eb-143">OUTPUTS</span></span>

## <span data-ttu-id="f72eb-144">注意</span><span class="sxs-lookup"><span data-stu-id="f72eb-144">NOTES</span></span>

## <span data-ttu-id="f72eb-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="f72eb-145">RELATED LINKS</span></span>

[<span data-ttu-id="f72eb-146">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-146">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="f72eb-147">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-147">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="f72eb-148">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-148">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f72eb-149">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-149">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="f72eb-150">Start-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-150">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f72eb-151">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-151">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="f72eb-152">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-152">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="f72eb-153">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f72eb-153">Wait-Job</span></span>](Wait-Job.md)
