---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203931"
---
# <span data-ttu-id="876c2-103">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="876c2-103">Start-DscConfiguration</span></span>

## <span data-ttu-id="876c2-104">概要</span><span class="sxs-lookup"><span data-stu-id="876c2-104">SYNOPSIS</span></span>
<span data-ttu-id="876c2-105">將組態套用至節點。</span><span class="sxs-lookup"><span data-stu-id="876c2-105">Applies configuration to nodes.</span></span>

## <span data-ttu-id="876c2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="876c2-106">SYNTAX</span></span>

### <span data-ttu-id="876c2-107">ComputerNameAndPathSet (預設) </span><span class="sxs-lookup"><span data-stu-id="876c2-107">ComputerNameAndPathSet (Default)</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="876c2-108">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="876c2-108">CimSessionAndPathSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="876c2-109">ComputerNameAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="876c2-109">ComputerNameAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="876c2-110">CimSessionAndUseExistingSet</span><span class="sxs-lookup"><span data-stu-id="876c2-110">CimSessionAndUseExistingSet</span></span>

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="876c2-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="876c2-111">DESCRIPTION</span></span>
<span data-ttu-id="876c2-112">**Start-DscConfiguration** Cmdlet 會將組態套用至節點。</span><span class="sxs-lookup"><span data-stu-id="876c2-112">The **Start-DscConfiguration** cmdlet applies configuration to nodes.</span></span>
<span data-ttu-id="876c2-113">搭配 *UseExisting* 參數使用時，會套用目的電腦上的現有設定。</span><span class="sxs-lookup"><span data-stu-id="876c2-113">When used with the *UseExisting* parameter, the existing configuration on the target computer is applied.</span></span>
<span data-ttu-id="876c2-114">藉由指定電腦名稱稱或使用通用訊息模型 (CIM) 會話，指定您想要將設定套用到哪些電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-114">Specify which computers that you want to apply configuration to by specifying computer names or by using Common Information Model (CIM) sessions.</span></span>

<span data-ttu-id="876c2-115">根據預設，此 Cmdlet 會建立工作，並傳回 **Job** 物件。</span><span class="sxs-lookup"><span data-stu-id="876c2-115">By default, this cmdlet creates a job and returns a **Job** object.</span></span>
<span data-ttu-id="876c2-116">如需背景工作的詳細資訊，請輸入 `Get-Help about_Jobs` 。</span><span class="sxs-lookup"><span data-stu-id="876c2-116">For more information about background jobs, type `Get-Help about_Jobs`.</span></span>
<span data-ttu-id="876c2-117">若要以互動方式使用此 Cmdlet，請指定 *Wait* 參數。</span><span class="sxs-lookup"><span data-stu-id="876c2-117">To use this cmdlet interactively, specify the *Wait* parameter.</span></span>

<span data-ttu-id="876c2-118">指定 *Verbose* 參數，以查看此 Cmdlet 在套用組態設定時如何運作的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="876c2-118">Specify the *Verbose* parameter to see details of what the cmdlet does when it applies configuration settings.</span></span>

## <span data-ttu-id="876c2-119">範例</span><span class="sxs-lookup"><span data-stu-id="876c2-119">EXAMPLES</span></span>

### <span data-ttu-id="876c2-120">範例1：套用設定</span><span class="sxs-lookup"><span data-stu-id="876c2-120">Example 1: Apply configuration settings</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

<span data-ttu-id="876c2-121">此命令會將組態設定從 C:\DSC\Configurations\ 套用至該資料夾中包含設定的每部電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-121">This command applies the configuration settings from C:\DSC\Configurations\ to the every computer that has settings in that folder.</span></span>
<span data-ttu-id="876c2-122">此命令會為所部署的每個目標節點，傳回 **Job** 物件。</span><span class="sxs-lookup"><span data-stu-id="876c2-122">The command returns **Job** objects for each target node deployed to.</span></span>

### <span data-ttu-id="876c2-123">範例2：套用設定並等候設定完成</span><span class="sxs-lookup"><span data-stu-id="876c2-123">Example 2: Apply configuration settings and wait for configuration to complete</span></span>

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

<span data-ttu-id="876c2-124">此命令會將組態從 C:\DSC\Configurations\ 套用到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-124">This command applies the configuration from C:\DSC\Configurations\ to the local computer.</span></span>
<span data-ttu-id="876c2-125">此命令會為所部署的每個目標節點，傳回 **Job** 物件，在此案例中，只有本機電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-125">The command returns **Job** objects for each target node deployed to, in this case, just the local computer.</span></span>
<span data-ttu-id="876c2-126">這個範例會指定 *Verbose* 參數。</span><span class="sxs-lookup"><span data-stu-id="876c2-126">This example specifies the *Verbose* parameter.</span></span>
<span data-ttu-id="876c2-127">因此，此命令會在繼續進行時，將訊息傳送至主控台。</span><span class="sxs-lookup"><span data-stu-id="876c2-127">Therefore, the command sends messages to the console as it proceeds.</span></span>
<span data-ttu-id="876c2-128">此命令包含 *Wait* 參數。</span><span class="sxs-lookup"><span data-stu-id="876c2-128">The command includes the *Wait* parameter.</span></span>
<span data-ttu-id="876c2-129">因此，您無法使用主控台，直到命令完成所有設定工作。</span><span class="sxs-lookup"><span data-stu-id="876c2-129">Therefore, you cannot use the console until the command finishes all configuration tasks.</span></span>

### <span data-ttu-id="876c2-130">範例3：使用 CIM 會話套用設定設定</span><span class="sxs-lookup"><span data-stu-id="876c2-130">Example 3: Apply configuration settings by using a CIM session</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

<span data-ttu-id="876c2-131">這個範例會將組態設定套用至指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-131">This example applies configuration settings to a specified computer.</span></span>
<span data-ttu-id="876c2-132">這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="876c2-132">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="876c2-133">或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-133">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="876c2-134">第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="876c2-134">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="876c2-135">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="876c2-135">The command prompts you for a password.</span></span>
<span data-ttu-id="876c2-136">如需詳細資訊，請鍵入 `Get-Help NewCimSession`。</span><span class="sxs-lookup"><span data-stu-id="876c2-136">For more information, type `Get-Help NewCimSession`.</span></span>

<span data-ttu-id="876c2-137">第二個命令會將設定從 C:\dsc\configurations\ 套用套用至儲存在 $Session 變數中的 **CimSession** 物件所識別的電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-137">The second command applies the configuration settings from C:\DSC\Configurations\ to the computers identified by the **CimSession** objects stored in the $Session variable.</span></span>
<span data-ttu-id="876c2-138">在這個範例中，$Session 變數對於名為 Server01 的電腦，僅包含 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="876c2-138">In this example, the $Session variable contains a CIM session only for the computer named Server01.</span></span>
<span data-ttu-id="876c2-139">此命令會套用該組態。</span><span class="sxs-lookup"><span data-stu-id="876c2-139">The command applies the configuration.</span></span>
<span data-ttu-id="876c2-140">此命令會為每部已設定的電腦建立 **Job** 物件。</span><span class="sxs-lookup"><span data-stu-id="876c2-140">The command creates **Job** objects for each configured computer.</span></span>

## <span data-ttu-id="876c2-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="876c2-141">PARAMETERS</span></span>

### <span data-ttu-id="876c2-142">-CimSession</span><span class="sxs-lookup"><span data-stu-id="876c2-142">-CimSession</span></span>
<span data-ttu-id="876c2-143">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="876c2-143">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="876c2-144">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="876c2-144">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="876c2-145">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="876c2-145">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="876c2-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="876c2-146">-ComputerName</span></span>
<span data-ttu-id="876c2-147">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="876c2-147">Specifies an array of computer names.</span></span>
<span data-ttu-id="876c2-148">此參數會將 *路徑* 參數中具有設定檔的電腦限制為數組中指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-148">This parameter restricts the computers that have configuration documents in the *Path* parameter to those specified in the array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="876c2-149">-Credential</span><span class="sxs-lookup"><span data-stu-id="876c2-149">-Credential</span></span>
<span data-ttu-id="876c2-150">指定目標電腦的使用者名稱和密碼，做為 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="876c2-150">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="876c2-151">若要取得 **PSCredential** 物件，請使用 Get-credential Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="876c2-151">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="876c2-152">如需詳細資訊，請鍵入 `Get-Help Get-Credential`。</span><span class="sxs-lookup"><span data-stu-id="876c2-152">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="876c2-153">-Force</span><span class="sxs-lookup"><span data-stu-id="876c2-153">-Force</span></span>
<span data-ttu-id="876c2-154">停止目的電腦上目前正在執行的設定作業，並開始新的 Start-Configuration 作業。</span><span class="sxs-lookup"><span data-stu-id="876c2-154">Stops the configuration operation currently running on the target computer and begins the new Start-Configuration operation.</span></span>
<span data-ttu-id="876c2-155">如果本機 Configuration Manager 的 **RefreshMode** 屬性設定為 **Pull** ，則指定此參數會將它變更為 **Push** 。</span><span class="sxs-lookup"><span data-stu-id="876c2-155">If the **RefreshMode** property of the Local Configuration Manager is set to **Pull** , specifying this parameter changes it to **Push** .</span></span>

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

### <span data-ttu-id="876c2-156">-JobName</span><span class="sxs-lookup"><span data-stu-id="876c2-156">-JobName</span></span>
<span data-ttu-id="876c2-157">指定工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="876c2-157">Specifies a friendly name for a job.</span></span>
<span data-ttu-id="876c2-158">如果您指定這個參數，Cmdlet 就會當做一個工作執行，而且它會傳回 **Job** 物件。</span><span class="sxs-lookup"><span data-stu-id="876c2-158">If you specify this parameter, the cmdlet runs as a job, and it returns a **Job** object.</span></span>

<span data-ttu-id="876c2-159">根據預設，Windows PowerShell 會指派名稱 JobN，其中 N 是整數。</span><span class="sxs-lookup"><span data-stu-id="876c2-159">By default, Windows PowerShell assigns the name JobN where N is an integer.</span></span>

<span data-ttu-id="876c2-160">如果您指定 *Wait* 參數，請不要指定此參數。</span><span class="sxs-lookup"><span data-stu-id="876c2-160">If you specify the *Wait* parameter, do not specify this parameter.</span></span>

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

### <span data-ttu-id="876c2-161">-Path</span><span class="sxs-lookup"><span data-stu-id="876c2-161">-Path</span></span>
<span data-ttu-id="876c2-162">指定包含組態設定檔之資料夾的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="876c2-162">Specifies a file path of a folder that contains configuration settings files.</span></span>
<span data-ttu-id="876c2-163">此 Cmdlet 會發佈這些設定，並將這些設定套用到在指定路徑中具有設定檔案的電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-163">This cmdlet publishes and applies these configuration settings to computers that have settings files in the specified path.</span></span>
<span data-ttu-id="876c2-164">每個目標節點都必須具有下列格式的設定檔： NetBIOS 名稱. mof。</span><span class="sxs-lookup"><span data-stu-id="876c2-164">Each target node must have a settings file of the following format: NetBIOS Name.mof.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="876c2-165">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="876c2-165">-ThrottleLimit</span></span>
<span data-ttu-id="876c2-166">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="876c2-166">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="876c2-167">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="876c2-167">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="876c2-168">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="876c2-168">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="876c2-169">-UseExisting</span><span class="sxs-lookup"><span data-stu-id="876c2-169">-UseExisting</span></span>
<span data-ttu-id="876c2-170">指出此 Cmdlet 會套用現有的設定。</span><span class="sxs-lookup"><span data-stu-id="876c2-170">Indicates that this cmdlet applies the existing configuration.</span></span>
<span data-ttu-id="876c2-171">設定可以存在於目的電腦上，方法是使用 **update-dscconfiguration** 或使用 Publish-DscConfiguration Cmdlet 的發行集制定。</span><span class="sxs-lookup"><span data-stu-id="876c2-171">The configuration can exist on the target computer by enactment using **Start-DscConfiguration** or by publication using the Publish-DscConfiguration cmdlet.</span></span>

<span data-ttu-id="876c2-172">在您為此 Cmdlet 指定此參數之前，請先參閱[Windows PowerShell 5.0 的新功能](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)中的資訊。</span><span class="sxs-lookup"><span data-stu-id="876c2-172">Before you specify this parameter for this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="876c2-173">-Wait</span><span class="sxs-lookup"><span data-stu-id="876c2-173">-Wait</span></span>
<span data-ttu-id="876c2-174">指出此 Cmdlet 會封鎖主控台，直到完成所有設定工作為止。</span><span class="sxs-lookup"><span data-stu-id="876c2-174">Indicates that the cmdlet blocks the console until it finishes all configuration tasks.</span></span>

<span data-ttu-id="876c2-175">如果您指定此參數，請不要指定 *JobName* 參數。</span><span class="sxs-lookup"><span data-stu-id="876c2-175">If you specify this parameter, do not specify the *JobName* parameter.</span></span>

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

### <span data-ttu-id="876c2-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="876c2-176">-Confirm</span></span>
<span data-ttu-id="876c2-177">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="876c2-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="876c2-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="876c2-178">-WhatIf</span></span>
<span data-ttu-id="876c2-179">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="876c2-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="876c2-180">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="876c2-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="876c2-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="876c2-181">CommonParameters</span></span>
<span data-ttu-id="876c2-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="876c2-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="876c2-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="876c2-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="876c2-184">輸入</span><span class="sxs-lookup"><span data-stu-id="876c2-184">INPUTS</span></span>

## <span data-ttu-id="876c2-185">輸出</span><span class="sxs-lookup"><span data-stu-id="876c2-185">OUTPUTS</span></span>

## <span data-ttu-id="876c2-186">注意</span><span class="sxs-lookup"><span data-stu-id="876c2-186">NOTES</span></span>

## <span data-ttu-id="876c2-187">相關連結</span><span class="sxs-lookup"><span data-stu-id="876c2-187">RELATED LINKS</span></span>

[<span data-ttu-id="876c2-188">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="876c2-188">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="876c2-189">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="876c2-189">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="876c2-190">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="876c2-190">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="876c2-191">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="876c2-191">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="876c2-192">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="876c2-192">Stop-DscConfiguration</span></span>](Stop-DscConfiguration.md)

[<span data-ttu-id="876c2-193">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="876c2-193">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="876c2-194">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="876c2-194">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)
