---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
title: WMF 5.1 的 DSC 改善
ms.openlocfilehash: 04bf8ed820d24f1062e05d19c8f3b0c041298979
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="3013e-103">WMF 5.1 的預期狀態設定 (DSC) 改善</span><span class="sxs-lookup"><span data-stu-id="3013e-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="3013e-104">DSC 類別資源改善</span><span class="sxs-lookup"><span data-stu-id="3013e-104">DSC class resource improvements</span></span>

<span data-ttu-id="3013e-105">WMF 5.1 中已修正下列已知問題︰</span><span class="sxs-lookup"><span data-stu-id="3013e-105">In WMF 5.1, we have fixed the following known issues:</span></span>
* <span data-ttu-id="3013e-106">如果類別型 DSC 資源的 Get() 函式傳回複雜/雜湊表類型，Get-DscConfiguration 可能會傳回空值 (null) 或錯誤。</span><span class="sxs-lookup"><span data-stu-id="3013e-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
* <span data-ttu-id="3013e-107">當 DSC 設定使用 RunAs 認證時，Get-DscConfiguration 就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3013e-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
* <span data-ttu-id="3013e-108">類別型資源無法用於複合設定中。</span><span class="sxs-lookup"><span data-stu-id="3013e-108">Class-based resource cannot be used in a composite configuration.</span></span>
* <span data-ttu-id="3013e-109">如果類別型資源有其本身類型的屬性，Start-DscConfiguration 會停止回應。</span><span class="sxs-lookup"><span data-stu-id="3013e-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
* <span data-ttu-id="3013e-110">類別型資源不能用為獨佔資源。</span><span class="sxs-lookup"><span data-stu-id="3013e-110">Class-based resource cannot be used as an exclusive resource.</span></span>


## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="3013e-111">DSC 資源偵錯改善</span><span class="sxs-lookup"><span data-stu-id="3013e-111">DSC resource debugging improvements</span></span>
<span data-ttu-id="3013e-112">在 WMF 5.0 中，PowerShell 偵錯工具並未直接停在類別資源方法 (Get/Set/Test)。</span><span class="sxs-lookup"><span data-stu-id="3013e-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="3013e-113">在 WMF 5.1 中，偵錯工具會停在類別資源方法，方式如同 MOF 資源方法。</span><span class="sxs-lookup"><span data-stu-id="3013e-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="3013e-114">DSC 提取用戶端支援 TLS1.1 和 TLS1.2</span><span class="sxs-lookup"><span data-stu-id="3013e-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>
<span data-ttu-id="3013e-115">DSC 提取用戶端過去只支援 HTTPS 連線的 SSL3.0 和 TLS1.0。</span><span class="sxs-lookup"><span data-stu-id="3013e-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="3013e-116">強制使用更安全的通訊協定時，提取用戶端就會停止運作。</span><span class="sxs-lookup"><span data-stu-id="3013e-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="3013e-117">在 WMF 5.1 中，DSC 提取用戶端不再支援 SSL 3.0，卻新增了更安全的 TLS 1.1 和 TLS 1.2 通訊協定支援。</span><span class="sxs-lookup"><span data-stu-id="3013e-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="3013e-118">改善的提取伺服器登錄</span><span class="sxs-lookup"><span data-stu-id="3013e-118">Improved pull server registration</span></span> ##

<span data-ttu-id="3013e-119">在舊版的 WMF 中，在使用 ESENT 資料庫時，同時登錄/報告 DSC 提取伺服器的要求，會導致 LCM 無法登錄及 (或) 報告。</span><span class="sxs-lookup"><span data-stu-id="3013e-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="3013e-120">在這種情況下，提取伺服器的事件記錄檔會出現「執行個體名稱已在使用中」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3013e-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="3013e-121">這是因為在多執行緒案例中使用不正確的模式存取 ESENT 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3013e-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="3013e-122">WMF 5.1 已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="3013e-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="3013e-123">WMF 5.1 中可以正常同時登錄或報告 (包含 ESENT 資料庫)。</span><span class="sxs-lookup"><span data-stu-id="3013e-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="3013e-124">只有 ESENT 資料庫會發生這個問題，OLEDB 資料庫無此問題。</span><span class="sxs-lookup"><span data-stu-id="3013e-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="3013e-125">在 ESENT 資料庫執行個體上啟用循環記錄</span><span class="sxs-lookup"><span data-stu-id="3013e-125">Enable Circular log on ESENT database instance</span></span>
<span data-ttu-id="3013e-126">在舊版的 DSC-PullServer 中，ESENT 資料庫記錄檔會填滿提取伺服器的磁碟空間，因為資料庫執行個體是在沒有循環記錄的情況下建立的。</span><span class="sxs-lookup"><span data-stu-id="3013e-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="3013e-127">在此版本中，您可以選擇使用提取伺服器的 web.config，控制執行個體的循環記錄行為。</span><span class="sxs-lookup"><span data-stu-id="3013e-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="3013e-128">根據預設，CircularLogging 會設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="3013e-128">By default CircularLogging is set to TRUE.</span></span>
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="3013e-129">提取命名慣例的部分設定</span><span class="sxs-lookup"><span data-stu-id="3013e-129">Pull partial configuration naming convention</span></span>
<span data-ttu-id="3013e-130">在舊版中，提取伺服器/服務的部分設定命名慣例 MOF 檔案名稱，應該符合本機設定管理員設定中指定的部分設定名稱，該本機設定管理員設定必須依次比對 MOF 檔案中內嵌的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="3013e-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="3013e-131">請參閱下方的快照集︰</span><span class="sxs-lookup"><span data-stu-id="3013e-131">See the snapshots below:</span></span>

<span data-ttu-id="3013e-132">•   本機組態設定，定義允許接收節點的部分設定。</span><span class="sxs-lookup"><span data-stu-id="3013e-132">•   Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![中繼設定範例](../images/MetaConfigPartialOne.png)

<span data-ttu-id="3013e-134">•   部分設定定義範例</span><span class="sxs-lookup"><span data-stu-id="3013e-134">•   Sample partial configuration definition</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="3013e-135">•   內嵌在產生之 MOF 檔案中的 'ConfigurationName'。</span><span class="sxs-lookup"><span data-stu-id="3013e-135">•   'ConfigurationName' embedded in the generated MOF file.</span></span>

![產生的 MOF 檔案範例](../images/PartialGeneratedMof.png)

<span data-ttu-id="3013e-137">•   提取設定存放庫中的檔案名稱</span><span class="sxs-lookup"><span data-stu-id="3013e-137">•   FileName in the pull configuration repository</span></span>

![設定存放庫中的檔案名稱](../images/PartialInConfigRepository.png)

<span data-ttu-id="3013e-139">Azure 自動化服務名稱以前產生的 MOF 檔案為 `<ConfigurationName>.<NodeName>.mof`。</span><span class="sxs-lookup"><span data-stu-id="3013e-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="3013e-140">因此下面的設定會編譯為 PartialOne.localhost.mof。</span><span class="sxs-lookup"><span data-stu-id="3013e-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="3013e-141">如此即不可能從 Azure 自動化服務提取您其中一項部分設定。</span><span class="sxs-lookup"><span data-stu-id="3013e-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="3013e-142">在 WMF 5.1 中，提取伺服器/服務中的部分設定可以命名為 `<ConfigurationName>.<NodeName>.mof`。</span><span class="sxs-lookup"><span data-stu-id="3013e-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="3013e-143">但若電腦從提取伺服器/服務中提取了單一設定，則提取伺服器存放庫上的設定檔可以有任意的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="3013e-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="3013e-144">此命名彈性可讓您使用 Azure 自動化服務部分管理節點，其中節點的某些設定來自 Azure 自動化 DSC，且某項部分設定是您在本機管理的。</span><span class="sxs-lookup"><span data-stu-id="3013e-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="3013e-145">下面的中繼設定會設定由本機及 Azure 自動化服務管理的節點。</span><span class="sxs-lookup"><span data-stu-id="3013e-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PULL"
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation service.
        PartialConfiguration PartialConfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
        }

        # This partial configuration is managed locally.
        PartialConfiguration OnPremisesConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
 ```

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="3013e-146">使用 PsDscRunAsCredential 和 DSC 複合資源</span><span class="sxs-lookup"><span data-stu-id="3013e-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="3013e-147">我們新增了支援以使用 [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) 和 DSC [複合](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite)資源。</span><span class="sxs-lookup"><span data-stu-id="3013e-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="3013e-148">在設定內使用複合資源時，您現在可以指定一個 PsDscRunAsCredential 值。</span><span class="sxs-lookup"><span data-stu-id="3013e-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="3013e-149">指定後，複合資源內的所有資源都會以 RunAs 使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="3013e-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="3013e-150">如果複合資源呼叫另一項複合資源，也會以 RunAs 使用者身分執行其所有資源。</span><span class="sxs-lookup"><span data-stu-id="3013e-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="3013e-151">RunAs 認證會傳播至複合資源階層的所有層級。</span><span class="sxs-lookup"><span data-stu-id="3013e-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="3013e-152">如果複合資源內的任何資源指定自己的 PsDscRunAsCredential 值，則設定編譯期間就會發生合併錯誤。</span><span class="sxs-lookup"><span data-stu-id="3013e-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="3013e-153">本範例示範如何使用包含在 PSDesiredStateConfiguration 模組內的 [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) 複合資源。</span><span class="sxs-lookup"><span data-stu-id="3013e-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>



```powershell

Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }

}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}


InstallWindowsFeature -ConfigurationData $configData

```

##<a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="3013e-154">DSC 模組和設定簽署驗證</span><span class="sxs-lookup"><span data-stu-id="3013e-154">DSC module and configuration signing validations</span></span>
<span data-ttu-id="3013e-155">在 DSC 中，設定和模組會從提取伺服器散發到受管理的電腦。</span><span class="sxs-lookup"><span data-stu-id="3013e-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="3013e-156">如果提取伺服器遭到入侵，攻擊者可以修改提取伺服器上的設定和模組，將其散發到所有受管理的節點以危害所有節點。</span><span class="sxs-lookup"><span data-stu-id="3013e-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

 <span data-ttu-id="3013e-157">在 WMF 5.1 中，DSC 支援驗證類別目錄和設定 (.MOF) 檔案的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="3013e-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="3013e-158">這項功能會防止節點執行未經受信任簽署者簽署的設定或模組檔案，或經受信任簽署者簽署後遭竄改的檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>



###<a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="3013e-159">如何簽署設定和模組</span><span class="sxs-lookup"><span data-stu-id="3013e-159">How to sign configuration and module</span></span>
***
* <span data-ttu-id="3013e-160">設定檔 (.MOF)：現有的 PowerShell Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 已擴充，可支援簽署 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="3013e-161">模組：已透過簽署對應的模組類別目錄完成模組簽署，使用步驟如下：</span><span class="sxs-lookup"><span data-stu-id="3013e-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="3013e-162">建立類別目錄檔案︰類別目錄檔案包含密碼編譯雜湊或指紋的集合。</span><span class="sxs-lookup"><span data-stu-id="3013e-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="3013e-163">每個指紋都會對應至模組所包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="3013e-164">已新增新的 [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) Cmdlet，讓使用者為其模組建立類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="3013e-165">簽署類別目錄檔案︰使用 [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) 簽署類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="3013e-166">將類別目錄檔案放在模組資料夾內。</span><span class="sxs-lookup"><span data-stu-id="3013e-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="3013e-167">依照慣例，模組類別目錄檔案應該位於與模組同名的模組資料夾內。</span><span class="sxs-lookup"><span data-stu-id="3013e-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="3013e-168">啟用簽署驗證的 LocalConfigurationManager 設定</span><span class="sxs-lookup"><span data-stu-id="3013e-168">LocalConfigurationManager settings to enable signing validations</span></span>

####<a name="pull"></a><span data-ttu-id="3013e-169">提取</span><span class="sxs-lookup"><span data-stu-id="3013e-169">Pull</span></span>
<span data-ttu-id="3013e-170">節點的 LocalConfigurationManager 會根據其目前的設定，執行模組和設定的簽署驗證。</span><span class="sxs-lookup"><span data-stu-id="3013e-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="3013e-171">預設停用簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="3013e-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="3013e-172">將 'SignatureValidation' 區塊加入節點的中繼設定定義可啟用簽章驗證，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3013e-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
 ```

<span data-ttu-id="3013e-173">在節點上設定上述中繼設定，可在下載的設定和模組上啟用簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="3013e-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="3013e-174">本機設定管理員會執行下列步驟來驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="3013e-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="3013e-175">驗證設定檔 (.MOF) 的簽章是否有效。</span><span class="sxs-lookup"><span data-stu-id="3013e-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="3013e-176">它會使用 5.1 中已擴充的 PowerShell Cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx)，以支援 MOF 簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="3013e-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="3013e-177">驗證授權簽署者的憑證授權單位是否受信任。</span><span class="sxs-lookup"><span data-stu-id="3013e-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="3013e-178">將設定的模組/資源相依性下載至暫存位置。</span><span class="sxs-lookup"><span data-stu-id="3013e-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="3013e-179">驗證模組內是否包含類別目錄簽章。</span><span class="sxs-lookup"><span data-stu-id="3013e-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="3013e-180">尋找 `<moduleName>.cat`檔案，並使用 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) Cmdlet 驗證其簽章。</span><span class="sxs-lookup"><span data-stu-id="3013e-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="3013e-181">驗證授權簽署者的憑證授權單位是否受信任。</span><span class="sxs-lookup"><span data-stu-id="3013e-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="3013e-182">使用新的 [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) Cmdlet 來驗證模組內容是否未經竄改。</span><span class="sxs-lookup"><span data-stu-id="3013e-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="3013e-183">將模組安裝到 $env:ProgramFiles\WindowsPowerShell\Modules\\</span><span class="sxs-lookup"><span data-stu-id="3013e-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="3013e-184">處理設定</span><span class="sxs-lookup"><span data-stu-id="3013e-184">Process configuration</span></span>

> <span data-ttu-id="3013e-185">注意︰只有第一次在系統上套用設定時，或下載並安裝模組時，才會執行模組類別目錄和設定上的簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="3013e-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="3013e-186">一致性執行不會驗證 Current.mof 或其模組相依性的簽章。</span><span class="sxs-lookup"><span data-stu-id="3013e-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="3013e-187">如果驗證在任何階段失敗，例如從提取伺服器提取的設定未經簽署，則會終止處理設定並顯示下列錯誤，以及刪除所有暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![錯誤輸出設定範例](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="3013e-189">同樣地，提取目錄未經簽署的模組也會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3013e-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![錯誤輸出模組範例](../images/PullUnisgnedCatalog.png)

####<a name="push"></a><span data-ttu-id="3013e-191">推入</span><span class="sxs-lookup"><span data-stu-id="3013e-191">Push</span></span>
<span data-ttu-id="3013e-192">透過使用推入所傳遞的設定，可能在傳送到節點之前即已在來源遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="3013e-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="3013e-193">本機設定管理員會對已推入或發行的設定，執行類似的簽章驗證步驟。</span><span class="sxs-lookup"><span data-stu-id="3013e-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="3013e-194">以下是推入簽章驗證的完整範例。</span><span class="sxs-lookup"><span data-stu-id="3013e-194">Below is a complete example of signature validation for push.</span></span>

* <span data-ttu-id="3013e-195">在節點上啟用簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="3013e-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```
* <span data-ttu-id="3013e-196">建立設定檔範例。</span><span class="sxs-lookup"><span data-stu-id="3013e-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* <span data-ttu-id="3013e-197">嘗試將未經簽署的設定檔推入至節點。</span><span class="sxs-lookup"><span data-stu-id="3013e-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* <span data-ttu-id="3013e-199">使用程式碼簽署憑證簽署設定檔。</span><span class="sxs-lookup"><span data-stu-id="3013e-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

* <span data-ttu-id="3013e-201">嘗試推入簽署的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="3013e-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)