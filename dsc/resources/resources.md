---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 資源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676941"
---
# <a name="dsc-resources"></a>DSC 資源

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。 資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。

資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。  類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。

每個資源都有 * 判斷使用中的資源所需的語法的結構描述[組態](../configurations/configurations.md)。 可以透過下列方式定義資源的結構描述：

- **'.Schema.mof'** 檔案：大部分的資源定義他們*結構描述*'.schema.mof' 在檔案中，使用[Managed 物件格式](/windows/desktop/wmisdk/managed-object-format--mof-)。
- **'\<資源名稱\>。 schema.psm1'** 檔案：[複合資源](../configurations/compositeConfigs.md)定義其*結構描述*在 '<ResourceName>。 schema.psm1' 檔案中，使用[參數區塊](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)。
- **'\<資源名稱\>.psm1'** 檔案：類別型的 DSC 資源定義他們*結構描述*類別定義中。 語法項目會標示為類別的屬性。 如需詳細資訊，請參閱 < [< about_classes >](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。

若要擷取的 DSC 資源的語法，請使用[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 搭配`-Syntax`參數。 這種使用方式，類似於使用[Get-command](/powershell/module/microsoft.powershell.core/get-command)與`-Syntax`參數，以取得 cmdlet 的語法。 您看到的輸出會顯示您所指定之資源的資源區塊所用的範本。

```powershell
Get-DscResource -Syntax Service
```

雖然此資源的語法可能在未來變更，您看到的輸出應該會類似如下的輸出。 喜歡 cmdlet 語法*金鑰*方括號所示，都是選擇性。 指定每個索引鍵所預期的資料的類型的類型。

> [!NOTE]
> **請確定**金鑰是選擇性的因為它會預設為"Present"。

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

在組態中，內**服務**資源區塊可能會看起來像這樣來**請確定**多工緩衝處理器服務正在執行。

> [!NOTE]
> 之前在組態中使用的資源，您必須匯入使用[Import-dscresource](../configurations/import-dscresource.md)。

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

設定可以包含多個相同的資源類型執行個體。 每個執行個體必須具有唯一名稱。 在下列範例中，第二個**服務**資源區塊會新增至"DHCP"服務設定。

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
> 從 PowerShell 5.0 開始，已新增 DSC intellisense。 這項新功能可讓您使用\< 索引標籤\>並\<Ctrl + 空格鍵\>到自動完成索引鍵的名稱。

![資源 Tab 鍵自動完成](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>內建資源

除了社群資源，還有 Windows、 Linux、 資源和資源跨節點相依性的內建資源。 您可以使用上述步驟，以判斷這些資源和使用方式的語法。 提供這些資源的頁面都已封存底下**參考**。

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
* [WindowsPackageCabResource Resource](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess 資源](../reference/resources/windows/windowsProcessResource.md)

[跨節點相依性](../configurations/crossNodeDependencies.md)資源

* [WaitForAll 資源](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome 資源](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny 資源](../reference/resources/windows/waitForAnyResource.md)

封裝管理資源

* [PackageManagement 資源](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource Resource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux 上的資源

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
