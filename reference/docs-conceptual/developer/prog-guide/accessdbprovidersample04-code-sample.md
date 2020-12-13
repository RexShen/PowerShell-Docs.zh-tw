---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample04 程式碼範例
description: AccessDbProviderSample04 程式碼範例
ms.openlocfilehash: bb70ce9f1b1c94349c354a8771fedf7fcb1bb320
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647559"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="f2663-103">AccessDbProviderSample04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f2663-103">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="f2663-104">下列程式碼顯示 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)時所述的 Windows PowerShell 提供者的執行。</span><span class="sxs-lookup"><span data-stu-id="f2663-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="f2663-105">此提供者適用于多層式資料存放區。</span><span class="sxs-lookup"><span data-stu-id="f2663-105">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="f2663-106">對於這種類型的資料存放區，存放區的最上層包含根專案，而且每個後續層級稱為子專案的節點。</span><span class="sxs-lookup"><span data-stu-id="f2663-106">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="f2663-107">藉由允許使用者在這些子節點上工作，使用者就可以透過資料存放區以階層方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="f2663-107">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f2663-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f2663-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="f2663-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2663-109">See Also</span></span>

[<span data-ttu-id="f2663-110">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f2663-110">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
