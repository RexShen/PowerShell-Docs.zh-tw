---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC PackageManagementSource 資源
ms.openlocfilehash: 4a4219f3c4ad7e547025a2b9cde442c7b69eeac4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557136"
---
# <a name="dsc-packagemanagementsource-resource"></a><span data-ttu-id="810b7-103">DSC PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="810b7-103">DSC PackageManagementSource Resource</span></span>

> <span data-ttu-id="810b7-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="810b7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="810b7-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **PackageManagementSource** 資源提供在目標節點上註冊或取消註冊「套件管理」來源的機制。</span><span class="sxs-lookup"><span data-stu-id="810b7-105">The **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to register or unregister Package Management sources on a target node.</span></span>
<span data-ttu-id="810b7-106">**以此方式註冊的「套件管理」來源會登錄在系統內容下，可供系統帳戶或 DSC 引擎使用。**</span><span class="sxs-lookup"><span data-stu-id="810b7-106">**Package Management sources registered in this way are registered under the System context, usable by the System account or by the DSC engine.**</span></span> <span data-ttu-id="810b7-107">此資源需要 **PackageManagement** 模組，可從 [PowerShell Gallery](https://PowerShellGallery.com) 取得。</span><span class="sxs-lookup"><span data-stu-id="810b7-107">This resource requires the **PackageManagement** module, available from the [PowerShell Gallery](https://PowerShellGallery.com).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="810b7-108">**PackageManagement** 模組至少應為 1.1.7.0 版，以下才是正確的屬性資訊。</span><span class="sxs-lookup"><span data-stu-id="810b7-108">The **PackageManagement** module should be at least version 1.1.7.0 for the following property information to be correct.</span></span>

## <a name="syntax"></a><span data-ttu-id="810b7-109">語法</span><span class="sxs-lookup"><span data-stu-id="810b7-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="810b7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="810b7-110">Properties</span></span>

|<span data-ttu-id="810b7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="810b7-111">Property</span></span> |<span data-ttu-id="810b7-112">描述</span><span class="sxs-lookup"><span data-stu-id="810b7-112">Description</span></span> |
|---|---|
|<span data-ttu-id="810b7-113">名稱</span><span class="sxs-lookup"><span data-stu-id="810b7-113">Name</span></span> |<span data-ttu-id="810b7-114">指定要在您的系統上註冊或取消註冊的套件來源名稱。</span><span class="sxs-lookup"><span data-stu-id="810b7-114">Specifies the name of the package source to be registered or unregistered on your system.</span></span> |
|<span data-ttu-id="810b7-115">ProviderName</span><span class="sxs-lookup"><span data-stu-id="810b7-115">ProviderName</span></span> |<span data-ttu-id="810b7-116">指定 OneGet 提供者的名稱，您可透過它與套件來源進行 interop。</span><span class="sxs-lookup"><span data-stu-id="810b7-116">Specifies the name of the OneGet provider through which you can interop with the package source.</span></span> |
|<span data-ttu-id="810b7-117">SourceLocation</span><span class="sxs-lookup"><span data-stu-id="810b7-117">SourceLocation</span></span> |<span data-ttu-id="810b7-118">指定套件來源的 URI。</span><span class="sxs-lookup"><span data-stu-id="810b7-118">Specifies the URI of the package source.</span></span> |
|<span data-ttu-id="810b7-119">InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="810b7-119">InstallationPolicy</span></span> |<span data-ttu-id="810b7-120">由內建 Nuget 提供者之類的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="810b7-120">Used by providers such as the built-in Nuget Provider.</span></span> <span data-ttu-id="810b7-121">判斷您是否信任套件來源。</span><span class="sxs-lookup"><span data-stu-id="810b7-121">Determines whether you trust the package's source.</span></span> <span data-ttu-id="810b7-122">值為下列其中之一：**Untrusted**、**Trusted**。</span><span class="sxs-lookup"><span data-stu-id="810b7-122">One of: **Untrusted** or **Trusted**.</span></span> |
|<span data-ttu-id="810b7-123">SourceCredential</span><span class="sxs-lookup"><span data-stu-id="810b7-123">SourceCredential</span></span> |<span data-ttu-id="810b7-124">提供遠端來源套件的存取權。</span><span class="sxs-lookup"><span data-stu-id="810b7-124">Provides access to the package on a remote source.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="810b7-125">通用屬性</span><span class="sxs-lookup"><span data-stu-id="810b7-125">Common properties</span></span>

|<span data-ttu-id="810b7-126">屬性</span><span class="sxs-lookup"><span data-stu-id="810b7-126">Property</span></span> |<span data-ttu-id="810b7-127">描述</span><span class="sxs-lookup"><span data-stu-id="810b7-127">Description</span></span> |
|---|---|
|<span data-ttu-id="810b7-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="810b7-128">DependsOn</span></span> |<span data-ttu-id="810b7-129">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="810b7-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="810b7-130">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="810b7-130">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="810b7-131">Ensure</span><span class="sxs-lookup"><span data-stu-id="810b7-131">Ensure</span></span> |<span data-ttu-id="810b7-132">判斷套件來源是否已註冊或已取消註冊。</span><span class="sxs-lookup"><span data-stu-id="810b7-132">Determines whether the package source is to be registered or unregistered.</span></span> <span data-ttu-id="810b7-133">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="810b7-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="810b7-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="810b7-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="810b7-135">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="810b7-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="810b7-136">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="810b7-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="810b7-137">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="810b7-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="810b7-138">範例</span><span class="sxs-lookup"><span data-stu-id="810b7-138">Example</span></span>

<span data-ttu-id="810b7-139">此範例會使用 **PackageManagementSource** DSC 資源註冊 `https://nuget.org` 套件來源。</span><span class="sxs-lookup"><span data-stu-id="810b7-139">This example registers the `https://nuget.org` package source using the **PackageManagementSource** DSC resource.</span></span>

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
