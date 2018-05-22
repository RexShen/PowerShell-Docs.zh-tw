---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 在 PowerShell 4.0 使用設定識別碼設定提取用戶端
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="667e3-103">在 PowerShell 4.0 使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="667e3-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="667e3-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="667e3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="667e3-105">必須告知每個目標節點使用提取模式和指定的 URL，其中它可連絡提取伺服器以取得設定。</span><span class="sxs-lookup"><span data-stu-id="667e3-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="667e3-106">若要這樣做，您必須使用必要的資訊來設定本機設定管理員 (LCM)。</span><span class="sxs-lookup"><span data-stu-id="667e3-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="667e3-107">若要設定 LCM，您可以建立一種特殊的設定，稱為「中繼設定」。</span><span class="sxs-lookup"><span data-stu-id="667e3-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="667e3-108">如需設定 LCM 的詳細資訊，請參閱 [Windows PowerShell 4.0 預期狀態設定本機設定管理員](metaConfig4.md)</span><span class="sxs-lookup"><span data-stu-id="667e3-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="667e3-109">下列指令碼會設定 LCM 從名為 "PullServer" 的伺服器提取設定：</span><span class="sxs-lookup"><span data-stu-id="667e3-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="667e3-110">在此指令碼中，**DownloadManagerCustomData** 會傳遞提取伺服器的 URL，並 (適用於此範例) 允許不安全的連線。</span><span class="sxs-lookup"><span data-stu-id="667e3-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="667e3-111">執行這個指令碼之後，它會建立新的輸出資料夾，稱為 **SimpleMetaConfigurationForPull**，並在該處放入中繼設定 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="667e3-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="667e3-112">若要套用此設定，請以 **ComputerName** (使用 "localhost") 和 **Path** (目標節點的 localhost.meta.mof 檔案位置路徑) 參數使用 **Set-DscLocalConfigurationManager**。</span><span class="sxs-lookup"><span data-stu-id="667e3-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="667e3-113">例如：</span><span class="sxs-lookup"><span data-stu-id="667e3-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="667e3-114">設定識別碼</span><span class="sxs-lookup"><span data-stu-id="667e3-114">Configuration ID</span></span>
<span data-ttu-id="667e3-115">此指令碼將 LCM 的 **ConfigurationID** 屬性設為先前針對這個用途建立的 GUID (可透過 **New-Guid** Cmdlet 建立 GUID)。</span><span class="sxs-lookup"><span data-stu-id="667e3-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="667e3-116">**ConfigurationID** 供 LCM 用來在提取伺服器上尋找適當設定。</span><span class="sxs-lookup"><span data-stu-id="667e3-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="667e3-117">提取伺服器上的設定 MOF 檔案必須命名為 `ConfigurationID.mof`，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="667e3-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="667e3-118">從 SMB 伺服器提取</span><span class="sxs-lookup"><span data-stu-id="667e3-118">Pulling from an SMB server</span></span>

<span data-ttu-id="667e3-119">如果將提取伺服器設定為 SMB 檔案共用，而不是 Web 服務，您會指定 **DscFileDownloadManager**，而不是 **WebDownLoadManager**。</span><span class="sxs-lookup"><span data-stu-id="667e3-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="667e3-120">**DscFileDownloadManager** 採用 **SourcePath** 屬性而非 **ServerUrl**。</span><span class="sxs-lookup"><span data-stu-id="667e3-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="667e3-121">下列指令碼會設定 LCM，使其從名為 "CONTOSO-SERVER" 的伺服器上名為 "SmbDscShare" 的 SMB 共用提取設定：</span><span class="sxs-lookup"><span data-stu-id="667e3-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
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
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="667e3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="667e3-122">See Also</span></span>

- [<span data-ttu-id="667e3-123">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="667e3-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="667e3-124">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="667e3-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)