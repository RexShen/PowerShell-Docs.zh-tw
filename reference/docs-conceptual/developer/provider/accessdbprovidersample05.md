---
title: AccessDBProviderSample05 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a26661f2-a63c-4ca7-ad3e-dcb4d32ce5a1
caps.latest.revision: 8
ms.openlocfilehash: 43d18672ec4f52961b2a2460635468a2d6fb41e5
ms.sourcegitcommit: 109f132360e8adbbdaf5dbc42a270be73d9dfa9b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84633374"
---
# <a name="accessdbprovidersample05"></a><span data-ttu-id="33d84-102">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="33d84-102">AccessDBProviderSample05</span></span>

<span data-ttu-id="33d84-103">這個範例示範如何覆寫容器方法來支援對 `Move-Item` 和 Cmdlet 的呼叫 `Join-Path` 。</span><span class="sxs-lookup"><span data-stu-id="33d84-103">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="33d84-104">當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="33d84-104">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="33d84-105">這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="33d84-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="33d84-106">示範</span><span class="sxs-lookup"><span data-stu-id="33d84-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33d84-107">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="33d84-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="33d84-108">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="33d84-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="33d84-109">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="33d84-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="33d84-110">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="33d84-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="33d84-111">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="33d84-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="33d84-112">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="33d84-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="33d84-113">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="33d84-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="33d84-114">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="33d84-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="33d84-115">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="33d84-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="33d84-116">定義一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="33d84-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="33d84-117">覆寫[NavigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法來變更 Cmdlet 的行為 `Move-Item` ，讓使用者可以將專案從一個位置移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="33d84-117">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="33d84-118">（此範例不會示範如何將動態參數新增至 `Move-Item` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="33d84-118">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="33d84-119">覆寫[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法，以變更 Cmdlet 的行為 `Join-Path` 。</span><span class="sxs-lookup"><span data-stu-id="33d84-119">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="33d84-120">正在覆寫[NavigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法。</span><span class="sxs-lookup"><span data-stu-id="33d84-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="33d84-121">正在覆寫[NavigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法。</span><span class="sxs-lookup"><span data-stu-id="33d84-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="33d84-122">正在覆寫[NavigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法。</span><span class="sxs-lookup"><span data-stu-id="33d84-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="33d84-123">正在覆寫[NavigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法。</span><span class="sxs-lookup"><span data-stu-id="33d84-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="33d84-124">範例</span><span class="sxs-lookup"><span data-stu-id="33d84-124">Example</span></span>

<span data-ttu-id="33d84-125">這個範例會示範如何覆寫在 Microsoft Access 資料基底中移動專案所需的方法。</span><span class="sxs-lookup"><span data-stu-id="33d84-125">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="33d84-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33d84-126">See Also</span></span>

[<span data-ttu-id="33d84-127">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="33d84-127">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="33d84-128">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="33d84-128">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="33d84-129">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="33d84-129">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="33d84-130">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="33d84-130">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
