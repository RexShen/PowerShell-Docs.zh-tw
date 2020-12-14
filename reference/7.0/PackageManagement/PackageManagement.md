---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113634
Help Version: 7.0.1.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 01b1bce187cd0526e56abc812f91b44a2c022a29
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890850"
---
# <span data-ttu-id="34c6f-103">PackageManagement 模組</span><span class="sxs-lookup"><span data-stu-id="34c6f-103">PackageManagement Module</span></span>

## <span data-ttu-id="34c6f-104">說明</span><span class="sxs-lookup"><span data-stu-id="34c6f-104">Description</span></span>

<span data-ttu-id="34c6f-105">本主題顯示套件管理 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="34c6f-105">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34c6f-106">從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。</span><span class="sxs-lookup"><span data-stu-id="34c6f-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="34c6f-107">如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="34c6f-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="34c6f-108">使用下列命令，以確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="34c6f-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="34c6f-109">如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。</span><span class="sxs-lookup"><span data-stu-id="34c6f-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="34c6f-110">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="34c6f-110">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="34c6f-111">Find-Package</span><span class="sxs-lookup"><span data-stu-id="34c6f-111">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="34c6f-112">尋找可用套件來源中的軟體套件。</span><span class="sxs-lookup"><span data-stu-id="34c6f-112">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="34c6f-113">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="34c6f-113">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="34c6f-114">傳回可供安裝的套件管理封裝提供者的清單。</span><span class="sxs-lookup"><span data-stu-id="34c6f-114">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="34c6f-115">Get-Package</span><span class="sxs-lookup"><span data-stu-id="34c6f-115">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="34c6f-116">傳回與 **PackageManagement** 一起安裝的所有軟體套件清單。</span><span class="sxs-lookup"><span data-stu-id="34c6f-116">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="34c6f-117">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="34c6f-117">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="34c6f-118">傳回連接到套件管理的封裝提供者清單。</span><span class="sxs-lookup"><span data-stu-id="34c6f-118">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="34c6f-119">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="34c6f-119">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="34c6f-120">取得為封裝提供者註冊的封裝來源清單。</span><span class="sxs-lookup"><span data-stu-id="34c6f-120">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="34c6f-121">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="34c6f-121">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="34c6f-122">將套件管理封裝提供者加入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="34c6f-122">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="34c6f-123">Install-Package</span><span class="sxs-lookup"><span data-stu-id="34c6f-123">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="34c6f-124">安裝一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="34c6f-124">Installs one or more software packages.</span></span>

### [<span data-ttu-id="34c6f-125">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="34c6f-125">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="34c6f-126">安裝一或多個套件管理封裝提供者。</span><span class="sxs-lookup"><span data-stu-id="34c6f-126">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="34c6f-127">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="34c6f-127">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="34c6f-128">加入指定套件提供者的套件來源。</span><span class="sxs-lookup"><span data-stu-id="34c6f-128">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="34c6f-129">Save-Package</span><span class="sxs-lookup"><span data-stu-id="34c6f-129">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="34c6f-130">將封裝儲存到本機電腦，而不進行安裝。</span><span class="sxs-lookup"><span data-stu-id="34c6f-130">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="34c6f-131">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="34c6f-131">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="34c6f-132">取代指定封裝提供者的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="34c6f-132">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="34c6f-133">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="34c6f-133">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="34c6f-134">卸載一或多個軟體套件。</span><span class="sxs-lookup"><span data-stu-id="34c6f-134">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="34c6f-135">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="34c6f-135">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="34c6f-136">移除已註冊的套件來源。</span><span class="sxs-lookup"><span data-stu-id="34c6f-136">Removes a registered package source.</span></span>
