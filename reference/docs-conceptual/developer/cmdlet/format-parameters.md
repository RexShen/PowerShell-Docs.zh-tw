---
title: 格式參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369747"
---
# <a name="format-parameters"></a><span data-ttu-id="b9631-102">格式參數</span><span class="sxs-lookup"><span data-stu-id="b9631-102">Format Parameters</span></span>

<span data-ttu-id="b9631-103">下表列出用來格式化或產生資料之參數的建議名稱和功能。</span><span class="sxs-lookup"><span data-stu-id="b9631-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="b9631-104">參數</span><span class="sxs-lookup"><span data-stu-id="b9631-104">Parameter</span></span>|<span data-ttu-id="b9631-105">功能</span><span class="sxs-lookup"><span data-stu-id="b9631-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="b9631-106">**As**</span><span class="sxs-lookup"><span data-stu-id="b9631-106">**As**</span></span><br><span data-ttu-id="b9631-107">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="b9631-107">Data type: Keyword</span></span>|<span data-ttu-id="b9631-108">執行此參數以指定 Cmdlet 輸出格式。</span><span class="sxs-lookup"><span data-stu-id="b9631-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="b9631-109">例如，可能的值可以是文字或腳本。</span><span class="sxs-lookup"><span data-stu-id="b9631-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="b9631-110">**二進位**</span><span class="sxs-lookup"><span data-stu-id="b9631-110">**Binary**</span></span><br><span data-ttu-id="b9631-111">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b9631-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="b9631-112">執行這個參數，以指出 Cmdlet 會處理二進位值。</span><span class="sxs-lookup"><span data-stu-id="b9631-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="b9631-113">**編碼方式**</span><span class="sxs-lookup"><span data-stu-id="b9631-113">**Encoding**</span></span><br><span data-ttu-id="b9631-114">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="b9631-114">Data type: Keyword</span></span>|<span data-ttu-id="b9631-115">執行此參數來指定支援的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="b9631-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="b9631-116">例如，可能的值為 ASCII、UTF8、Unicode、UTF7、BigEndianUnicode、Byte 和 String。</span><span class="sxs-lookup"><span data-stu-id="b9631-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="b9631-117">**換**</span><span class="sxs-lookup"><span data-stu-id="b9631-117">**NewLine**</span></span><br><span data-ttu-id="b9631-118">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b9631-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="b9631-119">執行此參數，以便在指定參數時支援分行符號。</span><span class="sxs-lookup"><span data-stu-id="b9631-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="b9631-120">**簡短名稱**</span><span class="sxs-lookup"><span data-stu-id="b9631-120">**ShortName**</span></span><br><span data-ttu-id="b9631-121">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b9631-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="b9631-122">請執行此參數，以便在指定參數時支援簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="b9631-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="b9631-123">**寬度**</span><span class="sxs-lookup"><span data-stu-id="b9631-123">**Width**</span></span><br><span data-ttu-id="b9631-124">資料類型： Int32</span><span class="sxs-lookup"><span data-stu-id="b9631-124">Data type: Int32</span></span>|<span data-ttu-id="b9631-125">執行此參數，讓使用者可以指定輸出裝置的寬度。</span><span class="sxs-lookup"><span data-stu-id="b9631-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="b9631-126">**回繞**</span><span class="sxs-lookup"><span data-stu-id="b9631-126">**Wrap**</span></span><br><span data-ttu-id="b9631-127">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="b9631-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="b9631-128">執行此參數，以便在指定參數時支援文字換行。</span><span class="sxs-lookup"><span data-stu-id="b9631-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="b9631-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9631-129">See Also</span></span>

[<span data-ttu-id="b9631-130">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="b9631-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="b9631-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9631-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b9631-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b9631-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
