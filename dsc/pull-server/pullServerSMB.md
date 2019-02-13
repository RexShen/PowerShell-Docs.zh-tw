---
ms.date: 04/11/2018
keywords: dsc,powershell,設定,安裝
title: 設定 DSC SMB 提取伺服器
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676697"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>設定 DSC SMB 提取伺服器

適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) 提取伺服器是裝載 SMB 檔案共用的電腦，可在目標節點要求時，將 DSC 設定檔和 DSC 資源提供給這些節點使用。

若要針對 DSC 使用 SMB 提取伺服器，您必須︰

- 在執行 PowerShell 4.0 或更新版本的伺服器上設定 SMB 檔案共用
- 設定執行 PowerShell 4.0 或更新版本的用戶端從該 SMB 共用提取

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>使用 xSmbShare 資源建立 SMB 檔案共用

設定 SMB 檔案共用的方式有幾種，讓我們看看如何使用 DSC 來執行這項作業。

### <a name="install-the-xsmbshare-resource"></a>安裝 xSmbShare 資源

呼叫 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 安裝 **xSmbShare** 模組。

> [!NOTE]
> `Install-Module` 已納入 **PowerShellGet** 模組，此模組隨附於 PowerShell 5.0。 您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。
> **XSmbShare** 包含 DSC 資源 **xSmbShare**，可用來建立 SMB 檔案共用。

### <a name="create-the-directory-and-file-share"></a>建立目錄和檔案共用

下列設定使用 **File** 資源為共用建立目錄，並使用 **xSmbShare** 資源設定 SMB 共用︰

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

此設定會建立目錄`C:\DscSmbShare`，如果它尚未存在，並接著該目錄做為 SMB 檔案共用。 **FullAccess**應該授予需要寫入或刪除檔案共用中的任何帳戶。 **ReadAccess**必須有從共用取得設定及 （或） DSC 資源的任何用戶端節點。

> [!NOTE]
> DSC 預設會以執行 「 系統 」 帳戶，因此電腦本身必須具有共用的存取權。

### <a name="give-file-system-access-to-the-pull-client"></a>將檔案系統存取權授與提取用戶端

將 **ReadAccess** 授與用戶端節點可讓該節點存取 SMB 共用，但無法存取該共用內的檔案或資料夾。 您必須明確授與用戶端節點存取 SMB 共用資料夾和子資料夾。 我們可以透過 DSC 來達成，方法是使用 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 模組中所包含的 **cNtfsPermissionEntry** 資源來新增。 下列設定會新增 **cNtfsPermissionEntry** 區塊，將 ReadAndExecute 存取權授與提取用戶端︰

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

## <a name="placing-configurations-and-resources"></a>放置設定和資源

儲存您想要用戶端節點提取到 SMB 共用資料夾的任何設定 MOF 檔案及 (或) DSC 資源。

任何設定 MOF 檔案必須命名為 *ConfigurationID*.mof，其中 *ConfigurationID* 是目標節點 LCM 的 **ConfigurationID** 屬性值。 如需有關設定提取用戶端的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。

> [!NOTE]
> 如果您使用 SMB 提取伺服器，就必須使用設定識別碼。 SMB 不支援設定名稱。

每個資源模組都必須根據下列模式進行壓縮及命名：`{Module Name}_{Module Version}.zip`。 例如，名為 xWebAdminstration 且模組版本為 3.1.2.0 的模組會命名為 'xWebAdministration_3.2.1.0.zip'。 一個壓縮檔必須包含一個模組版本。 不支援不同版本的模組 zip 檔案中。 在封裝 DSC 資源模組，以搭配提取伺服器使用之前，您需要的目錄結構進行小幅變更。

WMF 5.0 中包含 DSC 資源的模組預設格式為 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`。

針對提取伺服器進行封裝之前，只需移除 `{Module version}` 資料夾，以便讓路徑變成 `{Module Folder}\DscResources\{DSC Resource Folder}\`。 完成這項變更之後，如上所述壓縮資料夾，並將這些壓縮檔放在 SMB 共用資料夾中。

## <a name="creating-the-mof-checksum"></a>建立 MOF 總和檢查碼

設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。
若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) Cmdlet。 此 Cmdlet 會使用 `Path` 參數來指定設定 MOF 所在的資料夾。 此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。
如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。

總和檢查碼檔案必須存在於和設定 MOF 檔案相同的目錄中 (預設為 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`)，而且具有相同名稱，附加副檔名為 `.checksum`。

> [!NOTE]
> 如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。

## <a name="setting-up-a-pull-client-for-smb"></a>設定 SMB 的提取用戶端

若要設定從 SMB 共用提取設定及/或資源的用戶端，您可以使用 **ConfigurationRepositoryShare** 和 **ResourceRepositoryShare** 區塊設定用戶端的本機設定管理員 (LCM)，指定要從中提取設定和 DSC 資源的共用。

如需設定 LCM 的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。

> [!NOTE]
> 為了簡單起見，這個範例使用 **PSDscAllowPlainTextPassword**，以允許將純文字密碼傳遞至 **Credential** 參數。 如需更安全地傳遞認證的詳細資訊，請參閱[設定資料的認證選項](../configurations/configDataCredentials.md)。
>
> 即使您只要提取資源，也**必須**在 SMB 提取伺服器之中繼設定的 [設定] 區塊中指定 **ConfigurationID**。

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

## <a name="acknowledgements"></a>致謝

感謝以下特殊：

- Mike F. Robbins，本主題中的內容參考了他所撰寫有關針對 DSC 使用 SMB 的文章。 他的部落格位於 [Mike F Robbins](http://mikefrobbins.com/)。
- Serge Nikalaichyk，負責撰寫 **cNtfsAccessControl** 模組。 此模組的來源位置為 [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 預期狀態設定概觀](../overview/overview.md)

[制定組態](enactingConfigurations.md)

[使用設定識別碼設定提取用戶端](pullClientConfigID.md)
