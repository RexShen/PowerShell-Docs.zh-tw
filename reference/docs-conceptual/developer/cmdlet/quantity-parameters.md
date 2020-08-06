---
title: 數量參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7ff6562380bb6336b08879b31d8d9fed47bfb6a7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781812"
---
# <a name="quantity-parameters"></a><span data-ttu-id="c84b6-102">數量參數</span><span class="sxs-lookup"><span data-stu-id="c84b6-102">Quantity Parameters</span></span>

<span data-ttu-id="c84b6-103">下表列出數量參數的建議名稱和功能。</span><span class="sxs-lookup"><span data-stu-id="c84b6-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="c84b6-104">參數</span><span class="sxs-lookup"><span data-stu-id="c84b6-104">Parameter</span></span>|<span data-ttu-id="c84b6-105">功能</span><span class="sxs-lookup"><span data-stu-id="c84b6-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="c84b6-106">**全部**</span><span class="sxs-lookup"><span data-stu-id="c84b6-106">**All**</span></span><br><span data-ttu-id="c84b6-107">資料類型：布林值</span><span class="sxs-lookup"><span data-stu-id="c84b6-107">Data type: Boolean</span></span>|<span data-ttu-id="c84b6-108">執行此參數，以 `true` 指出所有資源都應採取動作，而不是預設的資源子集。</span><span class="sxs-lookup"><span data-stu-id="c84b6-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="c84b6-109">執行此參數，以 `false` 指出資源的子集。</span><span class="sxs-lookup"><span data-stu-id="c84b6-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="c84b6-110">**配置**</span><span class="sxs-lookup"><span data-stu-id="c84b6-110">**Allocation**</span></span><br><span data-ttu-id="c84b6-111">資料類型： Int32</span><span class="sxs-lookup"><span data-stu-id="c84b6-111">Data type: Int32</span></span>|<span data-ttu-id="c84b6-112">執行此參數，讓使用者可以指定要配置的專案數。</span><span class="sxs-lookup"><span data-stu-id="c84b6-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="c84b6-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="c84b6-113">**BlockCount**</span></span><br><span data-ttu-id="c84b6-114">資料類型： Int64</span><span class="sxs-lookup"><span data-stu-id="c84b6-114">Data type: Int64</span></span>|<span data-ttu-id="c84b6-115">執行此參數，讓使用者可以指定區塊計數。</span><span class="sxs-lookup"><span data-stu-id="c84b6-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="c84b6-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="c84b6-116">**Count**</span></span><br><span data-ttu-id="c84b6-117">資料類型： Int64</span><span class="sxs-lookup"><span data-stu-id="c84b6-117">Data type: Int64</span></span>|<span data-ttu-id="c84b6-118">執行此參數，讓使用者可以指定計數。</span><span class="sxs-lookup"><span data-stu-id="c84b6-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="c84b6-119">**範圍**</span><span class="sxs-lookup"><span data-stu-id="c84b6-119">**Scope**</span></span><br><span data-ttu-id="c84b6-120">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="c84b6-120">Data type: Keyword</span></span>|<span data-ttu-id="c84b6-121">執行此參數，讓使用者可以指定要操作的範圍。</span><span class="sxs-lookup"><span data-stu-id="c84b6-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c84b6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c84b6-122">See Also</span></span>

[<span data-ttu-id="c84b6-123">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="c84b6-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="c84b6-124">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c84b6-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c84b6-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c84b6-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
