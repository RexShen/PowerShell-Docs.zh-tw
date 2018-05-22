---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagementSource 資源
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="80557-103">DSC PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="80557-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="80557-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="80557-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="80557-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。</span><span class="sxs-lookup"><span data-stu-id="80557-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="80557-106">**以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="80557-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="80557-107">此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。</span><span class="sxs-lookup"><span data-stu-id="80557-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

## <a name="syntax"></a><span data-ttu-id="80557-108">語法</span><span class="sxs-lookup"><span data-stu-id="80557-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="80557-109">Properties</span><span class="sxs-lookup"><span data-stu-id="80557-109">Properties</span></span>
|  <span data-ttu-id="80557-110">屬性</span><span class="sxs-lookup"><span data-stu-id="80557-110">Property</span></span>  |  <span data-ttu-id="80557-111">描述</span><span class="sxs-lookup"><span data-stu-id="80557-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="80557-112">名稱</span><span class="sxs-lookup"><span data-stu-id="80557-112">Name</span></span>| <span data-ttu-id="80557-113">指定要在您的系統上註冊或取消註冊的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="80557-113">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="80557-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="80557-114">Ensure</span></span>| <span data-ttu-id="80557-115">判斷套件來源是否已註冊或已取消註冊。</span><span class="sxs-lookup"><span data-stu-id="80557-115">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="80557-116">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="80557-116">InstallationPolicy</span></span>| <span data-ttu-id="80557-117">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="80557-117">Determines whether you trust the package source.</span></span> <span data-ttu-id="80557-118">只能是 "Untrusted" 或 "Trusted"。</span><span class="sxs-lookup"><span data-stu-id="80557-118">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="80557-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="80557-119">ProviderName</span></span>| <span data-ttu-id="80557-120">指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。</span><span class="sxs-lookup"><span data-stu-id="80557-120">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="80557-121">SourceUri</span><span class="sxs-lookup"><span data-stu-id="80557-121">SourceUri</span></span>| <span data-ttu-id="80557-122">指定套件來源的 URI。</span><span class="sxs-lookup"><span data-stu-id="80557-122">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="80557-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="80557-123">SourceCredential</span></span>| <span data-ttu-id="80557-124">提供遠端來源套件的存取權。</span><span class="sxs-lookup"><span data-stu-id="80557-124">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="80557-125">範例</span><span class="sxs-lookup"><span data-stu-id="80557-125">Example</span></span>

<span data-ttu-id="80557-126">此範例會使用 **PackageManagementSource** DSC 資源註冊 http://nuget.org 套件來源。</span><span class="sxs-lookup"><span data-stu-id="80557-126">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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