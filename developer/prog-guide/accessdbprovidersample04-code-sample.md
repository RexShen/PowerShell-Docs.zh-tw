---
title: AccessDbProviderSample04 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853604"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="6b399-102">AccessDbProviderSample04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6b399-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="6b399-103">下列程式碼顯示中所述的 Windows PowerShell 提供者的實作[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6b399-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="6b399-104">此提供者適用於多層資料存放區。</span><span class="sxs-lookup"><span data-stu-id="6b399-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="6b399-105">針對此類型的資料存放區中，存放區的最上層包含根項目，以及每個後續的層級指節點的子項目。</span><span class="sxs-lookup"><span data-stu-id="6b399-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="6b399-106">藉由讓使用者能夠在這些子節點上運作，使用者可以階層方式透過資料存放區互動。</span><span class="sxs-lookup"><span data-stu-id="6b399-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6b399-107">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6b399-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="6b399-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b399-108">See Also</span></span>

[<span data-ttu-id="6b399-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6b399-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)