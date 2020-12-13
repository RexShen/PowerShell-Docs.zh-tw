---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample05
description: AccessDBProviderSample05
ms.openlocfilehash: ad273720ded0b200530f4f81482d01a8fbb82aa3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656911"
---
# <a name="accessdbprovidersample05"></a><span data-ttu-id="cb41a-103">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="cb41a-103">AccessDBProviderSample05</span></span>

<span data-ttu-id="cb41a-104">這個範例會示範如何覆寫容器方法，以支援對 `Move-Item` 和 `Join-Path` Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="cb41a-104">This sample shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span> <span data-ttu-id="cb41a-105">當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="cb41a-105">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span> <span data-ttu-id="cb41a-106">此範例中的提供者類別衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別。</span><span class="sxs-lookup"><span data-stu-id="cb41a-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cb41a-107">示範</span><span class="sxs-lookup"><span data-stu-id="cb41a-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb41a-108">您的提供者類別很可能衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="cb41a-108">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="cb41a-109">[System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="cb41a-109">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="cb41a-110">請參閱 [AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="cb41a-110">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="cb41a-111">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="cb41a-111">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="cb41a-112">請參閱 [AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="cb41a-112">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="cb41a-113">[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="cb41a-113">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="cb41a-114">如需根據提供者功能選擇要衍生自哪一個提供者類別的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cb41a-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="cb41a-115">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="cb41a-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="cb41a-116">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="cb41a-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="cb41a-117">定義一個衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="cb41a-117">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

- <span data-ttu-id="cb41a-118">覆寫 [>navigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法來變更 Cmdlet 的行為 `Move-Item` ，讓使用者可以將專案從某個位置移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="cb41a-118">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method to change the behavior of the `Move-Item` cmdlet, allowing the user to move items from one location to another.</span></span> <span data-ttu-id="cb41a-119"> (此範例不會示範如何將動態參數新增至 `Move-Item` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="cb41a-119">(This sample does not show how to add dynamic parameters to the `Move-Item` cmdlet.)</span></span>

- <span data-ttu-id="cb41a-120">覆寫 [>navigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 方法，以變更 Cmdlet 的行為 `Join-Path` 。</span><span class="sxs-lookup"><span data-stu-id="cb41a-120">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method to change the behavior of the `Join-Path` cmdlet.</span></span>

- <span data-ttu-id="cb41a-121">正在覆寫 [>navigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 方法。</span><span class="sxs-lookup"><span data-stu-id="cb41a-121">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method.</span></span>

- <span data-ttu-id="cb41a-122">正在覆寫 [>navigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 方法。</span><span class="sxs-lookup"><span data-stu-id="cb41a-122">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method.</span></span>

- <span data-ttu-id="cb41a-123">正在覆寫 [>navigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 方法。</span><span class="sxs-lookup"><span data-stu-id="cb41a-123">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method.</span></span>

- <span data-ttu-id="cb41a-124">正在覆寫 [>navigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 方法。</span><span class="sxs-lookup"><span data-stu-id="cb41a-124">Overwriting the [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method.</span></span>

## <a name="example"></a><span data-ttu-id="cb41a-125">範例</span><span class="sxs-lookup"><span data-stu-id="cb41a-125">Example</span></span>

<span data-ttu-id="cb41a-126">這個範例會示範如何覆寫在 Microsoft Access 資料基底中移動專案所需的方法。</span><span class="sxs-lookup"><span data-stu-id="cb41a-126">This sample shows how to overwrite the methods needed to move items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a><span data-ttu-id="cb41a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb41a-127">See Also</span></span>

[<span data-ttu-id="cb41a-128">System.management.automation.provider.itemCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="cb41a-128">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="cb41a-129">ContainerCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="cb41a-129">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="cb41a-130">>navigationCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="cb41a-130">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="cb41a-131">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="cb41a-131">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
