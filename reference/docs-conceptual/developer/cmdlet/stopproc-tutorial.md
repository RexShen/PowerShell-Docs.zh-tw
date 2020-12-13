---
ms.date: 09/13/2016
ms.topic: reference
title: StopProc 教學課程
description: StopProc 教學課程
ms.openlocfilehash: 95229ee3c4905d295bd6991fe8ccf8c9840c3cdd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646441"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="ebf8b-103">StopProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="ebf8b-103">StopProc Tutorial</span></span>

<span data-ttu-id="ebf8b-104">本節提供建立 Stop-Proc Cmdlet 的教學課程，此教學課程非常類似 Windows PowerShell 所提供的 [停止進程](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-104">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="ebf8b-105">本教學課程提供的程式碼片段可說明如何實作為 Cmdlet 的程式碼，以及程式碼的說明。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="ebf8b-106">本教學課程中的主題</span><span class="sxs-lookup"><span data-stu-id="ebf8b-106">Topics in this Tutorial</span></span>

<span data-ttu-id="ebf8b-107">本教學課程中的主題是設計成依序讀取，每個主題都是以上一個主題中討論的內容為基礎。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="ebf8b-108">[建立修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md) 本節說明如何建立支援系統修改的 Cmdlet，例如停止在電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-108">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="ebf8b-109">[將使用者訊息新增至您的 Cmdlet](./adding-user-messages-to-your-cmdlet.md) 本節說明如何將寫入使用者訊息、偵錯工具訊息、警告訊息和進度資訊的功能新增至您的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-109">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="ebf8b-110">[將別名、萬用字元擴充和說明新增至 Cmdlet 參數](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) 本節說明如何建立支援參數別名、說明和萬用字元擴充的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-110">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="ebf8b-111">[將參數集合新增至 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md) 本節說明如何將參數集合新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-111">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="ebf8b-112">參數集可讓 Cmdlet 根據使用者指定的參數，以不同的方式運作。</span><span class="sxs-lookup"><span data-stu-id="ebf8b-112">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebf8b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf8b-113">See Also</span></span>

[<span data-ttu-id="ebf8b-114">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ebf8b-114">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="ebf8b-115">新增使用者訊息到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ebf8b-115">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="ebf8b-116">新增別名、萬用字元擴充與說明到 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="ebf8b-116">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="ebf8b-117">將參數集合新增至 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ebf8b-117">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="ebf8b-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ebf8b-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
