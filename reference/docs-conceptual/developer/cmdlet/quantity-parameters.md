---
ms.date: 09/13/2016
ms.topic: reference
title: 數量參數
description: 數量參數
ms.openlocfilehash: 3f7c23eec34a709b1f2d59f611c93909b20f4124
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650307"
---
# <a name="quantity-parameters"></a><span data-ttu-id="819b8-103">數量參數</span><span class="sxs-lookup"><span data-stu-id="819b8-103">Quantity Parameters</span></span>

<span data-ttu-id="819b8-104">下表列出數量參數的建議名稱和功能。</span><span class="sxs-lookup"><span data-stu-id="819b8-104">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="819b8-105">參數</span><span class="sxs-lookup"><span data-stu-id="819b8-105">Parameter</span></span>|<span data-ttu-id="819b8-106">功能</span><span class="sxs-lookup"><span data-stu-id="819b8-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="819b8-107">**全部**</span><span class="sxs-lookup"><span data-stu-id="819b8-107">**All**</span></span><br><span data-ttu-id="819b8-108">資料類型：布林值</span><span class="sxs-lookup"><span data-stu-id="819b8-108">Data type: Boolean</span></span>|<span data-ttu-id="819b8-109">請執行此參數，以 `true` 指出所有資源都應採取動作，而不是預設的資源子集。</span><span class="sxs-lookup"><span data-stu-id="819b8-109">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="819b8-110">執行這個參數，以 `false` 指出資源的子集。</span><span class="sxs-lookup"><span data-stu-id="819b8-110">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="819b8-111">**配置**</span><span class="sxs-lookup"><span data-stu-id="819b8-111">**Allocation**</span></span><br><span data-ttu-id="819b8-112">資料類型： Int32</span><span class="sxs-lookup"><span data-stu-id="819b8-112">Data type: Int32</span></span>|<span data-ttu-id="819b8-113">執行此參數，讓使用者可以指定要配置的專案數目。</span><span class="sxs-lookup"><span data-stu-id="819b8-113">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="819b8-114">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="819b8-114">**BlockCount**</span></span><br><span data-ttu-id="819b8-115">資料類型： Int64</span><span class="sxs-lookup"><span data-stu-id="819b8-115">Data type: Int64</span></span>|<span data-ttu-id="819b8-116">執行此參數，讓使用者可以指定區塊計數。</span><span class="sxs-lookup"><span data-stu-id="819b8-116">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="819b8-117">**Count**</span><span class="sxs-lookup"><span data-stu-id="819b8-117">**Count**</span></span><br><span data-ttu-id="819b8-118">資料類型： Int64</span><span class="sxs-lookup"><span data-stu-id="819b8-118">Data type: Int64</span></span>|<span data-ttu-id="819b8-119">執行此參數，讓使用者可以指定計數。</span><span class="sxs-lookup"><span data-stu-id="819b8-119">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="819b8-120">**範圍**</span><span class="sxs-lookup"><span data-stu-id="819b8-120">**Scope**</span></span><br><span data-ttu-id="819b8-121">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="819b8-121">Data type: Keyword</span></span>|<span data-ttu-id="819b8-122">執行此參數，讓使用者可以指定要操作的範圍。</span><span class="sxs-lookup"><span data-stu-id="819b8-122">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="819b8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="819b8-123">See Also</span></span>

[<span data-ttu-id="819b8-124">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="819b8-124">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="819b8-125">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="819b8-125">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="819b8-126">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="819b8-126">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
