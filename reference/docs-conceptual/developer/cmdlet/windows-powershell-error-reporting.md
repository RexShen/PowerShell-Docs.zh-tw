---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 錯誤報告
description: Windows PowerShell 錯誤報告
ms.openlocfilehash: 438e3d96bf52d8ac1f770c0550ae49b356d616eb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650115"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="6da81-103">Windows PowerShell 錯誤報告</span><span class="sxs-lookup"><span data-stu-id="6da81-103">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="6da81-104">本節中的主題將討論 Cmdlet 報告錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="6da81-104">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6da81-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="6da81-105">In This Section</span></span>

<span data-ttu-id="6da81-106">[錯誤報表概念](./error-reporting-concepts.md) 描述 Cmdlet 可用來報告錯誤的兩種機制。</span><span class="sxs-lookup"><span data-stu-id="6da81-106">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="6da81-107">[終止錯誤](./terminating-errors.md) 描述用來報告終止錯誤的方法，也就是可以從 Cmdlet 內呼叫該方法，以及在呼叫方法時，可由 Windows PowerShell 執行時間傳回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6da81-107">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="6da81-108">[非終止錯誤](./non-terminating-errors.md) 描述用來報告非終止錯誤的方法，以及可以從 Cmdlet 內呼叫該方法的位置。</span><span class="sxs-lookup"><span data-stu-id="6da81-108">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="6da81-109">[依類別顯示錯誤資訊](./displaying-error-information.md) 討論使用者可以顯示錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="6da81-109">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="6da81-110">[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md) 描述錯誤記錄的元件。</span><span class="sxs-lookup"><span data-stu-id="6da81-110">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="6da81-111">[解讀 ErrorRecord 物件](./interpreting-errorrecord-objects.md) 討論如何解讀 ErrorRecord 物件。</span><span class="sxs-lookup"><span data-stu-id="6da81-111">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="6da81-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6da81-112">See Also</span></span>

[<span data-ttu-id="6da81-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6da81-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
