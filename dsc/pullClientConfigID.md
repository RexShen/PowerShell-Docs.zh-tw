---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用設定識別碼設定提取用戶端
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="a784a-103">使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="a784a-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="a784a-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a784a-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a784a-105">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="a784a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a784a-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="a784a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a784a-107">必須告知每個目標節點使用提取模式和指定的 URL，其中它可連絡提取伺服器以取得設定。</span><span class="sxs-lookup"><span data-stu-id="a784a-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="a784a-108">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="a784a-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="a784a-109">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="a784a-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="a784a-110">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="a784a-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="a784a-111">**注意**：本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="a784a-111">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="a784a-112">如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="a784a-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="a784a-113">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="a784a-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="a784a-114">在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="a784a-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="a784a-115">**ServerURL**</span><span class="sxs-lookup"><span data-stu-id="a784a-115">The **ServerURL**</span></span>

<span data-ttu-id="a784a-116">執行這個指令碼之後，它會建立新的輸出資料夾，名為 **PullClientConfigID**，並在該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="a784a-116">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="a784a-117">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="a784a-117">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="a784a-118">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="a784a-118">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="a784a-119">例如：`Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="a784a-119">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="a784a-120">設定識別碼</span><span class="sxs-lookup"><span data-stu-id="a784a-120">Configuration ID</span></span>

<span data-ttu-id="a784a-121">此指令碼將 LCM 的 **ConfigurationID** 屬性設為先前針對這個用途建立的 GUID (您可以透過 **New-Guid** Cmdlet 建立 GUID)。</span><span class="sxs-lookup"><span data-stu-id="a784a-121">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="a784a-122">**ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="a784a-122">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="a784a-123">提取伺服器上的設定 MOF 檔案必須命名為 _ConfigurationID_.mof，其中 _ConfigurationID_ 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="a784a-123">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="a784a-124">SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="a784a-124">SMB pull server</span></span>

<span data-ttu-id="a784a-125">若要設定用戶端從 SMB 伺服器提取設定，請使用 **ConfigurationRepositoryShare** 區塊。</span><span class="sxs-lookup"><span data-stu-id="a784a-125">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="a784a-126">在 **ConfigurationRepositoryShare** 區塊中，您可以設定 **SourcePath** 屬性指定伺服器的路徑。</span><span class="sxs-lookup"><span data-stu-id="a784a-126">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="a784a-127">下列中繼設定會設定目標節點從名為 **SMBPullServer** 的 SMB 提取伺服器提取。</span><span class="sxs-lookup"><span data-stu-id="a784a-127">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="a784a-128">資源和報表伺服器</span><span class="sxs-lookup"><span data-stu-id="a784a-128">Resource and report servers</span></span>

<span data-ttu-id="a784a-129">如果在 LCM 設定中只指定了 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如上述範例所示)，提取用戶端將會從指定的伺服器提取資源，但不會將報表傳送給伺服器。</span><span class="sxs-lookup"><span data-stu-id="a784a-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="a784a-130">您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。</span><span class="sxs-lookup"><span data-stu-id="a784a-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="a784a-131">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="a784a-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }


        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="a784a-132">您也可以對資源和報告指定不同的提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="a784a-132">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="a784a-133">若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。</span><span class="sxs-lookup"><span data-stu-id="a784a-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="a784a-134">若要指定報表伺服器，您可使用 **ReportRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="a784a-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="a784a-135">報表伺服器不得為 SMB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a784a-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="a784a-136">下列中繼設定會設定提取用戶端從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源，然後傳送狀態報表給 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="a784a-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

## <a name="see-also"></a><span data-ttu-id="a784a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a784a-137">See Also</span></span>

* [<span data-ttu-id="a784a-138">以設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="a784a-138">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)