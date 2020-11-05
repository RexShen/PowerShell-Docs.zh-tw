---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: PowerShell 預期狀態設定部分設定
description: DSC 可讓設定以片段形式傳送及從多個來源傳送。 目標節點上的 LCM 會先將片段結合，再以單一設定的形式加以套用。
ms.openlocfilehash: 3afe5d684cabec9c8ab528347610b6dd00c5d4e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661613"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="79526-105">PowerShell 預期狀態設定部分設定</span><span class="sxs-lookup"><span data-stu-id="79526-105">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="79526-106">適用於︰Windows PowerShell 5.0 及更新版本。</span><span class="sxs-lookup"><span data-stu-id="79526-106">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="79526-107">在 PowerShell 5.0 中，預期狀態設定 (DSC) 可讓設定以片段形式和從多個來源傳送。</span><span class="sxs-lookup"><span data-stu-id="79526-107">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="79526-108">目標節點上本機設定管理員 (LCM) 先將片段放在一起，再當成單一設定套用。</span><span class="sxs-lookup"><span data-stu-id="79526-108">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="79526-109">這項功能可讓團隊或個人之間共用設定控制權。</span><span class="sxs-lookup"><span data-stu-id="79526-109">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="79526-110">例如，如果兩個或多個開發人員小組在一項服務共同作業，便有可能每個人都想要建立設定來管理服務的一部分。</span><span class="sxs-lookup"><span data-stu-id="79526-110">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="79526-111">每一種設定可能提取自不同提取伺服器，因此無法將它們加入開發的不同階段。</span><span class="sxs-lookup"><span data-stu-id="79526-111">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="79526-112">部分設定也可讓不同的個人或小組控制設定節點的不同層面，而不需要協調單一設定文件的編輯。</span><span class="sxs-lookup"><span data-stu-id="79526-112">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="79526-113">例如，一個小組可能會負責部署 VM 和作業系統，而另一個小組負責在該 VM 上部署其他應用程式和服務。</span><span class="sxs-lookup"><span data-stu-id="79526-113">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="79526-114">藉由部分設定，每個小組都可以建立自己的設定，而不會讓任一組的設定不必要地複雜。</span><span class="sxs-lookup"><span data-stu-id="79526-114">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="79526-115">您可以藉由推送模式、提取模式或兩者組合來使用部分設定。</span><span class="sxs-lookup"><span data-stu-id="79526-115">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="79526-116">推送模式中的部分設定</span><span class="sxs-lookup"><span data-stu-id="79526-116">Partial configurations in push mode</span></span>

<span data-ttu-id="79526-117">若要在推送模式下使用部分設定，您可以設定目標節點上的 LCM 接收部分設定。</span><span class="sxs-lookup"><span data-stu-id="79526-117">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="79526-118">每個部分設定都必須使用 `Publish-DSCConfiguration` Cmdlet 推送至目標。</span><span class="sxs-lookup"><span data-stu-id="79526-118">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="79526-119">目標節點接著將部分設定結合至單一設定中，您也可以呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來套用設定。</span><span class="sxs-lookup"><span data-stu-id="79526-119">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="79526-120">設定推送模式部分設定的 LCM</span><span class="sxs-lookup"><span data-stu-id="79526-120">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="79526-121">若要設定推送模式中部分設定的 LCM，請對每個部分設定建立 **DSCLocalConfigurationManager** 設定與一個 **PartialConfiguration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="79526-121">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="79526-122">如需設定 LCM 的詳細資訊，請參閱 [Windows 設定本機設定管理員](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="79526-122">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span> <span data-ttu-id="79526-123">下列範例顯示預期會有兩個部分設定的 LCM 設定，其中一個部署作業系統，另一個部署及設定 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="79526-123">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="79526-124">每個部分設定的 **RefreshMode** 均設為 "Push"。</span><span class="sxs-lookup"><span data-stu-id="79526-124">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="79526-125">**PartialConfiguration** 區塊的名稱 (在此情況下為 "ServiceAccountConfig" 和 "SharePointConfig") 必須完全符合推送至目標節點的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="79526-125">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="79526-126">每個 **PartialConfiguration** 區塊的名稱都必須符合設定在設定指令碼中指定的實際名稱，而不是應為目標節點或 `localhost` 名稱的 MOF 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79526-126">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="79526-127">發佈和啟動推送模式部分設定</span><span class="sxs-lookup"><span data-stu-id="79526-127">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="79526-128">然後您可對每個設定呼叫 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)，傳遞包含設定文件的資料夾作為 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="79526-128">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="79526-129">`Publish-DSCConfiguration` 將設定 MOF 檔案放至目標節點。</span><span class="sxs-lookup"><span data-stu-id="79526-129">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="79526-130">發佈這兩種設定之後，您可以在目標節點上呼叫 `Start-DSCConfiguration –UseExisting`。</span><span class="sxs-lookup"><span data-stu-id="79526-130">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="79526-131">例如，如果您編譯了撰寫節點上的下列設定 MOF 文件︰</span><span class="sxs-lookup"><span data-stu-id="79526-131">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="79526-132">您會發行並執行設定，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="79526-132">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="79526-133">執行 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet 的使用者必須在目標節點上具備系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="79526-133">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="79526-134">提取模式中的部分設定</span><span class="sxs-lookup"><span data-stu-id="79526-134">Partial configurations in pull mode</span></span>

<span data-ttu-id="79526-135">部分設定可從一或多個提取伺服器提取 (如需提取伺服器的詳細資訊，請參閱 [Windows PowerShell 期望狀態設定提取伺服器](pullServer.md))。</span><span class="sxs-lookup"><span data-stu-id="79526-135">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="79526-136">若要這樣做，您必須在目標節點上設定 LCM，以提取部分設定，並在提取伺服器上適當地命名和放置設定文件。</span><span class="sxs-lookup"><span data-stu-id="79526-136">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="79526-137">設定提取節點設定 LCM</span><span class="sxs-lookup"><span data-stu-id="79526-137">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="79526-138">若要設定 LCM 從提取伺服器提取部分設定，您必須在 **ConfigurationRepositoryWeb** (適用於 HTTP 提取伺服器) 或 **ConfigurationRepositoryShare** (適用於 SMB 提取伺服器) 區塊定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="79526-138">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="79526-139">接著建立 **PartialConfiguration** 區塊，該區塊可使用 **ConfigurationSource** 屬性參考提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="79526-139">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="79526-140">您也需要建立 **Settings** 區塊以指定 LCM 使用提取模式，並指定提取伺服器與目標節點用來識別設定的 **ConfigurationNames** 或 **ConfigurationID** 。</span><span class="sxs-lookup"><span data-stu-id="79526-140">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="79526-141">下列中繼設定會定義名為 CONTOSO-PullSrv 的 HTTP 提取伺服器，和使用該提取伺服器的兩個部分設定。</span><span class="sxs-lookup"><span data-stu-id="79526-141">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="79526-142">如需使用 **ConfigurationNames** 設定 LCM 的詳細資訊，請參閱 [使用設定名稱設定提取用戶端](pullClientConfigNames.md)。</span><span class="sxs-lookup"><span data-stu-id="79526-142">For more information about configuring the LCM using **ConfigurationNames** , see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="79526-143">如需使用 **ConfigurationID** 設定 LCM 的相關資訊，請參閱 [使用設定識別碼設定提取用戶端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="79526-143">For information about configuring the LCM using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="79526-144">使用設定名稱設定提取節點設定的 LCM</span><span class="sxs-lookup"><span data-stu-id="79526-144">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="79526-145">使用 ConfigurationID 設定提取節點設定的 LCM</span><span class="sxs-lookup"><span data-stu-id="79526-145">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="79526-146">您可以從一部以上的提取伺服器提取部分設定，只需要定義每部提取伺服器，然後在每個 **PartialConfiguration** 區塊中參考適當的提取伺服器即可。</span><span class="sxs-lookup"><span data-stu-id="79526-146">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="79526-147">建立中繼設定之後，您必須執行此設定來建立設定文件 (MOF 檔案)，然後呼叫 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) 以設定 LCM。</span><span class="sxs-lookup"><span data-stu-id="79526-147">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="79526-148">在提取伺服器上放置設定文件並為其命名 (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="79526-148">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="79526-149">部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program
Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79526-149">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="79526-150">PowerShell 5.1 中命名提取伺服器上的命名設定文件</span><span class="sxs-lookup"><span data-stu-id="79526-150">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="79526-151">如果您僅從個別提取伺服器提取單一部分設定，設定文件可以使用任何名稱。</span><span class="sxs-lookup"><span data-stu-id="79526-151">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="79526-152">如果您從提取伺服器提取多個部分設定，設定文件可以命名為 `<ConfigurationName>.mof` (其中 *ConfigurationName* 是部分設定的名稱) 或是 `<ConfigurationName>.<NodeName>.mof` (其中 *ConfigurationName* 是部分設定的名稱，而 *NodeName* 是目標節點的名稱)。</span><span class="sxs-lookup"><span data-stu-id="79526-152">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="79526-153">這可讓您從 Azure 自動化 DSC 提取伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="79526-153">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="79526-154">PowerShell 5.0 中命名提取伺服器上的命名設定文件</span><span class="sxs-lookup"><span data-stu-id="79526-154">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="79526-155">設定文件必須命名如下：`ConfigurationName.mof`，其中 *ConfigurationName* 是部分設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="79526-155">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="79526-156">在此範例中，設定文件應該命名如下：</span><span class="sxs-lookup"><span data-stu-id="79526-156">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="79526-157">在提取伺服器上放置設定文件並為其命名 (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="79526-157">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="79526-158">部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="79526-158">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="79526-159">設定文件必須命名如下：`<ConfigurationName>.<ConfigurationID>.mof`，其中 _ConfigurationName_ 是部分設定的名稱，而 _ConfigurationID_ 是目標節點上 LCM 中所定義的設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="79526-159">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="79526-160">在此範例中，設定文件應該命名如下：</span><span class="sxs-lookup"><span data-stu-id="79526-160">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="79526-161">從提取伺服器中執行部分設定</span><span class="sxs-lookup"><span data-stu-id="79526-161">Running partial configurations from a pull server</span></span>

<span data-ttu-id="79526-162">在已設定目標節點上的 LCM 後，並已在提取伺服器上建立設定文件並正確加以命名後，目標節點將會提取部分設定、結合部分設定，並依據 LCM 屬性 **RefreshFrequencyMins** 所指定的固定間隔套用所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="79526-162">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="79526-163">如果您想要強制重新整理，可以呼叫 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) Cmdlet 以提取設定，然後呼叫 `Start-DSCConfiguration –UseExisting` 加以套用。</span><span class="sxs-lookup"><span data-stu-id="79526-163">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="79526-164">混合推送和提取模式中的部分設定</span><span class="sxs-lookup"><span data-stu-id="79526-164">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="79526-165">您也可以混和部分設定的推送和提取模式。</span><span class="sxs-lookup"><span data-stu-id="79526-165">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="79526-166">也就是說，推送另一個部分設定時，您可能會有一個從提取伺服器提取的部分設定。</span><span class="sxs-lookup"><span data-stu-id="79526-166">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="79526-167">指定每個部分設定的重新整理模式，如同先前小節中所述。</span><span class="sxs-lookup"><span data-stu-id="79526-167">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="79526-168">例如，下列中繼設定描述相同的範例，其中 `ServiceAccountConfig` 部分設定處於 Pull 模式，而 `SharePointConfig` 部分設定則處於 Push 模式。</span><span class="sxs-lookup"><span data-stu-id="79526-168">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="79526-169">使用 ConfigurationNames 的混合推送和提取模式</span><span class="sxs-lookup"><span data-stu-id="79526-169">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="79526-170">使用 ConfigurationID 的混合推送和提取模式</span><span class="sxs-lookup"><span data-stu-id="79526-170">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="79526-171">請注意，在 Settings 區塊中指定的 **RefreshMode** 為 "Pull"，但 `SharePointConfig` 部分設定的 **RefreshMode** 則是 "Push"。</span><span class="sxs-lookup"><span data-stu-id="79526-171">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="79526-172">如上面所述，對其各自的重新整理模式命名和放置設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="79526-172">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="79526-173">呼叫 `Publish-DSCConfiguration` 來發佈 `SharePointConfig` 部分設定，然後等待 `ServiceAccountConfig` 設定從提取伺服器上提取，或藉由呼叫 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) 強制重新整理。</span><span class="sxs-lookup"><span data-stu-id="79526-173">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="79526-174">ServiceAccountConfig 部分設定範例</span><span class="sxs-lookup"><span data-stu-id="79526-174">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="79526-175">SharePointConfig 部分設定範例</span><span class="sxs-lookup"><span data-stu-id="79526-175">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="79526-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79526-176">See Also</span></span>

[<span data-ttu-id="79526-177">Windows PowerShell 預期狀態設定提取伺服器</span><span class="sxs-lookup"><span data-stu-id="79526-177">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="79526-178">Windows 設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="79526-178">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
