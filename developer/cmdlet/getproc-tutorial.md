---
title: GetProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862454"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="cb954-102">GetProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="cb954-102">GetProc Tutorial</span></span>

<span data-ttu-id="cb954-103">本節提供的教學課程，建立 Get-proc cmdlet 是非常類似[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Windows PowerShell 所提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cb954-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="cb954-104">本教學課程提供的說明 cmdlet 實作的方式的程式碼片段和程式碼的說明。</span><span class="sxs-lookup"><span data-stu-id="cb954-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="cb954-105">在本教學課程的主題</span><span class="sxs-lookup"><span data-stu-id="cb954-105">Topics in this Tutorial</span></span>

<span data-ttu-id="cb954-106">在本教學課程主題被設計來建置在上一個主題中討論的內容上的每個主題來循序讀取。</span><span class="sxs-lookup"><span data-stu-id="cb954-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="cb954-107">[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)本章節描述如何建立 cmdlet 會從本機電腦，而不使用參數，擷取資訊，然後將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="cb954-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="cb954-108">[加入參數，該程序命令列輸入](./adding-parameters-that-process-command-line-input.md)本章節描述如何將參數新增至 Get-proc cmdlet，讓此指令程式可以處理明確傳遞至 cmdlet 的物件為基礎的輸入。</span><span class="sxs-lookup"><span data-stu-id="cb954-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="cb954-109">所述的實作這裡擷取其名稱為基礎的處理程序，並再將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="cb954-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="cb954-110">[加入參數，該程序管線輸入](./adding-parameters-that-process-pipeline-input.md)本章節描述如何將參數新增至 Get-proc cmdlet，讓此指令程式可以處理透過管線傳遞給它的物件。</span><span class="sxs-lookup"><span data-stu-id="cb954-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="cb954-111">描述實作 cmdlet 這裡擷取物件傳遞至 cmdlet，為基礎的處理序，並再將資訊寫入管線。</span><span class="sxs-lookup"><span data-stu-id="cb954-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="cb954-112">[將非終止錯誤報告加入至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)本章節描述如何新增非終止錯誤回報給 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cb954-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="cb954-113">此處所述的實作會偵測到非終止錯誤發生時處理輸入，並將錯誤記錄寫入至資料流時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb954-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb954-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb954-114">See Also</span></span>

[<span data-ttu-id="cb954-115">建立不含參數的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cb954-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="cb954-116">加入處理命令列輸入的參數</span><span class="sxs-lookup"><span data-stu-id="cb954-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="cb954-117">新增處理程序管線輸入的參數</span><span class="sxs-lookup"><span data-stu-id="cb954-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="cb954-118">加入非終止錯誤回報給您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cb954-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="cb954-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cb954-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
