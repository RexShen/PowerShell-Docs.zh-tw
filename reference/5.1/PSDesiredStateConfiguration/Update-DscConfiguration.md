---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203072"
---
# <span data-ttu-id="9fe52-103">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fe52-103">Update-DscConfiguration</span></span>

## <span data-ttu-id="9fe52-104">概要</span><span class="sxs-lookup"><span data-stu-id="9fe52-104">SYNOPSIS</span></span>
<span data-ttu-id="9fe52-105">檢查提取伺服器以取得更新的設定，並加以套用。</span><span class="sxs-lookup"><span data-stu-id="9fe52-105">Checks the pull server for an updated configuration and applies it.</span></span>

## <span data-ttu-id="9fe52-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9fe52-106">SYNTAX</span></span>

### <span data-ttu-id="9fe52-107">ComputerNameSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="9fe52-107">ComputerNameSet (Default)</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9fe52-108">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="9fe52-108">CimSessionSet</span></span>

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9fe52-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9fe52-109">DESCRIPTION</span></span>
<span data-ttu-id="9fe52-110">指令 `Update-DscConfiguration` 程式會連接到提取伺服器，如果它與節點上的最新內容不同，則會下載設定，然後將設定套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="9fe52-110">The `Update-DscConfiguration` cmdlet connects to a pull server, downloads the configuration if it differs from what is current on the node, and then applies the configuration to the computer.</span></span>

<span data-ttu-id="9fe52-111">此 Cmdlet 僅適用于2014年11月更新彙總套件的一部分，可從 Microsoft 支援服務程式庫 [Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) 。</span><span class="sxs-lookup"><span data-stu-id="9fe52-111">This cmdlet is available only as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span>

## <span data-ttu-id="9fe52-112">範例</span><span class="sxs-lookup"><span data-stu-id="9fe52-112">EXAMPLES</span></span>

### <span data-ttu-id="9fe52-113">範例 1︰更新組態</span><span class="sxs-lookup"><span data-stu-id="9fe52-113">Example 1: Update a configuration</span></span>

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

<span data-ttu-id="9fe52-114">執行此命令之後，伺服器會連線到已註冊的提取服務、下載最新的已指派設定，然後加以套用。</span><span class="sxs-lookup"><span data-stu-id="9fe52-114">After running this command, the server will connect to the registered pull service, download the latest assigned configuration, and then apply it.</span></span>
<span data-ttu-id="9fe52-115">-Wait 和-Verbose 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9fe52-115">The -Wait and -Verbose parameters are optional.</span></span>
<span data-ttu-id="9fe52-116">當您以互動方式工作時，這些參數會結合套用設定時有關進度和成功或失敗的即時意見反應。</span><span class="sxs-lookup"><span data-stu-id="9fe52-116">When working interactively, these parameters combined enable real-time feedback about progress and success or failure when applying the configuration.</span></span>

### <span data-ttu-id="9fe52-117">範例2：透過 CIM 會話連接來更新設定</span><span class="sxs-lookup"><span data-stu-id="9fe52-117">Example 2: Update a configuration by connecting over a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

<span data-ttu-id="9fe52-118">第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="9fe52-118">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="9fe52-119">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="9fe52-119">The command prompts you for a password.</span></span>
<span data-ttu-id="9fe52-120">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="9fe52-120">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="9fe52-121">第二個命令會更新儲存在 $Session 的 **CimSession** 中指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="9fe52-121">The second command updates the computer specified in the **CimSession** stored in $Session.</span></span>
<span data-ttu-id="9fe52-122">此命令會指定 *Wait* 參數。</span><span class="sxs-lookup"><span data-stu-id="9fe52-122">The command specifies the *Wait* parameter.</span></span>
<span data-ttu-id="9fe52-123">主控台要到目前的命令完成之後，才會接受其他命令。</span><span class="sxs-lookup"><span data-stu-id="9fe52-123">The console does not accept additional commands until the current command finishes.</span></span>

## <span data-ttu-id="9fe52-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9fe52-124">PARAMETERS</span></span>

### <span data-ttu-id="9fe52-125">-CimSession</span><span class="sxs-lookup"><span data-stu-id="9fe52-125">-CimSession</span></span>
<span data-ttu-id="9fe52-126">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9fe52-126">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="9fe52-127">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="9fe52-127">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="9fe52-128">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="9fe52-128">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9fe52-129">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9fe52-129">-ComputerName</span></span>
<span data-ttu-id="9fe52-130">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="9fe52-130">Specifies an array of computer names.</span></span>
<span data-ttu-id="9fe52-131">此 Cmdlet 會將組態設定套用到此參數指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="9fe52-131">The cmdlet applies the configuration settings to the computers that this parameter specifies.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9fe52-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="9fe52-132">-Credential</span></span>
<span data-ttu-id="9fe52-133">指定目標電腦的使用者名稱和密碼，做為 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="9fe52-133">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="9fe52-134">若要取得 **PSCredential** 物件，請使用 Get-credential Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9fe52-134">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="9fe52-135">如需詳細資訊，請鍵入 `Get-Help Get-Credential`。</span><span class="sxs-lookup"><span data-stu-id="9fe52-135">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fe52-136">-JobName</span><span class="sxs-lookup"><span data-stu-id="9fe52-136">-JobName</span></span>
<span data-ttu-id="9fe52-137">指定工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="9fe52-137">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="9fe52-138">如果您指定這個參數，Cmdlet 就會當做一個工作執行，而且它會傳回 **Job** 物件。</span><span class="sxs-lookup"><span data-stu-id="9fe52-138">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="9fe52-139">根據預設，Windows PowerShell 會指派名稱 JobN，其中 N 是整數。</span><span class="sxs-lookup"><span data-stu-id="9fe52-139">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="9fe52-140">如果您指定 *Wait* 參數，請不要指定此參數。</span><span class="sxs-lookup"><span data-stu-id="9fe52-140">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9fe52-141">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9fe52-141">-ThrottleLimit</span></span>
<span data-ttu-id="9fe52-142">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="9fe52-142">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="9fe52-143">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="9fe52-143">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="9fe52-144">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="9fe52-144">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="9fe52-145">-Wait</span><span class="sxs-lookup"><span data-stu-id="9fe52-145">-Wait</span></span>
<span data-ttu-id="9fe52-146">指出此 Cmdlet 會封鎖主控台，直到完成所有設定工作為止。</span><span class="sxs-lookup"><span data-stu-id="9fe52-146">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="9fe52-147">如果您指定此參數，請不要指定 *JobName* 參數。</span><span class="sxs-lookup"><span data-stu-id="9fe52-147">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="9fe52-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9fe52-148">-Confirm</span></span>
<span data-ttu-id="9fe52-149">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="9fe52-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9fe52-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9fe52-150">-WhatIf</span></span>
<span data-ttu-id="9fe52-151">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9fe52-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9fe52-152">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="9fe52-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9fe52-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9fe52-153">CommonParameters</span></span>
<span data-ttu-id="9fe52-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9fe52-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9fe52-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9fe52-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9fe52-156">輸入</span><span class="sxs-lookup"><span data-stu-id="9fe52-156">INPUTS</span></span>

## <span data-ttu-id="9fe52-157">輸出</span><span class="sxs-lookup"><span data-stu-id="9fe52-157">OUTPUTS</span></span>

## <span data-ttu-id="9fe52-158">注意</span><span class="sxs-lookup"><span data-stu-id="9fe52-158">NOTES</span></span>

## <span data-ttu-id="9fe52-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="9fe52-159">RELATED LINKS</span></span>

[<span data-ttu-id="9fe52-160">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="9fe52-160">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="9fe52-161">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fe52-161">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="9fe52-162">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="9fe52-162">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="9fe52-163">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fe52-163">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="9fe52-164">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fe52-164">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="9fe52-165">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fe52-165">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="9fe52-166">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fe52-166">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
