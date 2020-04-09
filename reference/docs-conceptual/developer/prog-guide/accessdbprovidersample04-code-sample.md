---
title: AccessDbProviderSample04 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 60f0ed4e3d39ee93ab63023161d09a6c7b914798
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978571"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="7c29a-102">AccessDbProviderSample04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7c29a-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="7c29a-103">下列程式碼示範如何執行[建立 Windows Powershell 容器提供者](./creating-a-windows-powershell-container-provider.md)中所述的 windows powershell 提供者。</span><span class="sxs-lookup"><span data-stu-id="7c29a-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>
<span data-ttu-id="7c29a-104">此提供者適用于多層式資料存放區。</span><span class="sxs-lookup"><span data-stu-id="7c29a-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="7c29a-105">對於這種類型的資料存放區，存放區的最上層包含根專案，而每個後續層級稱為子專案的節點。</span><span class="sxs-lookup"><span data-stu-id="7c29a-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="7c29a-106">藉由允許使用者在這些子節點上工作，使用者可以透過資料存放區以階層方式進行互動。</span><span class="sxs-lookup"><span data-stu-id="7c29a-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7c29a-107">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7c29a-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a><span data-ttu-id="7c29a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c29a-108">See Also</span></span>

[<span data-ttu-id="7c29a-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7c29a-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
