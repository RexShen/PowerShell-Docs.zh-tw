---
title: Windows PowerShell 錯誤報表 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7f7afcf5186732734976304c8e58e4d940156e1e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783954"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="bce92-102">Windows PowerShell 錯誤報告</span><span class="sxs-lookup"><span data-stu-id="bce92-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="bce92-103">本節中的主題將討論 Cmdlet 如何報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="bce92-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bce92-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="bce92-104">In This Section</span></span>

<span data-ttu-id="bce92-105">[錯誤報表概念](./error-reporting-concepts.md)說明 Cmdlet 可以用來報告錯誤的兩個機制。</span><span class="sxs-lookup"><span data-stu-id="bce92-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="bce92-106">[終止錯誤](./terminating-errors.md)描述用來報告終止錯誤的方法，其中可以從 Cmdlet 內呼叫該方法，以及呼叫方法時，Windows PowerShell 執行時間可以傳回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bce92-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="bce92-107">[非終止錯誤](./non-terminating-errors.md)描述用來報告非終止錯誤的方法，以及可以從 Cmdlet 內呼叫該方法的位置。</span><span class="sxs-lookup"><span data-stu-id="bce92-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="bce92-108">[依類別顯示錯誤資訊](./displaying-error-information.md)討論使用者可以顯示錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="bce92-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="bce92-109">[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)描述錯誤記錄的元件。</span><span class="sxs-lookup"><span data-stu-id="bce92-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="bce92-110">[解讀 ErrorRecord 物件](./interpreting-errorrecord-objects.md)討論如何解讀 ErrorRecord 物件。</span><span class="sxs-lookup"><span data-stu-id="bce92-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="bce92-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bce92-111">See Also</span></span>

[<span data-ttu-id="bce92-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bce92-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
