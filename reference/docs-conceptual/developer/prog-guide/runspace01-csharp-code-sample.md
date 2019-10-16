---
title: Runspace01 （C#）程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 39e7d49b51942da51a581ab33dbe46ab848ca1c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366637"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="9a5bc-102">Runspace01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9a5bc-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="9a5bc-103">以下是[建立主控台應用程式（可執行指定的命令](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)）中所述之運行空間的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="9a5bc-104">若要這樣做，應用程式會叫用運行空間，然後叫用命令。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="9a5bc-105">（請注意，此應用程式不會指定執行空間設定資訊，也不會明確建立管線）。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="9a5bc-106">所叫用的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="9a5bc-107">您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此執行時間的原始程式檔（runspace01.cs）。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9a5bc-108">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9a5bc-109">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="9a5bc-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9a5bc-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9a5bc-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="9a5bc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a5bc-111">See Also</span></span>

[<span data-ttu-id="9a5bc-112">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="9a5bc-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9a5bc-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9a5bc-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
