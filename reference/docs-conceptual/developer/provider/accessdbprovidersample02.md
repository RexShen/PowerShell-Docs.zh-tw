---
title: AccessDBProviderSample02 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9a0444d17bec230633e1dd1709455f6ba83dd5c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786895"
---
# <a name="accessdbprovidersample02"></a><span data-ttu-id="95334-102">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="95334-102">AccessDBProviderSample02</span></span>

<span data-ttu-id="95334-103">這個範例會示範如何覆寫[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[DriveCmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援對 `New-PSDrive` 和 Cmdlet 的呼叫，並提供。 `Remove-PSDrive`</span><span class="sxs-lookup"><span data-stu-id="95334-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span> <span data-ttu-id="95334-104">這個範例中的提供者類別衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="95334-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="95334-105">示範</span><span class="sxs-lookup"><span data-stu-id="95334-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="95334-106">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="95334-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="95334-107">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="95334-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="95334-108">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="95334-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="95334-109">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="95334-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="95334-110">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="95334-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="95334-111">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="95334-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="95334-112">請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="95334-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="95334-113">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="95334-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="95334-114">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="95334-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="95334-115">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="95334-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="95334-116">定義提供者類別，以從[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別驅動。</span><span class="sxs-lookup"><span data-stu-id="95334-116">Defining a provider class that drives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span>

- <span data-ttu-id="95334-117">覆寫[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以支援建立新的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="95334-117">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to support creating new drives.</span></span> <span data-ttu-id="95334-118"> (此範例不會示範如何將動態參數新增至 `New-PSDrive` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="95334-118">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="95334-119">覆寫[DriveCmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援移除現有的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="95334-119">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

## <a name="example"></a><span data-ttu-id="95334-120">範例</span><span class="sxs-lookup"><span data-stu-id="95334-120">Example</span></span>

<span data-ttu-id="95334-121">這個範例會示範如何覆寫[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[DriveCmdletprovider.. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法中的程式。</span><span class="sxs-lookup"><span data-stu-id="95334-121">This sample shows how to overwrite the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods.</span></span> <span data-ttu-id="95334-122">針對此範例提供者，建立磁片磁碟機時，其連線資訊會儲存在 `AccessDBPsDriveInfo` 物件中。</span><span class="sxs-lookup"><span data-stu-id="95334-122">For this sample provider, when a drive is created its connection information is stored in an `AccessDBPsDriveInfo` object.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="95334-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95334-123">See Also</span></span>

[<span data-ttu-id="95334-124">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="95334-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="95334-125">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="95334-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="95334-126">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="95334-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="95334-127">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="95334-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
