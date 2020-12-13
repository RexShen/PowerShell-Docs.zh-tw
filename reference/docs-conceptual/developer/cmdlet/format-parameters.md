---
ms.date: 09/13/2016
ms.topic: reference
title: 格式參數
description: 格式參數
ms.openlocfilehash: 5f970683fedc71b208ff6becad761d94611a91a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652817"
---
# <a name="format-parameters"></a><span data-ttu-id="dd9da-103">格式參數</span><span class="sxs-lookup"><span data-stu-id="dd9da-103">Format Parameters</span></span>

<span data-ttu-id="dd9da-104">下表列出用於格式化或產生資料之參數的建議名稱和功能。</span><span class="sxs-lookup"><span data-stu-id="dd9da-104">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="dd9da-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd9da-105">Parameter</span></span>|<span data-ttu-id="dd9da-106">功能</span><span class="sxs-lookup"><span data-stu-id="dd9da-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="dd9da-107">**按照**</span><span class="sxs-lookup"><span data-stu-id="dd9da-107">**As**</span></span><br><span data-ttu-id="dd9da-108">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="dd9da-108">Data type: Keyword</span></span>|<span data-ttu-id="dd9da-109">請執行此參數來指定 Cmdlet 輸出格式。</span><span class="sxs-lookup"><span data-stu-id="dd9da-109">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="dd9da-110">例如，可能的值可能是文字或腳本。</span><span class="sxs-lookup"><span data-stu-id="dd9da-110">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="dd9da-111">**二進位**</span><span class="sxs-lookup"><span data-stu-id="dd9da-111">**Binary**</span></span><br><span data-ttu-id="dd9da-112">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dd9da-112">Data type: SwitchParameter</span></span>|<span data-ttu-id="dd9da-113">執行此參數，表示 Cmdlet 會處理二進位值。</span><span class="sxs-lookup"><span data-stu-id="dd9da-113">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="dd9da-114">**編碼方式**</span><span class="sxs-lookup"><span data-stu-id="dd9da-114">**Encoding**</span></span><br><span data-ttu-id="dd9da-115">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="dd9da-115">Data type: Keyword</span></span>|<span data-ttu-id="dd9da-116">請執行此參數來指定支援的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="dd9da-116">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="dd9da-117">例如，可能的值可能是 ASCII、UTF8、Unicode、UTF7、BigEndianUnicode、Byte 和 String。</span><span class="sxs-lookup"><span data-stu-id="dd9da-117">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="dd9da-118">**除**</span><span class="sxs-lookup"><span data-stu-id="dd9da-118">**NewLine**</span></span><br><span data-ttu-id="dd9da-119">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dd9da-119">Data type: SwitchParameter</span></span>|<span data-ttu-id="dd9da-120">請執行此參數，以在指定參數時支援分行符號。</span><span class="sxs-lookup"><span data-stu-id="dd9da-120">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="dd9da-121">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="dd9da-121">**ShortName**</span></span><br><span data-ttu-id="dd9da-122">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dd9da-122">Data type: SwitchParameter</span></span>|<span data-ttu-id="dd9da-123">請執行此參數，以在指定參數時支援簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="dd9da-123">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="dd9da-124">**寬度**</span><span class="sxs-lookup"><span data-stu-id="dd9da-124">**Width**</span></span><br><span data-ttu-id="dd9da-125">資料類型： Int32</span><span class="sxs-lookup"><span data-stu-id="dd9da-125">Data type: Int32</span></span>|<span data-ttu-id="dd9da-126">執行此參數，讓使用者可以指定輸出裝置的寬度。</span><span class="sxs-lookup"><span data-stu-id="dd9da-126">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="dd9da-127">**包裝**</span><span class="sxs-lookup"><span data-stu-id="dd9da-127">**Wrap**</span></span><br><span data-ttu-id="dd9da-128">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="dd9da-128">Data type: SwitchParameter</span></span>|<span data-ttu-id="dd9da-129">請執行此參數，以在指定參數時支援文字換行。</span><span class="sxs-lookup"><span data-stu-id="dd9da-129">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="dd9da-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd9da-130">See Also</span></span>

[<span data-ttu-id="dd9da-131">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="dd9da-131">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="dd9da-132">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dd9da-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="dd9da-133">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dd9da-133">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
