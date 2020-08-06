---
title: AccessDBProviderSample01 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 50ec218e8d0fe6b2be5c8ac00956f72c6723f84a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786912"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="47ebd-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="47ebd-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="47ebd-103">這個範例會示範如何宣告直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="47ebd-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="47ebd-104">包含在此僅為完整性用途。</span><span class="sxs-lookup"><span data-stu-id="47ebd-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="47ebd-105">示範</span><span class="sxs-lookup"><span data-stu-id="47ebd-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47ebd-106">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="47ebd-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="47ebd-107">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="47ebd-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="47ebd-108">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="47ebd-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="47ebd-109">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="47ebd-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="47ebd-110">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="47ebd-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="47ebd-111">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="47ebd-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="47ebd-112">請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="47ebd-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="47ebd-113">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="47ebd-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="47ebd-114">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="47ebd-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="47ebd-115">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="47ebd-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="47ebd-116">定義可直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="47ebd-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="47ebd-117">範例</span><span class="sxs-lookup"><span data-stu-id="47ebd-117">Example</span></span>

<span data-ttu-id="47ebd-118">這個範例會示範如何定義提供者類別，以及如何宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="47ebd-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="47ebd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47ebd-119">See Also</span></span>

[<span data-ttu-id="47ebd-120">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="47ebd-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="47ebd-121">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="47ebd-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="47ebd-122">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="47ebd-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="47ebd-123">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="47ebd-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
