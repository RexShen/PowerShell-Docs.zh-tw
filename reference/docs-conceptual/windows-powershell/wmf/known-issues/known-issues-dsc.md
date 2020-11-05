---
ms.date: 06/12/2017
title: 預期狀態設定 (DSC) 的已知問題和限制
description: Windows PowerShell 5.x 中 DSC 的已知問題與限制
ms.openlocfilehash: 1163ed9e130430f6bbca98405a8993bb054dd1a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662045"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="f4ae0-103">預期狀態設定 (DSC) 的已知問題和限制</span><span class="sxs-lookup"><span data-stu-id="f4ae0-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="f4ae0-104">重大變更：用來加密/解密 DSC 設定密碼的憑證，在安裝 WMF 5.0 RTM 之後可能無法運作</span><span class="sxs-lookup"><span data-stu-id="f4ae0-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="f4ae0-105">在 WMF 4.0 和 WMF 5.0 Preview 版本中，DSC 不允許組態中的密碼長度超過 121 個字元。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="f4ae0-106">DSC 已強制使用短密碼，即使需要冗長的強式密碼亦同。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="f4ae0-107">這項重大變更允許 DSC 組態中的密碼為任意長度。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="f4ae0-108">**解決方案：** 以 [資料編密] 或 [金鑰編密] 的金鑰使用方式，與 [文件加密增強] 金鑰使用方式 (1.3.6.1.4.1.311.80.1) 重新建立憑證。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="f4ae0-109">如需詳細資訊，請參閱 [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="f4ae0-110">DSC Cmdlet 在安裝 WMF 5.0 RTM 之後可能會失敗</span><span class="sxs-lookup"><span data-stu-id="f4ae0-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="f4ae0-111">`Start-DscConfiguration` 和其他 DSC Cmdlet 可能會在安裝 WMF 5.0 RTM 之後失敗，並傳回下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="f4ae0-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="f4ae0-112">**解決方案：** 在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令來刪除 DSCEngineCache.mof︰</span><span class="sxs-lookup"><span data-stu-id="f4ae0-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="f4ae0-113">如果 WMF 5.0 RTM 安裝在 WMF 5.0 Production Preview 之上，DSC Cmdlet 就有可能無法運作</span><span class="sxs-lookup"><span data-stu-id="f4ae0-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="f4ae0-114">**解決方案：** 在提高權限的 PowerShell 工作階段 (以系統管理員身分執行) 中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="f4ae0-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="f4ae0-115">在 DebugMode 中使用 Get-DscConfiguration 時，LCM 可能會陷入不穩定的狀態</span><span class="sxs-lookup"><span data-stu-id="f4ae0-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="f4ae0-116">如果 LCM 處於 DebugMode，按下 CTRL+C 以停止處理 `Get-DscConfiguration`，可能會造成 LCM 進入不穩定狀態，而使得大部分的 DSC Cmdlet 都將無法運作。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won't work.</span></span>

<span data-ttu-id="f4ae0-117">**解決方案：** 對 `Get-DscConfiguration` Cmdlet 進行偵錯時，請勿按下 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-117">**Resolution:** Don't press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="f4ae0-118">Stop-DscConfiguration 在 DebugMode 中可能不會回應</span><span class="sxs-lookup"><span data-stu-id="f4ae0-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="f4ae0-119">如果 LCM 處於 DebugMode，則嘗試停止 `Get-DscConfiguration` 所啟動的作業時，`Stop-DscConfiguration` 可能不會回應</span><span class="sxs-lookup"><span data-stu-id="f4ae0-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="f4ae0-120">**解決方案：** 完成對 `Get-DscConfiguration` 所啟動的作業進行偵錯，如 [偵錯 DSC 資源](/powershell/scripting/dsc/troubleshooting/debugResource)中所述。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="f4ae0-121">在 DebugMode 中不顯示詳細的錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="f4ae0-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="f4ae0-122">如果 LCM 處於 **DebugMode** ，則 DSC 資源不會顯示詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-122">If LCM is in **DebugMode** , no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="f4ae0-123">**解決方案：** 停用 **DebugMode** 以查看資源中的詳細訊息</span><span class="sxs-lookup"><span data-stu-id="f4ae0-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="f4ae0-124">DscConfigurationStatus Cmdlet 無法擷取 Invoke-DscResource 作業</span><span class="sxs-lookup"><span data-stu-id="f4ae0-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="f4ae0-125">使用 `Invoke-DscResource` Cmdlet 直接叫用任何資源的方法之後，就無法透過 `Get-DscConfigurationStatus` 擷取這類作業的記錄。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource's methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="f4ae0-126">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="f4ae0-127">Get-DscConfigurationStatus 傳回提取循環作業，作為類型 **一致性**</span><span class="sxs-lookup"><span data-stu-id="f4ae0-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="f4ae0-128">將節點設定為 PULL 重新整理模式時，對於每個執行的提取作業，`Get-DscConfigurationStatus` Cmdlet 會將作業類型報告為 **一致性** ，而非「初始」  。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="f4ae0-129">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="f4ae0-130">Invoke-DscResource Cmdlet 不會以這些作業所產生的順序傳回訊息</span><span class="sxs-lookup"><span data-stu-id="f4ae0-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="f4ae0-131">`Invoke-DscResource` Cmdlet 不會以 LCM 或 DSC 資源產生它們的順序來傳回詳細資訊、警告和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="f4ae0-132">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="f4ae0-133">以 Invoke-DscResource 使用 DSC 資源時，無法輕易偵錯 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="f4ae0-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="f4ae0-134">當 LCM 在偵錯模式中執行時，`Invoke-DscResource` Cmdlet 不會提供要連線以進行偵錯的 Runspace 相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="f4ae0-135">如需詳細資訊，請參閱[偵錯 DSC 資源](/powershell/scripting/dsc/troubleshooting/debugResource)。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="f4ae0-136">**解決方案：** 使用 `Get-PSHostProcessInfo`、`Enter-PSHostProcess`、`Get-Runspace` 及 `Debug-Runspace` Cmdlet 來探索並附加至 Runspace，以對 DSC 資源進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="f4ae0-137">相同節點的各種部分組態文件不能有相同的資源名稱</span><span class="sxs-lookup"><span data-stu-id="f4ae0-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="f4ae0-138">對於部署到單一節點上的多個部分組態，相同的資源名稱會造成執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="f4ae0-139">**解決方案：** 在不同的部分設定中使用不同資源名稱 (即使是相同的資源)。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="f4ae0-140">Start-DscConfiguration –UseExisting 無法使用 -Credential</span><span class="sxs-lookup"><span data-stu-id="f4ae0-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="f4ae0-141">搭配 **UseExisting** 參數使用 `Start-DscConfiguration` 時，會忽略 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="f4ae0-142">DSC 會使用預設處理序身分識別，繼續作業；</span><span class="sxs-lookup"><span data-stu-id="f4ae0-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="f4ae0-143">而如果在遠端節點上繼續作業時需要不同的認證，這樣做會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="f4ae0-144">**解決方案：** 使用遠端 DSC 作業的 CIM 工作階段︰</span><span class="sxs-lookup"><span data-stu-id="f4ae0-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="f4ae0-145">以 IPv6 位址作為 DSC 組態中的節點名稱</span><span class="sxs-lookup"><span data-stu-id="f4ae0-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="f4ae0-146">在此版本中，不支援以 IPv6 位址作為 DSC 組態指令碼中的節點名稱。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="f4ae0-147">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="f4ae0-148">對 `Class-Based` DSC 資源進行偵錯</span><span class="sxs-lookup"><span data-stu-id="f4ae0-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="f4ae0-149">在此版本中，不支援以類別為基礎的 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="f4ae0-150">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="f4ae0-151">在 DSC 以類別為基礎之資源的 $script 範圍中定義的變數和函式，不會在對 DSC 資源的多個呼叫之間保留</span><span class="sxs-lookup"><span data-stu-id="f4ae0-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="f4ae0-152">如果設定使用任何以類別為基礎的資源，且該資源具有 `$script` 範圍中定義的變數或函式時，對 `Start-DSCConfiguration` 的多個連續呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="f4ae0-153">**解決方案：** 在 DSC 資源類別本身中定義所有變數和函式。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="f4ae0-154">沒有 `$script` 範圍變數/函式。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="f4ae0-155">當資源正在使用 PSDscRunAsCredential 時偵錯 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="f4ae0-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="f4ae0-156">在此版本中，當資源正在使用設定中的 **PSDscRunAsCredential** 屬性時，不支援 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="f4ae0-157">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="f4ae0-158">對於 DSC 複合資源不支援 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f4ae0-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="f4ae0-159">**解決方案：** 使用 Credential 屬性 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="f4ae0-160">範例 ServiceSet 和 WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="f4ae0-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="f4ae0-161">Get-DscResource-Syntax 並未正確反映 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f4ae0-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="f4ae0-162">當資源將 **PsDscRunAsCredential** 標記為強制或不支援它時， **Syntax** 參數就不會正確反映它。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="f4ae0-163">**解決方案：** 無。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-163">**Resolution:** None.</span></span> <span data-ttu-id="f4ae0-164">不過，使用 IntelliSense 時，在 ISE 中撰寫設定會反映有關 **PsDscRunAsCredential** 屬性的正確中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="f4ae0-165">WindowsOptionalFeature 不適用於 Windows 7</span><span class="sxs-lookup"><span data-stu-id="f4ae0-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="f4ae0-166">**WindowsOptionalFeature** DSC 資源不適用於 Windows 7。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="f4ae0-167">此資源需要 DISM 模組，以及在 Windows 8 起和較新版本 Windows 作業系統中可用的 DISM Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="f4ae0-168">針對以類別為基礎的 DSC 資源，Import-DscResource -ModuleVersion 可能無法如預期般運作</span><span class="sxs-lookup"><span data-stu-id="f4ae0-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="f4ae0-169">如果編譯節點有多個以類別為基礎的 DSC 資源模組版本，`Import-DscResource -ModuleVersion` 就不會挑選指定的版本，並產生下列編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="f4ae0-170">**解決方案：** 藉由將 **ModuleSpecification** 物件定義為 **ModuleName** 參數，並指定 **RequiredVersion** 索引鍵來匯入所需的版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4ae0-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="f4ae0-171">某些像登錄資源這樣的 DSC 資源可能會啟動，花費較長的時間來處理要求。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="f4ae0-172">**解決方法 1：** 建立排程工作，定期清除下列資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="f4ae0-173">**解決方法 2：** 變更 DSC 設定，清除設定結尾的 *CommandAnalysis* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f4ae0-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
