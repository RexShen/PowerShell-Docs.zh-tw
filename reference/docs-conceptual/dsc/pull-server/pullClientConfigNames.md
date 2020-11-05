---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 5.0 及更新版本中使用設定名稱來設定提取用戶端
description: 此文章說明如何在 PowerShell 5.0 與更新版本中使用設定名稱來設定提取用戶端
ms.openlocfilehash: db2b08605dd8bc7e48d9d5153861ce9b36118e21
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644910"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="767dc-104">在 PowerShell 5.0 及更新版本中使用設定名稱來設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="767dc-104">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="767dc-105">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="767dc-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="767dc-106">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="767dc-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="767dc-107">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="767dc-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="767dc-108">在設定提取用戶端前，您應先設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="767dc-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="767dc-109">雖然此順序非必要，但它有助於疑難排解，且可協助您確認註冊成功。</span><span class="sxs-lookup"><span data-stu-id="767dc-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="767dc-110">若要設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="767dc-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="767dc-111">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="767dc-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="767dc-112">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="767dc-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="767dc-113">每個目標節點都設定為下載設定、資源，甚至是報告其狀態。</span><span class="sxs-lookup"><span data-stu-id="767dc-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="767dc-114">下列各節會示範如何使用 SMB 共用或 HTTP DSC 提取伺服器來設定提取用戶端。</span><span class="sxs-lookup"><span data-stu-id="767dc-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="767dc-115">當節點的 LCM 重新整理時，它會連到設定的位置來下載任何所指派設定。</span><span class="sxs-lookup"><span data-stu-id="767dc-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="767dc-116">若有任何必要資源不存在於節點上，則其會自動從設定的位置下載它們。</span><span class="sxs-lookup"><span data-stu-id="767dc-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="767dc-117">若節點已使用[報表伺服器](reportServer.md)進行設定，它接著便會報告作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="767dc-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="767dc-118">本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="767dc-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="767dc-119">如需在 PowerShell 4.0 中設定提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="767dc-119">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="767dc-120">設定提取用戶端 LCM</span><span class="sxs-lookup"><span data-stu-id="767dc-120">Configure the pull client LCM</span></span>

<span data-ttu-id="767dc-121">執行以下任何一個範例，便會建立名為 **PullClientConfigName** 的新輸出資料夾，並在該處放置中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="767dc-121">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="767dc-122">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="767dc-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="767dc-123">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="767dc-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="767dc-124">例如：</span><span class="sxs-lookup"><span data-stu-id="767dc-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="767dc-125">設定名稱</span><span class="sxs-lookup"><span data-stu-id="767dc-125">Configuration Name</span></span>

<span data-ttu-id="767dc-126">下列範例會將 LCM 的 **ConfigurationName** 屬性設為專為此用途建立的先前編譯設定名稱。</span><span class="sxs-lookup"><span data-stu-id="767dc-126">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="767dc-127">**ConfigurationName** 可讓 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="767dc-127">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="767dc-128">提取伺服器上的設定 MOF 檔案必須命名為 `<ConfigurationName>.mof`，在此案例中為 "ClientConfig.mof"。</span><span class="sxs-lookup"><span data-stu-id="767dc-128">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="767dc-129">如需詳細資訊，請參閱[將設定發佈到提取伺服器 (v4/v5)](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="767dc-129">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="767dc-130">設定提取用戶端來下載設定</span><span class="sxs-lookup"><span data-stu-id="767dc-130">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="767dc-131">每個用戶端都必須在 **提取** 模式中設定，並提供儲存其設定的提取伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="767dc-131">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="767dc-132">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="767dc-132">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="767dc-133">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="767dc-133">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="767dc-134">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="767dc-134">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="767dc-135">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="767dc-135">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="767dc-136">在此指令碼中， **ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="767dc-136">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="767dc-137">**ServerURL** 屬性會指定提取伺服器的端點。</span><span class="sxs-lookup"><span data-stu-id="767dc-137">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="767dc-138">**RegistrationKey** 屬性是提取伺服器的所有用戶端節點與該提取伺服器之間的共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="767dc-138">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="767dc-139">相同的值儲存在提取伺服器上的檔案。</span><span class="sxs-lookup"><span data-stu-id="767dc-139">The same value is stored in a file on the pull server.</span></span><span data-ttu-id="767dc-140"> > [!NOTE] > 註冊金鑰僅適用於 **Web** 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="767dc-140"> > [!NOTE] > Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="767dc-141">您在 **SMB** 提取伺服器仍必須使用 **ConfigurationID** 。</span><span class="sxs-lookup"><span data-stu-id="767dc-141">You must still use **ConfigurationID** with an **SMB** pull server.</span></span> <span data-ttu-id="767dc-142">> 如需使用 **ConfigurationID** 設定提取伺服器的資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="767dc-142">> For information about configuring a pull server by using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="767dc-143">**ConfigurationNames** 屬性是陣列，會指定用於用戶端節點的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="767dc-143">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span><span data-ttu-id="767dc-144"> >**注意：** 如果您在 **ConfigurationNames** 中指定多個值，就也必須在設定中指定 **PartialConfiguration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="767dc-144"> >**Note:** If you specify more than one value in the **ConfigurationNames** , you must also specify **PartialConfiguration** blocks in your configuration.</span></span> <span data-ttu-id="767dc-145">> 如需部分設定的相關資訊，請參閱 [PowerShell Desired State Configuration 部分設定](partialConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="767dc-145">>For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="767dc-146">設定提取用戶端以下載資源</span><span class="sxs-lookup"><span data-stu-id="767dc-146">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="767dc-147">若您在 LCM 設定中只指定 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如同先前範例)，提取用戶端會從儲存您 ".mof" 檔案的相同位置提取資源。</span><span class="sxs-lookup"><span data-stu-id="767dc-147">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="767dc-148">您也可以指定不同位置，讓用戶端可以下載資源。</span><span class="sxs-lookup"><span data-stu-id="767dc-148">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="767dc-149">若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。</span><span class="sxs-lookup"><span data-stu-id="767dc-149">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="767dc-150">下列範例會顯示中繼設定，其設定用戶端從提取伺服器下載設定，並從 SMB 共用下載資源。</span><span class="sxs-lookup"><span data-stu-id="767dc-150">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="767dc-151">設定提取用戶端以報告狀態</span><span class="sxs-lookup"><span data-stu-id="767dc-151">Set up a Pull Client to report status</span></span>

<span data-ttu-id="767dc-152">您可以針對設定、資源和報告使用單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="767dc-152">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="767dc-153">根據預設，不會針對用戶端設定報告。</span><span class="sxs-lookup"><span data-stu-id="767dc-153">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="767dc-154">若要設定用戶端報告狀態，您必須建立一個 **ReportRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="767dc-154">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="767dc-155">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="767dc-155">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="767dc-156">報表伺服器不可以是 SMB 共用。</span><span class="sxs-lookup"><span data-stu-id="767dc-156">A report server cannot be an SMB share.</span></span>

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
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="767dc-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="767dc-157">See Also</span></span>

- [<span data-ttu-id="767dc-158">以設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="767dc-158">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
- [<span data-ttu-id="767dc-159">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="767dc-159">Setting up a DSC web pull server</span></span>](pullServer.md)
