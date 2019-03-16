---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055541"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="cc215-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="cc215-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="cc215-103">此範例示範如何覆寫內容方法，以支援呼叫`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc215-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="cc215-104">當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="cc215-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="cc215-105">在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且會實作[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。</span><span class="sxs-lookup"><span data-stu-id="cc215-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cc215-106">示範</span><span class="sxs-lookup"><span data-stu-id="cc215-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc215-107">您的提供者類別會很有可能是衍生自下列類別的其中一個，並且可能實作其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="cc215-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="cc215-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cc215-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="cc215-109">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="cc215-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="cc215-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cc215-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="cc215-111">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="cc215-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="cc215-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cc215-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="cc215-113">如需有關選擇哪一個提供者類別衍生自基礎提供者功能，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cc215-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="cc215-114">此範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="cc215-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="cc215-115">宣告`CmdletProvider`屬性。</span><span class="sxs-lookup"><span data-stu-id="cc215-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="cc215-116">定義提供者類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，宣告[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。</span><span class="sxs-lookup"><span data-stu-id="cc215-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="cc215-117">覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以變更的行為`Clear-Content`cmdlet，可讓使用者從項目移除內容。</span><span class="sxs-lookup"><span data-stu-id="cc215-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="cc215-118">(此範例不會顯示如何加入動態參數，以便`Clear-Content`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="cc215-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="cc215-119">覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以變更的行為`Get-Content`cmdlet，讓使用者能夠擷取內容的項目。</span><span class="sxs-lookup"><span data-stu-id="cc215-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="cc215-120">(此範例不會顯示如何加入動態參數，以便`Get-Content`指令程式。)。</span><span class="sxs-lookup"><span data-stu-id="cc215-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="cc215-121">覆寫[Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以變更的行為`Set-Content`cmdlet，可讓使用者更新的項目內容。</span><span class="sxs-lookup"><span data-stu-id="cc215-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="cc215-122">(此範例不會顯示如何加入動態參數，以便`Set-Content`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="cc215-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="cc215-123">範例</span><span class="sxs-lookup"><span data-stu-id="cc215-123">Example</span></span>

<span data-ttu-id="cc215-124">此範例示範如何覆寫清除、 取得及設定 Microsoft Access 資料中的項目內容的基底所需的方法。</span><span class="sxs-lookup"><span data-stu-id="cc215-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="cc215-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc215-125">See Also</span></span>

[<span data-ttu-id="cc215-126">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="cc215-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="cc215-127">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="cc215-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="cc215-128">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="cc215-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="cc215-129">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="cc215-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)