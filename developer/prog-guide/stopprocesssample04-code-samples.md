---
title: StopProcessSample04 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc68af2b-f622-47c4-964f-b07f3d5bdf14
caps.latest.revision: 5
ms.openlocfilehash: fdb78ac93befba66041c4e45834f8a857e3670b6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862114"
---
# <a name="stopprocesssample04-code-samples"></a><span data-ttu-id="a8c12-102">StopProcessSample04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a8c12-102">StopProcessSample04 Code Samples</span></span>

<span data-ttu-id="a8c12-103">以下是 StopProc00 cmdlet 範例的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a8c12-103">Here are the code samples for the StopProc00 sample cmdlet.</span></span> <span data-ttu-id="a8c12-104">這是`Stop-Process`cmdlet 的範例中所述[新增至 Cmdlet 的參數集](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="a8c12-104">This is the `Stop-Process` cmdlet sample described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="a8c12-105">`Stop-Process`指令程式設計來停止處理程序會擷取使用 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="a8c12-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="a8c12-106">您可以下載C#(stopprocesssample04.cs) 和 VB.NET (stopprocesssample04.vb) 的 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件使用此停止程序 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8c12-106">You can download the C# (stopprocesssample04.cs) and VB.NET (stopprocesssample04.vb) for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a8c12-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a8c12-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="a8c12-108">您可以下載C#(stopprocesssample04.cs) 和 VB.NET (stopprocesssample04.vb) 的 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件使用此停止程序 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8c12-108">You can download the C# (stopprocesssample04.cs) and VB.NET (stopprocesssample04.vb) for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a8c12-109">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a8c12-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="a8c12-110">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="a8c12-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="a8c12-111">完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="a8c12-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="a8c12-112">語言</span><span class="sxs-lookup"><span data-stu-id="a8c12-112">Language</span></span>|<span data-ttu-id="a8c12-113">主題</span><span class="sxs-lookup"><span data-stu-id="a8c12-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="a8c12-114">C#</span><span class="sxs-lookup"><span data-stu-id="a8c12-114">C#</span></span>|[<span data-ttu-id="a8c12-115">StopProc04 (C#) Sample Code</span><span class="sxs-lookup"><span data-stu-id="a8c12-115">StopProc04 (C#) Sample Code</span></span>](./stopprocesssample04-csharp-sample-code.md)|
|<span data-ttu-id="a8c12-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="a8c12-116">VB.NET</span></span>|[<span data-ttu-id="a8c12-117">StopProc04 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="a8c12-117">StopProc04 (VB.NET) Sample Code</span></span>](./stopprocesssample04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="a8c12-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8c12-118">See Also</span></span>

[<span data-ttu-id="a8c12-119">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="a8c12-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a8c12-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a8c12-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)