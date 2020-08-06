---
title: 格式參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8e031f62aa8bcb0e9d5b900b2eace7187b1f3dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784277"
---
# <a name="format-parameters"></a><span data-ttu-id="54771-102">格式參數</span><span class="sxs-lookup"><span data-stu-id="54771-102">Format Parameters</span></span>

<span data-ttu-id="54771-103">下表列出用來格式化或產生資料之參數的建議名稱和功能。</span><span class="sxs-lookup"><span data-stu-id="54771-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="54771-104">參數</span><span class="sxs-lookup"><span data-stu-id="54771-104">Parameter</span></span>|<span data-ttu-id="54771-105">功能</span><span class="sxs-lookup"><span data-stu-id="54771-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="54771-106">**一旦**</span><span class="sxs-lookup"><span data-stu-id="54771-106">**As**</span></span><br><span data-ttu-id="54771-107">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="54771-107">Data type: Keyword</span></span>|<span data-ttu-id="54771-108">執行此參數以指定 Cmdlet 輸出格式。</span><span class="sxs-lookup"><span data-stu-id="54771-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="54771-109">例如，可能的值可以是文字或腳本。</span><span class="sxs-lookup"><span data-stu-id="54771-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="54771-110">**二進位**</span><span class="sxs-lookup"><span data-stu-id="54771-110">**Binary**</span></span><br><span data-ttu-id="54771-111">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="54771-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="54771-112">執行這個參數，以指出 Cmdlet 會處理二進位值。</span><span class="sxs-lookup"><span data-stu-id="54771-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="54771-113">**編碼**</span><span class="sxs-lookup"><span data-stu-id="54771-113">**Encoding**</span></span><br><span data-ttu-id="54771-114">資料類型：關鍵字</span><span class="sxs-lookup"><span data-stu-id="54771-114">Data type: Keyword</span></span>|<span data-ttu-id="54771-115">執行此參數來指定支援的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="54771-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="54771-116">例如，可能的值為 ASCII、UTF8、Unicode、UTF7、BigEndianUnicode、Byte 和 String。</span><span class="sxs-lookup"><span data-stu-id="54771-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="54771-117">**換**</span><span class="sxs-lookup"><span data-stu-id="54771-117">**NewLine**</span></span><br><span data-ttu-id="54771-118">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="54771-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="54771-119">執行此參數，以便在指定參數時支援分行符號。</span><span class="sxs-lookup"><span data-stu-id="54771-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="54771-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="54771-120">**ShortName**</span></span><br><span data-ttu-id="54771-121">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="54771-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="54771-122">請執行此參數，以便在指定參數時支援簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="54771-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="54771-123">**寬度**</span><span class="sxs-lookup"><span data-stu-id="54771-123">**Width**</span></span><br><span data-ttu-id="54771-124">資料類型： Int32</span><span class="sxs-lookup"><span data-stu-id="54771-124">Data type: Int32</span></span>|<span data-ttu-id="54771-125">執行此參數，讓使用者可以指定輸出裝置的寬度。</span><span class="sxs-lookup"><span data-stu-id="54771-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="54771-126">**包裝**</span><span class="sxs-lookup"><span data-stu-id="54771-126">**Wrap**</span></span><br><span data-ttu-id="54771-127">資料類型： SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="54771-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="54771-128">執行此參數，以便在指定參數時支援文字換行。</span><span class="sxs-lookup"><span data-stu-id="54771-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="54771-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54771-129">See Also</span></span>

[<span data-ttu-id="54771-130">Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="54771-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="54771-131">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="54771-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="54771-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="54771-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
