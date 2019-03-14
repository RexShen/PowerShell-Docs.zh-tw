---
title: StopProc 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794394"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="dc3b7-102">StopProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="dc3b7-102">StopProc Tutorial</span></span>

<span data-ttu-id="dc3b7-103">本節提供建立非常類似的停止程序指令程式的教學課程[Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) Windows PowerShell 所提供的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="dc3b7-104">本教學課程提供的說明 cmdlet 實作的方式的程式碼片段和程式碼的說明。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="dc3b7-105">在本教學課程的主題</span><span class="sxs-lookup"><span data-stu-id="dc3b7-105">Topics in this Tutorial</span></span>

<span data-ttu-id="dc3b7-106">在本教學課程主題被設計來建置在上一個主題中討論的內容上的每個主題來循序讀取。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="dc3b7-107">[建立 Cmdlet 會修改系統](./creating-a-cmdlet-that-modifies-the-system.md)本章節描述如何建立支援修改系統，例如停止處理程序在電腦上執行的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="dc3b7-108">[將使用者訊息新增至您的 Cmdlet](./adding-user-messages-to-your-cmdlet.md)本章節描述如何加入可將使用者訊息、 偵錯訊息，警告訊息，以及進度資訊寫入您的 cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="dc3b7-109">[新增萬用字元展開的別名和 Cmdlet 參數有助於](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)本章節描述如何建立 cmdlet 支援參數別名、 說明與萬用字元展開。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="dc3b7-110">[新增至 Cmdlet 的參數會設定](./adding-parameter-sets-to-a-cmdlet.md)本章節描述如何新增到 cmdlet 的參數集合。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="dc3b7-111">參數集可讓操作 cmdlet 根據使用者所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="dc3b7-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc3b7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3b7-112">See Also</span></span>

[<span data-ttu-id="dc3b7-113">建立 Cmdlet 會修改系統</span><span class="sxs-lookup"><span data-stu-id="dc3b7-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="dc3b7-114">將使用者訊息新增至您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dc3b7-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="dc3b7-115">新增萬用字元展開的別名，並協助 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="dc3b7-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="dc3b7-116">將參數集加入至指令程式</span><span class="sxs-lookup"><span data-stu-id="dc3b7-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="dc3b7-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dc3b7-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
