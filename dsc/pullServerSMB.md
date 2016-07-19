---
title: "設定 DSC SMB 提取伺服器"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 35ac9b38086b12fb48844c56a488854f63529e21

---

# 設定 DSC SMB 提取伺服器

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

DSC [SMB](https://technet.microsoft.com/en-us/library/hh831795.aspx) 提取伺服器是 SMB 檔案共用，可在目標節點要求時，將 DSC 設定檔及 (或) DSC 資源提供給這些節點使用。

若要針對 DSC 使用 SMB 提取伺服器，您必須︰
- 在執行 PowerShell 4.0 或更新版本的伺服器上設定 SMB 檔案共用
- 設定執行 PowerShell 4.0 或更新版本的用戶端從該 SMB 共用提取

## 使用 xSmbShare 資源建立 SMB 檔案共用

設定 SMB 檔案共用的方式有幾種，讓我們看看如何使用 DSC 來執行這項作業。

### 安裝 xSmbShare 資源

呼叫 [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) Cmdlet 安裝 **xSmbShare** 模組。
>**注意**：**Install-Module** 已納入 **PowerShellGet** 模組，其隨附於 PowerShell 5.0。 您可以在 [PackageManagement PowerShell 模組預覽](https://www.microsoft.com/en-us/download/details.aspx?id=49186)下載 PowerShell 3.0 和 4.0 的 **PowerShellGet** 模組。 **XSmbShare** 包含 DSC 資源 **xSmbShare**，可用來建立 SMB 檔案共用。

### 建立目錄和檔案共用

下列設定使用 [File](fileResource.md) 資源為共用建立目錄，並使用 **xSmbShare** 設定 SMB 共用︰

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
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

此設定會建立目錄 `C:\DscSmbShare` (如果尚未存在)，然後使用該目錄作為 SMB 檔案共用。 **FullAccess** 應該授予需要寫入檔案共用或從中刪除的任何帳戶，而 **ReadAccess** 必須授予會從共用取得設定且 (或) DSC 資源的任何用戶端節點 (這是因為 DSC 預設會以系統帳戶執行，因此電腦本身必須具有共用的存取權)。


### 將檔案系統存取權授與提取用戶端

將 **ReadAccess** 授與用戶端節點可讓該節點存取 SMB 共用，但無法存取該共用內的檔案或資料夾。 您必須明確授與 SMB 共用資料夾和子資料夾的用戶端節點存取權。 我們可以透過 DSC 來達成，方法是使用 [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) 模組中所包含的 **cNtfsPermissionEntry** 資源來新增。 下列設定會新增 **cNtfsPermissionEntry** 區塊，將 ReadAndExecute 存取權授與提取用戶端︰

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl
 
    Node localhost {
 
        File CreateFolder {
 
            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
 
        }
 
        xSMBShare CreateShare {
 
            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
 
        }

        cNtfsPermissionEntry PermissionSet1 {
            
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

## 放置設定和資源

儲存您想要用戶端節點提取到 SMB 共用資料夾的任何設定 MOF 檔案及 (或) DSC 資源。

任何設定 MOF 檔案必須命名為 _ConfigurationID_.mof，其中 _ConfigurationID_ 是目標節點 LCM 的 **ConfigurationID** 屬性值。 如需有關設定提取用戶端的詳細資訊，請參閱[使用設定識別碼設定提取用戶端](pullClientConfigID.md)。

>**注意**︰如果您使用 SMB 提取伺服器，就必須使用設定識別碼。 SMB 不支援設定名稱。

用戶端所需的任何資源都必須以封存的 `.zip` 檔案形式，放置在 SMB 共用資料夾中。  

## 建立 MOF 總和檢查碼
設定 MOF 檔案需要與總和檢查碼檔案配對，以便目標節點上的 LCM 可驗證設定。 若要建立總和檢查碼，請呼叫 [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) Cmdlet。 此 Cmdlet 會使用 **Path** 參數，指定設定 MOF 所在的資料夾。 此 Cmdlet 會建立名為 `ConfigurationMOFName.mof.checksum` 的總和檢查碼檔案，其中 `ConfigurationMOFName` 是設定 MOF 檔案的名稱。 如果在指定的資料夾中有多個設定 MOF 檔案，就會在每個設定資料夾中各建立一個總和檢查碼。

總和檢查碼檔案必須存在於和設定 MOF 檔案相同的目錄中 (預設為 `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`)，而且具有相同名稱，附加副檔名為 `.checksum`。

>**注意**：如果您以任何方式變更設定 MOF 檔案，也必須重新建立總和檢查碼檔案。

## 致謝

特別感謝下列人士：

- Mike F. Robbins，本主題中的內容參考了他所撰寫有關針對 DSC 使用 SMB 的文章。 他的部落格位於 [Mike F Robbins](http://mikefrobbins.com/)。
- Serge Nikalaichyk，負責撰寫 **cNtfsAccessControl** 模組。 此模組的原始檔位於 https://github.com/SNikalaichyk/cNtfsAccessControl。

## 另請參閱
- [Windows PowerShell 預期狀態設定概觀](overview.md)
- [施行設定](enactingConfigurations.md)
- [使用設定識別碼設定提取用戶端](pullClientConfigID.md)

 



<!--HONumber=Jun16_HO4-->


