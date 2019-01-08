---
ms.date: 06/20/2018
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagementSource 資源
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047119"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="53eaf-103">DSC PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="53eaf-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="53eaf-104">適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0 中，Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="53eaf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="53eaf-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。</span><span class="sxs-lookup"><span data-stu-id="53eaf-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span> <span data-ttu-id="53eaf-106">**以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="53eaf-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="53eaf-107">此資源需要 **PackageManagement** 模組，可從 http://PowerShellGallery.com 取得。</span><span class="sxs-lookup"><span data-stu-id="53eaf-107">This resource requires the **PackageManagement** module, available from http://PowerShellGallery.com.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53eaf-108">**PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="53eaf-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="53eaf-109">語法</span><span class="sxs-lookup"><span data-stu-id="53eaf-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="53eaf-110">Properties</span><span class="sxs-lookup"><span data-stu-id="53eaf-110">Properties</span></span>

|  <span data-ttu-id="53eaf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="53eaf-111">Property</span></span>  |  <span data-ttu-id="53eaf-112">描述</span><span class="sxs-lookup"><span data-stu-id="53eaf-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="53eaf-113">名稱</span><span class="sxs-lookup"><span data-stu-id="53eaf-113">Name</span></span>| <span data-ttu-id="53eaf-114">指定要在您的系統上註冊或取消註冊的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="53eaf-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span>|
| <span data-ttu-id="53eaf-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="53eaf-115">ProviderName</span></span>| <span data-ttu-id="53eaf-116">指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。</span><span class="sxs-lookup"><span data-stu-id="53eaf-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span>|
| <span data-ttu-id="53eaf-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="53eaf-117">SourceLocation</span></span>| <span data-ttu-id="53eaf-118">指定套件來源的 URI。</span><span class="sxs-lookup"><span data-stu-id="53eaf-118">Specifies the URI of the package source.</span></span>|
| <span data-ttu-id="53eaf-119">Ensure</span><span class="sxs-lookup"><span data-stu-id="53eaf-119">Ensure</span></span>| <span data-ttu-id="53eaf-120">判斷套件來源是否已註冊或已取消註冊。</span><span class="sxs-lookup"><span data-stu-id="53eaf-120">Determines whether the package source is to be registered or unregistered.</span></span>|
| <span data-ttu-id="53eaf-121">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="53eaf-121">InstallationPolicy</span></span>| <span data-ttu-id="53eaf-122">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="53eaf-122">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="53eaf-123">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="53eaf-123">Determines whether you trust the package's source.</span></span> <span data-ttu-id="53eaf-124">值為： 或  其中一個。「 不受信任 」，「 信任 」。</span><span class="sxs-lookup"><span data-stu-id="53eaf-124">One of: "Untrusted", "Trusted".</span></span>|
| <span data-ttu-id="53eaf-125">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="53eaf-125">SourceCredential</span></span>| <span data-ttu-id="53eaf-126">提供遠端來源套件的存取權。</span><span class="sxs-lookup"><span data-stu-id="53eaf-126">Provides access to the package on a remote source.</span></span>|

## <a name="example"></a><span data-ttu-id="53eaf-127">範例</span><span class="sxs-lookup"><span data-stu-id="53eaf-127">Example</span></span>

<span data-ttu-id="53eaf-128">此範例會使用 **PackageManagementSource** DSC 資源註冊 http://nuget.org 套件來源。</span><span class="sxs-lookup"><span data-stu-id="53eaf-128">This example registers the http://nuget.org package source using the **PackageManagementSource** DSC resource.</span></span>

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