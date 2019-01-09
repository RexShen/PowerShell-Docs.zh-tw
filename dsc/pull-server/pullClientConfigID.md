---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定提取用戶端使用設定識別碼，在 PowerShell 5.0 和更新版本
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400772"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="49ef3-103">設定提取用戶端使用設定識別碼，在 PowerShell 5.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="49ef3-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="49ef3-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="49ef3-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49ef3-105">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="49ef3-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="49ef3-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="49ef3-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="49ef3-107">設定提取用戶端之前, 您應該設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="49ef3-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="49ef3-108">雖然此順序並不需要，它會協助進行疑難排解，並幫助您確認註冊成功。</span><span class="sxs-lookup"><span data-stu-id="49ef3-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="49ef3-109">若要設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="49ef3-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="49ef3-110">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="49ef3-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="49ef3-111">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="49ef3-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="49ef3-112">若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。</span><span class="sxs-lookup"><span data-stu-id="49ef3-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="49ef3-113">下列各節會示範如何設定提取用戶端與 SMB 共用或 HTTP DSC 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="49ef3-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="49ef3-114">當節點 LCM 重新整理時，它會連至下載任何指派的組態設定的位置。</span><span class="sxs-lookup"><span data-stu-id="49ef3-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="49ef3-115">如果任何必要的資源不存在的節點上，它會從設定的位置自動下載它們。</span><span class="sxs-lookup"><span data-stu-id="49ef3-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="49ef3-116">如果節點已設有[報表伺服器](reportServer.md)，它接著會報告作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="49ef3-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="49ef3-117">**注意**：本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="49ef3-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="49ef3-118">如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="49ef3-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="49ef3-119">設定提取用戶端 LCM</span><span class="sxs-lookup"><span data-stu-id="49ef3-119">Configure the pull client LCM</span></span>

<span data-ttu-id="49ef3-120">執行任何下列範例會建立新的輸出資料夾，名為**PullClientConfigID**和該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="49ef3-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="49ef3-121">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="49ef3-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="49ef3-122">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="49ef3-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="49ef3-123">例如：</span><span class="sxs-lookup"><span data-stu-id="49ef3-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="49ef3-124">設定識別碼</span><span class="sxs-lookup"><span data-stu-id="49ef3-124">Configuration ID</span></span>

<span data-ttu-id="49ef3-125">下列設定範例**ConfigurationID**屬性將 lcm **Guid** ，先前針對此目的。</span><span class="sxs-lookup"><span data-stu-id="49ef3-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="49ef3-126">**ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="49ef3-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="49ef3-127">提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="49ef3-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="49ef3-128">如需詳細資訊，請參閱[發佈到提取伺服器 (v4/v5) 的組態](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="49ef3-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="49ef3-129">您可以建立的隨機**Guid**下方，或使用範例[New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="49ef3-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="49ef3-130">如需使用詳細資訊**Guid**在您環境中，請參閱[Guid 的計劃](/powershell/dsc/secureserver#guids)。</span><span class="sxs-lookup"><span data-stu-id="49ef3-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="49ef3-131">若要下載組態設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="49ef3-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="49ef3-132">必須設定每個用戶端**提取**模式和指定的提取伺服器的 url 儲存其組態。</span><span class="sxs-lookup"><span data-stu-id="49ef3-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="49ef3-133">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="49ef3-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="49ef3-134">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="49ef3-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="49ef3-135">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="49ef3-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="49ef3-136">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="49ef3-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="49ef3-137">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="49ef3-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="49ef3-138">在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="49ef3-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="49ef3-139">**ServerUrl**指定 DSC 提取的 url</span><span class="sxs-lookup"><span data-stu-id="49ef3-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="49ef3-140">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="49ef3-140">SMB Share</span></span>

<span data-ttu-id="49ef3-141">下列指令碼會設定 LCM 提取設定從 SMB 共用`\\SMBPullServer\Pull`。</span><span class="sxs-lookup"><span data-stu-id="49ef3-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="49ef3-142">在 指令碼**ConfigurationRepositoryShare**區塊定義提取伺服器，即在此情況下，只是 SMB 共用。</span><span class="sxs-lookup"><span data-stu-id="49ef3-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="49ef3-143">設定提取用戶端下載資源</span><span class="sxs-lookup"><span data-stu-id="49ef3-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="49ef3-144">如果您只有指定**ConfigurationRepositoryWeb**或是**ConfigurationRepositoryShare**封鎖在 LCM 設定 （如同上述範例中），提取用戶端會從相同的資源它會擷取其組態的位置。</span><span class="sxs-lookup"><span data-stu-id="49ef3-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="49ef3-145">您也可以指定不同資源的位置。</span><span class="sxs-lookup"><span data-stu-id="49ef3-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="49ef3-146">若要指定資源位置做為個別的伺服器，請使用**ResourceRepositoryWeb**區塊。</span><span class="sxs-lookup"><span data-stu-id="49ef3-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="49ef3-147">若要指定為 SMB 共用的資源位置，請使用**ResourceRepositoryShare**區塊。</span><span class="sxs-lookup"><span data-stu-id="49ef3-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="49ef3-148">您可以結合**ConfigurationRepositoryWeb**具有**ResourceRepositoryShare**或是**ConfigurationRepositoryShare**具有**ResourceRepositoryWeb**.</span><span class="sxs-lookup"><span data-stu-id="49ef3-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="49ef3-149">這個範例不會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="49ef3-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="49ef3-150">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="49ef3-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="49ef3-151">下列中繼設定會設定提取用戶端取得其組態，從**Contoso-pullsrv**和其資源**Contoso-resourcesrv**。</span><span class="sxs-lookup"><span data-stu-id="49ef3-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="49ef3-152">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="49ef3-152">SMB Share</span></span>

<span data-ttu-id="49ef3-153">下列範例示範中繼設定會設定用戶端以提取設定從 SMB 共用的中繼`\\SMBPullServer\Configurations`，並從 SMB 共用的資源`\\SMBPullServer\Resources`。</span><span class="sxs-lookup"><span data-stu-id="49ef3-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="49ef3-154">自動下載在推送模式中的資源</span><span class="sxs-lookup"><span data-stu-id="49ef3-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="49ef3-155">從 PowerShell 5.0 開始，您的提取用戶端可以下載模組從 SMB 共用，即使它們已針對**推播**模式。</span><span class="sxs-lookup"><span data-stu-id="49ef3-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="49ef3-156">這是在情況下您不想設定提取伺服器中特別有用。</span><span class="sxs-lookup"><span data-stu-id="49ef3-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="49ef3-157">**ResourceRepositoryShare**區塊可以用未指定**ConfigurationRepositoryShare**。</span><span class="sxs-lookup"><span data-stu-id="49ef3-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="49ef3-158">下列範例示範中繼設定會設定用戶端以提取資源從 SMB 共用， `\\SMBPullServer\Resources`。</span><span class="sxs-lookup"><span data-stu-id="49ef3-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="49ef3-159">當節點已**PUSHED**設定時，它會自動下載任何必要的資源，從指定的共用。</span><span class="sxs-lookup"><span data-stu-id="49ef3-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="49ef3-160">設定提取用戶端報告狀態</span><span class="sxs-lookup"><span data-stu-id="49ef3-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="49ef3-161">根據預設，節點不會傳送報表至已設定的提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="49ef3-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="49ef3-162">您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。</span><span class="sxs-lookup"><span data-stu-id="49ef3-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="49ef3-163">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="49ef3-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="49ef3-164">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="49ef3-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="49ef3-165">若要指定報表伺服器，您可使用 **ReportRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="49ef3-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="49ef3-166">報表伺服器不得為 SMB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="49ef3-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="49ef3-167">下列中繼設定會設定提取用戶端從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源，然後傳送狀態報表給 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="49ef3-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="49ef3-168">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="49ef3-168">SMB Share</span></span>

<span data-ttu-id="49ef3-169">報表伺服器不是 SMB 共用。</span><span class="sxs-lookup"><span data-stu-id="49ef3-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="49ef3-170">後續步驟</span><span class="sxs-lookup"><span data-stu-id="49ef3-170">Next Steps</span></span>

<span data-ttu-id="49ef3-171">設定提取用戶端之後, 您可以使用下列指南來執行後續步驟：</span><span class="sxs-lookup"><span data-stu-id="49ef3-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="49ef3-172">將設定發佈至提取伺服器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="49ef3-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="49ef3-173">封裝資源並上傳到提取伺服器 (v4)</span><span class="sxs-lookup"><span data-stu-id="49ef3-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="49ef3-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49ef3-174">See Also</span></span>

* [<span data-ttu-id="49ef3-175">以設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="49ef3-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
