---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 設定提取用戶端使用設定名稱，在 PowerShell 5.0 和更新版本
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400896"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="06401-103">設定提取用戶端使用設定名稱，在 PowerShell 5.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="06401-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="06401-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="06401-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06401-105">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="06401-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="06401-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="06401-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="06401-107">設定提取用戶端之前, 您應該設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="06401-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="06401-108">雖然此順序並不需要，它會協助進行疑難排解，並幫助您確認註冊成功。</span><span class="sxs-lookup"><span data-stu-id="06401-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="06401-109">若要設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="06401-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="06401-110">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="06401-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="06401-111">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="06401-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="06401-112">若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。</span><span class="sxs-lookup"><span data-stu-id="06401-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="06401-113">下列各節會示範如何設定提取用戶端與 SMB 共用或 HTTP DSC 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="06401-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="06401-114">當節點 LCM 重新整理時，它會連至下載任何指派的組態設定的位置。</span><span class="sxs-lookup"><span data-stu-id="06401-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="06401-115">如果任何必要的資源不存在的節點上，它會從設定的位置自動下載它們。</span><span class="sxs-lookup"><span data-stu-id="06401-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="06401-116">如果節點已設有[報表伺服器](reportServer.md)，它接著會報告作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="06401-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="06401-117">**注意**：本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="06401-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="06401-118">如需設定 PowerShell 4.0 中提取用戶端的詳細資訊，請參閱[設定提取用戶端在 PowerShell 4.0 使用設定識別碼](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="06401-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="06401-119">設定提取用戶端 LCM</span><span class="sxs-lookup"><span data-stu-id="06401-119">Configure the pull client LCM</span></span>

<span data-ttu-id="06401-120">執行任何下列範例會建立新的輸出資料夾，名為**PullClientConfigName**和該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="06401-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="06401-121">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="06401-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="06401-122">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="06401-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="06401-123">例如：</span><span class="sxs-lookup"><span data-stu-id="06401-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="06401-124">設定名稱</span><span class="sxs-lookup"><span data-stu-id="06401-124">Configuration Name</span></span>

<span data-ttu-id="06401-125">下列設定範例**ConfigurationName**針對這個用途建立的先前已編譯的設定，名稱將 lcm 的屬性。</span><span class="sxs-lookup"><span data-stu-id="06401-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="06401-126">**ConfigurationName**供 LCM 用來尋找適當設定提取伺服器上。</span><span class="sxs-lookup"><span data-stu-id="06401-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="06401-127">提取伺服器的設定 MOF 檔案必須命名為`<ConfigurationName>.mof`，在此案例中，「 ClientConfig.mof"。</span><span class="sxs-lookup"><span data-stu-id="06401-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="06401-128">如需詳細資訊，請參閱 <<c0> [ 發佈到提取伺服器 (v4/v5) 的組態](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="06401-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="06401-129">若要下載組態設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="06401-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="06401-130">必須設定每個用戶端**提取**模式和指定的提取伺服器的 url 儲存其組態。</span><span class="sxs-lookup"><span data-stu-id="06401-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="06401-131">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="06401-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="06401-132">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="06401-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="06401-133">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="06401-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="06401-134">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="06401-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="06401-135">在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="06401-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="06401-136">**ServerURL** 屬性會指定提取伺服器的端點。</span><span class="sxs-lookup"><span data-stu-id="06401-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="06401-137">**RegistrationKey** 屬性是提取伺服器的所有用戶端節點與該提取伺服器之間的共用金鑰。</span><span class="sxs-lookup"><span data-stu-id="06401-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="06401-138">相同的值儲存在提取伺服器上的檔案。</span><span class="sxs-lookup"><span data-stu-id="06401-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="06401-139">**注意**：註冊金鑰僅適用於**web**提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="06401-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="06401-140">您在 **SMB** 提取伺服器仍必須使用 **ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="06401-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="06401-141">如需使用 **ConfigurationID** 設定提取伺服器的資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="06401-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="06401-142">**ConfigurationNames** 屬性是陣列，會指定用於用戶端節點的設定名稱。</span><span class="sxs-lookup"><span data-stu-id="06401-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="06401-143">**注意：** 如果您在 **ConfigurationNames** 中指定多個值，就也必須在設定中指定 **PartialConfiguration** 區塊。</span><span class="sxs-lookup"><span data-stu-id="06401-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="06401-144">如需部分設定的相關資訊，請參閱 [PowerShell 預期狀態設定部分設定](partialConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="06401-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="06401-145">設定提取用戶端下載資源</span><span class="sxs-lookup"><span data-stu-id="06401-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="06401-146">如果您只有指定**ConfigurationRepositoryWeb**或是**ConfigurationRepositoryShare**封鎖在 LCM 設定 （如同上例），提取用戶端會從相同的資源儲存 「.mof 」 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="06401-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="06401-147">您也可以指定不同的位置，其中用戶端可以下載資源。</span><span class="sxs-lookup"><span data-stu-id="06401-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="06401-148">若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。</span><span class="sxs-lookup"><span data-stu-id="06401-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="06401-149">下列範例示範中繼設定，將用戶端設定來設定從提取伺服器，並從 SMB 共用的資源。</span><span class="sxs-lookup"><span data-stu-id="06401-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="06401-150">設定提取用戶端報告狀態</span><span class="sxs-lookup"><span data-stu-id="06401-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="06401-151">您可以針對設定、 資源和報告使用單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="06401-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="06401-152">報告未設定用戶端的預設。</span><span class="sxs-lookup"><span data-stu-id="06401-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="06401-153">若要設定的用戶端報告狀態，您必須建立**ReportRepositoryWeb**區塊。</span><span class="sxs-lookup"><span data-stu-id="06401-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="06401-154">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="06401-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="06401-155">報表伺服器不是 SMB 共用。</span><span class="sxs-lookup"><span data-stu-id="06401-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="06401-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06401-156">See Also</span></span>

* [<span data-ttu-id="06401-157">以設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="06401-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="06401-158">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="06401-158">Setting up a DSC web pull server</span></span>](pullServer.md)
