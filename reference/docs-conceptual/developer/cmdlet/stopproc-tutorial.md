---
title: StopProc 教學課程 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e298c729b7ac59141638052d19b95ab77aa25cd6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786470"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="998c0-102">StopProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="998c0-102">StopProc Tutorial</span></span>

<span data-ttu-id="998c0-103">本節提供建立停止程式 Cmdlet 的教學課程，這與 Windows PowerShell 所提供的[停止進程](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)Cmdlet 非常類似。</span><span class="sxs-lookup"><span data-stu-id="998c0-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="998c0-104">本教學課程提供程式碼片段，說明如何實作為 Cmdlet，以及程式碼的說明。</span><span class="sxs-lookup"><span data-stu-id="998c0-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="998c0-105">本教學課程中的主題</span><span class="sxs-lookup"><span data-stu-id="998c0-105">Topics in this Tutorial</span></span>

<span data-ttu-id="998c0-106">本教學課程中的主題設計為依序閱讀，每個主題都會根據上一個主題中所討論的內容來建立。</span><span class="sxs-lookup"><span data-stu-id="998c0-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="998c0-107">[建立可修改系統的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)本節說明如何建立支援系統修改的 Cmdlet，例如停止電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="998c0-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="998c0-108">[將使用者訊息新增至您的 Cmdlet](./adding-user-messages-to-your-cmdlet.md)本節說明如何將寫入使用者訊息、偵錯工具訊息、警告訊息和進度資訊的功能新增至您的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="998c0-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="998c0-109">[將別名、萬用字元擴充和說明新增至 Cmdlet 參數](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)本節說明如何建立支援參數別名、說明和萬用字元擴充的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="998c0-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="998c0-110">[將參數集新增至 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)本節說明如何將參數集新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="998c0-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="998c0-111">參數集可讓 Cmdlet 根據使用者所指定的參數，以不同的方式運作。</span><span class="sxs-lookup"><span data-stu-id="998c0-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="998c0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="998c0-112">See Also</span></span>

[<span data-ttu-id="998c0-113">建立可修改系統的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="998c0-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="998c0-114">新增使用者訊息到您的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="998c0-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="998c0-115">新增別名、萬用字元擴充與說明到 Cmdlet 參數</span><span class="sxs-lookup"><span data-stu-id="998c0-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="998c0-116">將參數集新增至 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="998c0-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="998c0-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="998c0-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
