---
title: 錯誤報告概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855074"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="6b605-102">錯誤報告概念</span><span class="sxs-lookup"><span data-stu-id="6b605-102">Error Reporting Concepts</span></span>

<span data-ttu-id="6b605-103">Windows PowerShell 提供兩種機制來報告錯誤： 機制之一*終止錯誤*和另一個機制來*非終止錯誤*。</span><span class="sxs-lookup"><span data-stu-id="6b605-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="6b605-104">務必針對您的 cmdlet，來報告錯誤正確，讓主應用程式執行您的 cmdlet 可因應以適當方式。</span><span class="sxs-lookup"><span data-stu-id="6b605-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="6b605-105">您的指令程式應該呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法發生錯誤時則否，或不應該允許 cmdlet 以繼續處理其輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="6b605-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="6b605-106">您的指令程式應該呼叫[System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)指令程式可以繼續處理輸入的物件時，報告非終止錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="6b605-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="6b605-107">這兩種方法提供主應用程式可用來調查的錯誤原因的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="6b605-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="6b605-108">您可以使用下列指導方針來判斷錯誤是否為終止或非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b605-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="6b605-109">錯誤會終止錯誤，如果它會防止您的 cmdlet，從繼續處理目前的物件或已成功處理任何進一步的輸入的物件，不論其內容。</span><span class="sxs-lookup"><span data-stu-id="6b605-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="6b605-110">如果不想您的 cmdlet 以繼續處理目前的物件或任何進一步的輸入的物件，不論其內容，錯誤會終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b605-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="6b605-111">錯誤發生的 cmdlet 中，不會接受或傳回物件，或是接受或傳回只有一個物件的 cmdlet 中發生，是終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b605-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="6b605-112">如果您想要繼續處理目前的物件和任何進一步的輸入物件的 cmdlet，錯誤會是一個非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b605-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="6b605-113">如果它與相關的特定輸入的物件或輸入物件的子集，錯誤會是一個非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="6b605-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b605-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b605-114">See Also</span></span>

[<span data-ttu-id="6b605-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="6b605-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="6b605-116">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="6b605-116">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="6b605-117">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="6b605-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="6b605-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b605-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
