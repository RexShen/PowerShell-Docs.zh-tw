---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203075"
---
# <span data-ttu-id="189a2-103">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="189a2-103">Test-DscConfiguration</span></span>

## <span data-ttu-id="189a2-104">概要</span><span class="sxs-lookup"><span data-stu-id="189a2-104">SYNOPSIS</span></span>
<span data-ttu-id="189a2-105">測試節點上的實際設定是否符合預期設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-105">Tests whether the actual configuration on the nodes matches the desired configuration.</span></span>

## <span data-ttu-id="189a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="189a2-106">SYNTAX</span></span>

### <span data-ttu-id="189a2-107">ComputerNameSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="189a2-107">ComputerNameSet (Default)</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### <span data-ttu-id="189a2-108">ComputerNameAndPathSet</span><span class="sxs-lookup"><span data-stu-id="189a2-108">ComputerNameAndPathSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="189a2-109">ComputerNameAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="189a2-109">ComputerNameAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="189a2-110">CimSessionAndPathSet</span><span class="sxs-lookup"><span data-stu-id="189a2-110">CimSessionAndPathSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="189a2-111">CimSessionAndReferenceConfigurationSet</span><span class="sxs-lookup"><span data-stu-id="189a2-111">CimSessionAndReferenceConfigurationSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### <span data-ttu-id="189a2-112">CimSessionSet</span><span class="sxs-lookup"><span data-stu-id="189a2-112">CimSessionSet</span></span>

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## <span data-ttu-id="189a2-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="189a2-113">DESCRIPTION</span></span>
<span data-ttu-id="189a2-114">**Test-DscConfiguration** Cmdlet 會測試節點上的實際設定是否符合預期設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-114">The **Test-DscConfiguration** cmdlet tests whether the actual configuration on the nodes matches the desired configuration.</span></span>
<span data-ttu-id="189a2-115">使用電腦名稱或通用訊息模型 (CIM) 工作階段，來指定您想要測試設定的電腦。</span><span class="sxs-lookup"><span data-stu-id="189a2-115">Specify which computers for which you want to test configurations by using computer names or Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="189a2-116">如果您沒有指定目標電腦，此 Cmdlet 會測試本機電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-116">If you do not specify a target computer, the cmdlet tests configuration of the local computer.</span></span>

<span data-ttu-id="189a2-117">如果所需的與實際設定相符，此 Cmdlet 會傳回字串值 ' True '。</span><span class="sxs-lookup"><span data-stu-id="189a2-117">If the desired and actual configurations match, the cmdlet returns a string value of 'True'.</span></span>
<span data-ttu-id="189a2-118">否則，它會傳回字串值 ' False '。</span><span class="sxs-lookup"><span data-stu-id="189a2-118">Otherwise, it returns a string value of 'False'.</span></span>

## <span data-ttu-id="189a2-119">範例</span><span class="sxs-lookup"><span data-stu-id="189a2-119">EXAMPLES</span></span>

### <span data-ttu-id="189a2-120">範例 1：測試本機電腦的設定</span><span class="sxs-lookup"><span data-stu-id="189a2-120">Example 1: Test configuration for the local computer</span></span>

```
PS C:\> Test-DscConfiguration
```

<span data-ttu-id="189a2-121">此命令會測試本機電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-121">This command tests configuration for the local computer.</span></span>

### <span data-ttu-id="189a2-122">範例 2：測試指定電腦的設定</span><span class="sxs-lookup"><span data-stu-id="189a2-122">Example 2: Test configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

<span data-ttu-id="189a2-123">這個範例會測試 CIM 工作階段所指定之電腦上的設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-123">This example test configuration from a computer specified by a CIM session.</span></span>
<span data-ttu-id="189a2-124">這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="189a2-124">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="189a2-125">或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="189a2-125">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="189a2-126">第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="189a2-126">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="189a2-127">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="189a2-127">The command prompts you for a password.</span></span>
<span data-ttu-id="189a2-128">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="189a2-128">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="189a2-129">第二個命令會測試以 $Session 變數儲存的 **CimSession** 物件所識別之電腦的設定，在此案例中是名為 Server01 的電腦。</span><span class="sxs-lookup"><span data-stu-id="189a2-129">The second command tests configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

### <span data-ttu-id="189a2-130">範例 3︰測試設定並提供詳細的結果</span><span class="sxs-lookup"><span data-stu-id="189a2-130">Example 3: Test configurations with detailed results</span></span>

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

<span data-ttu-id="189a2-131">此命令會針對 *ComputerName* 參數所指定一組電腦測試設定並傳回詳細資訊，包括整體狀態、處於預期狀態的資源、未處於預期狀態的資源及電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="189a2-131">This command tests configurations for a set of computers specified by the *ComputerName* parameter and returns detailed information that includes the overall state, resources that are in the desired state, resources that are not in the desired state and computer name.</span></span>

### <span data-ttu-id="189a2-132">範例 4：測試資料夾中指定的設定</span><span class="sxs-lookup"><span data-stu-id="189a2-132">Example 4: Test configurations specified in a folder</span></span>

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

<span data-ttu-id="189a2-133">此命令會測試 *Path* 參數所指定資料夾中定義的設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-133">This command tests configurations that are defined in a folder specified by the *Path* parameter.</span></span>
<span data-ttu-id="189a2-134">設定都是針對一組電腦進行測試，每一個都是依設定檔的檔案名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="189a2-134">The configurations are tested against a set of computers, each identified by the file name of the configuration file.</span></span>

### <span data-ttu-id="189a2-135">範例 5：測試檔案中指定的設定</span><span class="sxs-lookup"><span data-stu-id="189a2-135">Example 5: Test configurations specified in a file</span></span>

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

<span data-ttu-id="189a2-136">此命令會根據 *ComputerName* 參數所指定的一組電腦，來測試檔案中定義的設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-136">This command tests a configuration defined in a file against a set of computers specified by the *ComputerName* parameter.</span></span>

## <span data-ttu-id="189a2-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="189a2-137">PARAMETERS</span></span>

### <span data-ttu-id="189a2-138">-AsJob</span><span class="sxs-lookup"><span data-stu-id="189a2-138">-AsJob</span></span>
<span data-ttu-id="189a2-139">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="189a2-139">Indicates that this cmdlet runs the command as a background job.</span></span>

<span data-ttu-id="189a2-140">如果您指定 *AsJob* 參數，此命令就會傳回代表工作的物件，然後顯示命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="189a2-140">If you specify the *AsJob* parameter, the command returns an object that represents the job, and then displays the command prompt.</span></span>
<span data-ttu-id="189a2-141">您可以繼續在工作階段中運作，直到工作完成。</span><span class="sxs-lookup"><span data-stu-id="189a2-141">You can continue to work in the session until the job finishes.</span></span>
<span data-ttu-id="189a2-142">工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="189a2-142">The job is created on the local computer and the results from remote computers are automatically returned to the local computer.</span></span>
<span data-ttu-id="189a2-143">若要管理工作，請使用各項 Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="189a2-143">To manage the job, use the Job cmdlets.</span></span>
<span data-ttu-id="189a2-144">若要取得工作結果，請使用 Receive-Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="189a2-144">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="189a2-145">若要使用這個參數，本機電腦和遠端電腦必須針對遠端執行功能進行設定，並且在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以系統管理員身分執行] 選項來開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="189a2-145">To use this parameter, the local and remote computers must be configured for remoting, and on Windows Vista and later versions of the Windows operating system, you must open Windows PowerShell with the Run as administrator option.</span></span>
<span data-ttu-id="189a2-146">如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="189a2-146">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

<span data-ttu-id="189a2-147">如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="189a2-147">For more information about Windows PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="189a2-148">-CimSession</span><span class="sxs-lookup"><span data-stu-id="189a2-148">-CimSession</span></span>
<span data-ttu-id="189a2-149">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="189a2-149">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="189a2-150">輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="189a2-150">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="189a2-151">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="189a2-151">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="189a2-152">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="189a2-152">-ComputerName</span></span>
<span data-ttu-id="189a2-153">指定此 Cmdlet 測試設定所在的電腦名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="189a2-153">Specifies an array of computer names on which this cmdlet tests the configuration.</span></span>
<span data-ttu-id="189a2-154">此 Cmdlet 會在 *Path* 參數所指定的位置中，對這些電腦測試設定文件。</span><span class="sxs-lookup"><span data-stu-id="189a2-154">The cmdlet tests the configuration document in the location specified by the *Path* parameter to these computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="189a2-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="189a2-155">-Credential</span></span>
<span data-ttu-id="189a2-156">指定目標電腦的使用者名稱和密碼，做為 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="189a2-156">Specifies a user name and password, as a **PSCredential** object, for the target computer.</span></span>
<span data-ttu-id="189a2-157">若要取得 **PSCredential** 物件，請使用 Get-credential Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="189a2-157">To obtain a **PSCredential** object, use the Get-Credential cmdlet.</span></span>
<span data-ttu-id="189a2-158">如需詳細資訊，請鍵入 `Get-Help Get-Credential`。</span><span class="sxs-lookup"><span data-stu-id="189a2-158">For more information, type `Get-Help Get-Credential`.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="189a2-159">-Detailed</span><span class="sxs-lookup"><span data-stu-id="189a2-159">-Detailed</span></span>
<span data-ttu-id="189a2-160">指出此 Cmdlet 會傳回比較設定文件與節點預期狀態的詳細結果。</span><span class="sxs-lookup"><span data-stu-id="189a2-160">Indicates that this cmdlet returns a detailed result of comparing the configuration document with the desired state of the nodes.</span></span>
<span data-ttu-id="189a2-161">結果包括整體狀態、處於預期狀態的資源、未處於預期狀態的資源，以及電腦名稱等資訊。</span><span class="sxs-lookup"><span data-stu-id="189a2-161">The result includes information such as overall state, resources that are in the desired state, resources that are not in desired state, and computer name.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="189a2-162">-Path</span><span class="sxs-lookup"><span data-stu-id="189a2-162">-Path</span></span>
<span data-ttu-id="189a2-163">指定包含設定文件檔的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="189a2-163">Specifies the path of a folder that contains configuration document files.</span></span>
<span data-ttu-id="189a2-164">此 Cmdlet 會針對 *ComputerName* 或 *CimSession* 參數所指定的電腦預期狀態測試設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-164">The cmdlet tests the configuration against the desired state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="189a2-165">-ReferenceConfiguration</span><span class="sxs-lookup"><span data-stu-id="189a2-165">-ReferenceConfiguration</span></span>
<span data-ttu-id="189a2-166">指定設定文件檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="189a2-166">Specifies the path of the configuration document file.</span></span>
<span data-ttu-id="189a2-167">此 Cmdlet 會針對 *ComputerName* 或 *CimSession* 參數所指定的電腦實際狀態測試設定。</span><span class="sxs-lookup"><span data-stu-id="189a2-167">This cmdlet tests the configuration against the actual state of computers specified by the *ComputerName* or *CimSession* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="189a2-168">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="189a2-168">-ThrottleLimit</span></span>
<span data-ttu-id="189a2-169">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="189a2-169">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="189a2-170">如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。</span><span class="sxs-lookup"><span data-stu-id="189a2-170">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="189a2-171">節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="189a2-171">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="189a2-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="189a2-172">CommonParameters</span></span>
<span data-ttu-id="189a2-173">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="189a2-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="189a2-174">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="189a2-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="189a2-175">輸入</span><span class="sxs-lookup"><span data-stu-id="189a2-175">INPUTS</span></span>

## <span data-ttu-id="189a2-176">輸出</span><span class="sxs-lookup"><span data-stu-id="189a2-176">OUTPUTS</span></span>

## <span data-ttu-id="189a2-177">注意</span><span class="sxs-lookup"><span data-stu-id="189a2-177">NOTES</span></span>

## <span data-ttu-id="189a2-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="189a2-178">RELATED LINKS</span></span>

[<span data-ttu-id="189a2-179">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="189a2-179">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="189a2-180">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="189a2-180">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="189a2-181">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="189a2-181">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="189a2-182">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="189a2-182">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="189a2-183">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="189a2-183">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)
