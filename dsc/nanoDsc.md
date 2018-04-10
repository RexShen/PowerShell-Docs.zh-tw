---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: 在 Nano Server 上使用 DSC
ms.openlocfilehash: 9ebc1f046893c360538009b5ecbcfb6456f92bbb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="e32a3-103">在 Nano Server 上使用 DSC</span><span class="sxs-lookup"><span data-stu-id="e32a3-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="e32a3-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e32a3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e32a3-105">您可以選用 Windows Server 2016 媒體上 `NanoServer\Packages` 資料夾中的 **Nano Server 上的 DSC** 封裝。</span><span class="sxs-lookup"><span data-stu-id="e32a3-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="e32a3-106">當您建立 Nano Server 的 VHD 時，可以安裝此套件，方法是指定 **Microsoft-NanoServer-DSC-Package** 作為 **New-NanoServerImage** 函數中 **Packages** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="e32a3-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="e32a3-107">例如，如果要建立虛擬機器的 VHD，命令會如下所示︰</span><span class="sxs-lookup"><span data-stu-id="e32a3-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="e32a3-108">如需安裝及使用 Nano Server 以及如何透過 PowerShell 遠端來管理 Nano Server 的相關資訊，請參閱 [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx) (開始使用 Nano Server)。</span><span class="sxs-lookup"><span data-stu-id="e32a3-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx).</span></span>


## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="e32a3-109">Nano Server 提供的 DSC 功能</span><span class="sxs-lookup"><span data-stu-id="e32a3-109">DSC features available on Nano Server</span></span>

 <span data-ttu-id="e32a3-110">相較於完整版的 Windows Server，Nano Server 僅支援一組有限的 API，所以目前 Nano Server 上的 DSC 和執行於完整 SKU 上的 DSC 相較，並不具備完整的同位功能。</span><span class="sxs-lookup"><span data-stu-id="e32a3-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="e32a3-111">Nano Server 上的 DSC 正在開發中，功能還不夠完備。</span><span class="sxs-lookup"><span data-stu-id="e32a3-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

 <span data-ttu-id="e32a3-112">目前於 Nano Server 上提供的 DSC 功能如下︰</span><span class="sxs-lookup"><span data-stu-id="e32a3-112">The following DSC features are currently available on Nano Server:</span></span>


* <span data-ttu-id="e32a3-113">推入與提取模式</span><span class="sxs-lookup"><span data-stu-id="e32a3-113">Both push and pull modes</span></span>

* <span data-ttu-id="e32a3-114">完整版 Windows Server 的所有現有 DSC Cmdlet 包括︰</span><span class="sxs-lookup"><span data-stu-id="e32a3-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
  * [<span data-ttu-id="e32a3-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e32a3-115">Get-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn407378.aspx)
  * [<span data-ttu-id="e32a3-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e32a3-116">Set-DscLocalConfigurationManager</span></span>](https://technet.microsoft.com/library/dn521621.aspx)
  * [<span data-ttu-id="e32a3-117">啟用-DscDebug</span><span class="sxs-lookup"><span data-stu-id="e32a3-117">Enable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [<span data-ttu-id="e32a3-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="e32a3-118">Disable-DscDebug</span></span>](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [<span data-ttu-id="e32a3-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e32a3-119">Start-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [<span data-ttu-id="e32a3-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e32a3-120">Stop-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [<span data-ttu-id="e32a3-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e32a3-121">Get-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [<span data-ttu-id="e32a3-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e32a3-122">Test-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [<span data-ttu-id="e32a3-123">Publish-DscConfiguraiton</span><span class="sxs-lookup"><span data-stu-id="e32a3-123">Publish-DscConfiguraiton</span></span>](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [<span data-ttu-id="e32a3-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e32a3-124">Update-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [<span data-ttu-id="e32a3-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="e32a3-125">Restore-DscConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [<span data-ttu-id="e32a3-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="e32a3-126">Remove-DscConfigurationDocument</span></span>](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [<span data-ttu-id="e32a3-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="e32a3-127">Get-DscConfigurationStatus</span></span>](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [<span data-ttu-id="e32a3-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="e32a3-128">Invoke-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [<span data-ttu-id="e32a3-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="e32a3-129">Find-DscResource</span></span>](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [<span data-ttu-id="e32a3-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="e32a3-130">Get-DscResource</span></span>](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [<span data-ttu-id="e32a3-131">New-DscChecksum</span><span class="sxs-lookup"><span data-stu-id="e32a3-131">New-DscChecksum</span></span>](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* <span data-ttu-id="e32a3-132">編譯設定 (請參閱 [DSC 設定](configurations.md))。</span><span class="sxs-lookup"><span data-stu-id="e32a3-132">Compiling configurations (see [DSC configurations](configurations.md))</span></span>

  <span data-ttu-id="e32a3-133">**問題︰** 密碼加密 (請參閱[保護 MOF 檔案](securemof.md)) 在設定編譯期間無法運作。</span><span class="sxs-lookup"><span data-stu-id="e32a3-133">**Issue:** Password encryption (see [Securing the MOF File](securemof.md)) during configuration compilation doesn't work.</span></span>

* <span data-ttu-id="e32a3-134">編譯中繼設定 (請參閱[設定本機設定管理員](metaConfig.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](metaConfig.md))</span></span>

* <span data-ttu-id="e32a3-135">執行使用者內容下的資源 (請參閱[以使用者認證執行 DSC (RunAs)](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](runAsUser.md))</span></span>

* <span data-ttu-id="e32a3-136">類別型資源 (請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](authoringResourceClass.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](authoringResourceClass.md))</span></span>

* <span data-ttu-id="e32a3-137">為 DSC 資源偵錯 (請參閱[為 DSC 資源偵錯](debugresource.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-137">Debugging of DSC resources (see [Debugging DSC resources](debugresource.md))</span></span>

  <span data-ttu-id="e32a3-138">**問題︰** 如果資源使用 PsDscRunAsCredential 則無法運作 (請參閱[以使用者認證執行 DSC](runAsUser.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](runAsUser.md))</span></span>

* [<span data-ttu-id="e32a3-139">指定節點之間的相依性</span><span class="sxs-lookup"><span data-stu-id="e32a3-139">Specifying cross-node dependencies</span></span>](crossNodeDependencies.md)

* [<span data-ttu-id="e32a3-140">資源的版本管理</span><span class="sxs-lookup"><span data-stu-id="e32a3-140">Resource versioning</span></span>](sxsResource.md)

* <span data-ttu-id="e32a3-141">提取用戶端 (設定與資源) (請參閱[使用設定名稱設定提取用戶端](pullClientConfigNames.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](pullClientConfigNames.md))</span></span>

* [<span data-ttu-id="e32a3-142">部分設定 (提取與推送)</span><span class="sxs-lookup"><span data-stu-id="e32a3-142">Partial configurations (pull & push)</span></span>](partialConfigs.md)

* [<span data-ttu-id="e32a3-143">回報至提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e32a3-143">Reporting to pull server</span></span>](reportServer.md)

* <span data-ttu-id="e32a3-144">MOF 加密</span><span class="sxs-lookup"><span data-stu-id="e32a3-144">MOF encryption</span></span>

* <span data-ttu-id="e32a3-145">事件記錄</span><span class="sxs-lookup"><span data-stu-id="e32a3-145">Event logging</span></span>

* <span data-ttu-id="e32a3-146">Azure 自動化 DSC 報告</span><span class="sxs-lookup"><span data-stu-id="e32a3-146">Azure Automation DSC reporting</span></span>

* <span data-ttu-id="e32a3-147">可完全正常運作的資源</span><span class="sxs-lookup"><span data-stu-id="e32a3-147">Resources that are fully functional</span></span>
  * [<span data-ttu-id="e32a3-148">Archive</span><span class="sxs-lookup"><span data-stu-id="e32a3-148">Archive</span></span>](archiveResource.md)
  * [<span data-ttu-id="e32a3-149">Environment</span><span class="sxs-lookup"><span data-stu-id="e32a3-149">Environment</span></span>](environmentResource.md)
  * [<span data-ttu-id="e32a3-150">File</span><span class="sxs-lookup"><span data-stu-id="e32a3-150">File</span></span>](fileResource.md)
  * [<span data-ttu-id="e32a3-151">Log</span><span class="sxs-lookup"><span data-stu-id="e32a3-151">Log</span></span>](logResource.md)
  * <span data-ttu-id="e32a3-152">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="e32a3-152">ProcessSet</span></span>
  * [<span data-ttu-id="e32a3-153">Registry</span><span class="sxs-lookup"><span data-stu-id="e32a3-153">Registry</span></span>](registryResource.md)
  * [<span data-ttu-id="e32a3-154">Script</span><span class="sxs-lookup"><span data-stu-id="e32a3-154">Script</span></span>](scriptResource.md)
  * <span data-ttu-id="e32a3-155">WindowsPackageCab</span><span class="sxs-lookup"><span data-stu-id="e32a3-155">WindowsPackageCab</span></span>
  * [<span data-ttu-id="e32a3-156">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="e32a3-156">WindowsProcess</span></span>](windowsProcessResource.md)
  * <span data-ttu-id="e32a3-157">WaitForAll (請參閱[指定跨節點相依性](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-157">WaitForAll (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="e32a3-158">WaitForAny (請參閱[指定跨節點相依性](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-158">WaitForAny (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>
  * <span data-ttu-id="e32a3-159">WaitForSome (請參閱[指定跨節點相依性](crossNodeDependencies.md))</span><span class="sxs-lookup"><span data-stu-id="e32a3-159">WaitForSome (see [Specifying cross-node dependencies](crossNodeDependencies.md))</span></span>

* <span data-ttu-id="e32a3-160">部分運作的資源</span><span class="sxs-lookup"><span data-stu-id="e32a3-160">Resources that are partially functional</span></span>
  * [<span data-ttu-id="e32a3-161">群組</span><span class="sxs-lookup"><span data-stu-id="e32a3-161">Group</span></span>](groupResource.md)
  * <span data-ttu-id="e32a3-162">GroupSet</span><span class="sxs-lookup"><span data-stu-id="e32a3-162">GroupSet</span></span>

  <span data-ttu-id="e32a3-163">**問題︰** 若呼叫特定執行個體兩次 (執行兩次相同的設定)，則上述資源會失敗</span><span class="sxs-lookup"><span data-stu-id="e32a3-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  * [<span data-ttu-id="e32a3-164">Service</span><span class="sxs-lookup"><span data-stu-id="e32a3-164">Service</span></span>](serviceResource.md)
  * <span data-ttu-id="e32a3-165">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="e32a3-165">ServiceSet</span></span>

  <span data-ttu-id="e32a3-166">**問題︰** 只適用於開始/停止 (狀態) 服務。</span><span class="sxs-lookup"><span data-stu-id="e32a3-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="e32a3-167">如果嘗試變更啟動類型、認證、描述等其他服務屬性，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="e32a3-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="e32a3-168">擲回的錯誤類似如下︰</span><span class="sxs-lookup"><span data-stu-id="e32a3-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="e32a3-169">找不到類型 [management.managementobject]：請確認已載入包含此類型的組件。</span><span class="sxs-lookup"><span data-stu-id="e32a3-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

* <span data-ttu-id="e32a3-170">無法正常運作的資源</span><span class="sxs-lookup"><span data-stu-id="e32a3-170">Resources that are not functional</span></span>
  * [<span data-ttu-id="e32a3-171">User</span><span class="sxs-lookup"><span data-stu-id="e32a3-171">User</span></span>](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="e32a3-172">Nano Server 上不提供的 DSC 功能</span><span class="sxs-lookup"><span data-stu-id="e32a3-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="e32a3-173">目前於 Nano Server 上沒有提供下列 DSC 功能︰</span><span class="sxs-lookup"><span data-stu-id="e32a3-173">The following DSC features are not currently available on Nano Server:</span></span>

* <span data-ttu-id="e32a3-174">使用加密密碼將 MOF 文件解密</span><span class="sxs-lookup"><span data-stu-id="e32a3-174">Decrypting MOF document with encrypted password(s)</span></span>
* <span data-ttu-id="e32a3-175">提取伺服器 -- 目前無法在 Nano Server 上設定提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e32a3-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
* <span data-ttu-id="e32a3-176">任何不在功能清單中的項目皆可使用</span><span class="sxs-lookup"><span data-stu-id="e32a3-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="e32a3-177">在 Nano Server 上使用自訂 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="e32a3-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="e32a3-178">因為 Nano Server 上僅提供有限的 Windows API 與 CLR 程式庫，所以在 Windows 完整 CLR 版能執行的 DSC 資源，在 Nano Server 上不一定有效。</span><span class="sxs-lookup"><span data-stu-id="e32a3-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="e32a3-179">請先完成端對端測試，再將任何 DSC 自訂資源部署至生產環境。</span><span class="sxs-lookup"><span data-stu-id="e32a3-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="e32a3-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e32a3-180">See Also</span></span>
- [<span data-ttu-id="e32a3-181">開始使用 Nano Server</span><span class="sxs-lookup"><span data-stu-id="e32a3-181">Getting Started with Nano Server</span></span>](https://technet.microsoft.com/library/mt126167.aspx)