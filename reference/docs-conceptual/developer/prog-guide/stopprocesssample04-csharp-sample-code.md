---
title: StopProcessSample04 （C#）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: df5591e351790d18bf2a5b5554d792ab8175dcc6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416053"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="2427f-102">StopProcessSample04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="2427f-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="2427f-103">以下是 StopProc04 範例C# Cmdlet 的完整範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="2427f-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="2427f-104">這是[將參數集新增至 Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述 `Stop-Process` Cmdlet 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2427f-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="2427f-105">`Stop-Process` Cmdlet 是設計用來停止使用 Get-Proc Cmdlet 抓取的進程（如[建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)所述）。</span><span class="sxs-lookup"><span data-stu-id="2427f-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="2427f-106">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個停止程式 Cmdlet 的（stopprocesssample04.cs）原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="2427f-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2427f-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="2427f-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="2427f-108">下載的來源檔案可在**\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="2427f-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="2427f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2427f-109">See Also</span></span>

[<span data-ttu-id="2427f-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="2427f-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2427f-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2427f-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
