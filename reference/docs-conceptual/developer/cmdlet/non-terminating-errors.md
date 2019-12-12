---
title: 非終止錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369597"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="ca653-102">非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="ca653-102">Non-Terminating Errors</span></span>

<span data-ttu-id="ca653-103">本主題討論用來報告非終止錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="ca653-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="ca653-104">它也會討論如何從 Cmdlet 內呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ca653-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="ca653-105">當發生非終止錯誤時，此 Cmdlet 應該會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca653-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="ca653-106">當 Cmdlet 回報非終止錯誤時，此 Cmdlet 可以繼續在此輸入物件以及進一步的傳入管線物件上操作。</span><span class="sxs-lookup"><span data-stu-id="ca653-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="ca653-107">如果指令程式呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，此 Cmdlet 可以撰寫錯誤記錄，以描述造成非終止錯誤的狀況。</span><span class="sxs-lookup"><span data-stu-id="ca653-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="ca653-108">如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="ca653-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="ca653-109">Cmdlet 可以視需要從其輸入處理方法中呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 。</span><span class="sxs-lookup"><span data-stu-id="ca653-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="ca653-110">不過，Cmdlet 只能從呼叫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)的執行緒，以 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 的身分，來進行指令程式的自管理元件的呼叫。 （或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ）輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="ca653-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="ca653-111">請不要從另一個執行緒呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 。</span><span class="sxs-lookup"><span data-stu-id="ca653-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="ca653-112">相反地，會將錯誤傳達回到主執行緒。</span><span class="sxs-lookup"><span data-stu-id="ca653-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca653-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca653-113">See Also</span></span>

[<span data-ttu-id="ca653-114">WriteError 的管理元件</span><span class="sxs-lookup"><span data-stu-id="ca653-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="ca653-115">BeginProcessing 的管理元件</span><span class="sxs-lookup"><span data-stu-id="ca653-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="ca653-116">ProcessRecord 的管理元件</span><span class="sxs-lookup"><span data-stu-id="ca653-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="ca653-117">System.servicemodel. Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ca653-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="ca653-118">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="ca653-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="ca653-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ca653-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
