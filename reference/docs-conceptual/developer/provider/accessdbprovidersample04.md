---
title: AccessDBProviderSample04 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 097591528fd12cdf9f134a0fd8a0bd278f216fab
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786861"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="06d52-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="06d52-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="06d52-103">這個範例示範如何覆寫容器方法來支援對 `Copy-Item` 、 `Get-ChildItem` 、 `New-Item` 和 Cmdlet 的呼叫 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="06d52-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="06d52-104">當資料存放區包含容器項目時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="06d52-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="06d52-105">容器是常見父項目底下的一組子項目。</span><span class="sxs-lookup"><span data-stu-id="06d52-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="06d52-106">這個範例中的提供者類別衍生自[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="06d52-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="06d52-107">示範</span><span class="sxs-lookup"><span data-stu-id="06d52-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06d52-108">您的提供者類別很可能會衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 。</span><span class="sxs-lookup"><span data-stu-id="06d52-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="06d52-109">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="06d52-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="06d52-110">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="06d52-110">Declaring the `CmdletProvider` attribute.</span></span>
- <span data-ttu-id="06d52-111">定義一個衍生自[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="06d52-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>
- <span data-ttu-id="06d52-112">覆寫[ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以變更 Cmdlet 的行為， `Copy-Item` 讓使用者可以將專案從一個位置複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="06d52-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="06d52-113"> (此範例不會示範如何將動態參數新增至 `Copy-Item` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="06d52-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>
- <span data-ttu-id="06d52-114">覆寫[ContainerCmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，以變更 ChildItems 指令程式的行為，讓使用者能夠抓取父項目的子專案（item）。</span><span class="sxs-lookup"><span data-stu-id="06d52-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="06d52-115"> (此範例不會示範如何將動態參數新增至 ChildItems Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="06d52-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>
- <span data-ttu-id="06d52-116">當指定 Cmdlet 的參數時，覆寫[ContainerCmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以變更 ChildItems 指令程式的行為 `Name` 。</span><span class="sxs-lookup"><span data-stu-id="06d52-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>
- <span data-ttu-id="06d52-117">覆寫[ContainerCmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以變更 Cmdlet 的行為 `New-Item` ，讓使用者可以將專案新增至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="06d52-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="06d52-118"> (此範例不會示範如何將動態參數新增至 `New-Item` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="06d52-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>
- <span data-ttu-id="06d52-119">覆寫[ContainerCmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以變更 Cmdlet 的行為 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="06d52-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="06d52-120"> (此範例不會示範如何將動態參數新增至 `Remove-Item` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="06d52-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="06d52-121">範例</span><span class="sxs-lookup"><span data-stu-id="06d52-121">Example</span></span>

<span data-ttu-id="06d52-122">這個範例會示範如何覆寫複製、建立和移除專案所需的方法，以及取得父專案子專案的方法。</span><span class="sxs-lookup"><span data-stu-id="06d52-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="06d52-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06d52-123">See Also</span></span>

[<span data-ttu-id="06d52-124">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="06d52-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="06d52-125">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="06d52-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="06d52-126">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="06d52-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="06d52-127">設計 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="06d52-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
