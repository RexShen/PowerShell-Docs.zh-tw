---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: fd013384a4b588bcdb397d7771425fe5c031c48f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856694"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="a2700-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="a2700-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="a2700-103">此範例示範如何覆寫容器方法，以支援呼叫`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a2700-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="a2700-104">當資料存放區包含容器項目時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="a2700-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="a2700-105">容器是常見父項目底下的一組子項目。</span><span class="sxs-lookup"><span data-stu-id="a2700-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="a2700-106">在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="a2700-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a2700-107">示範</span><span class="sxs-lookup"><span data-stu-id="a2700-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2700-108">您的提供者類別很可能會衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="a2700-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="a2700-109">此範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="a2700-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="a2700-110">宣告`CmdletProvider`屬性。</span><span class="sxs-lookup"><span data-stu-id="a2700-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="a2700-111">定義提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="a2700-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="a2700-112">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以變更的行為`Copy-Item`cmdlet 可讓使用者從一個位置的項目複製到另一個。</span><span class="sxs-lookup"><span data-stu-id="a2700-112">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Copyitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="a2700-113">(此範例不會顯示如何加入動態參數，以便`Copy-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="a2700-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="a2700-114">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法來取得 ChildItems cmdlet，可讓使用者擷取父項目的子項目的行為變更.</span><span class="sxs-lookup"><span data-stu-id="a2700-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="a2700-115">（此範例不會顯示如何將動態參數新增至 Get ChildItems cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="a2700-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="a2700-116">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以變更 Get ChildItems cmdlet 的行為時`Name`指定此 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="a2700-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="a2700-117">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以變更的行為`New-Item`cmdlet，可讓使用者將項目加入至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="a2700-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="a2700-118">(此範例不會顯示如何加入動態參數，以便`New-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="a2700-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="a2700-119">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以變更的行為`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a2700-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="a2700-120">(此範例不會顯示如何加入動態參數，以便`Remove-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="a2700-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="a2700-121">範例</span><span class="sxs-lookup"><span data-stu-id="a2700-121">Example</span></span>

<span data-ttu-id="a2700-122">此範例示範如何覆寫來複製、 建立和移除項目，以及方法讓子系的父項目的項目所需的方法。</span><span class="sxs-lookup"><span data-stu-id="a2700-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="a2700-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2700-123">See Also</span></span>

[<span data-ttu-id="a2700-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a2700-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="a2700-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a2700-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="a2700-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="a2700-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="a2700-127">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="a2700-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)