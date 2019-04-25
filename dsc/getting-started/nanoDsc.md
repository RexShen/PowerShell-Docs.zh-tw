---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 在 Nano Server 上使用 DSC
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079722"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="d7ac1-103">在 Nano Server 上使用 DSC</span><span class="sxs-lookup"><span data-stu-id="d7ac1-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="d7ac1-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7ac1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d7ac1-105">您可以選用 Windows Server 2016 媒體上 `NanoServer\Packages` 資料夾中的 **Nano Server 上的 DSC** 封裝。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="d7ac1-106">當您建立 Nano Server 的 VHD 時，可以安裝此套件，方法是指定 **Microsoft-NanoServer-DSC-Package** 作為 **New-NanoServerImage** 函數中 **Packages** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="d7ac1-107">例如，如果要建立虛擬機器的 VHD，命令會如下所示︰</span><span class="sxs-lookup"><span data-stu-id="d7ac1-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="d7ac1-108">如需安裝及使用 Nano Server 以及如何透過 PowerShell 遠端來管理 Nano Server 的相關資訊，請參閱 [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (開始使用 Nano Server)。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="d7ac1-109">Nano Server 提供的 DSC 功能</span><span class="sxs-lookup"><span data-stu-id="d7ac1-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="d7ac1-110">相較於完整版的 Windows Server，Nano Server 僅支援一組有限的 API，所以目前 Nano Server 上的 DSC 和執行於完整 SKU 上的 DSC 相較，並不具備完整的同位功能。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="d7ac1-111">Nano Server 上的 DSC 正在開發中，功能還不夠完備。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="d7ac1-112">目前於 Nano Server 上提供的 DSC 功能如下︰</span><span class="sxs-lookup"><span data-stu-id="d7ac1-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="d7ac1-113">推入與提取模式</span><span class="sxs-lookup"><span data-stu-id="d7ac1-113">Both push and pull modes</span></span>

- <span data-ttu-id="d7ac1-114">完整版 Windows Server 的所有現有 DSC Cmdlet 包括︰</span><span class="sxs-lookup"><span data-stu-id="d7ac1-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="d7ac1-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d7ac1-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="d7ac1-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d7ac1-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="d7ac1-117">啟用-DscDebug</span><span class="sxs-lookup"><span data-stu-id="d7ac1-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="d7ac1-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="d7ac1-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="d7ac1-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="d7ac1-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="d7ac1-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="d7ac1-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="d7ac1-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="d7ac1-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="d7ac1-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7ac1-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="d7ac1-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="d7ac1-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="d7ac1-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d7ac1-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="d7ac1-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="d7ac1-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="d7ac1-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="d7ac1-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [<span data-ttu-id="d7ac1-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="d7ac1-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="d7ac1-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="d7ac1-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="d7ac1-132">編譯設定 (請參閱 [DSC 設定](../configurations/configurations.md))。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="d7ac1-133">**問題：** 密碼加密 (請參閱[保護 MOF 檔案](../pull-server/secureMOF.md)) 在設定編譯期間無法運作。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="d7ac1-134">編譯中繼設定 (請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="d7ac1-135">執行使用者內容下的資源 (請參閱[以使用者認證執行 DSC (RunAs)](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="d7ac1-136">類別型資源 (請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](../resources/authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](../resources/authoringResourceClass.md))</span></span>

- <span data-ttu-id="d7ac1-137">為 DSC 資源偵錯 (請參閱[為 DSC 資源偵錯](../troubleshooting/debugResource.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="d7ac1-138">**問題：** 如果資源使用 PsDscRunAsCredential 則無法運作 (請參閱[以使用者認證執行 DSC](../configurations/runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="d7ac1-139">指定節點之間的相依性</span><span class="sxs-lookup"><span data-stu-id="d7ac1-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="d7ac1-140">資源的版本管理</span><span class="sxs-lookup"><span data-stu-id="d7ac1-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="d7ac1-141">提取用戶端 (設定與資源) (請參閱[使用設定名稱設定提取用戶端](../pull-server/pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="d7ac1-142">部分設定 (提取與推送)</span><span class="sxs-lookup"><span data-stu-id="d7ac1-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="d7ac1-143">回報至提取伺服器</span><span class="sxs-lookup"><span data-stu-id="d7ac1-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="d7ac1-144">MOF 加密</span><span class="sxs-lookup"><span data-stu-id="d7ac1-144">MOF encryption</span></span>

- <span data-ttu-id="d7ac1-145">事件記錄</span><span class="sxs-lookup"><span data-stu-id="d7ac1-145">Event logging</span></span>

- <span data-ttu-id="d7ac1-146">Azure 自動化 DSC 報告</span><span class="sxs-lookup"><span data-stu-id="d7ac1-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="d7ac1-147">可完全正常運作的資源</span><span class="sxs-lookup"><span data-stu-id="d7ac1-147">Resources that are fully functional</span></span>

- <span data-ttu-id="d7ac1-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-148">**Archive**</span></span>
- <span data-ttu-id="d7ac1-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-149">**Environment**</span></span>
- <span data-ttu-id="d7ac1-150">**File**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-150">**File**</span></span>
- <span data-ttu-id="d7ac1-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-151">**Log**</span></span>
- <span data-ttu-id="d7ac1-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-152">**ProcessSet**</span></span>
- <span data-ttu-id="d7ac1-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-153">**Registry**</span></span>
- <span data-ttu-id="d7ac1-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-154">**Script**</span></span>
- <span data-ttu-id="d7ac1-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="d7ac1-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-156">**WindowsProcess**</span></span>
- <span data-ttu-id="d7ac1-157">**WaitForAll** (請參閱[指定跨節點相依性](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="d7ac1-158">**WaitForAny** (請參閱[指定跨節點相依性](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="d7ac1-159">**WaitForSome** (請參閱[指定跨節點相依性](../configurations/crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="d7ac1-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="d7ac1-160">部分運作的資源</span><span class="sxs-lookup"><span data-stu-id="d7ac1-160">Resources that are partially functional</span></span>
- <span data-ttu-id="d7ac1-161">**群組**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-161">**Group**</span></span>
- <span data-ttu-id="d7ac1-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-162">**GroupSet**</span></span>

  <span data-ttu-id="d7ac1-163">**問題：** 若呼叫特定執行個體兩次 (執行兩次相同的設定)，則上述資源會失敗</span><span class="sxs-lookup"><span data-stu-id="d7ac1-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="d7ac1-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-164">**Service**</span></span>
- <span data-ttu-id="d7ac1-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-165">**ServiceSet**</span></span>

  <span data-ttu-id="d7ac1-166">**問題：** 只適用於開始/停止 (狀態) 服務。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="d7ac1-167">如果嘗試變更啟動類型、認證、描述等其他服務屬性，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="d7ac1-168">擲回的錯誤類似如下︰</span><span class="sxs-lookup"><span data-stu-id="d7ac1-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="d7ac1-169">找不到類型 [management.managementobject]：請確認已載入包含此類型的組件。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="d7ac1-170">無法正常運作的資源</span><span class="sxs-lookup"><span data-stu-id="d7ac1-170">Resources that are not functional</span></span>
- <span data-ttu-id="d7ac1-171">**User**</span><span class="sxs-lookup"><span data-stu-id="d7ac1-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="d7ac1-172">Nano Server 上不提供的 DSC 功能</span><span class="sxs-lookup"><span data-stu-id="d7ac1-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="d7ac1-173">目前於 Nano Server 上沒有提供下列 DSC 功能︰</span><span class="sxs-lookup"><span data-stu-id="d7ac1-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="d7ac1-174">使用加密密碼將 MOF 文件解密</span><span class="sxs-lookup"><span data-stu-id="d7ac1-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="d7ac1-175">提取伺服器 -- 目前無法在 Nano Server 上設定提取伺服器</span><span class="sxs-lookup"><span data-stu-id="d7ac1-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="d7ac1-176">任何不在功能清單中的項目皆可使用</span><span class="sxs-lookup"><span data-stu-id="d7ac1-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="d7ac1-177">在 Nano Server 上使用自訂 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d7ac1-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="d7ac1-178">因為 Nano Server 上僅提供有限的 Windows API 與 CLR 程式庫，所以在 Windows 完整 CLR 版能執行的 DSC 資源，在 Nano Server 上不一定有效。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="d7ac1-179">請先完成端對端測試，再將任何 DSC 自訂資源部署至生產環境。</span><span class="sxs-lookup"><span data-stu-id="d7ac1-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7ac1-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7ac1-180">See Also</span></span>

- [<span data-ttu-id="d7ac1-181">開始使用 Nano Server</span><span class="sxs-lookup"><span data-stu-id="d7ac1-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
