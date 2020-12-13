---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc 教學課程
description: GetProc 教學課程
ms.openlocfilehash: 9379e791dd5361fcf5b79061bf0a601ebeb84f42
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652775"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="615ca-103">GetProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="615ca-103">GetProc Tutorial</span></span>

<span data-ttu-id="615ca-104">本節提供的教學課程可讓您建立與 Windows PowerShell 所提供之 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 非常類似的 Get-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="615ca-104">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="615ca-105">本教學課程提供的程式碼片段可說明如何實作為 Cmdlet 的程式碼，以及程式碼的說明。</span><span class="sxs-lookup"><span data-stu-id="615ca-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="615ca-106">本教學課程中的主題</span><span class="sxs-lookup"><span data-stu-id="615ca-106">Topics in this Tutorial</span></span>

<span data-ttu-id="615ca-107">本教學課程中的主題是設計成依序讀取，每個主題都是以上一個主題中討論的內容為基礎。</span><span class="sxs-lookup"><span data-stu-id="615ca-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="615ca-108">[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md) 本節說明如何建立 Cmdlet，以在不使用參數的情況下，從本機電腦抓取資訊，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="615ca-108">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="615ca-109">[加入處理 Command-Line 輸入的參數](./adding-parameters-that-process-command-line-input.md) 本節說明如何將參數新增至 Get-Proc Cmdlet，讓 Cmdlet 可以根據傳遞給 Cmdlet 的明確物件來處理輸入。</span><span class="sxs-lookup"><span data-stu-id="615ca-109">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="615ca-110">此處所述的執行會根據其名稱來抓取進程，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="615ca-110">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="615ca-111">[加入處理管線輸入的參數](./adding-parameters-that-process-pipeline-input.md) 本節說明如何將參數新增至 Get-Proc Cmdlet，讓 Cmdlet 可以處理透過管線傳遞給它的物件。</span><span class="sxs-lookup"><span data-stu-id="615ca-111">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="615ca-112">此處所述的執行 Cmdlet 會根據傳遞給 Cmdlet 的物件來抓取進程，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="615ca-112">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="615ca-113">[將非終止錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) 本節說明如何將非終止錯誤報表新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="615ca-113">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="615ca-114">此處所述的執行會偵測處理輸入時所發生的非終止錯誤，並將錯誤記錄寫入至錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="615ca-114">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="615ca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="615ca-115">See Also</span></span>

[<span data-ttu-id="615ca-116">建立不含參數的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="615ca-116">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="615ca-117">加入處理 Command-Line 輸入的參數</span><span class="sxs-lookup"><span data-stu-id="615ca-117">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="615ca-118">新增處理管道輸入的參數</span><span class="sxs-lookup"><span data-stu-id="615ca-118">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="615ca-119">將非終止錯誤報表新增至您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="615ca-119">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="615ca-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="615ca-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
