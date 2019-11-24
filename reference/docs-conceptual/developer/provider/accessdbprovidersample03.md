---
title: AccessDBProviderSample03 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359987"
---
# <a name="accessdbprovidersample03"></a><span data-ttu-id="8072d-102">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="8072d-102">AccessDBProviderSample03</span></span>

<span data-ttu-id="8072d-103">這個範例會示範如何覆寫[ItemCmdletprovider. Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[ItemCmdletprovider. Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援 `Get-Item` 和 `Set-Item` Cmdlet 的呼叫，並將其提供給。</span><span class="sxs-lookup"><span data-stu-id="8072d-103">This sample shows how to overwrite the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span> <span data-ttu-id="8072d-104">這個範例中的提供者類別衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="8072d-104">The provider class in this sample derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8072d-105">演示</span><span class="sxs-lookup"><span data-stu-id="8072d-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8072d-106">您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：</span><span class="sxs-lookup"><span data-stu-id="8072d-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="8072d-107">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="8072d-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>
> -   <span data-ttu-id="8072d-108">[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="8072d-108">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="8072d-109">請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="8072d-109">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="8072d-110">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="8072d-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="8072d-111">請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="8072d-111">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="8072d-112">如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8072d-112">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="8072d-113">這個範例會示範下列各項：</span><span class="sxs-lookup"><span data-stu-id="8072d-113">This sample demonstrates the following:</span></span>

- <span data-ttu-id="8072d-114">宣告 `CmdletProvider` 屬性。</span><span class="sxs-lookup"><span data-stu-id="8072d-114">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="8072d-115">定義一個衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的提供者類別。</span><span class="sxs-lookup"><span data-stu-id="8072d-115">Defining a provider class that derives from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

- <span data-ttu-id="8072d-116">覆寫[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法來變更 `New-PSDrive` Cmdlet 的行為，讓使用者能夠建立新的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8072d-116">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method to change the behavior of the `New-PSDrive` cmdlet, allowing the user to create new drives.</span></span> <span data-ttu-id="8072d-117">（此範例不會示範如何將動態參數新增至 `New-PSDrive` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="8072d-117">(This sample does not show how to add dynamic parameters to the `New-PSDrive` cmdlet.)</span></span>

- <span data-ttu-id="8072d-118">覆寫[DriveCmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援移除現有的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8072d-118">Overwriting the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method to support removing existing drives.</span></span>

- <span data-ttu-id="8072d-119">覆寫[ItemCmdletprovider. Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法來變更 `Get-Item` Cmdlet 的行為，讓使用者可以從資料存放區抓取專案。</span><span class="sxs-lookup"><span data-stu-id="8072d-119">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) method to change the behavior of the `Get-Item` cmdlet, allowing the user to retrieve items from the data store.</span></span> <span data-ttu-id="8072d-120">（此範例不會示範如何將動態參數新增至 `Get-Item` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="8072d-120">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="8072d-121">覆寫[ItemCmdletprovider. Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法來變更 `Set-Item` Cmdlet 的行為，讓使用者可以更新資料存放區中的專案。</span><span class="sxs-lookup"><span data-stu-id="8072d-121">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method to change the behavior of the `Set-Item` cmdlet, allowing the user to update the items in the data store.</span></span> <span data-ttu-id="8072d-122">（此範例不會示範如何將動態參數新增至 `Get-Item` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="8072d-122">(This sample does not show how to add dynamic parameters to the `Get-Item` cmdlet.)</span></span>

- <span data-ttu-id="8072d-123">覆寫[ItemCmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，以變更 `Test-Path` Cmdlet 的行為。</span><span class="sxs-lookup"><span data-stu-id="8072d-123">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method to change the behavior of the `Test-Path` cmdlet.</span></span> <span data-ttu-id="8072d-124">（此範例不會示範如何將動態參數新增至 `Test-Path` Cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="8072d-124">(This sample does not show how to add dynamic parameters to the `Test-Path` cmdlet.)</span></span>

- <span data-ttu-id="8072d-125">覆寫[ItemCmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以判斷提供的路徑是否有效。</span><span class="sxs-lookup"><span data-stu-id="8072d-125">Overwriting the [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method to determine if the provided path is valid.</span></span>

## <a name="example"></a><span data-ttu-id="8072d-126">範例</span><span class="sxs-lookup"><span data-stu-id="8072d-126">Example</span></span>

<span data-ttu-id="8072d-127">這個範例會示範如何覆寫在 Microsoft Access 資料基底中取得和設定專案所需的方法。</span><span class="sxs-lookup"><span data-stu-id="8072d-127">This sample shows how to overwrite the methods needed to get and set items in a Microsoft Access data base.</span></span>

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="8072d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8072d-128">See Also</span></span>

[<span data-ttu-id="8072d-129">提供者： ItemCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8072d-129">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="8072d-130">提供者： ContainerCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8072d-130">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="8072d-131">提供者： NavigationCmdletprovider</span><span class="sxs-lookup"><span data-stu-id="8072d-131">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="8072d-132">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="8072d-132">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)
