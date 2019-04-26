---
title: Windows PowerShell 概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: c4b13518ad6452a39ca49e897e1d3e353818d332
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081028"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="26f7e-102">Windows PowerShell 概念</span><span class="sxs-lookup"><span data-stu-id="26f7e-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="26f7e-103">本節包含可協助您了解 Windows PowerShell，從開發人員的觀點來看的概念性資訊。</span><span class="sxs-lookup"><span data-stu-id="26f7e-103">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>

|<span data-ttu-id="26f7e-104">主題名稱</span><span class="sxs-lookup"><span data-stu-id="26f7e-104">Topic Name</span></span>|<span data-ttu-id="26f7e-105">描述</span><span class="sxs-lookup"><span data-stu-id="26f7e-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="26f7e-106">Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="26f7e-106">Windows PowerShell Providers</span></span>](http://msdn.microsoft.com/en-us/a65c5c75-1131-4ade-90d3-a613dbe620e9)|<span data-ttu-id="26f7e-107">討論用來存取資料的 Windows PowerShell 提供者會儲存。</span><span class="sxs-lookup"><span data-stu-id="26f7e-107">A discussion about Windows PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="26f7e-108">Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="26f7e-108">Windows PowerShell Snap-ins</span></span>](http://msdn.microsoft.com/en-us/20e081a9-522c-48bf-9f21-faaf8cca2e82)|<span data-ttu-id="26f7e-109">註冊 cmdlet 與提供者的一種機制。</span><span class="sxs-lookup"><span data-stu-id="26f7e-109">A mechanism for registering cmdlets and providers.</span></span> <span data-ttu-id="26f7e-110">(另請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。)</span><span class="sxs-lookup"><span data-stu-id="26f7e-110">(See also, [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).)</span></span>|
|[<span data-ttu-id="26f7e-111">Windows PowerShell 執行階段</span><span class="sxs-lookup"><span data-stu-id="26f7e-111">Windows PowerShell Runtime</span></span>](http://msdn.microsoft.com/en-us/949f06e8-0224-4cd3-bbad-a0cebbb5dec8)|<span data-ttu-id="26f7e-112">目前的執行個體的 Windows PowerShell runspace。</span><span class="sxs-lookup"><span data-stu-id="26f7e-112">The current instance of the Windows PowerShell runspace.</span></span>|
|[<span data-ttu-id="26f7e-113">Windows PowerShell Runspace</span><span class="sxs-lookup"><span data-stu-id="26f7e-113">Windows PowerShell Runspaces</span></span>](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)|<span data-ttu-id="26f7e-114">作業的環境，其中可以處理命令。</span><span class="sxs-lookup"><span data-stu-id="26f7e-114">The operating environments where commands are processed.</span></span>|
|[<span data-ttu-id="26f7e-115">Windows PowerShell 的命名空間</span><span class="sxs-lookup"><span data-stu-id="26f7e-115">Windows PowerShell Namespaces</span></span>](http://msdn.microsoft.com/en-us/04bd2841-e90c-47d2-8a1f-3aeb3df35176)|<span data-ttu-id="26f7e-116">Windows PowerShell API 命名空間的概觀。</span><span class="sxs-lookup"><span data-stu-id="26f7e-116">Overview of Windows PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="26f7e-117">Windows PowerShell 說明</span><span class="sxs-lookup"><span data-stu-id="26f7e-117">Windows PowerShell Help</span></span>](http://msdn.microsoft.com/en-us/097b7c1c-a056-4b36-9c86-65b2ee702fc7)|<span data-ttu-id="26f7e-118">撰寫 cmdlet 說明的相關討論。</span><span class="sxs-lookup"><span data-stu-id="26f7e-118">A discussion about writing cmdlet Help.</span></span>|
|[<span data-ttu-id="26f7e-119">要求確認</span><span class="sxs-lookup"><span data-stu-id="26f7e-119">Requesting Confirmation</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="26f7e-120">討論如何 cmdlet 與提供者的意見反應向使用者要求的動作之前，不會執行。</span><span class="sxs-lookup"><span data-stu-id="26f7e-120">A discussion about how cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="26f7e-121">Windows PowerShell 物件概念</span><span class="sxs-lookup"><span data-stu-id="26f7e-121">Windows PowerShell Object Concepts</span></span>](http://msdn.microsoft.com/en-us/a1449178-b6fd-4ca8-a5e1-d747c2c54181)|<span data-ttu-id="26f7e-122">Windows PowerShell 如何處理物件。</span><span class="sxs-lookup"><span data-stu-id="26f7e-122">How Windows PowerShell handles objects.</span></span>|
|[<span data-ttu-id="26f7e-123">Windows PowerShell 擴充類型系統 (ETS)</span><span class="sxs-lookup"><span data-stu-id="26f7e-123">Windows PowerShell Extended Type System (ETS)</span></span>](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)|<span data-ttu-id="26f7e-124">以程式設計方式擴充物件。</span><span class="sxs-lookup"><span data-stu-id="26f7e-124">Programmatically extending objects.</span></span>|

## <a name="see-also"></a><span data-ttu-id="26f7e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26f7e-125">See Also</span></span>

[<span data-ttu-id="26f7e-126">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="26f7e-126">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)