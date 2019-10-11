---
ms.date: 04/11/2018
keywords: dsc,powershell,設定,安裝
title: 設定 DSC SMB 提取伺服器
ms.openlocfilehash: 25705d9ae06b3ce8daa352142cc0b84793ab6359
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953585"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="3d697-103">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="3d697-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="3d697-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3d697-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d697-105">提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="3d697-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="3d697-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="3d697-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="3d697-107">DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 提取伺服器是裝載 SMB 檔案共用的電腦，可在目標節點要求時，將 DSC 設定檔和 DSC 資源提供給這些節點使用。</span><span class="sxs-lookup"><span data-stu-id="3d697-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="3d697-108">若要針對 DSC 使用 SMB 提取伺服器，您必須︰</span><span class="sxs-lookup"><span data-stu-id="3d697-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="3d697-109">在執行 PowerShell 4.0 或更新版本的伺服器上設定 SMB 檔案共用</span><span class="sxs-lookup"><span data-stu-id="3d697-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="3d697-110">設定執行 PowerShell 4.0 或更新版本的用戶端從該 SMB 共用提取</span><span class="sxs-lookup"><span data-stu-id="3d697-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="3d697-111">使用 xSmbShare 資源建立 SMB 檔案共用</span><span class="sxs-lookup"><span data-stu-id="3d697-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="3d697-112">設定 SMB 檔案共用的方式有幾種，讓我們看看如何使用 DSC 來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="3d697-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="3d697-113">安裝 xSmbShare 資源</span><span class="sxs-lookup"><span data-stu-id="3d697-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="3d697-114">呼叫 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 安裝 **xSmbShare** 模組。</span><span class="sxs-lookup"><span data-stu-id="3d697-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="3d697-115">`Install-Module` 已納入 **PowerShellGet** 模組，此模組隨附於 PowerShell 5.0。</span><span class="sxs-lookup"><span data-stu-id="3d697-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="3d697-116">您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。</span><span class="sxs-lookup"><span data-stu-id="3d697-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="3d697-117">**XSmbShare** 包含 DSC 資源 **xSmbShare**，可用來建立 SMB 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="3d697-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="3d697-118">建立目錄和檔案共用</span><span class="sxs-lookup"><span data-stu-id="3d697-118">Create the directory and file share</span></span>

<span data-ttu-id="3d697-119">下列設定使用 **File** 資源為共用建立目錄，並使用 **xSmbShare** 資源設定 SMB 共用︰</span><span class="sxs-lookup"><span data-stu-id="3d697-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="3d697-120">此設定會建立目錄 `C:\DscSmbShare` (如果尚未存在)，然後使用該目錄作為 SMB 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="3d697-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="3d697-121">**FullAccess** 應授與給需要寫入或刪除檔案共用中項目的任何帳戶。</span><span class="sxs-lookup"><span data-stu-id="3d697-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="3d697-122">**ReadAccess** 必須授與給從共用取得設定和/或 DSC 資源的任何用戶端節點。</span><span class="sxs-lookup"><span data-stu-id="3d697-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="3d697-123">根據預設，DSC 會以系統帳戶執行，因此電腦本身必須具有共用的存取權限。</span><span class="sxs-lookup"><span data-stu-id="3d697-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="3d697-124">將檔案系統存取權授與提取用戶端</span><span class="sxs-lookup"><span data-stu-id="3d697-124">Give file system access to the pull client</span></span>

<span data-ttu-id="3d697-125">將 **ReadAccess** 授與用戶端節點可讓該節點存取 SMB 共用，但無法存取該共用內的檔案或資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d697-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="3d697-126">您必須明確授與 SMB 共用資料夾和子資料夾的用戶端節點存取權。</span><span class="sxs-lookup"><span data-stu-id="3d697-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="3d697-127">我們可以透過 DSC 來達成，方法是使用 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 模組中所包含的 **cNtfsPermissionEntry** 資源來新增。</span><span class="sxs-lookup"><span data-stu-id="3d697-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="3d697-128">下列設定會新增 **cNtfsPermissionEntry** 區塊，將 ReadAndExecute 存取權授與提取用戶端︰</span><span class="sxs-lookup"><span data-stu-id="3d697-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="3d697-129">放置設定和資源</span><span class="sxs-lookup"><span data-stu-id="3d697-129">Placing configurations and resources</span></span>

<span data-ttu-id="3d697-130">儲存您想要用戶端節點提取到 SMB 共用資料夾的任何設定 MOF 檔案及 (或) DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="3d697-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="3d697-131">任何設定 MOF 檔案必須命名為 *ConfigurationID*.mof，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d697-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="3d697-132">如需有關設定提取用戶端的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="3d697-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3d697-133">如果您使用 SMB 提取伺服器，就必須使用設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="3d697-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="3d697-134">SMB 不支援設定名稱。</span><span class="sxs-lookup"><span data-stu-id="3d697-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="3d697-135">每個資源模組都必須根據下列模式進行壓縮及命名：`{Module Name}_{Module Version}.zip`。</span><span class="sxs-lookup"><span data-stu-id="3d697-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="3d697-136">例如，名為 xWebAdminstration 且模組版本為 3.1.2.0 的模組會命名為 'xWebAdministration_3.2.1.0.zip'。</span><span class="sxs-lookup"><span data-stu-id="3d697-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="3d697-137">一個壓縮檔必須包含一個模組版本。</span><span class="sxs-lookup"><span data-stu-id="3d697-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="3d697-138">不支援在 ZIP 檔案中包含不同的模組版本。</span><span class="sxs-lookup"><span data-stu-id="3d697-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="3d697-139">在封裝搭配提取伺服器使用的 DSC 資源模組前，您需要對目錄結構進行小幅變更。</span><span class="sxs-lookup"><span data-stu-id="3d697-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="3d697-140">WMF 5.0 中包含 DSC 資源的模組預設格式為 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`。</span><span class="sxs-lookup"><span data-stu-id="3d697-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="3d697-141">針對提取伺服器進行封裝之前，只需移除 `{Module version}` 資料夾，以便讓路徑變成 `{Module Folder}\DscResources\{DSC Resource Folder}\`。</span><span class="sxs-lookup"><span data-stu-id="3d697-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="3d697-142">完成這項變更之後，如上所述壓縮資料夾，並將這些壓縮檔放在 SMB 共用資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3d697-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="3d697-143">建立 MOF 總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="3d697-143">Creating the MOF checksum</span></span>

<span data-ttu-id="3d697-144">設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。</span><span class="sxs-lookup"><span data-stu-id="3d697-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="3d697-145">若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d697-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="3d697-146">此 Cmdlet 會使用 `Path` 參數來指定設定 MOF 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3d697-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="3d697-147">此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d697-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="3d697-148">如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="3d697-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="3d697-149">總和檢查碼檔案必須存在於和設定 MOF 檔案相同的目錄中 (預設為 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`)，而且具有相同名稱，附加副檔名為 `.checksum`。</span><span class="sxs-lookup"><span data-stu-id="3d697-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="3d697-150">如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="3d697-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="3d697-151">設定 SMB 的提取用戶端</span><span class="sxs-lookup"><span data-stu-id="3d697-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="3d697-152">若要設定從 SMB 共用提取設定及/或資源的用戶端，您可以使用 **ConfigurationRepositoryShare** 和 **ResourceRepositoryShare** 區塊設定用戶端的本機設定管理員 (LCM)，指定要從中提取設定和 DSC 資源的共用。</span><span class="sxs-lookup"><span data-stu-id="3d697-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="3d697-153">如需設定 LCM 的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。</span><span class="sxs-lookup"><span data-stu-id="3d697-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3d697-154">為了簡單起見，這個範例使用 **PSDscAllowPlainTextPassword**，以允許將純文字密碼傳遞至 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="3d697-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="3d697-155">如需更安全地傳遞認證的詳細資訊，請參閱[設定資料的認證選項](../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="3d697-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="3d697-156">即使您只要提取資源，也**必須**在 SMB 提取伺服器之中繼設定的 [設定]  區塊中指定 **ConfigurationID**。</span><span class="sxs-lookup"><span data-stu-id="3d697-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

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

## <a name="acknowledgements"></a><span data-ttu-id="3d697-157">致謝</span><span class="sxs-lookup"><span data-stu-id="3d697-157">Acknowledgements</span></span>

<span data-ttu-id="3d697-158">特別感謝下列人員：</span><span class="sxs-lookup"><span data-stu-id="3d697-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="3d697-159">Mike F. Robbins，本主題中的內容參考了他所撰寫有關針對 DSC 使用 SMB 的文章。</span><span class="sxs-lookup"><span data-stu-id="3d697-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="3d697-160">他的部落格位於 [Mike F Robbins](http://mikefrobbins.com/)。</span><span class="sxs-lookup"><span data-stu-id="3d697-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="3d697-161">Serge Nikalaichyk，負責撰寫 **cNtfsAccessControl** 模組。</span><span class="sxs-lookup"><span data-stu-id="3d697-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="3d697-162">此模組的來源位置為 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)。</span><span class="sxs-lookup"><span data-stu-id="3d697-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d697-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d697-163">See also</span></span>

[<span data-ttu-id="3d697-164">Windows PowerShell 預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="3d697-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="3d697-165">制定組態</span><span class="sxs-lookup"><span data-stu-id="3d697-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="3d697-166">使用設定識別碼設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="3d697-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
