---
title: 數量參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369557"
---
# <a name="quantity-parameters"></a><span data-ttu-id="1e185-102">數量參數</span><span class="sxs-lookup"><span data-stu-id="1e185-102">Quantity Parameters</span></span>

<span data-ttu-id="1e185-103">下表列出數量參數的建議名稱和功能。</span><span class="sxs-lookup"><span data-stu-id="1e185-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="1e185-104">參數</span><span class="sxs-lookup"><span data-stu-id="1e185-104">Parameter</span></span>|<span data-ttu-id="1e185-105">功能</span><span class="sxs-lookup"><span data-stu-id="1e185-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="1e185-106">**全部**</span><span class="sxs-lookup"><span data-stu-id="1e185-106">**All**</span></span><br><span data-ttu-id="1e185-107">資料類型：布林值</span><span class="sxs-lookup"><span data-stu-id="1e185-107">Data type: Boolean</span></span>|<span data-ttu-id="1e185-108">請執行此參數，讓 `true` 表示應根據預設的資源子集來處理所有資源。</span><span class="sxs-lookup"><span data-stu-id="1e185-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="1e185-109">執行此參數，讓 `false` 表示資源的子集。</span><span class="sxs-lookup"><span data-stu-id="1e185-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="1e185-110">**配置**</span><span class="sxs-lookup"><span data-stu-id="1e185-110">**Allocation**</span></span><br><span data-ttu-id="1e185-111">資料類型： Int32</span><span class="sxs-lookup"><span data-stu-id="1e185-111">Data type: Int32</span></span>|<span data-ttu-id="1e185-112">執行此參數，讓使用者可以指定要配置的專案數。</span><span class="sxs-lookup"><span data-stu-id="1e185-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="1e185-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="1e185-113">**BlockCount**</span></span><br><span data-ttu-id="1e185-114">資料類型： Int64</span><span class="sxs-lookup"><span data-stu-id="1e185-114">Data type: Int64</span></span>|<span data-ttu-id="1e185-115">執行此參數，讓使用者可以指定區塊計數。</span><span class="sxs-lookup"><span data-stu-id="1e185-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="1e185-116">**計數**</span><span class="sxs-lookup"><span data-stu-id="1e185-116">**Count**</span></span><br><span data-ttu-id="1e185-117">資料類型： Int64</span><span class="sxs-lookup"><span data-stu-id="1e185-117">Data type: Int64</span></span>|<span data-ttu-id="1e185-118">執行此參數，讓使用者可以指定計數。</span><span class="sxs-lookup"><span data-stu-id="1e185-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="1e185-119">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="1e185-119">**Scope**</span></span><br><span data-ttu-id="1e185-120">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="1e185-120">Data type: Keyword</span></span>|<span data-ttu-id="1e185-121">執行此參數，讓使用者可以指定要操作的範圍。</span><span class="sxs-lookup"><span data-stu-id="1e185-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1e185-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e185-122">See Also</span></span>

[<span data-ttu-id="1e185-123">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="1e185-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="1e185-124">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1e185-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="1e185-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1e185-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
