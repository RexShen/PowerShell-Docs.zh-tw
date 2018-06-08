---
ms.date: 06/20/2018
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagementSource 資源
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753765"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="7547a-103">DSC PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="7547a-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="7547a-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0、Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="7547a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="7547a-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。</span><span class="sxs-lookup"><span data-stu-id="7547a-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="7547a-106">**以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="7547a-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="7547a-107">此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。</span><span class="sxs-lookup"><span data-stu-id="7547a-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7547a-108">**PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="7547a-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="7547a-109">語法</span><span class="sxs-lookup"><span data-stu-id="7547a-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7547a-110">Properties</span><span class="sxs-lookup"><span data-stu-id="7547a-110">Properties</span></span>

|  <span data-ttu-id="7547a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7547a-111">Property</span></span>  |  <span data-ttu-id="7547a-112">描述</span><span class="sxs-lookup"><span data-stu-id="7547a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="7547a-113">名稱</span><span class="sxs-lookup"><span data-stu-id="7547a-113">Name</span></span>| <span data-ttu-id="7547a-114">指定要在您的系統上註冊或取消註冊的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="7547a-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="7547a-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="7547a-115">ProviderName</span></span>| <span data-ttu-id="7547a-116">指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。</span><span class="sxs-lookup"><span data-stu-id="7547a-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="7547a-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="7547a-117">SourceLocation</span></span>| <span data-ttu-id="7547a-118">指定套件來源的 URI。</span><span class="sxs-lookup"><span data-stu-id="7547a-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="7547a-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="7547a-119">Ensure</span></span>| <span data-ttu-id="7547a-120">判斷套件來源是否已註冊或已取消註冊。</span><span class="sxs-lookup"><span data-stu-id="7547a-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="7547a-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="7547a-121">InstallationPolicy</span></span>| <span data-ttu-id="7547a-122">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="7547a-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="7547a-123">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="7547a-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="7547a-124">只能是 "Untrusted" 或 "Trusted"。</span><span class="sxs-lookup"><span data-stu-id="7547a-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="7547a-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="7547a-125">SourceCredential</span></span>| <span data-ttu-id="7547a-126">提供遠端來源套件的存取權。</span><span class="sxs-lookup"><span data-stu-id="7547a-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="7547a-127">範例</span><span class="sxs-lookup"><span data-stu-id="7547a-127">Example</span></span>

<span data-ttu-id="7547a-128">此範例會使用 **PackageManagementSource** DSC 資源註冊 http://nuget.org 套件來源。</span><span class="sxs-lookup"><span data-stu-id="7547a-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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