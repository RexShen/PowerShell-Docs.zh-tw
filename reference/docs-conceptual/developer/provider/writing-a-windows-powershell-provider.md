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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366187"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="0948d-102">撰寫 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="0948d-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="0948d-103">「撰寫 Windows PowerShell 提供者」適用于設計 Windows PowerShell 提供者的程式管理員，以及正在執行提供者程式碼的開發人員。</span><span class="sxs-lookup"><span data-stu-id="0948d-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="0948d-104">它將協助您瞭解 Windows PowerShell 提供者的工作方式，並提供可用來開始設計或撰寫您自己的提供者的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="0948d-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0948d-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="0948d-105">In This Section</span></span>

<span data-ttu-id="0948d-106">[Windows PowerShell 提供者快速入門](./windows-powershell-provider-quickstart.md)非常基本提供者的範例程式碼和逐步解說。</span><span class="sxs-lookup"><span data-stu-id="0948d-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="0948d-107">[Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)本節包含的主題說明 Windows PowerShell 提供者是什麼，以及它們的作用。</span><span class="sxs-lookup"><span data-stu-id="0948d-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="0948d-108">[撰寫專案提供者](./writing-an-item-provider.md)支援取得和設定專案之方法的範例程式碼和逐步解說。</span><span class="sxs-lookup"><span data-stu-id="0948d-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="0948d-109">[撰寫容器提供者](./writing-a-container-provider.md)支援容器之方法的範例程式碼和逐步解說（具有其他專案做為子系的專案）。</span><span class="sxs-lookup"><span data-stu-id="0948d-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="0948d-110">[撰寫導覽提供者](./writing-a-navigation-provider.md)方法的範例程式碼和逐步解說，可支援嵌套的容器、相對路徑，以及將專案從某個路徑移至另一個路徑。</span><span class="sxs-lookup"><span data-stu-id="0948d-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="0948d-111">[提供者範例](./provider-samples.md)本節提供提供者的範例。</span><span class="sxs-lookup"><span data-stu-id="0948d-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="0948d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0948d-112">See Also</span></span>

[<span data-ttu-id="0948d-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0948d-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)