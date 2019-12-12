---
title: AccessDBProviderSample01 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359997"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="57b2d-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="57b2d-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="57b2d-103">這個範例會示範如何宣告直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="57b2d-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="57b2d-104">包含在此僅為完整性用途。</span><span class="sxs-lookup"><span data-stu-id="57b2d-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="57b2d-105">示範</span><span class="sxs-lookup"><span data-stu-id="57b2d-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57b2d-106">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="57b2d-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="57b2d-107">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="57b2d-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="57b2d-108">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="57b2d-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="57b2d-109">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="57b2d-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="57b2d-110">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="57b2d-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="57b2d-111">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="57b2d-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="57b2d-112">請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="57b2d-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="57b2d-113">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="57b2d-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="57b2d-114">這個範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="57b2d-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="57b2d-115">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="57b2d-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="57b2d-116">定義可直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="57b2d-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="57b2d-117">範例</span><span class="sxs-lookup"><span data-stu-id="57b2d-117">Example</span></span>

<span data-ttu-id="57b2d-118">這個範例會示範如何定義提供者類別，以及如何宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="57b2d-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="57b2d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57b2d-119">See Also</span></span>

[<span data-ttu-id="57b2d-120">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="57b2d-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="57b2d-121">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="57b2d-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="57b2d-122">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="57b2d-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="57b2d-123">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="57b2d-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)