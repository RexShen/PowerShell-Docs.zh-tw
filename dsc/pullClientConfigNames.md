---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用設定名稱設定提取用戶端
ms.openlocfilehash: d71376d84b9d4b0e74fdccab4b9249b2ca4263cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188086"
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="50a3b-103">使用設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="50a3b-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="50a3b-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="50a3b-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50a3b-105">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="50a3b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="50a3b-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="50a3b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="50a3b-107">必須告知每個目標節點使用提取模式和指定的 URL，其中它可連絡提取伺服器以取得設定。</span><span class="sxs-lookup"><span data-stu-id="50a3b-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="50a3b-108">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="50a3b-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="50a3b-109">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="50a3b-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="50a3b-110">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="50a3b-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="50a3b-111">**注意**：本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="50a3b-111">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="50a3b-112">如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[使用 PowerShell 4.0 中的設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="50a3b-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="50a3b-113">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定：</span><span class="sxs-lookup"><span data-stu-id="50a3b-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="50a3b-114">在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="50a3b-115">**ServerURL** 屬性會指定提取伺服器的端點。</span><span class="sxs-lookup"><span data-stu-id="50a3b-115">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="50a3b-116">**RegistrationKey** 屬性是提取伺服器的所有用戶端節點與該提取伺服器之間的共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="50a3b-116">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="50a3b-117">相同的值儲存在提取伺服器上的檔案。</span><span class="sxs-lookup"><span data-stu-id="50a3b-117">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="50a3b-118">**ConfigurationNames** 屬性是陣列，會指定用於用戶端節點的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="50a3b-118">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="50a3b-119">在該提取伺服器上，此用戶端節點的設定 MOF 檔案名稱必須為 *ConfigurationNames*.mof，其中 *ConfigurationNames* 符合您在此中繼設定中設定的 **ConfigurationNames** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="50a3b-119">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="50a3b-120">**注意：** 如果您在 **ConfigurationNames**指定一個以上的值，就也必須在設定中指定 **PartialConfiguration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="50a3b-120">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="50a3b-121">如需部分設定的相關資訊，請參閱 [PowerShell 預期狀態設定部分設定](partialConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="50a3b-121">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="50a3b-122">執行這個指令碼之後，它會建立新的輸出資料夾，名為 **PullClientConfigNames**，並在該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="50a3b-122">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="50a3b-123">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="50a3b-123">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="50a3b-124">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="50a3b-124">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="50a3b-125">**注意**：註冊金鑰僅適用於 Web 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-125">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="50a3b-126">您仍然必須使用 **ConfigurationID** 與 SMB 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-126">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="50a3b-127">如需使用 **ConfigurationID** 設定提取伺服器的資訊，請參閱[使用設定識別碼設定提取用戶端](PullClientConfigNames.md)</span><span class="sxs-lookup"><span data-stu-id="50a3b-127">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="50a3b-128">資源和報表伺服器</span><span class="sxs-lookup"><span data-stu-id="50a3b-128">Resource and report servers</span></span>

<span data-ttu-id="50a3b-129">如果在 LCM 設定中只指定了 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如上述範例所示)，提取用戶端將會從指定的伺服器提取資源，但不會將報表傳送給伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="50a3b-130">您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。</span><span class="sxs-lookup"><span data-stu-id="50a3b-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="50a3b-131">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="50a3b-132">您也可以對資源和報告指定不同的提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-132">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="50a3b-133">若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。</span><span class="sxs-lookup"><span data-stu-id="50a3b-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="50a3b-134">若要指定報表伺服器，您可使用 **ReportRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="50a3b-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="50a3b-135">報表伺服器不得為 SMB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="50a3b-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="50a3b-136">下列中繼設定會設定提取用戶端從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源，然後傳送狀態報表給 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="50a3b-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="50a3b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50a3b-137">See Also</span></span>

* [<span data-ttu-id="50a3b-138">以設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="50a3b-138">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="50a3b-139">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="50a3b-139">Setting up a DSC web pull server</span></span>](pullServer.md)