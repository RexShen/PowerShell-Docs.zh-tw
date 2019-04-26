---
title: 撰寫 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a54ce657-e0e0-4b3e-b9dc-aed39876f933
caps.latest.revision: 11
ms.openlocfilehash: 58252956184703fdcdb3aa9b1db617c6e91294c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080827"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="6d56e-102">撰寫 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6d56e-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="6d56e-103">「 撰寫 Windows PowerShell 提供者 」 是設計 Windows PowerShell 提供者的程式管理員和開發人員實作提供者程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d56e-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="6d56e-104">它會協助您了解 Windows PowerShell 提供者的運作方式，並提供範例程式碼，可用來啟動設計或撰寫您自己的提供者。</span><span class="sxs-lookup"><span data-stu-id="6d56e-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6d56e-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="6d56e-105">In This Section</span></span>

<span data-ttu-id="6d56e-106">[Windows PowerShell 提供者的快速入門](./windows-powershell-provider-quickstart.md)程式碼範例和逐步解說中的一個非常基本的提供者。</span><span class="sxs-lookup"><span data-stu-id="6d56e-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="6d56e-107">[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)本節包含描述 Windows PowerShell 提供者為何，以及其運作方式的主題。</span><span class="sxs-lookup"><span data-stu-id="6d56e-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="6d56e-108">[撰寫項目提供者](./writing-an-item-provider.md)程式碼範例和逐步解說中的取得和設定項目所支援的方法。</span><span class="sxs-lookup"><span data-stu-id="6d56e-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="6d56e-109">[撰寫容器提供者](./writing-a-container-provider.md)程式碼範例和逐步解說中的方法，可支援容器 （有其他項目，做為子系的項目）。</span><span class="sxs-lookup"><span data-stu-id="6d56e-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="6d56e-110">[撰寫瀏覽提供者](./writing-a-navigation-provider.md)程式碼範例和逐步解說中的支援巢狀的容器、 相對路徑，以及移動的項目從某個路徑到另一個方法。</span><span class="sxs-lookup"><span data-stu-id="6d56e-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="6d56e-111">[提供者範例](./provider-samples.md)本節提供提供者的範例。</span><span class="sxs-lookup"><span data-stu-id="6d56e-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d56e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d56e-112">See Also</span></span>

[<span data-ttu-id="6d56e-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6d56e-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)