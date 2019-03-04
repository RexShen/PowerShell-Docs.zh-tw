---
title: Windows PowerShell 的錯誤報告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856154"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="499d9-102">Windows PowerShell 錯誤報告</span><span class="sxs-lookup"><span data-stu-id="499d9-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="499d9-103">在本節中的主題將討論如何 cmdlet 會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="499d9-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="499d9-104">在本節中</span><span class="sxs-lookup"><span data-stu-id="499d9-104">In This Section</span></span>

<span data-ttu-id="499d9-105">[錯誤報告概念](./error-reporting-concepts.md)說明 cmdlet 可用來報告錯誤的兩個機制。</span><span class="sxs-lookup"><span data-stu-id="499d9-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="499d9-106">[終止錯誤](./terminating-errors.md)說明用來報告終止的錯誤，其中該方法可以從內呼叫此指令程式，以及可以在呼叫方法時，Windows PowerShell 執行階段所傳回的例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="499d9-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="499d9-107">[非終止錯誤](./non-terminating-errors.md)說明用來報告非終止錯誤，其中該方法可以從內呼叫此指令程式的方法。</span><span class="sxs-lookup"><span data-stu-id="499d9-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="499d9-108">[依類別顯示錯誤資訊](./displaying-error-information.md)討論使用者可以顯示錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="499d9-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="499d9-109">[Windows PowerShell 的錯誤記錄](./windows-powershell-error-records.md)描述錯誤記錄的元件。</span><span class="sxs-lookup"><span data-stu-id="499d9-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="499d9-110">[解譯 ErrorRecord 物件](./interpreting-errorrecord-objects.md)討論 ErrorRecord 物件的解譯方式。</span><span class="sxs-lookup"><span data-stu-id="499d9-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="499d9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="499d9-111">See Also</span></span>

[<span data-ttu-id="499d9-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="499d9-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
