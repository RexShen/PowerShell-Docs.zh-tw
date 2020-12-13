---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample06
description: AccessDBProviderSample06
ms.openlocfilehash: a2037c6f13ba24ba2dcb4ffecbd802566452d64e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656923"
---
# <a name="accessdbprovidersample06"></a><span data-ttu-id="6f1e7-103">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="6f1e7-103">AccessDBProviderSample06</span></span>

<span data-ttu-id="6f1e7-104">這個範例會示範如何覆寫內容方法，以支援對 `Clear-Content` 、 `Get-Content` 和 Cmdlet 的呼叫 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-104">This sample shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span> <span data-ttu-id="6f1e7-105">當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-105">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span> <span data-ttu-id="6f1e7-106">此範例中的提供者類別衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別，它會實 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面，並將它實作為。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and it implements the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="6f1e7-107">示範</span><span class="sxs-lookup"><span data-stu-id="6f1e7-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6f1e7-108">您的提供者類別很可能衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="6f1e7-108">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> - <span data-ttu-id="6f1e7-109">[System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-109">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="6f1e7-110">請參閱 [AccessDBProviderSample03](./accessdbprovidersample03.md)。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-110">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> - <span data-ttu-id="6f1e7-111">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-111">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="6f1e7-112">請參閱 [AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-112">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> - <span data-ttu-id="6f1e7-113">[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別（System）。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-113">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>
>
> <span data-ttu-id="6f1e7-114">如需根據提供者功能選擇要衍生自哪一個提供者類別的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-114">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="6f1e7-115">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="6f1e7-115">This sample demonstrates the following:</span></span>

- <span data-ttu-id="6f1e7-116">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-116">Declaring the `CmdletProvider` attribute.</span></span>
- <span data-ttu-id="6f1e7-117">定義一個衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別的提供者類別，以及宣告 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面的提供者類別（class）。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-117">Defining a provider class that derives from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class and that declares the [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.</span></span>
- <span data-ttu-id="6f1e7-118">覆寫 [IcontentCmdletprovider. Clearcontent \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法，以變更 Cmdlet 的行為 `Clear-Content` ，讓使用者可以從專案中移除內容。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-118">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) method to change the behavior of the `Clear-Content` cmdlet, allowing the user to remove the content from an item.</span></span> <span data-ttu-id="6f1e7-119"> (此範例不會示範如何將動態參數新增至 `Clear-Content` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="6f1e7-119">(This sample does not show how to add dynamic parameters to the `Clear-Content` cmdlet.)</span></span>
- <span data-ttu-id="6f1e7-120">覆寫 [IcontentCmdletprovider. Getcontentreader \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 方法，以變更 Cmdlet 的行為 `Get-Content` ，讓使用者可以取出專案的內容，。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-120">Overwriting the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) method to change the behavior of the `Get-Content` cmdlet, allowing the user to retrieve the content of an item.</span></span> <span data-ttu-id="6f1e7-121"> (此範例不會示範如何將動態參數新增至 `Get-Content` Cmdlet。 ) 。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-121">(This sample does not show how to add dynamic parameters to the `Get-Content` cmdlet.).</span></span>
- <span data-ttu-id="6f1e7-122">覆寫 [Filesystemprovider. Getcontentwriter \*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 方法，以變更 Cmdlet 的行為 `Set-Content` ，讓使用者可以更新專案的內容。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-122">Overwriting the [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter\*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) method to change the behavior of the `Set-Content` cmdlet, allowing the user to update the content of an item.</span></span> <span data-ttu-id="6f1e7-123"> (此範例不會示範如何將動態參數新增至 `Set-Content` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="6f1e7-123">(This sample does not show how to add dynamic parameters to the `Set-Content` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="6f1e7-124">範例</span><span class="sxs-lookup"><span data-stu-id="6f1e7-124">Example</span></span>

<span data-ttu-id="6f1e7-125">此範例示範如何覆寫在 Microsoft Access 資料基底中清除、取得和設定專案內容所需的方法。</span><span class="sxs-lookup"><span data-stu-id="6f1e7-125">This sample shows how to overwrite the methods needed to clear, get, and set the content of items in a Microsoft Access data base.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="6f1e7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f1e7-126">See Also</span></span>

[<span data-ttu-id="6f1e7-127">System.management.automation.provider.itemCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="6f1e7-127">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="6f1e7-128">ContainerCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="6f1e7-128">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="6f1e7-129">>navigationCmdletprovider （系統管理）</span><span class="sxs-lookup"><span data-stu-id="6f1e7-129">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="6f1e7-130">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6f1e7-130">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
