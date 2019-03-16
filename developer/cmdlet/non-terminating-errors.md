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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054352"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="a3aff-102">非終止錯誤</span><span class="sxs-lookup"><span data-stu-id="a3aff-102">Non-Terminating Errors</span></span>

<span data-ttu-id="a3aff-103">本主題討論用來報告非終止錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="a3aff-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="a3aff-104">它也會討論如何從呼叫方法的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a3aff-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="a3aff-105">此 cmdlet 發生非終止錯誤時，應該藉由呼叫報告此錯誤[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="a3aff-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="a3aff-106">當此 cmdlet 會報告一個非終止錯誤時，此指令程式可以繼續運作和進一步的連入此輸入物件上的管線物件。</span><span class="sxs-lookup"><span data-stu-id="a3aff-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="a3aff-107">如果此 cmdlet 會呼叫[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，則此 cmdlet 可以寫入記錄時發生錯誤，描述造成非終止錯誤的條件。</span><span class="sxs-lookup"><span data-stu-id="a3aff-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="a3aff-108">如需詳細的錯誤記錄的詳細資訊，請參閱[Windows PowerShell 的錯誤記錄](./windows-powershell-error-records.md)。</span><span class="sxs-lookup"><span data-stu-id="a3aff-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="a3aff-109">指令程式可以呼叫[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)視需要在其輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="a3aff-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="a3aff-110">不過，可以呼叫 cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)只能從呼叫的執行緒[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)輸入處理方法。</span><span class="sxs-lookup"><span data-stu-id="a3aff-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="a3aff-111">請勿呼叫[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)從另一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="a3aff-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="a3aff-112">相反地，傳送回到主執行緒所發生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a3aff-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3aff-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3aff-113">See Also</span></span>

[<span data-ttu-id="a3aff-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="a3aff-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="a3aff-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="a3aff-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="a3aff-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="a3aff-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="a3aff-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="a3aff-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="a3aff-118">Windows PowerShell 錯誤記錄</span><span class="sxs-lookup"><span data-stu-id="a3aff-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="a3aff-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3aff-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
