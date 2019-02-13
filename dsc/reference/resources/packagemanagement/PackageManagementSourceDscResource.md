---
ms.date: 06/20/2018
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagementSource 資源
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677013"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1

Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。 **以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。** 此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。

> [!IMPORTANT]
> **PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。

## <a name="syntax"></a>語法

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Properties

|  屬性  |  描述   |
|---|---|
| 名稱| 指定要在您的系統上註冊或取消註冊的套件來源名稱。|
| ProviderName| 指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。|
| SourceLocation| 指定套件來源的 URI。|
| Ensure| 判斷套件來源是否已註冊或已取消註冊。|
| InstallationPolicy| 由內建 Nuget 提供者之類的提供者使用。 判斷您是否信任套件來源。 值為： 或  其中一個。「 不受信任 」，「 信任 」。|
| SourceCredential| 提供遠端來源套件的存取權。|

## <a name="example"></a>範例

此範例會使用 **PackageManagementSource** DSC 資源註冊 http://nuget.org 套件來源。

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```