---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample01
description: AccessDBProviderSample01
ms.openlocfilehash: 8bdfa3ad492935a22ce06846294c02961cab2c65
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653755"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="76519-103">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="76519-103">AccessDBProviderSample01</span></span>

<span data-ttu-id="76519-104">這個範例會示範如何宣告直接衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="76519-104">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="76519-105">包含在此僅為完整性用途。</span><span class="sxs-lookup"><span data-stu-id="76519-105">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="76519-106">示範</span><span class="sxs-lookup"><span data-stu-id="76519-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76519-107">您的提供者類別很可能衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="76519-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="76519-108">[System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="76519-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="76519-109">請參閱 [AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="76519-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="76519-110">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="76519-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="76519-111">請參閱 [AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="76519-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="76519-112">[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="76519-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="76519-113">請參閱 [AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="76519-113">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="76519-114">如需根據提供者功能選擇要衍生自哪一個提供者類別的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="76519-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="76519-115">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="76519-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="76519-116">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="76519-116">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="76519-117">定義可直接衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="76519-117">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="76519-118">範例</span><span class="sxs-lookup"><span data-stu-id="76519-118">Example</span></span>

<span data-ttu-id="76519-119">這個範例會示範如何定義提供者類別，以及如何宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="76519-119">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="76519-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76519-120">See Also</span></span>

[<span data-ttu-id="76519-121">System.management.automation.provider.itemCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="76519-121">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="76519-122">ContainerCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="76519-122">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="76519-123">>navigationCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="76519-123">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="76519-124">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="76519-124">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
