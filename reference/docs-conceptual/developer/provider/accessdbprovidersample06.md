---
title: AccessDBProviderSample06 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366327"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="a388b-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="a388b-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="a388b-103">這個範例示範如何覆寫內容方法，以支援對 `Clear-Content`、`Get-Content` 和 @no__t 2 Cmdlet 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a388b-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="a388b-104">當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="a388b-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="a388b-105">這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它會執行[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面（可能為例）。</span><span class="sxs-lookup"><span data-stu-id="a388b-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a388b-106">演示</span><span class="sxs-lookup"><span data-stu-id="a388b-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a388b-107">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="a388b-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="a388b-108">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="a388b-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="a388b-109">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="a388b-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="a388b-110">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="a388b-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="a388b-111">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="a388b-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="a388b-112">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="a388b-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="a388b-113">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a388b-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="a388b-114">這個範例會示範下列各項：</span><span class="sxs-lookup"><span data-stu-id="a388b-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a388b-115">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a388b-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a388b-116">定義一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的提供者類別，並宣告[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的，並將其宣告為。</span><span class="sxs-lookup"><span data-stu-id="a388b-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

- <span data-ttu-id="a388b-117">覆寫[IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以變更 @no__t 1 Cmdlet 的行為，讓使用者可以從專案中移除該內容。</span><span class="sxs-lookup"><span data-stu-id="a388b-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="a388b-118">（此範例不會示範如何將動態參數新增至 `Clear-Content` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="a388b-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>

- <span data-ttu-id="a388b-119">覆寫[IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以變更 @no__t 1 Cmdlet 的行為，讓使用者能夠抓取專案的內容（content）。</span><span class="sxs-lookup"><span data-stu-id="a388b-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="a388b-120">（此範例不會示範如何將動態參數新增至 `Get-Content` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="a388b-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>

- <span data-ttu-id="a388b-121">覆寫[Filesystemprovider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以變更 @no__t 1 Cmdlet 的行為，讓使用者可以更新專案的內容。</span><span class="sxs-lookup"><span data-stu-id="a388b-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="a388b-122">（此範例不會示範如何將動態參數新增至 `Set-Content` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="a388b-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="a388b-123">範例</span><span class="sxs-lookup"><span data-stu-id="a388b-123">Example</span></span>

<span data-ttu-id="a388b-124">這個範例會示範如何覆寫在 Microsoft Access 資料基底中清除、取得及設定專案內容所需的方法。</span><span class="sxs-lookup"><span data-stu-id="a388b-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="a388b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a388b-125">See Also</span></span>

[<span data-ttu-id="a388b-126">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a388b-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a388b-127">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a388b-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a388b-128">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a388b-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a388b-129">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="a388b-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
