---
title: AccessDBProviderSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: 57b6cfaa5f29300c60a5a745797111b6beba3133
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859404"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="cf26d-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="cf26d-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="cf26d-103">此範例示範如何覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)並[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)以支援呼叫的方法`Get-Item`和`Set-Item`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf26d-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="cf26d-104">在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cf26d-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cf26d-105">示範</span><span class="sxs-lookup"><span data-stu-id="cf26d-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf26d-106">您的提供者類別會很有可能是衍生自下列類別的其中一個，並且可能實作其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="cf26d-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="cf26d-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cf26d-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="cf26d-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cf26d-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="cf26d-109">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="cf26d-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="cf26d-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cf26d-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="cf26d-111">請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="cf26d-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="cf26d-112">如需有關選擇哪一個提供者類別衍生自基礎提供者功能，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cf26d-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="cf26d-113">此範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="cf26d-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="cf26d-114">宣告`CmdletProvider`屬性。</span><span class="sxs-lookup"><span data-stu-id="cf26d-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="cf26d-115">定義提供者類別衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="cf26d-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="cf26d-116">覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以變更的行為`New-PSDrive`cmdlet，讓使用者能夠建立新的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cf26d-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="cf26d-117">(此範例不會顯示如何加入動態參數，以便`New-PSDrive`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="cf26d-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="cf26d-118">覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援移除現有的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="cf26d-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="cf26d-119">覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以變更的行為`Get-Item`cmdlet，讓使用者能夠從資料存放區擷取項目。</span><span class="sxs-lookup"><span data-stu-id="cf26d-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="cf26d-120">(此範例不會顯示如何加入動態參數，以便`Get-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="cf26d-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="cf26d-121">覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以變更的行為`Set-Item`cmdlet，可讓使用者更新資料存放區中的項目。</span><span class="sxs-lookup"><span data-stu-id="cf26d-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="cf26d-122">(此範例不會顯示如何加入動態參數，以便`Get-Item`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="cf26d-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="cf26d-123">覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，以變更的行為`Test-Path`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cf26d-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="cf26d-124">(此範例不會顯示如何加入動態參數，以便`Test-Path`指令程式。)</span><span class="sxs-lookup"><span data-stu-id="cf26d-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="cf26d-125">覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以判斷提供的路徑是否有效。</span><span class="sxs-lookup"><span data-stu-id="cf26d-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="cf26d-126">範例</span><span class="sxs-lookup"><span data-stu-id="cf26d-126">Example</span></span>

<span data-ttu-id="cf26d-127">此範例示範如何覆寫來取得和設定 Microsoft Access 資料中的項目基底所需的方法。</span><span class="sxs-lookup"><span data-stu-id="cf26d-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="cf26d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf26d-128">See Also</span></span>

[<span data-ttu-id="cf26d-129">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="cf26d-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="cf26d-130">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="cf26d-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="cf26d-131">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="cf26d-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="cf26d-132">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="cf26d-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)