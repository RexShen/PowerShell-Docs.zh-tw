---
title: StopProcessSample04 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: 5a9e7a9ea13c9a62440b7cd80285751c901bcdd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862714"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="bb765-102">StopProcessSample04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="bb765-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="bb765-103">以下是完整的C#cmdlet StopProc04 範例的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="bb765-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="bb765-104">這是程式碼`Stop-Process`中所述的 cmdlet[新增至 Cmdlet 的參數集](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="bb765-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="bb765-105">`Stop-Process`指令程式設計來停止處理程序會擷取使用 Get-proc cmdlet (中所述[建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md))。</span><span class="sxs-lookup"><span data-stu-id="bb765-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="bb765-106">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此停止程序 cmdlet (stopprocesssample04.cs) 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="bb765-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bb765-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="bb765-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="bb765-108">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件此停止程序 cmdlet (stopprocesssample04.cs) 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="bb765-108">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bb765-109">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="bb765-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bb765-110">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="bb765-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="bb765-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb765-111">See Also</span></span>

[<span data-ttu-id="bb765-112">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="bb765-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bb765-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bb765-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)