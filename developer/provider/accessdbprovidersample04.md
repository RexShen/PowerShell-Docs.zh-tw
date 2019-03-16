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
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057615"
---
# <a name="accessdbprovidersample04"></a><span data-ttu-id="00122-102">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="00122-102">AccessDBProviderSample04</span></span>

<span data-ttu-id="00122-103">此範例示範如何覆寫容器方法，以支援呼叫`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00122-103">This sample shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span> <span data-ttu-id="00122-104">當資料存放區包含容器項目時，就應該實作這些方法。</span><span class="sxs-lookup"><span data-stu-id="00122-104">These methods should be implemented when the data store contains items that are containers.</span></span> <span data-ttu-id="00122-105">容器是常見父項目底下的一組子項目。</span><span class="sxs-lookup"><span data-stu-id="00122-105">A container is a group of child items under a common parent item.</span></span> <span data-ttu-id="00122-106">在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="00122-106">The provider class in this sample derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="00122-107">示範</span><span class="sxs-lookup"><span data-stu-id="00122-107">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00122-108">您的提供者類別很可能會衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span><span class="sxs-lookup"><span data-stu-id="00122-108">Your provider class will most likely derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)</span></span>

<span data-ttu-id="00122-109">此範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="00122-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="00122-110">宣告`CmdletProvider`屬性。</span><span class="sxs-lookup"><span data-stu-id="00122-110">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="00122-111">定義提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="00122-111">Defining a provider class that derives from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

- <span data-ttu-id="00122-112">覆寫[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以變更的行為`Copy-Item`cmdlet 可讓使用者從一個位置的項目複製到另一個。</span><span class="sxs-lookup"><span data-stu-id="00122-112">Overwriting the [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) method to change the behavior of the `Copy-Item` cmdlet which allows the user to copy items from one location to another.</span></span> <span data-ttu-id="00122-113">(此範例不會顯示如何加入動態參數，以便`Copy-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="00122-113">(This sample does not show how to add dynamic parameters to the `Copy-Item` cmdlet.)</span></span>

- <span data-ttu-id="00122-114">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法來取得 ChildItems cmdlet，可讓使用者擷取父項目的子項目的行為變更.</span><span class="sxs-lookup"><span data-stu-id="00122-114">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method to change the behavior of the Get-ChildItems cmdlet, which allows the user to retrieve the child items of the parent item.</span></span> <span data-ttu-id="00122-115">（此範例不會顯示如何將動態參數新增至 Get ChildItems cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="00122-115">(This sample does not show how to add dynamic parameters to the Get-ChildItems cmdlet.)</span></span>

- <span data-ttu-id="00122-116">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以變更 Get ChildItems cmdlet 的行為時`Name`指定此 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="00122-116">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method to change the behavior of the Get-ChildItems cmdlet when the `Name` parameter of the cmdlet is specified.</span></span>

- <span data-ttu-id="00122-117">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以變更的行為`New-Item`cmdlet，可讓使用者將項目加入至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="00122-117">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method to change the behavior of the `New-Item` cmdlet, which allows the user to add items to the data store.</span></span> <span data-ttu-id="00122-118">(此範例不會顯示如何加入動態參數，以便`New-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="00122-118">(This sample does not show how to add dynamic parameters to the `New-Item` cmdlet.)</span></span>

- <span data-ttu-id="00122-119">覆寫[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以變更的行為`Remove-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="00122-119">Overwriting the [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method to change the behavior of the `Remove-Item` cmdlet.</span></span> <span data-ttu-id="00122-120">(此範例不會顯示如何加入動態參數，以便`Remove-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="00122-120">(This sample does not show how to add dynamic parameters to the `Remove-Item` cmdlet.)</span></span>

## <a name="example"></a><span data-ttu-id="00122-121">範例</span><span class="sxs-lookup"><span data-stu-id="00122-121">Example</span></span>

<span data-ttu-id="00122-122">此範例示範如何覆寫來複製、 建立和移除項目，以及方法讓子系的父項目的項目所需的方法。</span><span class="sxs-lookup"><span data-stu-id="00122-122">This sample shows how to overwrite the methods needed to copy, create, and remove items, as well as methods for getting the child items of a parent item.</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="00122-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00122-123">See Also</span></span>

[<span data-ttu-id="00122-124">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="00122-124">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="00122-125">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="00122-125">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="00122-126">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="00122-126">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="00122-127">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="00122-127">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)