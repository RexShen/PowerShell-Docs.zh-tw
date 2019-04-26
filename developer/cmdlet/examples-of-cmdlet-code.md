---
title: Cmdlet 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068193"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="620dc-102">Cmdlet 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="620dc-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="620dc-103">本節包含 cmdlet 程式碼可供您開始撰寫自己的 cmdlet 的範例。</span><span class="sxs-lookup"><span data-stu-id="620dc-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="620dc-104">如果您想撰寫 cmdlet 的逐步指示，請參閱[撰寫的 cmdlet 的教學課程](./tutorials-for-writing-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="620dc-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="620dc-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="620dc-105">In This Section</span></span>

<span data-ttu-id="620dc-106">[如何撰寫一個簡單的 Cmdlet](./how-to-write-a-simple-cmdlet.md)此範例會顯示 cmdlet 的程式碼的基本結構。</span><span class="sxs-lookup"><span data-stu-id="620dc-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="620dc-107">[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)本範例示範如何宣告不同類型的參數。</span><span class="sxs-lookup"><span data-stu-id="620dc-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="620dc-108">[如何宣告參數集](./how-to-declare-parameter-sets.md)本範例示範如何宣告的參數，可以變更在 cmdlet 執行的動作集。</span><span class="sxs-lookup"><span data-stu-id="620dc-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="620dc-109">[如何驗證參數輸入](./how-to-validate-parameter-input.md)這些範例示範如何驗證參數的輸入。</span><span class="sxs-lookup"><span data-stu-id="620dc-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="620dc-110">[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)這個範例示範如何宣告的參數，在執行階段加入。</span><span class="sxs-lookup"><span data-stu-id="620dc-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="620dc-111">[如何叫用指令碼內 Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)本範例示範如何叫用的指令碼，提供給 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="620dc-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="620dc-112">[如何覆寫輸入處理方法](./how-to-override-input-processing-methods.md)這些範例示範用來覆寫 BeginProcessing、 ProcessRecord 和 EndProcessing 方法的基本結構。</span><span class="sxs-lookup"><span data-stu-id="620dc-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="620dc-113">[如何支援 ShouldProcess 呼叫](./how-to-request-confirmations.md)這個範例示範如何[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法應從呼叫中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="620dc-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="620dc-114">[如何支援交易](./how-to-support-transactions.md)這個範例示範如何指出此 cmdlet 支援交易，以及如何實作指令程式用在交易內時所要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="620dc-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="620dc-115">[如何支援工作](./how-to-support-jobs.md)這個範例示範如何撰寫 cmdlet 時支援作業。</span><span class="sxs-lookup"><span data-stu-id="620dc-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="620dc-116">[如何叫用 Cmdlet 從內 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)本範例示範如何叫用另一個 cmdlet，可讓您叫用的指令程式的功能新增至您正在開發的 cmdlet 中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="620dc-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="620dc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="620dc-117">See Also</span></span>

[<span data-ttu-id="620dc-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="620dc-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
