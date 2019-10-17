---
title: 撰寫 Cmdlet 的教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0b548aa-febf-45dd-bf71-2077730b9b73
caps.latest.revision: 6
ms.openlocfilehash: 767b392bd1603e83d80bad5b3fd9cb42ff142ce6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369317"
---
# <a name="tutorials-for-writing-cmdlets"></a><span data-ttu-id="f11ef-102">Cmdlet 撰寫教學課程</span><span class="sxs-lookup"><span data-stu-id="f11ef-102">Tutorials for Writing Cmdlets</span></span>

<span data-ttu-id="f11ef-103">本節包含撰寫 Cmdlet 的教學課程。</span><span class="sxs-lookup"><span data-stu-id="f11ef-103">This section contains tutorials for writing cmdlets.</span></span> <span data-ttu-id="f11ef-104">這些教學課程包含撰寫指令程式所需的程式碼，並說明為何需要程式碼。</span><span class="sxs-lookup"><span data-stu-id="f11ef-104">These tutorials include the code needed to write the cmdlets, plus an explanation of why the code is needed.</span></span> <span data-ttu-id="f11ef-105">這些主題對於剛開始撰寫 Cmdlet 的人來說非常有説明。</span><span class="sxs-lookup"><span data-stu-id="f11ef-105">These topics will be very helpful for those who are just starting to write cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f11ef-106">如需具有較少描述之程式碼範例的使用者，請參閱[Cmdlet 範例](./cmdlet-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f11ef-106">For those who want code examples with less description, see [Cmdlet Samples](./cmdlet-samples.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f11ef-107">在本節中</span><span class="sxs-lookup"><span data-stu-id="f11ef-107">In This Section</span></span>

<span data-ttu-id="f11ef-108">[GetProc 教學](./getproc-tutorial.md)課程-本教學課程說明如何定義 Cmdlet 類別並新增基本功能，例如新增參數和報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="f11ef-108">[GetProc Tutorial](./getproc-tutorial.md) - This tutorial describes how to define a cmdlet class and add basic functionality such as adding parameters and reporting errors.</span></span> <span data-ttu-id="f11ef-109">本教學課程中所述的 Cmdlet 非常類似于 Windows PowerShell 所提供的「[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f11ef-109">The cmdlet described in this tutorial is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="f11ef-110">[StopProc 教學](./stopproc-tutorial.md)課程-本教學課程說明如何定義 Cmdlet 並新增功能，例如使用者提示、萬用字元支援，以及使用參數集。</span><span class="sxs-lookup"><span data-stu-id="f11ef-110">[StopProc Tutorial](./stopproc-tutorial.md) - This tutorial describes how to define a cmdlet and add functionality such as user prompts, wildcard support, and the use of parameter sets.</span></span> <span data-ttu-id="f11ef-111">這裡所述的 Cmdlet 會執行與 Windows PowerShell 所提供的[停止進程](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="f11ef-111">The cmdlet described here performs the same task as the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span>

<span data-ttu-id="f11ef-112">[SelectStr 教學](./selectstr-tutorial.md)課程-本教學課程說明如何定義可存取資料存放區的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f11ef-112">[SelectStr Tutorial](./selectstr-tutorial.md) - This tutorial describes how to define a cmdlet that accesses a data store.</span></span> <span data-ttu-id="f11ef-113">這裡所述的 Cmdlet 會執行與 Windows PowerShell 所提供的[Select 字串](/powershell/module/microsoft.powershell.utility/select-string)Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="f11ef-113">The cmdlet described here performs the same task as the [Select-String](/powershell/module/microsoft.powershell.utility/select-string) cmdlet provided by Windows PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="f11ef-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11ef-114">See Also</span></span>

[<span data-ttu-id="f11ef-115">GetProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="f11ef-115">GetProc Tutorial</span></span>](./getproc-tutorial.md)

[<span data-ttu-id="f11ef-116">StopProc 教學課程</span><span class="sxs-lookup"><span data-stu-id="f11ef-116">StopProc Tutorial</span></span>](./stopproc-tutorial.md)

[<span data-ttu-id="f11ef-117">SelectStr 教學課程</span><span class="sxs-lookup"><span data-stu-id="f11ef-117">SelectStr Tutorial</span></span>](./selectstr-tutorial.md)

[<span data-ttu-id="f11ef-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f11ef-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)