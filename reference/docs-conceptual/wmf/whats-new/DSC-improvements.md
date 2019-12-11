---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的 DSC 改善
ms.openlocfilehash: a5efa38ce791a893580316bad7b61a6689153a86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416680"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="a9fac-103">WMF 5.1 的預期狀態設定 (DSC) 改善</span><span class="sxs-lookup"><span data-stu-id="a9fac-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="a9fac-104">DSC 類別資源改善</span><span class="sxs-lookup"><span data-stu-id="a9fac-104">DSC class resource improvements</span></span>

<span data-ttu-id="a9fac-105">WMF 5.1 中已修正下列已知問題︰</span><span class="sxs-lookup"><span data-stu-id="a9fac-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="a9fac-106">如果類別型 DSC 資源的 Get() 函式傳回複雜/雜湊表類型，Get-DscConfiguration 可能會傳回空值 (null) 或錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9fac-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="a9fac-107">當 DSC 設定使用 RunAs 認證時，Get-DscConfiguration 就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9fac-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="a9fac-108">類別型資源無法用於複合設定中。</span><span class="sxs-lookup"><span data-stu-id="a9fac-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="a9fac-109">如果類別型資源有其本身類型的屬性，Start-DscConfiguration 會停止回應。</span><span class="sxs-lookup"><span data-stu-id="a9fac-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="a9fac-110">類別型資源不能用為獨佔資源。</span><span class="sxs-lookup"><span data-stu-id="a9fac-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="a9fac-111">DSC 資源偵錯改善</span><span class="sxs-lookup"><span data-stu-id="a9fac-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="a9fac-112">在 WMF 5.0 中，PowerShell 偵錯工具並未直接停在類別資源方法 (Get/Set/Test)。</span><span class="sxs-lookup"><span data-stu-id="a9fac-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="a9fac-113">在 WMF 5.1 中，偵錯工具會停在類別資源方法，方式如同 MOF 資源方法。</span><span class="sxs-lookup"><span data-stu-id="a9fac-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="a9fac-114">DSC 提取用戶端支援 TLS1.1 和 TLS1.2</span><span class="sxs-lookup"><span data-stu-id="a9fac-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="a9fac-115">DSC 提取用戶端過去只支援 HTTPS 連線的 SSL3.0 和 TLS1.0。</span><span class="sxs-lookup"><span data-stu-id="a9fac-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="a9fac-116">強制使用更安全的通訊協定時，提取用戶端就會停止運作。</span><span class="sxs-lookup"><span data-stu-id="a9fac-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="a9fac-117">在 WMF 5.1 中，DSC 提取用戶端不再支援 SSL 3.0，卻新增了更安全的 TLS 1.1 和 TLS 1.2 通訊協定支援。</span><span class="sxs-lookup"><span data-stu-id="a9fac-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="a9fac-118">改善的提取伺服器登錄</span><span class="sxs-lookup"><span data-stu-id="a9fac-118">Improved pull server registration</span></span>

<span data-ttu-id="a9fac-119">在舊版的 WMF 中，在使用 ESENT 資料庫時，同時登錄/報告 DSC 提取伺服器的要求，會導致 LCM 無法登錄及 (或) 報告。</span><span class="sxs-lookup"><span data-stu-id="a9fac-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="a9fac-120">在這種情況下，提取伺服器的事件記錄檔會出現「執行個體名稱已在使用中」的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9fac-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="a9fac-121">這是因為在多執行緒的案例中使用不正確的模式來存取 ESENT 資料庫所導致的。</span><span class="sxs-lookup"><span data-stu-id="a9fac-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="a9fac-122">WMF 5.1 已修正此問題。</span><span class="sxs-lookup"><span data-stu-id="a9fac-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="a9fac-123">WMF 5.1 中可以正常同時登錄或報告 (包含 ESENT 資料庫)。</span><span class="sxs-lookup"><span data-stu-id="a9fac-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="a9fac-124">只有 ESENT 資料庫會發生這個問題，OLEDB 資料庫無此問題。</span><span class="sxs-lookup"><span data-stu-id="a9fac-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="a9fac-125">在 ESENT 資料庫執行個體上啟用循環記錄</span><span class="sxs-lookup"><span data-stu-id="a9fac-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="a9fac-126">在舊版的 DSC-PullServer 中，ESENT 資料庫記錄檔會填滿提取伺服器的磁碟空間，因為資料庫執行個體是在沒有循環記錄的情況下建立的。</span><span class="sxs-lookup"><span data-stu-id="a9fac-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="a9fac-127">在此版本中，您可以選擇使用提取伺服器的 web.config，控制執行個體的循環記錄行為。</span><span class="sxs-lookup"><span data-stu-id="a9fac-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="a9fac-128">根據預設，CircularLogging 會設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a9fac-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="a9fac-129">WOW64 支援設定關鍵字</span><span class="sxs-lookup"><span data-stu-id="a9fac-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="a9fac-130">64 位元電腦上的 WOW64 現在支援 `Configuration` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a9fac-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="a9fac-131">這代表可以定義 DSC 設定，以及可於 32 位元處理序中編譯，例如在 64 位元電腦上執行的 Windows PowerShell ISE (x86)。</span><span class="sxs-lookup"><span data-stu-id="a9fac-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="a9fac-132">提取命名慣例的部分設定</span><span class="sxs-lookup"><span data-stu-id="a9fac-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="a9fac-133">在舊版中，提取伺服器/服務的部分設定命名慣例 MOF 檔案名稱，應該符合本機設定管理員設定中指定的部分設定名稱，該本機設定管理員設定必須依次比對 MOF 檔案中內嵌的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="a9fac-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="a9fac-134">請參閱下方的快照集︰</span><span class="sxs-lookup"><span data-stu-id="a9fac-134">See the snapshots below:</span></span>

- <span data-ttu-id="a9fac-135">本機組態設定，當中定義了允許節點接收的部分設定。</span><span class="sxs-lookup"><span data-stu-id="a9fac-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![中繼設定範例](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="a9fac-137">部分設定定義範例</span><span class="sxs-lookup"><span data-stu-id="a9fac-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="a9fac-138">內嵌在所產生 MOF 檔案中的 'ConfigurationName'。</span><span class="sxs-lookup"><span data-stu-id="a9fac-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![產生的 MOF 檔案範例](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="a9fac-140">提取設定存放庫中的檔案名稱</span><span class="sxs-lookup"><span data-stu-id="a9fac-140">FileName in the pull configuration repository</span></span>

  ![設定存放庫中的檔案名稱](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="a9fac-142">Azure 自動化服務名稱以前產生的 MOF 檔案為 `<ConfigurationName>.<NodeName>.mof`。</span><span class="sxs-lookup"><span data-stu-id="a9fac-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="a9fac-143">因此下面的設定會編譯為 PartialOne.localhost.mof。</span><span class="sxs-lookup"><span data-stu-id="a9fac-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="a9fac-144">如此即不可能從 Azure 自動化服務提取您其中一項部分設定。</span><span class="sxs-lookup"><span data-stu-id="a9fac-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="a9fac-145">在 WMF 5.1 中，提取伺服器/服務中的部分設定可以命名為 `<ConfigurationName>.<NodeName>.mof`。</span><span class="sxs-lookup"><span data-stu-id="a9fac-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="a9fac-146">但若電腦從提取伺服器/服務中提取了單一設定，則提取伺服器存放庫上的設定檔可以有任意的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a9fac-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="a9fac-147">此命名彈性可讓您使用 Azure 自動化服務部分管理節點，其中節點的某些設定來自 Azure 自動化 DSC，且某項部分設定是您在本機管理的。</span><span class="sxs-lookup"><span data-stu-id="a9fac-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="a9fac-148">下面的中繼設定會設定由本機及 Azure 自動化服務管理的節點。</span><span class="sxs-lookup"><span data-stu-id="a9fac-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="a9fac-149">使用 PsDscRunAsCredential 和 DSC 複合資源</span><span class="sxs-lookup"><span data-stu-id="a9fac-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="a9fac-150">我們已新增搭配使用 [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) 和 DSC [複合](/powershell/scripting/dsc/authoringresourcecomposite)資源的支援。</span><span class="sxs-lookup"><span data-stu-id="a9fac-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="a9fac-151">在設定內使用複合資源時，您現在可以指定 **PsDscRunAsCredential** 的值。</span><span class="sxs-lookup"><span data-stu-id="a9fac-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="a9fac-152">指定後，複合資源內的所有資源都會以 RunAs 使用者身分執行。</span><span class="sxs-lookup"><span data-stu-id="a9fac-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="a9fac-153">如果複合資源會呼叫另一個複合資源，也會以 RunAs 使用者身分執行所有那些資源。</span><span class="sxs-lookup"><span data-stu-id="a9fac-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="a9fac-154">RunAs 認證會傳播至複合資源階層的所有層級。</span><span class="sxs-lookup"><span data-stu-id="a9fac-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="a9fac-155">如果複合資源內的任何資源會針對 **PsDscRunAsCredential** 指定自己的值，則會在設定編譯期間發生合併錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9fac-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="a9fac-156">本範例示範如何使用包含在 PSDesiredStateConfiguration 模組內的 [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) 複合資源。</span><span class="sxs-lookup"><span data-stu-id="a9fac-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="a9fac-157">允許在設定中的相同重複資源</span><span class="sxs-lookup"><span data-stu-id="a9fac-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="a9fac-158">DSC 不允許或不處理設定中定義的衝突資源。</span><span class="sxs-lookup"><span data-stu-id="a9fac-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="a9fac-159">它並不會去嘗試解決衝突，而是只會失敗。</span><span class="sxs-lookup"><span data-stu-id="a9fac-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="a9fac-160">當設定重複使用透過複合資源而變得更有用時，衝突發生頻率將會提高。</span><span class="sxs-lookup"><span data-stu-id="a9fac-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="a9fac-161">當衝突資源的定義相同時，DSC 應該進行智慧判斷並允許此情況。</span><span class="sxs-lookup"><span data-stu-id="a9fac-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="a9fac-162">在此版本中，我們支援具有相同定義的多個資源執行個體︰</span><span class="sxs-lookup"><span data-stu-id="a9fac-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="a9fac-163">在舊版中，因為 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 執行個體在盡力確保 「網頁伺服器」 角色已安裝時發生衝突，因此會出現編譯失敗的結果。</span><span class="sxs-lookup"><span data-stu-id="a9fac-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="a9fac-164">請注意在這兩種設定中，*所有*正在設定的屬性都是相同的。</span><span class="sxs-lookup"><span data-stu-id="a9fac-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="a9fac-165">由於這兩個資源中的*所有*屬性相同，現在這會讓編譯成功完成。</span><span class="sxs-lookup"><span data-stu-id="a9fac-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="a9fac-166">如果這兩個資源之間有任何不同的屬性，則不會將它們視為相同，且編譯將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a9fac-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="a9fac-167">DSC 模組和設定簽署驗證</span><span class="sxs-lookup"><span data-stu-id="a9fac-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="a9fac-168">在 DSC 中，設定和模組會從提取伺服器散發到受管理的電腦。</span><span class="sxs-lookup"><span data-stu-id="a9fac-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="a9fac-169">如果提取伺服器遭到入侵，攻擊者或許就能修改提取伺服器上的設定和模組，並將其散發到所有受控節點。</span><span class="sxs-lookup"><span data-stu-id="a9fac-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="a9fac-170">在 WMF 5.1 中，DSC 支援驗證類別目錄和設定 (.MOF) 檔案的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="a9fac-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="a9fac-171">這項功能會防止節點執行未經受信任簽署者簽署的設定或模組檔案，或經受信任簽署者簽署後遭竄改的檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="a9fac-172">如何簽署設定和模組</span><span class="sxs-lookup"><span data-stu-id="a9fac-172">How to sign configuration and module</span></span>

- <span data-ttu-id="a9fac-173">設定檔 (.MOF)：現有的 PowerShell Cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) 已擴充，可支援簽署 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="a9fac-174">模組：已透過使用下列步驟簽署對應的模組類別目錄來完成模組簽署：</span><span class="sxs-lookup"><span data-stu-id="a9fac-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="a9fac-175">建立類別目錄檔案：類別目錄檔案包含密碼編譯雜湊或指紋的集合。</span><span class="sxs-lookup"><span data-stu-id="a9fac-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="a9fac-176">每個指紋都會對應至模組所包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="a9fac-177">已新增新的 [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) Cmdlet，讓使用者為其模組建立類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="a9fac-178">簽署類別目錄檔案︰使用 [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) 簽署類別目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="a9fac-179">將類別目錄檔案放在模組資料夾內。</span><span class="sxs-lookup"><span data-stu-id="a9fac-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="a9fac-180">依照慣例，模組類別目錄檔案應該位於與模組同名的模組資料夾內。</span><span class="sxs-lookup"><span data-stu-id="a9fac-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="a9fac-181">啟用簽署驗證的 LocalConfigurationManager 設定</span><span class="sxs-lookup"><span data-stu-id="a9fac-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="a9fac-182">提取</span><span class="sxs-lookup"><span data-stu-id="a9fac-182">Pull</span></span>

<span data-ttu-id="a9fac-183">節點的 LocalConfigurationManager 會根據其目前的設定，執行模組和設定的簽署驗證。</span><span class="sxs-lookup"><span data-stu-id="a9fac-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="a9fac-184">預設停用簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="a9fac-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="a9fac-185">將 'SignatureValidation' 區塊加入節點的中繼設定定義可啟用簽章驗證，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9fac-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="a9fac-186">在節點上設定上述中繼設定，可在下載的設定和模組上啟用簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="a9fac-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="a9fac-187">本機設定管理員會執行下列步驟來驗證數位簽章。</span><span class="sxs-lookup"><span data-stu-id="a9fac-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="a9fac-188">使用 `Get-AuthenticodeSignature` Cmdlet 來驗證設定檔 (.MOF) 上的簽章有效。</span><span class="sxs-lookup"><span data-stu-id="a9fac-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="a9fac-189">驗證授權簽署者的憑證授權單位是否受信任。</span><span class="sxs-lookup"><span data-stu-id="a9fac-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="a9fac-190">將設定的模組/資源相依性下載至暫存位置。</span><span class="sxs-lookup"><span data-stu-id="a9fac-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="a9fac-191">驗證模組內是否包含類別目錄簽章。</span><span class="sxs-lookup"><span data-stu-id="a9fac-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="a9fac-192">尋找 `<moduleName>.cat` 檔案，並使用 `Get-AuthenticodeSignature` 來驗證它的簽章。</span><span class="sxs-lookup"><span data-stu-id="a9fac-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="a9fac-193">驗證授權簽署者的憑證授權單位是否受信任。</span><span class="sxs-lookup"><span data-stu-id="a9fac-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="a9fac-194">使用新的 `Test-FileCatalog` Cmdlet 來驗證模組的內容未經竄改。</span><span class="sxs-lookup"><span data-stu-id="a9fac-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="a9fac-195">`Install-Module` 到 `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="a9fac-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="a9fac-196">處理設定</span><span class="sxs-lookup"><span data-stu-id="a9fac-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="a9fac-197">只有第一次在系統上套用設定時，或下載並安裝模組時，才會執行模組類別目錄和設定上的簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="a9fac-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="a9fac-198">一致性執行不會驗證 Current.mof 或其模組相依性的簽章。</span><span class="sxs-lookup"><span data-stu-id="a9fac-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="a9fac-199">如果驗證在任何階段失敗，例如從提取伺服器提取的設定未經簽署，則會終止處理設定並顯示下列錯誤，以及刪除所有暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![錯誤輸出設定範例](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="a9fac-201">同樣地，提取目錄未經簽署的模組也會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="a9fac-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![錯誤輸出模組範例](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="a9fac-203">推入</span><span class="sxs-lookup"><span data-stu-id="a9fac-203">Push</span></span>

<span data-ttu-id="a9fac-204">透過使用推入所傳遞的設定，可能在傳送到節點之前即已在來源遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="a9fac-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="a9fac-205">本機設定管理員會對已推入或發行的設定，執行類似的簽章驗證步驟。</span><span class="sxs-lookup"><span data-stu-id="a9fac-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="a9fac-206">以下是推入簽章驗證的完整範例。</span><span class="sxs-lookup"><span data-stu-id="a9fac-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="a9fac-207">在節點上啟用簽章驗證。</span><span class="sxs-lookup"><span data-stu-id="a9fac-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="a9fac-208">建立設定檔範例。</span><span class="sxs-lookup"><span data-stu-id="a9fac-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="a9fac-209">嘗試將未經簽署的設定檔推入至節點。</span><span class="sxs-lookup"><span data-stu-id="a9fac-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="a9fac-211">使用程式碼簽署憑證簽署設定檔。</span><span class="sxs-lookup"><span data-stu-id="a9fac-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="a9fac-213">嘗試推入簽署的 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="a9fac-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
