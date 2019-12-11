---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 資源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954245"
---
# <a name="dsc-resources"></a>DSC 資源

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。 資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。

資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。  類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。

每個資源都有一個*結構描述，可判斷在[設定](../configurations/configurations.md)中使用資源所需的語法。 您可以透過下列方式定義資源的結構描述：

- **'Schema.Mof'** 檔案：大部分的資源都會使用[受控物件格式](/windows/desktop/wmisdk/managed-object-format--mof-)，在 '.schema.mof' 檔案中定義其「結構描述」  。
- **'\<資源名稱\>.schema.psm1'** 檔案：[複合資源](../configurations/compositeConfigs.md)會使用[參數區塊](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)，在 '<ResourceName>.schema.psm1' 檔案中定義其「結構描述」  。
- **'\<資源名稱\>.psm1'** 檔案：以類別為基礎的 DSC 資源會在類別定義中定義其「結構描述」  。 語法項目會標示為 Class 屬性。 如需詳細資訊，請參閱 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。

若要擷取 DSC 資源的語法，請搭配 `-Syntax` 參數使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet。 此使用方式類似於搭配 `-Syntax` 參數使用 [Get-Command](/powershell/module/microsoft.powershell.core/get-command) 來取得 Cmdlet 語法。 您看到的輸出將顯示針對您指定之資源的資源區塊所使用的範本。

```powershell
Get-DscResource -Syntax Service
```

雖然此資源的語法未來可能變更，但您看到的輸出應該類似下列輸出。 如同 Cmdlet 語法，方括弧中的「索引鍵」  均為選擇性。 類型會指定每個索引鍵所預期的資料類型。

> [!NOTE]
> **Ensure** 索引鍵是選擇性的，因為它會預設為 "Present"。

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

在設定內部，**服務**資源區塊可能看起來像這樣，以**確保**多工緩衝處理器服務正在執行。

> [!NOTE]
> 在設定中使用資源之前，您必須先使用 [Import-DSCResource](../configurations/import-dscresource.md) 來匯入該資源。

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

設定可以包含相同資源類型的多個執行個體。 每個執行個體都必須具有唯一名稱。 在下列範例中，會新增第二個**服務**資源區塊來設定 "DHCP" 服務。

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> 從 PowerShell 5.0 開始，已針對 DSC 新增 IntelliSense。 此新功能可讓您使用 \<TAB\> 和 \<Ctrl+空格鍵\> 自動完成索引鍵名稱。

![資源 Tab 鍵自動完成](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>內建資源

除了社群資源，還提供適用於 Windows 的內建資源、適用於 Linux 的資源，以及適用於跨節點相依性的資源。 您可以使用上述步驟，來判斷這些資源的語法以及使用它們的方式。 提供這些資源的頁面都已封存於**參考**下方。

Windows 內建資源

* [封存資源](../reference/resources/windows/archiveResource.md)
* [環境資源](../reference/resources/windows/environmentResource.md)
* [檔案資源](../reference/resources/windows/fileResource.md)
* [群組資源](../reference/resources/windows/groupResource.md)
* [GroupSet 資源](../reference/resources/windows/groupSetResource.md)
* [記錄檔資源](../reference/resources/windows/logResource.md)
* [封裝資源](../reference/resources/windows/packageResource.md)
* [ProcessSet 資源](../reference/resources/windows/ProcessSetResource.md)
* [登錄資源](../reference/resources/windows/registryResource.md)
* [指令碼資源](../reference/resources/windows/scriptResource.md)
* [服務資源](../reference/resources/windows/serviceResource.md)
* [ServiceSet 資源](../reference/resources/windows/serviceSetResource.md)
* [使用者資源](../reference/resources/windows/userResource.md)
* [WindowsFeature 資源](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet 資源](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature 資源](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet 資源](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource 資源](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess 資源](../reference/resources/windows/windowsProcessResource.md)

[跨節點相依性](../configurations/crossNodeDependencies.md)資源

* [WaitForAll 資源](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome 資源](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny 資源](../reference/resources/windows/waitForAnyResource.md)

套件管理資源

* [PackageManagement 資源](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource 資源](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux 資源

* [Linux 封存資源](../reference/resources/linux/lnxArchiveResource.md)
* [Linux 環境資源](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine 資源](../reference/resources/linux/lnxFileLineResource.md)
* [Linux 檔案資源](../reference/resources/linux/lnxFileResource.md)
* [Linux 群組資源](../reference/resources/linux/lnxGroupResource.md)
* [Linux 套件資源](../reference/resources/linux/lnxPackageResource.md)
* [Linux 指令碼資源](../reference/resources/linux/lnxScriptResource.md)
* [Linux 服務資源](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys 資源](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux 使用者資源](../reference/resources/linux/lnxUserResource.md)
