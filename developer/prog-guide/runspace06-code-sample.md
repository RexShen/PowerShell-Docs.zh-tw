---
title: RunSpace06 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734925"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="f8ca8-102">RunSpace06 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f8ca8-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="f8ca8-103">以下是原始程式碼，Runspace06 範例中所述[設定使用 Windows PowerShell 嵌入式管理單元的 Runspace](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)。</span><span class="sxs-lookup"><span data-stu-id="f8ca8-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="f8ca8-104">此範例應用程式會建立 runspace，根據 Windows PowerShell 嵌入式管理單元，然後用來執行管線，使用單一命令。</span><span class="sxs-lookup"><span data-stu-id="f8ca8-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="f8ca8-105">若要這樣做，應用程式會建立 runspace 的組態資訊、 建立 runspace，使用單一命令，會建立管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="f8ca8-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="f8ca8-106">您可以下載C#使用的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (runspace06.cs)。</span><span class="sxs-lookup"><span data-stu-id="f8ca8-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f8ca8-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="f8ca8-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f8ca8-108">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="f8ca8-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f8ca8-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f8ca8-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="f8ca8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8ca8-110">See Also</span></span>

[<span data-ttu-id="f8ca8-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="f8ca8-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f8ca8-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f8ca8-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)