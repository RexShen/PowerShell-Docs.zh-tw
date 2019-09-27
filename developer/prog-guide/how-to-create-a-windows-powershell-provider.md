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
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323082"
---
# <a name="how-to-create-a-windows-powershell-provider"></a><span data-ttu-id="765ec-102">如何建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-102">How to Create a Windows PowerShell Provider</span></span>

<span data-ttu-id="765ec-103">本節說明如何建立 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="765ec-103">This section describes how to build a Windows PowerShell provider.</span></span> <span data-ttu-id="765ec-104">Windows PowerShell 提供者可透過兩種方式來考慮。</span><span class="sxs-lookup"><span data-stu-id="765ec-104">A Windows PowerShell provider can be considered in two ways.</span></span> <span data-ttu-id="765ec-105">對使用者而言，提供者代表一組已儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="765ec-105">To the user, the provider represents a set of stored data.</span></span> <span data-ttu-id="765ec-106">例如，儲存的資料可以是 Internet Information Services （IIS）的資料庫、Microsoft Windows 登錄、Windows 檔案系統、Active Directory，以及 Windows PowerShell 所儲存的變數和別名資料。</span><span class="sxs-lookup"><span data-stu-id="765ec-106">For example, the stored data can be the Internet Information Services (IIS) Metabase, the Microsoft Windows Registry, the Windows file system, Active Directory, and the variable and alias data stored by Windows PowerShell.</span></span>

<span data-ttu-id="765ec-107">對開發人員而言，Windows PowerShell 提供者是使用者與使用者需要存取的資料之間的介面。</span><span class="sxs-lookup"><span data-stu-id="765ec-107">To the developer, the Windows PowerShell provider is the interface between the user and the data that the user needs to access.</span></span> <span data-ttu-id="765ec-108">從這個觀點來看，本節所述的每一種提供者都支援一組特定的基類和介面，可讓 Windows PowerShell 執行時間以一般方式向使用者公開特定 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="765ec-108">From this perspective, each type of provider described in this section supports a set of specific base classes and interfaces that allow the Windows PowerShell runtime to expose certain cmdlets to the user in a common way.</span></span>

## <a name="providers-provided-by-windows-powershell"></a><span data-ttu-id="765ec-109">Windows PowerShell 所提供的提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-109">Providers Provided by Windows PowerShell</span></span>

<span data-ttu-id="765ec-110">Windows PowerShell 提供數個提供者（例如 FileSystem 提供者、登錄提供者和別名提供者），用來存取已知的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="765ec-110">Windows PowerShell provides several providers (such as the FileSystem provider, Registry provider, and Alias provider) that are used to access known data stores.</span></span> <span data-ttu-id="765ec-111">如需 Windows PowerShell 提供之提供者的詳細資訊，請使用下列命令來存取線上說明：</span><span class="sxs-lookup"><span data-stu-id="765ec-111">For more information about the providers supplied by Windows PowerShell, use the following command to access online Help:</span></span>

<span data-ttu-id="765ec-112">**PS > get-help about_providers**</span><span class="sxs-lookup"><span data-stu-id="765ec-112">**PS>get-help about_providers**</span></span>

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a><span data-ttu-id="765ec-113">使用 Windows PowerShell 路徑存取儲存的資料</span><span class="sxs-lookup"><span data-stu-id="765ec-113">Accessing the Stored Data Using Windows PowerShell Paths</span></span>

<span data-ttu-id="765ec-114">Windows powershell 提供者可以透過使用 Windows PowerShell 路徑，以程式設計方式存取 windows powershell 執行時間和命令。</span><span class="sxs-lookup"><span data-stu-id="765ec-114">Windows PowerShell providers are accessible to the Windows PowerShell runtime and to commands programmatically through the use of Windows PowerShell paths.</span></span> <span data-ttu-id="765ec-115">在大部分的情況下，這些路徑是用來透過提供者直接存取資料。</span><span class="sxs-lookup"><span data-stu-id="765ec-115">Most of the time, these paths are used to directly access the data through the provider.</span></span> <span data-ttu-id="765ec-116">不過，某些路徑可以解析成提供者內部路徑，讓 Cmdlet 可以使用非 Windows PowerShell 應用程式開發介面（Api）來存取資料。</span><span class="sxs-lookup"><span data-stu-id="765ec-116">However, some paths can be resolved to provider-internal paths that allow a cmdlet to use non-Windows PowerShell application programming interfaces (APIs) to access the data.</span></span> <span data-ttu-id="765ec-117">如需 Windows powershell 提供者如何在 Windows PowerShell 中運作的詳細資訊，請參閱[Windows powershell 的運作方式](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。</span><span class="sxs-lookup"><span data-stu-id="765ec-117">For more information about how Windows PowerShell providers operate within Windows PowerShell, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a><span data-ttu-id="765ec-118">使用 Windows PowerShell 磁片磁碟機公開提供者 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="765ec-118">Exposing Provider Cmdlets Using Windows PowerShell Drives</span></span>

<span data-ttu-id="765ec-119">Windows PowerShell 提供者會使用虛擬 Windows PowerShell 磁片磁碟機來公開其支援的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="765ec-119">A Windows PowerShell provider exposes its supported cmdlets using virtual Windows PowerShell drives.</span></span> <span data-ttu-id="765ec-120">Windows PowerShell 會針對 Windows PowerShell 磁片磁碟機套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="765ec-120">Windows PowerShell applies the following rules for a Windows PowerShell drive:</span></span>

- <span data-ttu-id="765ec-121">磁片磁碟機的名稱可以是任何英數位元序列。</span><span class="sxs-lookup"><span data-stu-id="765ec-121">The name of a drive can be any alphanumeric sequence.</span></span>

- <span data-ttu-id="765ec-122">磁片磁碟機可以在路徑上的任何有效點指定，稱為「根」。</span><span class="sxs-lookup"><span data-stu-id="765ec-122">A drive can be specified at any valid point on a path, called a "root".</span></span>

- <span data-ttu-id="765ec-123">磁片磁碟機可以針對任何儲存的資料進行實作為，而不只是檔案系統。</span><span class="sxs-lookup"><span data-stu-id="765ec-123">A drive can be implemented for any stored data, not just the file system.</span></span>

- <span data-ttu-id="765ec-124">每個磁片磁碟機都會保留它自己目前的工作位置，讓使用者可以在磁片磁碟機之間切換時保留內容。</span><span class="sxs-lookup"><span data-stu-id="765ec-124">Each drive keeps its own current working location, allowing the user to retain context when shifting between drives.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="765ec-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="765ec-125">In This Section</span></span>

<span data-ttu-id="765ec-126">下表列出包含彼此建立之程式碼範例的主題。</span><span class="sxs-lookup"><span data-stu-id="765ec-126">The following table lists topics that include code examples that build on each other.</span></span> <span data-ttu-id="765ec-127">從第二個主題開始，Windows PowerShell 執行時間可以初始化並解除初始化基本 Windows PowerShell 提供者，下一個主題新增存取資料的功能，下一個主題新增運算元據的功能（儲存的資料中的專案）等等。</span><span class="sxs-lookup"><span data-stu-id="765ec-127">Starting with the second topic, the basic Windows PowerShell provider can be initialized and uninitialized by the Windows PowerShell runtime, the next topic adds functionality for accessing the data, the next topic adds functionality for manipulating the data (the items in the stored data), and so on.</span></span>

|<span data-ttu-id="765ec-128">主題</span><span class="sxs-lookup"><span data-stu-id="765ec-128">Topic</span></span>|<span data-ttu-id="765ec-129">定義</span><span class="sxs-lookup"><span data-stu-id="765ec-129">Definition</span></span>|
|-----------|----------------|
|[<span data-ttu-id="765ec-130">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-130">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)|<span data-ttu-id="765ec-131">本主題討論您在執行 Windows PowerShell 提供者之前應考慮的事項。</span><span class="sxs-lookup"><span data-stu-id="765ec-131">This topic discusses things you should consider before implementing a Windows PowerShell provider.</span></span> <span data-ttu-id="765ec-132">它會摘要說明所使用的 Windows PowerShell 提供者基類和介面。</span><span class="sxs-lookup"><span data-stu-id="765ec-132">It summarizes the Windows PowerShell provider base classes and interfaces that are used.</span></span>|
|[<span data-ttu-id="765ec-133">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-133">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)|<span data-ttu-id="765ec-134">本主題說明如何建立 Windows PowerShell 提供者，以允許 Windows PowerShell 執行時間初始化和取消初始化提供者。</span><span class="sxs-lookup"><span data-stu-id="765ec-134">This topic shows how to create a Windows PowerShell provider that allows the Windows PowerShell runtime to initialize and uninitialize the provider.</span></span>|
|[<span data-ttu-id="765ec-135">建立 Windows PowerShell 磁片磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-135">Creating a Windows PowerShell Drive Provider</span></span>](./creating-a-windows-powershell-drive-provider.md)|<span data-ttu-id="765ec-136">本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以透過 Windows PowerShell 磁片磁碟機存取資料存放區。</span><span class="sxs-lookup"><span data-stu-id="765ec-136">This topic shows how to create a Windows PowerShell provider that allows the user to access a data store through a Windows PowerShell drive.</span></span>|
|[<span data-ttu-id="765ec-137">建立 Windows PowerShell 專案提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-137">Creating a Windows PowerShell Item Provider</span></span>](./creating-a-windows-powershell-item-provider.md)|<span data-ttu-id="765ec-138">本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中的專案。</span><span class="sxs-lookup"><span data-stu-id="765ec-138">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the items in a data store.</span></span>|
|[<span data-ttu-id="765ec-139">建立 Windows PowerShell 容器提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-139">Creating a Windows PowerShell Container Provider</span></span>](./creating-a-windows-powershell-container-provider.md)|<span data-ttu-id="765ec-140">本主題說明如何建立可讓使用者在多層資料存放區上工作的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="765ec-140">This topic shows how to create a Windows PowerShell provider that allows the user to work on multilayer data stores.</span></span>|
|[<span data-ttu-id="765ec-141">建立 Windows PowerShell 流覽提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-141">Creating a Windows PowerShell Navigation Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)|<span data-ttu-id="765ec-142">本主題說明如何建立 Windows PowerShell 提供者，讓使用者以階層方式流覽資料存放區的專案。</span><span class="sxs-lookup"><span data-stu-id="765ec-142">This topic shows how to create a Windows PowerShell provider that allows the user to navigate the items of a data store in a hierarchical manner.</span></span>|
|[<span data-ttu-id="765ec-143">建立 Windows PowerShell 內容提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-143">Creating a Windows PowerShell Content Provider</span></span>](./creating-a-windows-powershell-content-provider.md)|<span data-ttu-id="765ec-144">本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中的專案內容。</span><span class="sxs-lookup"><span data-stu-id="765ec-144">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the content of items in a data store.</span></span>|
|[<span data-ttu-id="765ec-145">建立 Windows PowerShell 屬性提供者</span><span class="sxs-lookup"><span data-stu-id="765ec-145">Creating a Windows PowerShell Property Provider</span></span>](./creating-a-windows-powershell-property-provider.md)|<span data-ttu-id="765ec-146">本主題說明如何建立 Windows PowerShell 提供者，讓使用者可以運算元據存放區中專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="765ec-146">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the properties of items in a data store.</span></span>|

## <a name="see-also"></a><span data-ttu-id="765ec-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="765ec-147">See Also</span></span>

[<span data-ttu-id="765ec-148">Windows PowerShell 的運作方式</span><span class="sxs-lookup"><span data-stu-id="765ec-148">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="765ec-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="765ec-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="765ec-150">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="765ec-150">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
