---
ms.date: 04/11/2018
keywords: dsc,powershell,設定,安裝
title: 設定 DSC SMB 提取伺服器
ms.openlocfilehash: 1eac6c51aeca3ed573ba8fa27188103436004920
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892860"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="f5042-103">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="f5042-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="f5042-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f5042-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5042-105">提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="f5042-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="f5042-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="f5042-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="f5042-107">DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 提取伺服器是裝載 SMB 檔案共用的電腦，可在目標節點要求時，將 DSC 設定檔和 DSC 資源提供給這些節點使用。</span><span class="sxs-lookup"><span data-stu-id="f5042-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="f5042-108">若要針對 DSC 使用 SMB 提取伺服器，您必須︰</span><span class="sxs-lookup"><span data-stu-id="f5042-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="f5042-109">在執行 PowerShell 4.0 或更新版本的伺服器上設定 SMB 檔案共用</span><span class="sxs-lookup"><span data-stu-id="f5042-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="f5042-110">設定執行 PowerShell 4.0 或更新版本的用戶端從該 SMB 共用提取</span><span class="sxs-lookup"><span data-stu-id="f5042-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="f5042-111">使用 xSmbShare 資源建立 SMB 檔案共用</span><span class="sxs-lookup"><span data-stu-id="f5042-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="f5042-112">設定 SMB 檔案共用的方式有幾種，讓我們看看如何使用 DSC 來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="f5042-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="f5042-113">安裝 xSmbShare 資源</span><span class="sxs-lookup"><span data-stu-id="f5042-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="f5042-114">呼叫 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 安裝 **xSmbShare** 模組。</span><span class="sxs-lookup"><span data-stu-id="f5042-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="f5042-115">`Install-Module` 已納入 **PowerShellGet** 模組，此模組隨附於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="f5042-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="f5042-116">您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="f5042-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="f5042-117">**XSmbShare** 包含 DSC 資源 **xSmbShare**，可用來建立 SMB 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="f5042-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="f5042-118">建立目錄和檔案共用</span><span class="sxs-lookup"><span data-stu-id="f5042-118">Create the directory and file share</span></span>

<span data-ttu-id="f5042-119">下列設定使用 [File](fileResource.md) 資源為共用建立目錄，並使用 **xSmbShare** 資源設定 SMB 共用︰</span><span class="sxs-lookup"><span data-stu-id="f5042-119">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="f5042-120">此設定會建立目錄 `C:\DscSmbShare` (如果尚未存在)，然後使用該目錄作為 SMB 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="f5042-120">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="f5042-121">**FullAccess** 應該授與需要寫入檔案共用或從中刪除的任何帳戶，而 **ReadAccess** 必須授與會從共用取得設定及/或 DSC 資源的任何用戶端節點 (這是因為 DSC 預設會以系統帳戶執行，因此電腦本身必須具有共用的存取權)。</span><span class="sxs-lookup"><span data-stu-id="f5042-121">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="f5042-122">將檔案系統存取權授與提取用戶端</span><span class="sxs-lookup"><span data-stu-id="f5042-122">Give file system access to the pull client</span></span>

<span data-ttu-id="f5042-123">將 **ReadAccess** 授與用戶端節點可讓該節點存取 SMB 共用，但無法存取該共用內的檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5042-123">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="f5042-124">您必須明確授與 SMB 共用資料夾和子資料夾的用戶端節點存取權。</span><span class="sxs-lookup"><span data-stu-id="f5042-124">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="f5042-125">我們可以透過 DSC 來達成，方法是使用 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 模組中所包含的 **cNtfsPermissionEntry** 資源來新增。</span><span class="sxs-lookup"><span data-stu-id="f5042-125">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="f5042-126">下列設定會新增 **cNtfsPermissionEntry** 區塊，將 ReadAndExecute 存取權授與提取用戶端︰</span><span class="sxs-lookup"><span data-stu-id="f5042-126">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DSCSMB'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="f5042-127">放置設定和資源</span><span class="sxs-lookup"><span data-stu-id="f5042-127">Placing configurations and resources</span></span>

<span data-ttu-id="f5042-128">儲存您想要用戶端節點提取到 SMB 共用資料夾的任何設定 MOF 檔案及 (或) DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f5042-128">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="f5042-129">任何設定 MOF 檔案必須命名為 *ConfigurationID*.mof，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="f5042-129">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="f5042-130">如需有關設定提取用戶端的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="f5042-130">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f5042-131">如果您使用 SMB 提取伺服器，就必須使用設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="f5042-131">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="f5042-132">SMB 不支援設定名稱。</span><span class="sxs-lookup"><span data-stu-id="f5042-132">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="f5042-133">每個資源模組都必須根據下列模式 `{Module Name}_{Module Version}.zip` 進行壓縮及命名。</span><span class="sxs-lookup"><span data-stu-id="f5042-133">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="f5042-134">例如，名為 xWebAdminstration 且模組版本為 3.1.2.0 的模組會命名為 'xWebAdministration_3.2.1.0.zip'。</span><span class="sxs-lookup"><span data-stu-id="f5042-134">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="f5042-135">一個壓縮檔必須包含一個模組版本。</span><span class="sxs-lookup"><span data-stu-id="f5042-135">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="f5042-136">因為每個壓縮檔中只會有一個資源版本，所以不支援在 WMF 5.0 中新增可支援單一目錄中有多個模組版本的模組格式。</span><span class="sxs-lookup"><span data-stu-id="f5042-136">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="f5042-137">這表示在封裝 DSC 資源模組以搭配提取伺服器使用之前，您需要對目錄結構進行小幅變更。</span><span class="sxs-lookup"><span data-stu-id="f5042-137">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="f5042-138">WMF 5.0 中包含 DSC 資源的模組預設格式為 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`。</span><span class="sxs-lookup"><span data-stu-id="f5042-138">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="f5042-139">針對提取伺服器進行封裝之前，只需移除 `{Module version}` 資料夾，以便讓路徑變成 `{Module Folder}\DscResources\{DSC Resource Folder}\`。</span><span class="sxs-lookup"><span data-stu-id="f5042-139">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="f5042-140">完成這項變更之後，如上所述壓縮資料夾，並將這些壓縮檔放在 SMB 共用資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f5042-140">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="f5042-141">建立 MOF 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="f5042-141">Creating the MOF checksum</span></span>

<span data-ttu-id="f5042-142">設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。</span><span class="sxs-lookup"><span data-stu-id="f5042-142">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="f5042-143">若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5042-143">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="f5042-144">此 Cmdlet 會使用 `Path` 參數來指定設定 MOF 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f5042-144">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="f5042-145">此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5042-145">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="f5042-146">如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="f5042-146">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="f5042-147">總和檢查碼檔案必須存在於和設定 MOF 檔案相同的目錄中 (預設為 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`)，而且具有相同名稱，附加副檔名為 `.checksum`。</span><span class="sxs-lookup"><span data-stu-id="f5042-147">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="f5042-148">如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="f5042-148">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="f5042-149">設定 SMB 的提取用戶端</span><span class="sxs-lookup"><span data-stu-id="f5042-149">Setting up a pull client for SMB</span></span>

<span data-ttu-id="f5042-150">若要設定從 SMB 共用提取設定及/或資源的用戶端，您可以使用 **ConfigurationRepositoryShare** 和 **ResourceRepositoryShare** 區塊設定用戶端的本機設定管理員 (LCM)，指定要從中提取設定和 DSC 資源的共用。</span><span class="sxs-lookup"><span data-stu-id="f5042-150">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="f5042-151">如需設定 LCM 的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="f5042-151">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f5042-152">為了簡單起見，這個範例使用 **PSDscAllowPlainTextPassword**，以允許將純文字密碼傳遞至 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="f5042-152">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="f5042-153">如需更安全地傳遞認證的詳細資訊，請參閱[設定資料的認證選項](configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="f5042-153">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>
>
> <span data-ttu-id="f5042-154">即使您只要提取資源，也**必須**在 SMB 提取伺服器之中繼設定的 [設定] 區塊中指定 **ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="f5042-154">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="f5042-155">致謝</span><span class="sxs-lookup"><span data-stu-id="f5042-155">Acknowledgements</span></span>

<span data-ttu-id="f5042-156">特別感謝下列人士：</span><span class="sxs-lookup"><span data-stu-id="f5042-156">Special thanks to the following:</span></span>

- <span data-ttu-id="f5042-157">Mike F. Robbins，本主題中的內容參考了他所撰寫有關針對 DSC 使用 SMB 的文章。</span><span class="sxs-lookup"><span data-stu-id="f5042-157">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="f5042-158">他的部落格位於 [Mike F Robbins](http://mikefrobbins.com/)。</span><span class="sxs-lookup"><span data-stu-id="f5042-158">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="f5042-159">Serge Nikalaichyk，負責撰寫 **cNtfsAccessControl** 模組。</span><span class="sxs-lookup"><span data-stu-id="f5042-159">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="f5042-160">此模組的來源位置為 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)。</span><span class="sxs-lookup"><span data-stu-id="f5042-160">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5042-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5042-161">See also</span></span>

[<span data-ttu-id="f5042-162">Windows PowerShell 預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="f5042-162">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)

[<span data-ttu-id="f5042-163">制定組態</span><span class="sxs-lookup"><span data-stu-id="f5042-163">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="f5042-164">使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="f5042-164">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)