---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample02
description: AccessDBProviderSample02
ms.openlocfilehash: ebba2381370cf73f1e39015990f81dc4fd6dd937
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667431"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="99b93-103">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="99b93-103">AccessDBProviderSample02</span></span>

<span data-ttu-id="99b93-104">這個範例會示範如何覆寫 [DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 和 [DriveCmdletprovider... >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法，以支援對 `New-PSDrive` 和 Cmdlet 的呼叫 `Remove-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="99b93-104">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="99b93-105">此範例中的提供者類別衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別。</span><span class="sxs-lookup"><span data-stu-id="99b93-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="99b93-106">示範</span><span class="sxs-lookup"><span data-stu-id="99b93-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99b93-107">您的提供者類別很可能衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="99b93-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="99b93-108">[System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="99b93-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="99b93-109">請參閱 [AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="99b93-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="99b93-110">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="99b93-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="99b93-111">請參閱 [AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="99b93-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="99b93-112">[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="99b93-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="99b93-113">請參閱 [AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="99b93-113">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="99b93-114">如需根據提供者功能選擇要衍生自哪一個提供者類別的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="99b93-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="99b93-115">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="99b93-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="99b93-116">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="99b93-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="99b93-117">定義提供者類別，該類別會驅動 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別的驅動程式。</span><span class="sxs-lookup"><span data-stu-id="99b93-117">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="99b93-118">覆寫 [DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 方法，以支援建立新的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="99b93-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="99b93-119"> (此範例不會示範如何將動態參數新增至 `New-PSDrive` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="99b93-119">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="99b93-120">覆寫 [DriveCmdletprovider. >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法，以支援移除現有的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="99b93-120">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="99b93-121">範例</span><span class="sxs-lookup"><span data-stu-id="99b93-121">Example</span></span>

<span data-ttu-id="99b93-122">這個範例會示範如何覆寫 [DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 和 [DriveCmdletprovider.. >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="99b93-122">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="99b93-123">針對此範例提供者，建立磁片磁碟機時，它的連接資訊會儲存在 `AccessDBPsDriveInfo` 物件中。</span><span class="sxs-lookup"><span data-stu-id="99b93-123">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="99b93-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99b93-124">See Also</span></span>

[<span data-ttu-id="99b93-125">System.management.automation.provider.itemCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="99b93-125">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="99b93-126">ContainerCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="99b93-126">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="99b93-127">>navigationCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="99b93-127">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="99b93-128">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="99b93-128">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
