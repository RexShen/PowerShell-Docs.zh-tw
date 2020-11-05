---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 5.0 及更新版本中使用設定識別碼來設定提取用戶端
description: 此文章說明如何在 PowerShell 5.0 與更新版本中使用設定識別碼來設定提取用戶端
ms.openlocfilehash: 601858c08ce9a893a8941823d27fef3a60882b48
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664309"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="ab898-104">在 PowerShell 5.0 及更新版本中使用設定識別碼來設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="ab898-104">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="ab898-105">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ab898-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab898-106">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="ab898-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="ab898-107">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="ab898-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="ab898-108">在設定提取用戶端前，您應先設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab898-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="ab898-109">雖然此順序非必要，但它有助於疑難排解，且可協助您確認註冊成功。</span><span class="sxs-lookup"><span data-stu-id="ab898-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="ab898-110">若要設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="ab898-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="ab898-111">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="ab898-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="ab898-112">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="ab898-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="ab898-113">每個目標節點都設定為下載設定、資源，甚至是報告其狀態。</span><span class="sxs-lookup"><span data-stu-id="ab898-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="ab898-114">下列各節會示範如何使用 SMB 共用或 HTTP DSC 提取伺服器來設定提取用戶端。</span><span class="sxs-lookup"><span data-stu-id="ab898-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="ab898-115">當節點的 LCM 重新整理時，它會連到設定的位置來下載任何所指派設定。</span><span class="sxs-lookup"><span data-stu-id="ab898-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="ab898-116">若有任何必要資源不存在於節點上，則其會自動從設定的位置下載它們。</span><span class="sxs-lookup"><span data-stu-id="ab898-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="ab898-117">若節點已使用[報表伺服器](reportServer.md)進行設定，它接著便會報告作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="ab898-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="ab898-118">本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="ab898-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="ab898-119">如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="ab898-119">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="ab898-120">設定提取用戶端 LCM</span><span class="sxs-lookup"><span data-stu-id="ab898-120">Configure the pull client LCM</span></span>

<span data-ttu-id="ab898-121">執行以下任何一個範例，便會建立名為 **PullClientConfigID** 的新輸出資料夾，並在該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="ab898-121">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="ab898-122">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="ab898-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="ab898-123">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="ab898-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="ab898-124">例如：</span><span class="sxs-lookup"><span data-stu-id="ab898-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="ab898-125">設定識別碼</span><span class="sxs-lookup"><span data-stu-id="ab898-125">Configuration ID</span></span>

<span data-ttu-id="ab898-126">下列範例會將 LCM 的 **ConfigurationID** 屬性設為先前針對這個用途建立的 **Guid** 。</span><span class="sxs-lookup"><span data-stu-id="ab898-126">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="ab898-127">**ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="ab898-127">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="ab898-128">提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="ab898-128">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="ab898-129">如需詳細資訊，請參閱[將設定發佈到提取伺服器 (v4/v5)](publishConfigs.md)。</span><span class="sxs-lookup"><span data-stu-id="ab898-129">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="ab898-130">您可以使用以下範例建立隨機 **Guid** ，或是使用 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ab898-130">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="ab898-131">如需在您環境中使用 **Guid** 的詳細資訊，請參閱 [為 GUID 規劃](secureserver.md#guids)。</span><span class="sxs-lookup"><span data-stu-id="ab898-131">For more information about using **Guids** in your environment, see [Plan for Guids](secureserver.md#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="ab898-132">設定提取用戶端來下載設定</span><span class="sxs-lookup"><span data-stu-id="ab898-132">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="ab898-133">每個用戶端都必須在 **提取** 模式中設定，並提供儲存其設定的提取伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="ab898-133">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="ab898-134">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="ab898-134">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="ab898-135">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="ab898-135">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="ab898-136">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="ab898-136">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="ab898-137">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="ab898-137">HTTP DSC Pull Server</span></span>

<span data-ttu-id="ab898-138">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="ab898-138">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="ab898-139">在此指令碼中， **ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab898-139">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="ab898-140">**ServerUrl** 會指定 DSC 提取的 URL</span><span class="sxs-lookup"><span data-stu-id="ab898-140">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="ab898-141">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="ab898-141">SMB Share</span></span>

<span data-ttu-id="ab898-142">下列指令碼會設定 LCM，從 SMB 共用 `\\SMBPullServer\Pull` 提取設定。</span><span class="sxs-lookup"><span data-stu-id="ab898-142">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="ab898-143">在指令碼中， **ConfigurationRepositoryShare** 區塊會定義提取伺服器 (在此案例中只是一個 SMB 共用)。</span><span class="sxs-lookup"><span data-stu-id="ab898-143">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="ab898-144">設定提取用戶端以下載資源</span><span class="sxs-lookup"><span data-stu-id="ab898-144">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="ab898-145">若您在 LCM 設定中只指定 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如同先前範例)，提取用戶端會從擷取其設定的相同位置提取資源。</span><span class="sxs-lookup"><span data-stu-id="ab898-145">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="ab898-146">您也可以為資源指定不同的位置。</span><span class="sxs-lookup"><span data-stu-id="ab898-146">You can also specify separate locations for resources.</span></span> <span data-ttu-id="ab898-147">若要將資源位置指定為不同的伺服器，請使用 **ResourceRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ab898-147">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="ab898-148">若要將資源位置指定為 SMB 共用，請使用 **ResourceRepositoryShare** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ab898-148">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="ab898-149">您可以將 **ConfigurationRepositoryWeb** 與 **ResourceRepositoryShare** 合併，或是將 **ConfigurationRepositoryShare** 與 **ResourceRepositoryWeb** 合併。</span><span class="sxs-lookup"><span data-stu-id="ab898-149">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="ab898-150">此範例不會在以下顯示。</span><span class="sxs-lookup"><span data-stu-id="ab898-150">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="ab898-151">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="ab898-151">HTTP DSC Pull Server</span></span>

<span data-ttu-id="ab898-152">下列中繼設定會設定提取用戶端，以從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源。</span><span class="sxs-lookup"><span data-stu-id="ab898-152">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="ab898-153">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="ab898-153">SMB Share</span></span>

<span data-ttu-id="ab898-154">下列範例會顯示中繼設定，其設定用戶端從 SMB 共用 `\\SMBPullServer\Configurations` 提取設定，並從 SMB 共用 `\\SMBPullServer\Resources` 提取資源。</span><span class="sxs-lookup"><span data-stu-id="ab898-154">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="ab898-155">在推送模式中自動下載資源</span><span class="sxs-lookup"><span data-stu-id="ab898-155">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="ab898-156">從 PowerShell 5.0 開始，您的提取用戶端可從 SMB 共用下載模組，即使它們已針對 [推送] 模式設定也一樣。</span><span class="sxs-lookup"><span data-stu-id="ab898-156">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="ab898-157">這在您不想要設定提取伺服器的案例中特別有用。</span><span class="sxs-lookup"><span data-stu-id="ab898-157">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="ab898-158">**ResourceRepositoryShare** 區塊可在不指定 **ConfigurationRepositoryShare** 的情況下使用。</span><span class="sxs-lookup"><span data-stu-id="ab898-158">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="ab898-159">下列範例會顯示中繼設定，其設定用戶端從 SMB 共用 `\\SMBPullServer\Resources` 提取資源。</span><span class="sxs-lookup"><span data-stu-id="ab898-159">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="ab898-160">當節點獲得 **推送** 設定時，它便會從指定的共用自動下載任何必要資源。</span><span class="sxs-lookup"><span data-stu-id="ab898-160">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="ab898-161">設定提取用戶端以報告狀態</span><span class="sxs-lookup"><span data-stu-id="ab898-161">Set up a Pull Client to report status</span></span>

<span data-ttu-id="ab898-162">根據預設，節點不會將報告傳送到設定的提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab898-162">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="ab898-163">您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。</span><span class="sxs-lookup"><span data-stu-id="ab898-163">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="ab898-164">HTTP DSC 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="ab898-164">HTTP DSC Pull Server</span></span>

<span data-ttu-id="ab898-165">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab898-165">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="ab898-166">若要指定報表伺服器，您可使用 **ReportRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="ab898-166">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="ab898-167">報表伺服器不得為 SMB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="ab898-167">A report server cannot be an SMB server.</span></span> <span data-ttu-id="ab898-168">下列中繼設定會設定提取用戶端從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源，然後傳送狀態報表給 **CONTOSO-ReportSrv** ：</span><span class="sxs-lookup"><span data-stu-id="ab898-168">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv** , and to send status reports to **CONTOSO-ReportSrv** :</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="ab898-169">SMB 共用</span><span class="sxs-lookup"><span data-stu-id="ab898-169">SMB Share</span></span>

<span data-ttu-id="ab898-170">報表伺服器不可以是 SMB 共用。</span><span class="sxs-lookup"><span data-stu-id="ab898-170">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ab898-171">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ab898-171">Next Steps</span></span>

<span data-ttu-id="ab898-172">設定提取用戶端之後，您可以使用下列指南來執行後續步驟：</span><span class="sxs-lookup"><span data-stu-id="ab898-172">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="ab898-173">將設定發佈至提取伺服器 (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="ab898-173">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="ab898-174">封裝資源並上傳到提取伺服器 (v4)</span><span class="sxs-lookup"><span data-stu-id="ab898-174">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="ab898-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab898-175">See Also</span></span>

- [<span data-ttu-id="ab898-176">以設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="ab898-176">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
