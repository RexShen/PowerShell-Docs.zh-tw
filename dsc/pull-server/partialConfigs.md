---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: PowerShell 預期狀態設定部分設定
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676553"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="0282f-103">PowerShell 預期狀態設定部分設定</span><span class="sxs-lookup"><span data-stu-id="0282f-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="0282f-104">_適用於︰Windows PowerShell 5.0 及更新版本。_</span><span class="sxs-lookup"><span data-stu-id="0282f-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="0282f-105">在 PowerShell 5.0 中，預期狀態設定 (DSC) 可讓設定以片段形式和從多個來源傳送。</span><span class="sxs-lookup"><span data-stu-id="0282f-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="0282f-106">目標節點上本機設定管理員 (LCM) 先將片段放在一起，再當成單一設定套用。</span><span class="sxs-lookup"><span data-stu-id="0282f-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="0282f-107">這項功能可讓團隊或個人之間共用設定控制權。</span><span class="sxs-lookup"><span data-stu-id="0282f-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="0282f-108">例如，如果兩個或多個開發人員小組在一項服務共同作業，便有可能每個人都想要建立設定來管理服務的一部分。</span><span class="sxs-lookup"><span data-stu-id="0282f-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="0282f-109">每一種設定可能提取自不同提取伺服器，因此無法將它們加入開發的不同階段。</span><span class="sxs-lookup"><span data-stu-id="0282f-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="0282f-110">部分設定也可讓不同的個人或小組控制設定節點的不同層面，而不需要協調單一設定文件的編輯。</span><span class="sxs-lookup"><span data-stu-id="0282f-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="0282f-111">例如，一個小組可能會負責部署 VM 和作業系統，而另一個小組負責在該 VM 上部署其他應用程式和服務。</span><span class="sxs-lookup"><span data-stu-id="0282f-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="0282f-112">藉由部分設定，每個小組都可以建立自己的設定，而不會讓任一組的設定不必要地複雜。</span><span class="sxs-lookup"><span data-stu-id="0282f-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="0282f-113">您可以藉由推送模式、提取模式或兩者組合來使用部分設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="0282f-114">推送模式中的部分設定</span><span class="sxs-lookup"><span data-stu-id="0282f-114">Partial configurations in push mode</span></span>

<span data-ttu-id="0282f-115">若要在推送模式下使用部分設定，您可以設定目標節點上的 LCM 接收部分設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="0282f-116">每個部分設定都必須使用 `Publish-DSCConfiguration` Cmdlet 推送至目標。</span><span class="sxs-lookup"><span data-stu-id="0282f-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="0282f-117">目標節點接著會將部分設定結合至單一設定中，您也可以呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來套用設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="0282f-118">設定推送模式部分設定的 LCM</span><span class="sxs-lookup"><span data-stu-id="0282f-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="0282f-119">若要設定推送模式中部分設定的 LCM，請對每個部分設定建立 **DSCLocalConfigurationManager** 設定與一個 **PartialConfiguration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="0282f-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="0282f-120">如需設定 LCM 的詳細資訊，請參閱 [Windows Configuring the Local Configuration Manager (Windows 設定本機設定管理員)](/powershell/dsc/metaConfig)。</span><span class="sxs-lookup"><span data-stu-id="0282f-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span> <span data-ttu-id="0282f-121">下列範例顯示預期會有兩個部分設定的 LCM 設定，其中一個部署作業系統，另一個部署及設定 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="0282f-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="0282f-122">每個部分設定的 **RefreshMode** 設為 "Push"。</span><span class="sxs-lookup"><span data-stu-id="0282f-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="0282f-123">**PartialConfiguration** 區塊的名稱 (在此情況下為 "ServiceAccountConfig" 和 "SharePointConfig") 必須完全符合推送至目標節點的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="0282f-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="0282f-124">每個 **PartialConfiguration** 區塊的名稱都必須符合設定在設定指令碼中指定的實際名稱，而不是應為目標節點或 `localhost` 名稱的 MOF 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0282f-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="0282f-125">發佈和啟動推送模式部分設定</span><span class="sxs-lookup"><span data-stu-id="0282f-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="0282f-126">然後您可對每個設定呼叫 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)，傳遞包含設定文件的資料夾作為 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="0282f-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="0282f-127">`Publish-DSCConfiguration` 將設定 MOF 檔案放至目標節點。</span><span class="sxs-lookup"><span data-stu-id="0282f-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="0282f-128">發佈這兩種設定之後，您可以在目標節點上呼叫 `Start-DSCConfiguration –UseExisting`。</span><span class="sxs-lookup"><span data-stu-id="0282f-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="0282f-129">例如，如果您編譯了撰寫節點上的下列設定 MOF 文件︰</span><span class="sxs-lookup"><span data-stu-id="0282f-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

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

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="0282f-130">您會發行並執行設定，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="0282f-130">You would publish and run the configurations as follows:</span></span>

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
> <span data-ttu-id="0282f-131">執行 [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet 的使用者必須在目標節點上具備系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="0282f-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="0282f-132">提取模式中的部分設定</span><span class="sxs-lookup"><span data-stu-id="0282f-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="0282f-133">部分設定可從一或多個提取伺服器提取 (如需提取伺服器的詳細資訊，請參閱 [Windows PowerShell 期望狀態設定提取伺服器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="0282f-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="0282f-134">若要這樣做，您必須在目標節點上設定 LCM，以提取部分設定，並在提取伺服器上適當地命名和放置設定文件。</span><span class="sxs-lookup"><span data-stu-id="0282f-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="0282f-135">設定提取節點設定 LCM</span><span class="sxs-lookup"><span data-stu-id="0282f-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="0282f-136">若要設定 LCM 從提取伺服器提取部分設定，您必須在 **ConfigurationRepositoryWeb** (適用於 HTTP 提取伺服器) 或 **ConfigurationRepositoryShare** (適用於 SMB 提取伺服器) 區塊定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="0282f-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="0282f-137">接著建立 **PartialConfiguration** 區塊，該區塊可使用 **ConfigurationSource** 屬性參考提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="0282f-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="0282f-138">您也需要建立 **Settings** 區塊以指定 LCM 使用提取模式，並指定提取伺服器與目標節點用來識別設定的 **ConfigurationNames** 或 **ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="0282f-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="0282f-139">下列中繼設定會定義名為 CONTOSO-PullSrv 的 HTTP 提取伺服器，和使用該提取伺服器的兩個部分設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="0282f-140">如需使用 **ConfigurationNames** 設定 LCM 的詳細資訊，請參閱[使用設定名稱設定提取用戶端](pullClientConfigNames.md)。</span><span class="sxs-lookup"><span data-stu-id="0282f-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="0282f-141">如需使用 **ConfigurationID** 設定 LCM 的相關資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="0282f-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="0282f-142">使用設定名稱設定提取節點設定的 LCM</span><span class="sxs-lookup"><span data-stu-id="0282f-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="0282f-143">使用 ConfigurationID 設定提取節點設定的 LCM</span><span class="sxs-lookup"><span data-stu-id="0282f-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="0282f-144">您可以從一部以上的提取伺服器提取部分設定，只需要定義每部提取伺服器，然後在每個 **PartialConfiguration** 區塊中參考適當的提取伺服器即可。</span><span class="sxs-lookup"><span data-stu-id="0282f-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="0282f-145">建立中繼設定之後，您必須執行此設定來建立設定文件 (MOF 檔案)，然後呼叫 [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) 以設定 LCM。</span><span class="sxs-lookup"><span data-stu-id="0282f-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="0282f-146">在提取伺服器上放置設定文件並為其命名 (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="0282f-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="0282f-147">部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program
Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0282f-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="0282f-148">PowerShell 5.1 中命名提取伺服器上的命名設定文件</span><span class="sxs-lookup"><span data-stu-id="0282f-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="0282f-149">如果您僅從個別提取伺服器提取單一部分設定，設定文件可以使用任何名稱。</span><span class="sxs-lookup"><span data-stu-id="0282f-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="0282f-150">如果您從提取伺服器提取多個部分設定，設定文件可以命名為 `<ConfigurationName>.mof` (其中 *ConfigurationName* 是部分設定的名稱) 或是 `<ConfigurationName>.<NodeName>.mof` (其中 *ConfigurationName* 是部分設定的名稱，而 *NodeName* 是目標節點的名稱)。</span><span class="sxs-lookup"><span data-stu-id="0282f-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="0282f-151">這可讓您從 Azure 自動化 DSC 提取伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="0282f-152">PowerShell 5.0 中命名提取伺服器上的命名設定文件</span><span class="sxs-lookup"><span data-stu-id="0282f-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="0282f-153">設定文件必須命名如下：`ConfigurationName.mof`，其中 *ConfigurationName* 是部分設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="0282f-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="0282f-154">在此範例中，設定文件應該命名如下：</span><span class="sxs-lookup"><span data-stu-id="0282f-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="0282f-155">在提取伺服器上放置設定文件並為其命名 (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="0282f-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="0282f-156">部分設定文件必須位於提取伺服器的 `web.config` 檔案 (通常為 `C:\Program Files\WindowsPowerShell\DscService\Configuration`) 內指定為 **ConfigurationPath** 的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0282f-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="0282f-157">設定文件必須命名如下：`<ConfigurationName>.<ConfigurationID>.mof`，其中 _ConfigurationName_ 是部分設定的名稱，而 _ConfigurationID_ 是目標節點上 LCM 中所定義的設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="0282f-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="0282f-158">在此範例中，設定文件應該命名如下：</span><span class="sxs-lookup"><span data-stu-id="0282f-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="0282f-159">從提取伺服器中執行部分設定</span><span class="sxs-lookup"><span data-stu-id="0282f-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="0282f-160">已在目標節點上設定 LCM 之後，且已在提取伺服器上建立並正確將設定文件命名之後，目標節點將會提取部分設定、結合部分設定，並依據 LCM 屬性 **RefreshFrequencyMins** 所指定的固定間隔套用所產生的設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="0282f-161">如果您想要強制重新整理，可以呼叫 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) Cmdlet 以提取設定，然後呼叫 `Start-DSCConfiguration –UseExisting` 加以套用。</span><span class="sxs-lookup"><span data-stu-id="0282f-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="0282f-162">混合推送和提取模式中的部分設定</span><span class="sxs-lookup"><span data-stu-id="0282f-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="0282f-163">您也可以混和部分設定的推送和提取模式。</span><span class="sxs-lookup"><span data-stu-id="0282f-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="0282f-164">也就是說，推送另一個部分設定時，您可能會有一個從提取伺服器提取的部分設定。</span><span class="sxs-lookup"><span data-stu-id="0282f-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="0282f-165">指定每個部分設定的重新整理模式，如同先前小節中所述。</span><span class="sxs-lookup"><span data-stu-id="0282f-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="0282f-166">例如，下列中繼設定描述相同的範例，其中 `ServiceAccountConfig` 部分設定處於 Pull 模式，而 `SharePointConfig` 部分設定則處於 Push 模式。</span><span class="sxs-lookup"><span data-stu-id="0282f-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="0282f-167">使用 ConfigurationNames 的混合推送和提取模式</span><span class="sxs-lookup"><span data-stu-id="0282f-167">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="0282f-168">使用 ConfigurationID 的混合推送和提取模式</span><span class="sxs-lookup"><span data-stu-id="0282f-168">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="0282f-169">請注意，在 Settings 區塊中指定的 **RefreshMode** 為 "Pull"，但 `SharePointConfig` 部分設定的 **RefreshMode** 則是 "Push"。</span><span class="sxs-lookup"><span data-stu-id="0282f-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="0282f-170">如上面所述，對其各自的重新整理模式命名和放置設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="0282f-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="0282f-171">呼叫 `Publish-DSCConfiguration` 來發佈 `SharePointConfig` 部分設定，然後等待 `ServiceAccountConfig` 設定從提取伺服器上提取，或藉由呼叫 [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) 強制重新整理。</span><span class="sxs-lookup"><span data-stu-id="0282f-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="0282f-172">ServiceAccountConfig 部分設定範例</span><span class="sxs-lookup"><span data-stu-id="0282f-172">Example ServiceAccountConfig Partial Configuration</span></span>

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

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="0282f-173">SharePointConfig 部分設定範例</span><span class="sxs-lookup"><span data-stu-id="0282f-173">Example SharePointConfig Partial Configuration</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0282f-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0282f-174">See Also</span></span>

[<span data-ttu-id="0282f-175">Windows PowerShell 預期狀態設定提取伺服器</span><span class="sxs-lookup"><span data-stu-id="0282f-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="0282f-176">Windows 設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="0282f-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)