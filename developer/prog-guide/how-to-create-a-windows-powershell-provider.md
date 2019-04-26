---
title: 如何建立 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081745"
---
# <a name="how-to-create-a-windows-powershell-provider"></a><span data-ttu-id="9097a-102">如何建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-102">How to Create a Windows PowerShell Provider</span></span>

<span data-ttu-id="9097a-103">本節說明如何建置 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="9097a-103">This section describes how to build a Windows PowerShell provider.</span></span> <span data-ttu-id="9097a-104">Windows PowerShell 提供者可以視為兩種方式。</span><span class="sxs-lookup"><span data-stu-id="9097a-104">A Windows PowerShell provider can be considered in two ways.</span></span> <span data-ttu-id="9097a-105">給使用者，提供者會代表一組預存的資料。</span><span class="sxs-lookup"><span data-stu-id="9097a-105">To the user, the provider represents a set of stored data.</span></span> <span data-ttu-id="9097a-106">例如，儲存的資料可以是 Internet Information Services (IIS) Metabase、 Microsoft Windows 登錄、 Windows 檔案系統、 Active Directory 和 Windows PowerShell 所儲存的變數和別名資料。</span><span class="sxs-lookup"><span data-stu-id="9097a-106">For example, the stored data can be the Internet Information Services (IIS) Metabase, the Microsoft Windows Registry, the Windows file system, Active Directory, and the variable and alias data stored by Windows PowerShell.</span></span>

<span data-ttu-id="9097a-107">開發人員，Windows PowerShell 提供者會為使用者和使用者需要存取的資料之間的介面。</span><span class="sxs-lookup"><span data-stu-id="9097a-107">To the developer, the Windows PowerShell provider is the interface between the user and the data that the user needs to access.</span></span> <span data-ttu-id="9097a-108">從這個觀點來看，這一節所述的提供者的每個類型支援一組特定的基底類別和介面，允許 Windows PowerShell 執行階段公開給使用者的特定 cmdlet 的常見方式。</span><span class="sxs-lookup"><span data-stu-id="9097a-108">From this perspective, each type of provider described in this section supports a set of specific base classes and interfaces that allow the Windows PowerShell runtime to expose certain cmdlets to the user in a common way.</span></span>

## <a name="providers-provided-by-windows-powershell"></a><span data-ttu-id="9097a-109">Windows PowerShell 所提供的提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-109">Providers Provided by Windows PowerShell</span></span>

<span data-ttu-id="9097a-110">Windows PowerShell 提供數個提供者 （例如，FileSystem 提供者、 登錄提供者，以及別名提供者），用來存取已知的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="9097a-110">Windows PowerShell provides several providers (such as the FileSystem provider, Registry provider, and Alias provider) that are used to access known data stores.</span></span> <span data-ttu-id="9097a-111">如需有關 Windows PowerShell 所提供的提供者的詳細資訊，請使用下列命令來存取線上說明：</span><span class="sxs-lookup"><span data-stu-id="9097a-111">For more information about the providers supplied by Windows PowerShell, use the following command to access online Help:</span></span>

<span data-ttu-id="9097a-112">**PS > 取得說明 about_providers**</span><span class="sxs-lookup"><span data-stu-id="9097a-112">**PS>get-help about_providers**</span></span>

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a><span data-ttu-id="9097a-113">存取儲存的資料，使用 Windows PowerShell 路徑</span><span class="sxs-lookup"><span data-stu-id="9097a-113">Accessing the Stored Data Using Windows PowerShell Paths</span></span>

<span data-ttu-id="9097a-114">Windows PowerShell 提供者會存取 Windows PowerShell 執行階段，並以程式設計方式透過 Windows PowerShell 路徑使用的命令。</span><span class="sxs-lookup"><span data-stu-id="9097a-114">Windows PowerShell providers are accessible to the Windows PowerShell runtime and to commands programmatically through the use of Windows PowerShell paths.</span></span> <span data-ttu-id="9097a-115">大部分的情況下，這些路徑可直接透過提供者存取資料。</span><span class="sxs-lookup"><span data-stu-id="9097a-115">Most of the time, these paths are used to directly access the data through the provider.</span></span> <span data-ttu-id="9097a-116">不過，某些路徑是可解析成提供者內部的路徑，讓可使用非 Windows PowerShell 應用程式開發介面 (Api) 來存取資料的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9097a-116">However, some paths can be resolved to provider-internal paths that allow a cmdlet to use non-Windows PowerShell application programming interfaces (APIs) to access the data.</span></span> <span data-ttu-id="9097a-117">如需有關 Windows PowerShell 提供者在 Windows PowerShell 的運作方式的詳細資訊，請參閱 < [Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。</span><span class="sxs-lookup"><span data-stu-id="9097a-117">For more information about how Windows PowerShell providers operate within Windows PowerShell, see [How Windows PowerShell Works](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a><span data-ttu-id="9097a-118">公開提供者 Cmdlet 使用 Windows PowerShell 磁碟機</span><span class="sxs-lookup"><span data-stu-id="9097a-118">Exposing Provider Cmdlets Using Windows PowerShell Drives</span></span>

<span data-ttu-id="9097a-119">Windows PowerShell 提供者會公開其支援使用虛擬 Windows PowerShell 磁碟機的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9097a-119">A Windows PowerShell provider exposes its supported cmdlets using virtual Windows PowerShell drives.</span></span> <span data-ttu-id="9097a-120">Windows PowerShell 適用的 Windows PowerShell 磁碟機的下列規則：</span><span class="sxs-lookup"><span data-stu-id="9097a-120">Windows PowerShell applies the following rules for a Windows PowerShell drive:</span></span>

- <span data-ttu-id="9097a-121">磁碟機名稱可以是任何英數字元的序列。</span><span class="sxs-lookup"><span data-stu-id="9097a-121">The name of a drive can be any alphanumeric sequence.</span></span>

- <span data-ttu-id="9097a-122">在任何有效的時間點上的路徑，稱為 「 根 」，您可以指定磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9097a-122">A drive can be specified at any valid point on a path, called a "root".</span></span>

- <span data-ttu-id="9097a-123">磁碟機可以實作的任何預存的資料，不只是檔案系統。</span><span class="sxs-lookup"><span data-stu-id="9097a-123">A drive can be implemented for any stored data, not just the file system.</span></span>

- <span data-ttu-id="9097a-124">每個磁碟機中，會保留自己目前的工作位置，讓使用者能夠保留內容，當磁碟機之間轉移。</span><span class="sxs-lookup"><span data-stu-id="9097a-124">Each drive keeps its own current working location, allowing the user to retain context when shifting between drives.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9097a-125">在本節中</span><span class="sxs-lookup"><span data-stu-id="9097a-125">In This Section</span></span>

<span data-ttu-id="9097a-126">下表列出包含程式碼範例，可建立在彼此的主題。</span><span class="sxs-lookup"><span data-stu-id="9097a-126">The following table lists topics that include code examples that build on each other.</span></span> <span data-ttu-id="9097a-127">從開始第二個主題，基本的 Windows PowerShell 提供者可以初始化，並由 Windows PowerShell 執行階段未初始化下, 一個主題中新增功能存取資料下, 一個主題中新增功能操作資料 （中的項目儲存的資料），依此類推。</span><span class="sxs-lookup"><span data-stu-id="9097a-127">Starting with the second topic, the basic Windows PowerShell provider can be initialized and uninitialized by the Windows PowerShell runtime, the next topic adds functionality for accessing the data, the next topic adds functionality for manipulating the data (the items in the stored data), and so on.</span></span>

|<span data-ttu-id="9097a-128">主題</span><span class="sxs-lookup"><span data-stu-id="9097a-128">Topic</span></span>|<span data-ttu-id="9097a-129">定義</span><span class="sxs-lookup"><span data-stu-id="9097a-129">Definition</span></span>|
|-----------|----------------|
|[<span data-ttu-id="9097a-130">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-130">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)|<span data-ttu-id="9097a-131">本主題討論實作的 Windows PowerShell 提供者之前，您應該考慮的事項。</span><span class="sxs-lookup"><span data-stu-id="9097a-131">This topic discusses things you should consider before implementing a Windows PowerShell provider.</span></span> <span data-ttu-id="9097a-132">它也摘要說明 Windows PowerShell 提供者的基底類別和介面，可用。</span><span class="sxs-lookup"><span data-stu-id="9097a-132">It summarizes the Windows PowerShell provider base classes and interfaces that are used.</span></span>|
|[<span data-ttu-id="9097a-133">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-133">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)|<span data-ttu-id="9097a-134">本主題說明如何建立 Windows PowerShell 提供者，可讓 Windows PowerShell 執行階段初始化，並取消初始化提供者。</span><span class="sxs-lookup"><span data-stu-id="9097a-134">This topic shows how to create a Windows PowerShell provider that allows the Windows PowerShell runtime to initialize and uninitialize the provider.</span></span>|
|[<span data-ttu-id="9097a-135">建立 Windows PowerShell 磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-135">Creating a Windows PowerShell Drive Provider</span></span>](./creating-a-windows-powershell-drive-provider.md)|<span data-ttu-id="9097a-136">本主題說明如何建立 Windows PowerShell 提供者，可讓使用者透過 Windows PowerShell 磁碟機存取資料存放區。</span><span class="sxs-lookup"><span data-stu-id="9097a-136">This topic shows how to create a Windows PowerShell provider that allows the user to access a data store through a Windows PowerShell drive.</span></span>|
|[<span data-ttu-id="9097a-137">建立 Windows PowerShell 項目提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-137">Creating a Windows PowerShell Item Provider</span></span>](./creating-a-windows-powershell-item-provider.md)|<span data-ttu-id="9097a-138">本主題說明如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目。</span><span class="sxs-lookup"><span data-stu-id="9097a-138">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the items in a data store.</span></span>|
|[<span data-ttu-id="9097a-139">建立 Windows PowerShell 容器提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-139">Creating a Windows PowerShell Container Provider</span></span>](./creating-a-windows-powershell-container-provider.md)|<span data-ttu-id="9097a-140">本主題說明如何建立 Windows PowerShell 提供者，可讓使用者在多層的資料存放區上運作。</span><span class="sxs-lookup"><span data-stu-id="9097a-140">This topic shows how to create a Windows PowerShell provider that allows the user to work on multilayer data stores.</span></span>|
|[<span data-ttu-id="9097a-141">建立 Windows PowerShell 巡覽提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-141">Creating a Windows PowerShell Navigation Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)|<span data-ttu-id="9097a-142">本主題說明如何建立 Windows PowerShell 提供者，可讓使用者瀏覽資料存放區的項目，以階層方式。</span><span class="sxs-lookup"><span data-stu-id="9097a-142">This topic shows how to create a Windows PowerShell provider that allows the user to navigate the items of a data store in a hierarchical manner.</span></span>|
|[<span data-ttu-id="9097a-143">建立 Windows PowerShell 內容提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-143">Creating a Windows PowerShell Content Provider</span></span>](./creating-a-windows-powershell-content-provider.md)|<span data-ttu-id="9097a-144">本主題說明如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目內容。</span><span class="sxs-lookup"><span data-stu-id="9097a-144">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the content of items in a data store.</span></span>|
|[<span data-ttu-id="9097a-145">建立 Windows PowerShell 屬性提供者</span><span class="sxs-lookup"><span data-stu-id="9097a-145">Creating a Windows PowerShell Property Provider</span></span>](./creating-a-windows-powershell-property-provider.md)|<span data-ttu-id="9097a-146">本主題說明如何建立 Windows PowerShell 提供者，可讓使用者管理的資料存放區中的項目屬性。</span><span class="sxs-lookup"><span data-stu-id="9097a-146">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the properties of items in a data store.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9097a-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9097a-147">See Also</span></span>

[<span data-ttu-id="9097a-148">Windows PowerShell 的運作方式</span><span class="sxs-lookup"><span data-stu-id="9097a-148">How Windows PowerShell Works</span></span>](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="9097a-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9097a-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="9097a-150">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="9097a-150">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
