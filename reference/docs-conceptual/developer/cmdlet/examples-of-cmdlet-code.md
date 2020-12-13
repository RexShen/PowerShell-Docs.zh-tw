---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 程式碼範例
description: Cmdlet 程式碼範例
ms.openlocfilehash: 91dd2019300504697ad9a7a0c155a04600d09c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652926"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="c0eb9-103">Cmdlet 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c0eb9-103">Examples of Cmdlet Code</span></span>

<span data-ttu-id="c0eb9-104">本章節包含 Cmdlet 程式碼的範例，您可以用來開始撰寫自己的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-104">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0eb9-105">如果您想要撰寫 Cmdlet 的逐步指示，請參閱 [撰寫 Cmdlet 的教學](./tutorials-for-writing-cmdlets.md)課程。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-105">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c0eb9-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c0eb9-106">In This Section</span></span>

<span data-ttu-id="c0eb9-107">[如何撰寫簡單的 Cmdlet](./how-to-write-a-simple-cmdlet.md) 此範例顯示 Cmdlet 程式碼的基本結構。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-107">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="c0eb9-108">[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md) 此範例顯示如何宣告不同類型的參數。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-108">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="c0eb9-109">[如何宣告參數集](./how-to-declare-parameter-sets.md) 此範例示範如何宣告可變更 Cmdlet 所執行之動作的參數集。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-109">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="c0eb9-110">[如何驗證參數輸入](./how-to-validate-parameter-input.md) 這些範例會示範如何驗證參數輸入。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-110">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="c0eb9-111">[如何宣告動態參數](./how-to-declare-dynamic-parameters.md) 這個範例示範如何宣告在執行時間加入的參數。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-111">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="c0eb9-112">[如何在 Cmdlet 中叫用腳本](./how-to-invoke-scripts-within-a-cmdlet.md) 此範例說明如何叫用提供給 Cmdlet 的腳本。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-112">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="c0eb9-113">[如何覆寫輸入處理方法](./how-to-override-input-processing-methods.md) 這些範例顯示用來覆寫 BeginProcessing、ProcessRecord 和 EndProcessing 方法的基本結構。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-113">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="c0eb9-114">[如何支援 ShouldProcess 呼叫](./how-to-request-confirmations.md)這個範例會示範如何從 Cmdlet 內呼叫 ShouldProcess 和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的方法。（可能為[system.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)管理方法）。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-114">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="c0eb9-115">[如何支援交易](./how-to-support-transactions.md) 此範例示範如何指示 Cmdlet 支援交易，以及如何執行在交易中使用 Cmdlet 時所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-115">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="c0eb9-116">[如何支援作業](./how-to-support-jobs.md) 此範例示範如何在撰寫 Cmdlet 時支援工作。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-116">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="c0eb9-117">[如何從 Cmdlet 內叫用 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) 此範例示範如何從另一個 Cmdlet 中叫用 Cmdlet，此 Cmdlet 可讓您將叫用 Cmdlet 的功能新增到您正在開發的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0eb9-117">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0eb9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0eb9-118">See Also</span></span>

[<span data-ttu-id="c0eb9-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0eb9-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
