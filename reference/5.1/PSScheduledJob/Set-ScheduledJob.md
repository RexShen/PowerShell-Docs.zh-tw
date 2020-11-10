---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387901"
---
# <span data-ttu-id="ea0e9-103">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-103">Set-ScheduledJob</span></span>

## <span data-ttu-id="ea0e9-104">概要</span><span class="sxs-lookup"><span data-stu-id="ea0e9-104">SYNOPSIS</span></span>
<span data-ttu-id="ea0e9-105">變更排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-105">Changes scheduled jobs.</span></span>

## <span data-ttu-id="ea0e9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea0e9-106">SYNTAX</span></span>

### <span data-ttu-id="ea0e9-107">ScriptBlock (預設值)</span><span class="sxs-lookup"><span data-stu-id="ea0e9-107">ScriptBlock (Default)</span></span>

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="ea0e9-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="ea0e9-108">FilePath</span></span>

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### <span data-ttu-id="ea0e9-109">執行</span><span class="sxs-lookup"><span data-stu-id="ea0e9-109">Execution</span></span>

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## <span data-ttu-id="ea0e9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ea0e9-110">DESCRIPTION</span></span>
<span data-ttu-id="ea0e9-111">**Set-ScheduledJob** Cmdlet 會變更排程工作的屬性，例如工作執行的命令或執行工作所需的認證。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-111">The **Set-ScheduledJob** cmdlet changes the properties of scheduled jobs, such as the commands that the jobs run or the credentials required to run the job.</span></span>
<span data-ttu-id="ea0e9-112">您也可以使用它來清除排程工作的執行記錄。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-112">You can also use it to clear the execution history of the scheduled job.</span></span>

<span data-ttu-id="ea0e9-113">若要使用此 Cmdlet，請先使用 Get-ScheduledJob Cmdlet 來取得排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-113">To use this cmdlet, begin by using the Get-ScheduledJob cmdlet to get the scheduled job.</span></span>
<span data-ttu-id="ea0e9-114">然後，使用管線將排程工作傳送至 **register-scheduledjob** ，或將工作儲存在變數中，然後使用 *InputObject* 參數來識別工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-114">Then, pipe the scheduled job to **Set-ScheduledJob** or save the job in a variable and use the *InputObject* parameter to identify the job.</span></span>
<span data-ttu-id="ea0e9-115">使用 **Set-ScheduledJob** 的其他參數來變更工作屬性或清除執行記錄。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-115">Use the remaining parameters of **Set-ScheduledJob** to change the job properties or clear the execution history.</span></span>

<span data-ttu-id="ea0e9-116">雖然您可以使用 **Set-ScheduledJob** 變更排程工作的觸發程序和選項，但是 Add-JobTrigger、Set-JobTrigger 和 Set-ScheduledJobOption Cmdlet 提供更簡單的方式讓您完成那些工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-116">Although you can use **Set-ScheduledJob** to change the triggers and options of a scheduled job, the Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJobOption cmdlets provide much easier ways to accomplish those tasks.</span></span>
<span data-ttu-id="ea0e9-117">若要建立新的排程工作，請使用 Register-ScheduledJob Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-117">To create a new scheduled job, use the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="ea0e9-118">**Register-scheduledjob** 的 *Trigger* 參數會加入一個或多個工作觸發程式來啟動工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-118">The *Trigger* parameter of **Set-ScheduledJob** adds one or more job triggers that start the job.</span></span>
<span data-ttu-id="ea0e9-119">*觸發* 程式參數是選擇性的，因此您可以在建立排程工作時新增觸發程式、稍後新增工作觸發程式、新增 *RunNow* 參數以立即啟動工作、使用 Start-Job Cmdlet 來立即啟動作業，或將 untriggered 排程工作儲存為其他作業的範本。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-119">The *Trigger* parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the *RunNow* parameter to start the job immediately, use the Start-Job cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="ea0e9-120">**Set-ScheduledJob** 為 Windows PowerShell 內含之 PSScheduledJob 模組中的其中一個工作排程 Cmdlet 集合。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-120">**Set-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="ea0e9-121">如需排程工作的詳細資訊，請參閱 PSScheduledJob 模組中的「關於」主題。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-121">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="ea0e9-122">匯入 PSScheduledJob 模組，然後輸入：`Get-Help about_Scheduled*`，或參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-122">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="ea0e9-123">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ea0e9-124">範例</span><span class="sxs-lookup"><span data-stu-id="ea0e9-124">EXAMPLES</span></span>

### <span data-ttu-id="ea0e9-125">範例 1：變更工作執行的指令碼</span><span class="sxs-lookup"><span data-stu-id="ea0e9-125">Example 1: Change the script that a job runs</span></span>

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

<span data-ttu-id="ea0e9-126">此範例顯示如何變更排程工作中執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-126">This example shows how to change the script that is run in a scheduled job.</span></span>

<span data-ttu-id="ea0e9-127">第一個命令會使用 Get-ScheduledJob Cmdlet 來取得清查排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-127">The first command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job.</span></span>
<span data-ttu-id="ea0e9-128">輸出會顯示該工作執行 Get-Inventory.ps1 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-128">The output shows that the job runs the Get-Inventory.ps1 script.</span></span>

<span data-ttu-id="ea0e9-129">此命令並非必要；包含此命令僅為顯示指令碼變更的效果。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-129">This command is not required; it is included only to show the effect of the script change.</span></span>

### <span data-ttu-id="ea0e9-130">範例 2：刪除排程工作的執行記錄</span><span class="sxs-lookup"><span data-stu-id="ea0e9-130">Example 2: Delete the execution history of a scheduled job</span></span>

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="ea0e9-131">此命令會刪除 BackupArchive 排程工作的目前執行記錄與儲存的工作結果。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-131">This command deletes the current execution history and saved job results for the BackupArchive scheduled job.</span></span>

<span data-ttu-id="ea0e9-132">此命令會使用 Get-ScheduledJob Cmdlet 來取得 BackupArchive 排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-132">The command uses the Get-ScheduledJob cmdlet to get the BackupArchive scheduled job.</span></span>
<span data-ttu-id="ea0e9-133">管線運算子 (|) 會將工作傳送至 **Set-ScheduledJob** Cmdlet 以變更它。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-133">A pipeline operator (|) sends the job to the **Set-ScheduledJob** cmdlet to change it.</span></span>
<span data-ttu-id="ea0e9-134">**Register-scheduledjob** 指令 Cmdlet 會使用 *ClearExecutionHistory* 參數來刪除執行歷程記錄和儲存的結果。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-134">The **Set-ScheduledJob** cmdlet uses the *ClearExecutionHistory* parameter to delete the execution history and saved results.</span></span>

<span data-ttu-id="ea0e9-135">如需排程工作之執行記錄與儲存的工作結果的詳細資訊，請參閱 about_Scheduled_Jobs。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-135">For more information about the execution history and saved job results of scheduled jobs, see about_Scheduled_Jobs.</span></span>

### <span data-ttu-id="ea0e9-136">範例 3：變更遠端電腦上的排程工作</span><span class="sxs-lookup"><span data-stu-id="ea0e9-136">Example 3: Change scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

<span data-ttu-id="ea0e9-137">此命令會變更 Server01 與 Server02 電腦上所有排程工作的初始化指令碼。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-137">This command changes the initialization script in all scheduled jobs on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="ea0e9-138">此命令會使用 Invoke-Command Cmdlet，在 Server01 和 Server02 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-138">The command uses the Invoke-Command cmdlet to run a command on the Server01 and Server02 computers.</span></span>

<span data-ttu-id="ea0e9-139">遠端命令的開頭是可取得電腦上所有排程工作的 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-139">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="ea0e9-140">排程的工作會以管道傳送至 **register-scheduledjob** Cmdlet，這會將初始化腳本變更為 SetForRun.ps1。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-140">The scheduled jobs are piped to the **Set-ScheduledJob** cmdlet, which changes the initialization script to SetForRun.ps1.</span></span>

## <span data-ttu-id="ea0e9-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ea0e9-141">PARAMETERS</span></span>

### <span data-ttu-id="ea0e9-142">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="ea0e9-142">-ArgumentList</span></span>
<span data-ttu-id="ea0e9-143">指定由 *FilePath* 參數所指定之指令碼的參數值，或指定由 *ScriptBlock* 參數所指定之命令的參數值。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-143">Specifies values for the parameters of the script that is specified by the *FilePath* parameter or for the command that is specified by the *ScriptBlock* parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-144">-Authentication</span><span class="sxs-lookup"><span data-stu-id="ea0e9-144">-Authentication</span></span>
<span data-ttu-id="ea0e9-145">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-145">Specifies the mechanism that is used to authenticate the user's credentials.</span></span>
<span data-ttu-id="ea0e9-146">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="ea0e9-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ea0e9-147">預設</span><span class="sxs-lookup"><span data-stu-id="ea0e9-147">Default</span></span>
- <span data-ttu-id="ea0e9-148">基本</span><span class="sxs-lookup"><span data-stu-id="ea0e9-148">Basic</span></span>
- <span data-ttu-id="ea0e9-149">Credssp</span><span class="sxs-lookup"><span data-stu-id="ea0e9-149">Credssp</span></span>
- <span data-ttu-id="ea0e9-150">Digest</span><span class="sxs-lookup"><span data-stu-id="ea0e9-150">Digest</span></span>
- <span data-ttu-id="ea0e9-151">Kerberos</span><span class="sxs-lookup"><span data-stu-id="ea0e9-151">Kerberos</span></span>
- <span data-ttu-id="ea0e9-152">交涉</span><span class="sxs-lookup"><span data-stu-id="ea0e9-152">Negotiate</span></span>
- <span data-ttu-id="ea0e9-153">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="ea0e9-153">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="ea0e9-154">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-154">The default value is Default.</span></span> <span data-ttu-id="ea0e9-155">如需此參數值的詳細資訊，請參閱 PowerShell SDK 中的 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) 。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-155">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) in the PowerShell SDK.</span></span>

<span data-ttu-id="ea0e9-156">注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-156">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span>
<span data-ttu-id="ea0e9-157">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-157">This mechanism increases the security risk of the remote operation.</span></span>
<span data-ttu-id="ea0e9-158">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-158">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-159">-ClearExecutionHistory</span><span class="sxs-lookup"><span data-stu-id="ea0e9-159">-ClearExecutionHistory</span></span>
<span data-ttu-id="ea0e9-160">刪除排程工作的目前執行記錄與儲存的結果。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-160">Deletes the current execution history and the saved results of the scheduled job.</span></span>

<span data-ttu-id="ea0e9-161">工作執行記錄與工作結果會隨著排程工作儲存在工作建立所在電腦的 $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs 目錄。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-161">The job execution history and job results are saved with the scheduled job in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the computer on which the job is created.</span></span>
<span data-ttu-id="ea0e9-162">若要查看執行記錄，請使用 Get-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-162">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="ea0e9-163">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-163">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="ea0e9-164">此參數不會影響 [工作排程器] 寫入到 Windows 事件記錄檔的事件，而且它不會使得 Windows PowerShell 停止儲存工作結果。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-164">This parameter does not affect the events that Task Scheduler writes to the Windows event logs and it does not stop Windows PowerShell from saving job results.</span></span>
<span data-ttu-id="ea0e9-165">若要管理儲存的工作結果數目，請使用 *MaxResultCount* 參數。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-165">To manage the number of job results that are saved, use the *MaxResultCount* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="ea0e9-166">-Credential</span></span>
<span data-ttu-id="ea0e9-167">指定具有執行排程工作之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-167">Specifies a user account that has permission to run the scheduled job.</span></span>
<span data-ttu-id="ea0e9-168">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-168">The default is the current user.</span></span>

<span data-ttu-id="ea0e9-169">輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 中的物件。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-169">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one from the Get-Credential cmdlet.</span></span>
<span data-ttu-id="ea0e9-170">若您只輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-170">If you enter only a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-171">-FilePath</span><span class="sxs-lookup"><span data-stu-id="ea0e9-171">-FilePath</span></span>
<span data-ttu-id="ea0e9-172">指定排程工作所執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-172">Specifies a script that the scheduled job runs.</span></span>
<span data-ttu-id="ea0e9-173">輸入本機電腦上之 .ps1 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-173">Enter the path to a .ps1 file on the local computer.</span></span>
<span data-ttu-id="ea0e9-174">若要指定指令碼參數的預設值，請使用 *ArgumentList* 參數。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-174">To specify default values for the script parameters, use the *ArgumentList* parameter.</span></span>
<span data-ttu-id="ea0e9-175">每個排程工作都必須有 *ScriptBlock* 或 *FilePath* 值。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-175">Every scheduled job must have either a *ScriptBlock* or *FilePath* value.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-176">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="ea0e9-176">-InitializationScript</span></span>
<span data-ttu-id="ea0e9-177">指定 Windows PowerShell 指令碼 (.ps1) 的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-177">Specifies the fully qualified path to a Windows PowerShell script (.ps1).</span></span>
<span data-ttu-id="ea0e9-178">初始化指令碼會在執行 *ScriptBlock* 參數所指定的命令或 *FilePath* 參數所指定的指令碼之前，在針對背景工作所建立的工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-178">The initialization script runs in the session that is created for the background job before the commands that are specified by the *ScriptBlock* parameter or the script that is specified by the *FilePath* parameter.</span></span>
<span data-ttu-id="ea0e9-179">您可以使用初始化指令碼來設定工作階段，例如新增檔案/函式/別名、建立目錄，或檢查先決條件。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-179">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="ea0e9-180">若要指定會執行主要工作命令的指令碼，請使用 *FilePath* 參數。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-180">To specify a script that runs the primary job commands, use the *FilePath* parameter.</span></span>

<span data-ttu-id="ea0e9-181">如果初始化腳本產生錯誤（包括非終止錯誤），則排程工作的目前實例不會執行，且其狀態會是 [失敗]。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-181">If the initialization script generates an error, including a non-terminating error, the current instance of the scheduled job does not run and its status is Failed.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-182">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ea0e9-182">-InputObject</span></span>
<span data-ttu-id="ea0e9-183">指定要變更的排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-183">Specifies the scheduled job to be changed.</span></span>
<span data-ttu-id="ea0e9-184">輸入包含 **>scheduledjobdefinition** 物件的變數，或輸入可取得 **>scheduledjobdefinition** 物件的命令或運算式，例如 Get-ScheduledJob 命令。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-184">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="ea0e9-185">您也可以使用管線將 **ScheduledJobDefinition** 物件傳送至 **Set-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-185">You can also pipe a **ScheduledJobDefinition** object to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="ea0e9-186">若指定多個排程工作， **Set-ScheduledJob** 會對所有工作進行相同的變更。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-186">If you specify multiple scheduled jobs, **Set-ScheduledJob** makes the same changes to all jobs.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-187">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="ea0e9-187">-MaxResultCount</span></span>
<span data-ttu-id="ea0e9-188">指定要為排程工作保留幾個工作結果項目。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-188">Specifies how many job result entries are maintained for the scheduled job.</span></span>
<span data-ttu-id="ea0e9-189">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-189">The default value is 32.</span></span>

<span data-ttu-id="ea0e9-190">Windows PowerShell 會將每個觸發之排程工作執行個體的執行記錄與結果儲存在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-190">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span>
<span data-ttu-id="ea0e9-191">此參數的值決定針對此排程工作儲存的工作執行個體結果數目。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-191">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span>
<span data-ttu-id="ea0e9-192">當工作執行個體數目超過此值時，Windows PowerShell 會刪除最舊的工作執行個體結果，以便挪出空間儲存最新工作執行個體結果。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-192">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="ea0e9-193">作業執行歷程記錄和工作結果會儲存在工作建立所在電腦的 $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs \\ \<JobName\> \Output \\ \<Timestamp\> 目錄中。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-193">The job execution history and job results are saved in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\\\<JobName\>\Output\\\<Timestamp\> directories on the computer on which the job is created.</span></span>
<span data-ttu-id="ea0e9-194">若要查看執行記錄，請使用 Get-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-194">To see the execution history, use the Get-Job cmdlet.</span></span>
<span data-ttu-id="ea0e9-195">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-195">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="ea0e9-196">*MaxResultCount* 參數會設定排程工作之 ExecutionHistoryLength 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-196">The *MaxResultCount* parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="ea0e9-197">若要刪除目前的執行記錄與工作結果，請使用 *ClearExecutionHistory* 參數。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-197">To delete the current execution history and job results, use the *ClearExecutionHistory* parameter.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-198">-Name</span><span class="sxs-lookup"><span data-stu-id="ea0e9-198">-Name</span></span>
<span data-ttu-id="ea0e9-199">指定排程工作的新名稱與排程工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-199">Specifies a new name for the scheduled job and instances of the scheduled job.</span></span>
<span data-ttu-id="ea0e9-200">此名稱在本機電腦上必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-200">The name must be unique on the local computer.</span></span>

<span data-ttu-id="ea0e9-201">若要識別要變更的排程工作，請使用 *InputObject* 參數或使用管線將排程工作從 Get-ScheduledJob 傳送至 **Set-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-201">To identify the scheduled job to be changed, use the *InputObject* parameter or pipe a scheduled job from Get-ScheduledJob to **Set-ScheduledJob**.</span></span>

<span data-ttu-id="ea0e9-202">此參數不會變更磁碟上的工作執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-202">This parameter does not change the names of job instances on disk.</span></span>
<span data-ttu-id="ea0e9-203">它只會影響此命令完成後啟動的工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-203">It affects only job instances that are started after this command completes.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-204">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ea0e9-204">-PassThru</span></span>
<span data-ttu-id="ea0e9-205">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-205">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="ea0e9-206">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-206">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ea0e9-207">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="ea0e9-207">-RunAs32</span></span>
<span data-ttu-id="ea0e9-208">在 32 位元處理程序中執行排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-208">Runs the scheduled job in a 32-bit process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-209">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="ea0e9-209">-RunEvery</span></span>

<span data-ttu-id="ea0e9-210">用來指定執行作業的頻率。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-210">Used to specify how often to run the job.</span></span> <span data-ttu-id="ea0e9-211">例如，使用此選項可每隔15分鐘執行一次作業。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-211">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-212">-RunNow</span><span class="sxs-lookup"><span data-stu-id="ea0e9-212">-RunNow</span></span>
<span data-ttu-id="ea0e9-213">在 **register-scheduledjob** 指令程式執行之後，立即啟動作業。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-213">Starts a job immediately, as soon as the **Set-ScheduledJob** cmdlet is run.</span></span>
<span data-ttu-id="ea0e9-214">此參數可減少在登錄後觸發 [工作排程器] 以立即執行 Windows PowerShell 指令碼的需求，而且不需要使用者建立指定開始日期和時間的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-214">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and does not require users to create a trigger that specifies a starting date and time.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-215">-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ea0e9-215">-ScheduledJobOption</span></span>
<span data-ttu-id="ea0e9-216">設定排程工作的選項。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-216">Sets options for the scheduled job.</span></span>
<span data-ttu-id="ea0e9-217">輸入 **ScheduledJobOptions** 物件，例如您使用 New-ScheduledJobOption Cmdlet 或雜湊表值建立的物件。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-217">Enter a **ScheduledJobOptions** object, such as one that you create by using the New-ScheduledJobOption cmdlet, or a hash table value.</span></span>

<span data-ttu-id="ea0e9-218">您可以在登錄排程工作時設定排程工作的選項，或使用 Set-ScheduledJobOption 或 **Set-ScheduledJob** Cmdlet 來設定或變更選項。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-218">You can set options for a scheduled job when you register the scheduled job or use the Set-ScheduledJobOption or **Set-ScheduledJob** cmdlets to set or change options.</span></span>

<span data-ttu-id="ea0e9-219">許多選項與其預設值會決定排程工作是否會執行以及執行時間。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-219">Many of the options and their default values determine whether and when a scheduled job runs.</span></span>
<span data-ttu-id="ea0e9-220">排定工作之前，請務必檢閱這些選項。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-220">Be sure to review these options before scheduling a job.</span></span>
<span data-ttu-id="ea0e9-221">如需排程工作選項的描述 (包括預設值)，請參閱 New-ScheduledJobOption。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-221">For a description of the scheduled job options, including the default values, see New-ScheduledJobOption.</span></span>

<span data-ttu-id="ea0e9-222">若要提交雜湊表，請使用下列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-222">To submit a hash table, use the following keys.</span></span>
<span data-ttu-id="ea0e9-223">在下列雜湊表中，索引鍵隨著其預設值顯示。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-223">In the following hash table, the keys are shown with their default values.</span></span>

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-224">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="ea0e9-224">-ScriptBlock</span></span>
<span data-ttu-id="ea0e9-225">指定排程工作執行的命令。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-225">Specifies the commands that the scheduled job runs.</span></span>
<span data-ttu-id="ea0e9-226">使用大括弧 ( { } ) 括住命令以建立指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-226">Enclose the commands in braces ( { } ) to create a script block.</span></span>
<span data-ttu-id="ea0e9-227">若要指定命令參數的預設值，請使用 *ArgumentList* 參數。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-227">To specify default values for command parameters, use the *ArgumentList* parameter.</span></span>

<span data-ttu-id="ea0e9-228">每個 Register-ScheduledJob 命令都必須使用 *ScriptBlock* 或 *FilePath* 參數。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-228">Every Register-ScheduledJob command must use either the *ScriptBlock* or *FilePath* parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-229">-Trigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-229">-Trigger</span></span>
<span data-ttu-id="ea0e9-230">指定排程工作的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-230">Specifies the triggers for the scheduled job.</span></span>
<span data-ttu-id="ea0e9-231">輸入一或多個 **ScheduledJobTrigger** 物件，例如 New-JobTrigger Cmdlet 傳回的物件，或輸入由工作觸發程序索引鍵與值組成的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-231">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the New-JobTrigger cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="ea0e9-232">工作觸發程式會在一次性或週期性排程或事件發生時自動啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-232">A job trigger starts a scheduled job automatically on a one-time or recurring scheduled or when an event occurs.</span></span>

<span data-ttu-id="ea0e9-233">工作觸發程序是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-233">Job triggers are optional.</span></span>
<span data-ttu-id="ea0e9-234">您可以在建立排程工作時新增觸發程式、使用 Add-JobTrigger 或 Register-scheduledjob 指令 **程式** 稍後新增觸發程式，或使用 Start-Job Cmdlet 來立即啟動排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-234">You can add a trigger when you create the scheduled job, use the Add-JobTrigger or **Set-ScheduledJob** cmdlets to add triggers later, or use the Start-Job cmdlet to start the scheduled job immediately.</span></span>
<span data-ttu-id="ea0e9-235">您也可以建立及維護沒有工作觸發程序的排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-235">You can also create and maintain a scheduled job that has no job triggers.</span></span>

<span data-ttu-id="ea0e9-236">若要提交雜湊表，請使用下列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-236">To submit a hash table, use the following keys.</span></span>

<span data-ttu-id="ea0e9-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (或任何有效的時間字串) ; `DaysOfWeek="Monday", "Wednesday"` (或日期名稱的任何組合) ; `Interval=2` (或任何有效的頻率間隔) ; `RandomDelay="30minutes"` (或任何有效的 timespan 字串) ; `User="Domain1\User01"` (或任何有效的使用者;只能搭配 AtLogon 頻率值使用) </span><span class="sxs-lookup"><span data-stu-id="ea0e9-237">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01"` (or any valid user; used only with the AtLogon frequency value)</span></span>

<span data-ttu-id="ea0e9-238">}</span><span class="sxs-lookup"><span data-stu-id="ea0e9-238">}</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ea0e9-239">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea0e9-239">CommonParameters</span></span>
<span data-ttu-id="ea0e9-240">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-240">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea0e9-241">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-241">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea0e9-242">輸入</span><span class="sxs-lookup"><span data-stu-id="ea0e9-242">INPUTS</span></span>

### <span data-ttu-id="ea0e9-243">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="ea0e9-243">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="ea0e9-244">您可以使用管線傳送排程工作至 **Set-ScheduledJob** 。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-244">You can pipe scheduled jobs to **Set-ScheduledJob**.</span></span>

## <span data-ttu-id="ea0e9-245">輸出</span><span class="sxs-lookup"><span data-stu-id="ea0e9-245">OUTPUTS</span></span>

### <span data-ttu-id="ea0e9-246">無或 Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="ea0e9-246">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="ea0e9-247">若使用 *Passthru* 參數， **Set-ScheduledJob** 會傳回已變更的排程工作。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-247">If you use the *Passthru* parameter, **Set-ScheduledJob** returns the scheduled job that was changed.</span></span>
<span data-ttu-id="ea0e9-248">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="ea0e9-248">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ea0e9-249">注意</span><span class="sxs-lookup"><span data-stu-id="ea0e9-249">NOTES</span></span>

## <span data-ttu-id="ea0e9-250">相關連結</span><span class="sxs-lookup"><span data-stu-id="ea0e9-250">RELATED LINKS</span></span>

[<span data-ttu-id="ea0e9-251">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-251">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="ea0e9-252">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-252">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="ea0e9-253">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-253">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="ea0e9-254">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-254">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="ea0e9-255">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-255">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="ea0e9-256">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-256">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="ea0e9-257">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-257">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="ea0e9-258">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ea0e9-258">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="ea0e9-259">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-259">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="ea0e9-260">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ea0e9-260">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="ea0e9-261">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-261">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="ea0e9-262">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-262">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="ea0e9-263">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="ea0e9-263">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="ea0e9-264">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-264">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="ea0e9-265">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="ea0e9-265">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="ea0e9-266">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="ea0e9-266">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
