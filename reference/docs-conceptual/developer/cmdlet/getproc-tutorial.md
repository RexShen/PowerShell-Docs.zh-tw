---
title: GetProc 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364437"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="b6c0c-102">GetProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="b6c0c-102">GetProc Tutorial</span></span>

<span data-ttu-id="b6c0c-103">本節提供的教學課程可讓您建立與 Windows PowerShell 所提供的「[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet 非常相似的「處理常式」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="b6c0c-104">本教學課程提供程式碼片段，說明如何實作為 Cmdlet，以及程式碼的說明。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="b6c0c-105">本教學課程中的主題</span><span class="sxs-lookup"><span data-stu-id="b6c0c-105">Topics in this Tutorial</span></span>

<span data-ttu-id="b6c0c-106">本教學課程中的主題設計為依序閱讀，每個主題都會根據上一個主題中所討論的內容來建立。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="b6c0c-107">[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)本節說明如何建立在不使用參數的情況下，從本機電腦抓取資訊的 Cmdlet，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="b6c0c-108">[新增可處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)本節說明如何將參數新增至 Get-help Cmdlet，讓 Cmdlet 可以根據傳遞至 Cmdlet 的明確物件來處理輸入。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="b6c0c-109">此處所述的執行會根據其名稱來抓取進程，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="b6c0c-110">[加入處理管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)本節說明如何將參數新增至 Get-help Cmdlet，讓 Cmdlet 可以處理透過管線傳遞給它的物件。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="b6c0c-111">這裡所述的執行 Cmdlet 會根據傳遞給 Cmdlet 的物件來抓取處理常式，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="b6c0c-112">[將非終止錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)本節說明如何將非終止錯誤報表新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="b6c0c-113">此處所述的執行會偵測處理輸入時所發生的非終止錯誤，並將錯誤記錄寫入錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="b6c0c-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6c0c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6c0c-114">See Also</span></span>

[<span data-ttu-id="b6c0c-115">建立不含參數的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6c0c-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="b6c0c-116">新增可處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="b6c0c-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="b6c0c-117">加入處理管線輸入的參數</span><span class="sxs-lookup"><span data-stu-id="b6c0c-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="b6c0c-118">將非終止錯誤報表新增至您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6c0c-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="b6c0c-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b6c0c-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
