---
title: AccessDBProviderSample06 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 893eb80574c7f142f92906961588e22b1ced0052
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786827"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="41038-102">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="41038-102">AccessDBProviderSample06</span></span>

<span data-ttu-id="41038-103">這個範例示範如何覆寫內容方法，以支援對 `Clear-Content` 、 `Get-Content` 和 Cmdlet 的呼叫 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="41038-103">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="41038-104">當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="41038-104">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="41038-105">這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它會執行[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面（可能為例）。</span><span class="sxs-lookup"><span data-stu-id="41038-105">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="41038-106">示範</span><span class="sxs-lookup"><span data-stu-id="41038-106">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41038-107">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="41038-107">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="41038-108">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="41038-108">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="41038-109">請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="41038-109">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="41038-110">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="41038-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="41038-111">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="41038-111">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="41038-112">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="41038-112">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="41038-113">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="41038-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="41038-114">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="41038-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="41038-115">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="41038-115">Declaring the `CmdletProvider` attribute.</span></span>
- <span data-ttu-id="41038-116">定義一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的提供者類別，並宣告[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的，並將其宣告為。</span><span class="sxs-lookup"><span data-stu-id="41038-116">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>
- <span data-ttu-id="41038-117">覆寫[IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以變更 Cmdlet 的行為 `Clear-Content` ，讓使用者可以從專案中移除內容。</span><span class="sxs-lookup"><span data-stu-id="41038-117">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="41038-118"> (此範例不會示範如何將動態參數新增至 `Clear-Content` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="41038-118">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>
- <span data-ttu-id="41038-119">覆寫[IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以變更 Cmdlet 的行為 `Get-Content` ，讓使用者能夠抓取專案的內容（content）。</span><span class="sxs-lookup"><span data-stu-id="41038-119">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="41038-120"> (此範例不會示範如何將動態參數新增至 `Get-Content` Cmdlet。 ) 。</span><span class="sxs-lookup"><span data-stu-id="41038-120">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>
- <span data-ttu-id="41038-121">覆寫[Filesystemprovider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以變更 Cmdlet 的行為 `Set-Content` ，讓使用者可以更新專案的內容。</span><span class="sxs-lookup"><span data-stu-id="41038-121">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="41038-122"> (此範例不會示範如何將動態參數新增至 `Set-Content` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="41038-122">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="41038-123">範例</span><span class="sxs-lookup"><span data-stu-id="41038-123">Example</span></span>

<span data-ttu-id="41038-124">這個範例會示範如何覆寫在 Microsoft Access 資料基底中清除、取得及設定專案內容所需的方法。</span><span class="sxs-lookup"><span data-stu-id="41038-124">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="41038-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41038-125">See Also</span></span>

[<span data-ttu-id="41038-126">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="41038-126">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="41038-127">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="41038-127">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="41038-128">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="41038-128">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="41038-129">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="41038-129">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
