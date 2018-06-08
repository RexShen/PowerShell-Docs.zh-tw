---
ms.date: 06/20/2018
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagement 資源
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753782"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1

Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagement** 資源，提供在目標節點上安裝或解除安裝「套件管理」套件的機制。 此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。

> [!IMPORTANT]
> **PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。

## <a name="syntax"></a>語法

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Properties

|  屬性  |  描述   |
|---|---|
| 名稱| 指定要安裝或解除安裝之套件的名稱。|
| AdditionalParameters| 針對將傳至 `Get-Package -AdditionalArguments` 的參數，特定提供者的雜湊表。 例如，針對 NuGet 提供者，您可以傳遞 DestinationPath 之類的其他參數。|
| Ensure| 判斷是否要安裝或解除安裝套件。|
| MaximumVersion|指定所要尋找套件的最高允許版本。 如果不加入此參數，資源便會尋找可用的最高版本套件。|
| MinimumVersion|指定所要尋找套件的最低允許版本。 如果不加入此參數，資源便會尋找可用的最高版本套件，同時也會滿足 _MaximumVersion_ 參數所指定的最高指定版本。|
| ProviderName| 指定套件提供者名稱，以針對它設定套件搜尋的範圍。 您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。|
| RequiredVersion| 指定您要安裝之套件的確切版本。 如果未指定此參數，此 DSC 資源便會安裝套件的最新可用版本，同時也會滿足 _MaximumVersion_ 參數所指定的最高版本。|
| 來源| 指定可以找到套件的套件來源名稱。 這可以是 URI，或是向 `Register-PackageSource` 或 PackageManagementSource DSC 資源註冊的來源。|
| SourceCredential | 指定有權限安裝指定套件提供者或來源之套件的使用者帳戶。|

## <a name="additional-parameters"></a>其他參數

下表列出 AdditionalParameters 屬性的選項。
|  參數  | 描述   |
|---|---|
| DestinationPath| 由內建 Nuget 提供者之類的提供者使用。 指定您想要安裝套件的檔案位置。|
| InstallationPolicy| 由內建 Nuget 提供者之類的提供者使用。 判斷您是否信任套件來源。 只能是 "Untrusted" 或 "Trusted"。|

## <a name="example"></a>範例

此範例會使用 **PackageManagement** DSC 資源安裝 **JQuery** NuGet 套件和 **GistProvider** PowerShell 模組。 此範例會先確認必要的套件來源可以使用，然後定義 **JQuery** 和 **GistProvider** 套件 (分別是 NuGet 和 PowerShell) 的預期狀態 。

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```