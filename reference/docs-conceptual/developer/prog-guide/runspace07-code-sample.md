---
title: RunSpace07 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: ab68f96372f20a435217702c7f3ebde3de633919
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360147"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="69605-102">RunSpace07 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="69605-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="69605-103">以下是[建立可將命令新增至管線的主控台應用程式](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述之 Runspace07 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="69605-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="69605-104">這個範例應用程式會建立一個運行時、建立管線、將兩個命令新增至管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="69605-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="69605-105">新增至管線的命令為 `Get-Process` 和 @no__t 1 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="69605-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="69605-106">您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載原始程式檔（runspace07.cs）。</span><span class="sxs-lookup"><span data-stu-id="69605-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="69605-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="69605-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="69605-108">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="69605-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="69605-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="69605-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="69605-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69605-110">See Also</span></span>

[<span data-ttu-id="69605-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="69605-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="69605-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="69605-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
