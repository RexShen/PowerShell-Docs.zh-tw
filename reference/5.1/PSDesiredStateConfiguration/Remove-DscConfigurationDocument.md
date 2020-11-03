---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203936"
---
# <span data-ttu-id="4c1fe-103">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="4c1fe-103">Remove-DscConfigurationDocument</span></span>

## <span data-ttu-id="4c1fe-104">概要</span><span class="sxs-lookup"><span data-stu-id="4c1fe-104">SYNOPSIS</span></span>
<span data-ttu-id="4c1fe-105">從 DSC 設定存放區移除設定文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-105">Removes a configuration document from the DSC configuration store.</span></span>

## <span data-ttu-id="4c1fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4c1fe-106">SYNTAX</span></span>

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4c1fe-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4c1fe-107">DESCRIPTION</span></span>
<span data-ttu-id="4c1fe-108">`Remove-DscConfigurationDocument`Cmdlet 會從 Windows PowerShell Desired State Configuration (DSC) 設定存放區移除設定檔 ( mof 檔案) 。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-108">The `Remove-DscConfigurationDocument` cmdlet removes a configuration document (.mof file) from the Windows PowerShell Desired State Configuration (DSC) configuration store.</span></span>
<span data-ttu-id="4c1fe-109">在設定期間，此 `Start-DscConfiguration` Cmdlet 會將 mof 檔案複製到目的電腦上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-109">During configuration, the `Start-DscConfiguration` cmdlet copies a .mof file to a folder on the target computer.</span></span>
<span data-ttu-id="4c1fe-110">此 Cmdlet 會移除該設定文件，並進行其他清除工作。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-110">This cmdlet removes that configuration document and does additional cleanup.</span></span>

<span data-ttu-id="4c1fe-111">此 Cmdlet 僅適用于2014年11月更新彙總套件的一部分，可從 Microsoft 支援服務程式庫 [Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) 。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="4c1fe-112">範例</span><span class="sxs-lookup"><span data-stu-id="4c1fe-112">EXAMPLES</span></span>

### <span data-ttu-id="4c1fe-113">範例 1：移除目前的設定文件</span><span class="sxs-lookup"><span data-stu-id="4c1fe-113">Example 1: Remove the current configuration document</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

<span data-ttu-id="4c1fe-114">第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-114">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="4c1fe-115">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-115">The command prompts you for a password.</span></span>
<span data-ttu-id="4c1fe-116">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-116">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="4c1fe-117">第二個命令會針對 $Session 中儲存之 **CimSession** 所指定的電腦移除目前設定文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-117">The second command removes the current configuration document for the computer specified in the **CimSession** stored in $Session.</span></span>

## <span data-ttu-id="4c1fe-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4c1fe-118">PARAMETERS</span></span>

### <span data-ttu-id="4c1fe-119">-AsJob</span><span class="sxs-lookup"><span data-stu-id="4c1fe-119">-AsJob</span></span>
<span data-ttu-id="4c1fe-120">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-120">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="4c1fe-121">如果您指定 *AsJob* 參數，此命令就會傳回代表工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-121">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="4c1fe-122">您可以繼續在工作階段中運作，直到工作完成。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-122">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="4c1fe-123">工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-123">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="4c1fe-124">若要管理工作，請使用各項 Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-124">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="4c1fe-125">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-125">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="4c1fe-126">若要使用這個參數，本機電腦和遠端電腦必須針對遠端執行功能進行設定，並且在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以系統管理員身分執行] 選項來開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-126">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="4c1fe-127">如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-127">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="4c1fe-128">如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-128">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="4c1fe-129">-CimSession</span><span class="sxs-lookup"><span data-stu-id="4c1fe-129">-CimSession</span></span>
<span data-ttu-id="4c1fe-130">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-130">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="4c1fe-131">輸入電腦名稱稱或會話物件，例如 **CimSession** 或 **CimSession** Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-131">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c1fe-132">-Force</span><span class="sxs-lookup"><span data-stu-id="4c1fe-132">-Force</span></span>
<span data-ttu-id="4c1fe-133">指出此 Cmdlet 會在移除設定文件之前，先停止執行中的設定工作。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-133">Indicates that this cmdlet stops the running configuration job before it removes the configuration document.</span></span>
<span data-ttu-id="4c1fe-134">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4c1fe-135">-Stage</span><span class="sxs-lookup"><span data-stu-id="4c1fe-135">-Stage</span></span>
<span data-ttu-id="4c1fe-136">指定要移除的設定文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-136">Specifies which configuration document to remove.</span></span>
<span data-ttu-id="4c1fe-137">您可以指定多份文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-137">You can specify multiple documents.</span></span>
<span data-ttu-id="4c1fe-138">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="4c1fe-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4c1fe-139">Current。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-139">Current.</span></span>
<span data-ttu-id="4c1fe-140">移除說明系統目前狀態的設定文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-140">Remove the configuration document that describes the current state of the system.</span></span>
- <span data-ttu-id="4c1fe-141">Pending。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-141">Pending.</span></span>
<span data-ttu-id="4c1fe-142">移除說明系統暫止狀態的設定文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-142">Remove the configuration document that describes the pending state of the system.</span></span>
- <span data-ttu-id="4c1fe-143">Previous。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-143">Previous.</span></span>
<span data-ttu-id="4c1fe-144">移除說明系統先前狀態的設定文件。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-144">Remove the configuration document that describes the previous state of the system.</span></span>

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c1fe-145">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="4c1fe-145">-ThrottleLimit</span></span>
<span data-ttu-id="4c1fe-146">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-146">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="4c1fe-147">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-147">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="4c1fe-148">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-148">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4c1fe-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c1fe-149">-Confirm</span></span>
<span data-ttu-id="4c1fe-150">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4c1fe-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c1fe-151">-WhatIf</span></span>
<span data-ttu-id="4c1fe-152">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4c1fe-153">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4c1fe-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c1fe-154">CommonParameters</span></span>
<span data-ttu-id="4c1fe-155">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c1fe-156">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4c1fe-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c1fe-157">輸入</span><span class="sxs-lookup"><span data-stu-id="4c1fe-157">INPUTS</span></span>

### <span data-ttu-id="4c1fe-158">無</span><span class="sxs-lookup"><span data-stu-id="4c1fe-158">None</span></span>

## <span data-ttu-id="4c1fe-159">輸出</span><span class="sxs-lookup"><span data-stu-id="4c1fe-159">OUTPUTS</span></span>

### <span data-ttu-id="4c1fe-160">無</span><span class="sxs-lookup"><span data-stu-id="4c1fe-160">None</span></span>

## <span data-ttu-id="4c1fe-161">注意</span><span class="sxs-lookup"><span data-stu-id="4c1fe-161">NOTES</span></span>

## <span data-ttu-id="4c1fe-162">相關連結</span><span class="sxs-lookup"><span data-stu-id="4c1fe-162">RELATED LINKS</span></span>

[<span data-ttu-id="4c1fe-163">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="4c1fe-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="4c1fe-164">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c1fe-164">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="4c1fe-165">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="4c1fe-165">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)
