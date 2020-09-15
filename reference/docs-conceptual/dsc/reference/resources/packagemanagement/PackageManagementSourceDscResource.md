---
ms.date: 07/15/2020
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagementSource 資源
ms.openlocfilehash: b24558574f192347aace5a809d57385e01d9acb3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463885"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.x

Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。
**以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。** 此資源需要 **PackageManagement** 模組，可從 [PowerShell Gallery](https://PowerShellGallery.com) 取得。

> [!IMPORTANT]
> **PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。

## <a name="syntax"></a>語法

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>屬性

|屬性 |描述 |
|---|---|
|名稱 |指定要在您的系統上註冊或取消註冊的套件來源名稱。 |
|ProviderName |指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。 |
|SourceLocation |指定套件來源的 URI。 |
|InstallationPolicy |由內建 Nuget 提供者之類的提供者使用。 判斷您是否信任套件來源。 值為下列其中之一：**Untrusted**、**Trusted**。 |
|SourceCredential |提供遠端來源套件的存取權。 |

## <a name="common-properties"></a>通用屬性

|屬性 |描述 |
|---|---|
|DependsOn |表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |判斷套件來源是否已註冊或已取消註冊。 預設值為 **Present**。 |
|PsDscRunAsCredential |設定用於執行整個資源的認證。 |

> [!NOTE]
> 已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。 如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。

## <a name="example"></a>範例

此範例會使用 **PackageManagementSource** DSC 資源註冊 `https://nuget.org` 套件來源。

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```
