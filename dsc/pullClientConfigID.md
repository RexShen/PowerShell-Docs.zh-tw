---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "使用設定識別碼設定提取用戶端"
ms.openlocfilehash: bb14bff95c626b65e2d0d0072c39e4c571cea4b0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="2abd8-103">使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="2abd8-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="2abd8-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2abd8-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2abd8-105">必須告知每個目標節點使用提取模式和指定的 URL，其中它可連絡提取伺服器以取得設定。</span><span class="sxs-lookup"><span data-stu-id="2abd8-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="2abd8-106">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="2abd8-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="2abd8-107">若要設定 LCM，必須先建立一種特殊設定，再加上 **DSCLocalConfigurationManager** 屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="2abd8-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="2abd8-108">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="2abd8-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="2abd8-109">**注意**：本主題適用於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="2abd8-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="2abd8-110">如需設定 PowerShell 4.0 中提取用戶端的資訊，請參閱[在 PowerShell 4.0 中使用設定識別碼設定提取用戶端](pullClientConfigID4.md)。</span><span class="sxs-lookup"><span data-stu-id="2abd8-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="2abd8-111">下列指令碼會設定 LCM 從名為 "CONTOSO-PullSrv" 的伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="2abd8-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="2abd8-112">在此指令碼中，**ConfigurationRepositoryWeb** 區塊會定義提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="2abd8-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="2abd8-113">**ServerURL**</span><span class="sxs-lookup"><span data-stu-id="2abd8-113">The **ServerURL**</span></span>

<span data-ttu-id="2abd8-114">執行這個指令碼之後，它會建立新的輸出資料夾，名為 **PullClientConfigID**，並在該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="2abd8-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="2abd8-115">在此情況下，中繼設定 MOF 檔案將名為 `localhost.meta.mof`。</span><span class="sxs-lookup"><span data-stu-id="2abd8-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="2abd8-116">若要套用設定，請呼叫 **Set-DscLocalConfigurationManager** Cmdlet，其中 **Path** 設為中繼設定 MOF 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="2abd8-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="2abd8-117">例如：`Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="2abd8-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="2abd8-118">設定識別碼</span><span class="sxs-lookup"><span data-stu-id="2abd8-118">Configuration ID</span></span>

<span data-ttu-id="2abd8-119">此指令碼將 LCM 的 **ConfigurationID** 屬性設為先前針對這個用途建立的 GUID (您可以透過 **New-Guid** Cmdlet 建立 GUID)。</span><span class="sxs-lookup"><span data-stu-id="2abd8-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="2abd8-120">**ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="2abd8-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="2abd8-121">提取伺服器上的設定 MOF 檔案必須命名為 _ConfigurationID_.mof，其中 _ConfigurationID_ 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="2abd8-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="2abd8-122">SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="2abd8-122">SMB pull server</span></span>

<span data-ttu-id="2abd8-123">若要設定用戶端從 SMB 伺服器提取設定，請使用 **ConfigurationRepositoryShare** 區塊。</span><span class="sxs-lookup"><span data-stu-id="2abd8-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="2abd8-124">在 **ConfigurationRepositoryShare** 區塊中，您可以設定 **SourcePath** 屬性指定伺服器的路徑。</span><span class="sxs-lookup"><span data-stu-id="2abd8-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="2abd8-125">下列中繼設定會設定目標節點從名為 **SMBPullServer** 的 SMB 提取伺服器提取。</span><span class="sxs-lookup"><span data-stu-id="2abd8-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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

## <a name="resource-and-report-servers"></a><span data-ttu-id="2abd8-126">資源和報表伺服器</span><span class="sxs-lookup"><span data-stu-id="2abd8-126">Resource and report servers</span></span>

<span data-ttu-id="2abd8-127">如果在 LCM 設定中只指定了 **ConfigurationRepositoryWeb** 或 **ConfigurationRepositoryShare** 區塊 (如上述範例所示)，提取用戶端將會從指定的伺服器提取資源，但不會將報表傳送給伺服器。</span><span class="sxs-lookup"><span data-stu-id="2abd8-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="2abd8-128">您可以針對設定、資源和報告使用單一提取伺服器，但必須建立 **ReportRepositoryWeb** 區塊才可設定報告功能。</span><span class="sxs-lookup"><span data-stu-id="2abd8-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="2abd8-129">下列範例示範中繼設定，該中繼設定會設定用戶端以提取設定和資源，並將報告資料傳送至單一提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="2abd8-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="2abd8-130">您也可以對資源和報告指定不同的提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="2abd8-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="2abd8-131">若要指定資源伺服器，您可使用 **ResourceRepositoryWeb** (適用於 Web 提取伺服器) 或 **ResourceRepositoryShare** 區塊 (適用於 SMB 提取伺服器)。</span><span class="sxs-lookup"><span data-stu-id="2abd8-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="2abd8-132">若要指定報表伺服器，您可使用 **ReportRepositoryWeb** 區塊。</span><span class="sxs-lookup"><span data-stu-id="2abd8-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="2abd8-133">報表伺服器不得為 SMB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2abd8-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="2abd8-134">下列中繼設定會設定提取用戶端從 **CONTOSO-PullSrv** 取得其設定，並從 **CONTOSO-ResourceSrv** 取得其資源，然後傳送狀態報表給 **CONTOSO-ReportSrv**：</span><span class="sxs-lookup"><span data-stu-id="2abd8-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2abd8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2abd8-135">See Also</span></span>

* [<span data-ttu-id="2abd8-136">以設定名稱設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="2abd8-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

