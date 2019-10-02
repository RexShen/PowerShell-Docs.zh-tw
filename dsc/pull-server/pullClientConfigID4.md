---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 4.0 中使用設定識別碼來設定提取用戶端
ms.openlocfilehash: 9259c624c8725f7d76f61e9ad7caa42e1bfa308c
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324869"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="fb788-103">在 PowerShell 4.0 中使用設定識別碼來設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="fb788-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="fb788-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fb788-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb788-105">提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="fb788-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="fb788-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="fb788-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="fb788-107">在設定提取用戶端前，您應先設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="fb788-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="fb788-108">雖然此順序非必要，但它有助於疑難排解，且可協助您確認註冊成功。</span><span class="sxs-lookup"><span data-stu-id="fb788-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="fb788-109">若要設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="fb788-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="fb788-110">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="fb788-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="fb788-111">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="fb788-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="fb788-112">每個目標節點都設定為下載設定、資源，甚至是報告其狀態。</span><span class="sxs-lookup"><span data-stu-id="fb788-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="fb788-113">下列各節會示範如何使用 SMB 共用或 HTTP DSC 提取伺服器來設定提取用戶端。</span><span class="sxs-lookup"><span data-stu-id="fb788-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="fb788-114">當節點的 LCM 重新整理時，它會連到設定的位置來下載任何所指派設定。</span><span class="sxs-lookup"><span data-stu-id="fb788-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="fb788-115">若有任何必要資源不存在於節點上，則其會自動從設定的位置下載它們。</span><span class="sxs-lookup"><span data-stu-id="fb788-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="fb788-116">若節點已使用[報表伺服器](reportServer.md)進行設定，它接著便會報告作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="fb788-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="fb788-117">設定提取用戶端 LCM</span><span class="sxs-lookup"><span data-stu-id="fb788-117">Configure the pull client LCM</span></span>

<span data-ttu-id="fb788-118">執行以下任何一個範例，便會建立名為 **PullClientConfigID** 的新輸出資料夾，並在該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="fb788-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="fb788-119">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="fb788-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="fb788-120">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="fb788-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="fb788-121">例如：</span><span class="sxs-lookup"><span data-stu-id="fb788-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="fb788-122">設定識別碼</span><span class="sxs-lookup"><span data-stu-id="fb788-122">Configuration ID</span></span>

<span data-ttu-id="fb788-123">下列範例會將 LCM 的 **ConfigurationID** 屬性設定為先前基於此用途建立的 **Guid**。</span><span class="sxs-lookup"><span data-stu-id="fb788-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="fb788-124">**ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="fb788-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="fb788-125">提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="fb788-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="fb788-126">如需詳細資訊，請參閱[將設定發佈到提取伺服器 (v4/v5)](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="fb788-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="fb788-127">您可以使用下列範例來建立隨機的 **Guid**。</span><span class="sxs-lookup"><span data-stu-id="fb788-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="fb788-128">設定提取用戶端來下載設定</span><span class="sxs-lookup"><span data-stu-id="fb788-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="fb788-129">每個用戶端都必須在**提取**模式中設定，並提供儲存其設定的提取伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="fb788-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="fb788-130">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="fb788-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="fb788-131">若要設定 LCM，您可以搭配 **DSCLocalConfigurationManager** 區塊來建立特殊類型的設定。</span><span class="sxs-lookup"><span data-stu-id="fb788-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="fb788-132">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="fb788-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="fb788-133">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="fb788-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="fb788-134">如果將提取伺服器設定為 Web 服務，您就要將 **DownloadManagerName** 設定為 **WebDownloadManager**。</span><span class="sxs-lookup"><span data-stu-id="fb788-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="fb788-135">**WebDownloadManager** 要求您為 **DownloadManagerCustomData** 索引碼指定 **ServerUrl**。</span><span class="sxs-lookup"><span data-stu-id="fb788-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="fb788-136">您也可以指定 **AllowUnsecureConnection** 的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fb788-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="fb788-137">下列指令碼會設定 LCM 從名為 "PullServer" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="fb788-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="fb788-138">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="fb788-138">SMB Share</span></span>

<span data-ttu-id="fb788-139">如果將提取伺服器設定為 SMB 檔案共用，而不是 Web 服務，您就要將 **DownloadManagerName** 設定為 **DscFileDownloadManager**，而不是 **WebDownLoadManager**。</span><span class="sxs-lookup"><span data-stu-id="fb788-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="fb788-140">**DscFileDownloadManager** 要求您在 **DownloadManagerCustomData** 中指定 **SourcePath** 屬性。</span><span class="sxs-lookup"><span data-stu-id="fb788-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="fb788-141">下列指令碼會設定 LCM，使其從名為 "CONTOSO-SERVER" 的伺服器上名為 "SmbDscShare" 的 SMB 共用提取設定。</span><span class="sxs-lookup"><span data-stu-id="fb788-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="fb788-142">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fb788-142">Next Steps</span></span>

<span data-ttu-id="fb788-143">設定提取用戶端之後，您可以使用下列指南來執行後續步驟：</span><span class="sxs-lookup"><span data-stu-id="fb788-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="fb788-144">將設定發佈至提取伺服器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="fb788-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="fb788-145">封裝資源並上傳到提取伺服器 (v4)</span><span class="sxs-lookup"><span data-stu-id="fb788-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="fb788-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb788-146">See Also</span></span>

- [<span data-ttu-id="fb788-147">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="fb788-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="fb788-148">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="fb788-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
