---
title: 錯誤報表概念 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.openlocfilehash: ff010bbe1a87daa351ec13ed249ffc899781a8c3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774502"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="e2e5d-102">錯誤報告概念</span><span class="sxs-lookup"><span data-stu-id="e2e5d-102">Error Reporting Concepts</span></span>

<span data-ttu-id="e2e5d-103">Windows PowerShell 提供兩種報告錯誤的機制：一個用於*終止錯誤*的機制，以及另一個*非終止錯誤*的機制。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="e2e5d-104">您的 Cmdlet 必須正確地報告錯誤，讓執行 Cmdlet 的主應用程式能夠以適當的方式回應。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="e2e5d-105">當不是或不應允許 Cmdlet 繼續處理其輸入物件的錯誤發生時，您的 Cmdlet 應該會呼叫[Throwterminatingerror \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="e2e5d-106">當 Cmdlet 可以繼續處理輸入物件時，您的 Cmdlet 應該會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告非終止的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="e2e5d-107">這兩種方法都會提供錯誤記錄，讓主應用程式用來調查錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="e2e5d-108">使用下列指導方針，判斷錯誤是否為終止或非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="e2e5d-109">錯誤是終止錯誤，如果它會防止您的 Cmdlet 繼續處理目前的物件，或不能成功處理任何進一步的輸入物件（不論其內容為何）。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="e2e5d-110">如果您不想讓 Cmdlet 繼續處理目前的物件或任何進一步的輸入物件（不論其內容為何），錯誤就是終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="e2e5d-111">如果錯誤發生在不接受或傳回物件的 Cmdlet 中，或如果它發生在接受或只傳回一個物件的 Cmdlet 中，就會有一個終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="e2e5d-112">如果您想要讓 Cmdlet 繼續處理目前的物件和任何進一步的輸入物件，則會發生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="e2e5d-113">如果錯誤與特定的輸入物件或輸入物件的子集相關，則會發生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2e5d-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2e5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2e5d-114">See Also</span></span>

[<span data-ttu-id="e2e5d-115">Throwterminatingerror \* 的 \*</span><span class="sxs-lookup"><span data-stu-id="e2e5d-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="e2e5d-116">WriteError 的管理元件</span><span class="sxs-lookup"><span data-stu-id="e2e5d-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="e2e5d-117">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="e2e5d-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="e2e5d-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e2e5d-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
