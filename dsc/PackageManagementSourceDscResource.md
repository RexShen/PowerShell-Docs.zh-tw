---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC PackageManagementSource 資源"
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。 **以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。** 此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。

## <a name="syntax"></a>語法

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>[內容]
|  屬性  |  描述   | 
|---|---| 
| 名稱| 指定要在您的系統上註冊或取消註冊的套件來源名稱。| 
| Ensure| 判斷套件來源是否已註冊或已取消註冊。| 
| InstallationPolicy| 判斷您是否信任套件來源。 只能是 "Untrusted" 或 "Trusted"。| 
| ProviderName| 指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。| 
| SourceUri| 指定套件來源的 URI。| 
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
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

