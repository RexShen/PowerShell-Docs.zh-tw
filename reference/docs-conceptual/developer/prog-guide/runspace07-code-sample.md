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
ms.openlocfilehash: 55005a254ef50a2230121095770899cb3b9b70f1
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978215"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="b6d48-102">RunSpace07 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b6d48-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="b6d48-103">以下是[建立可將命令新增至管線的主控台應用程式](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述之 Runspace07 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6d48-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="b6d48-104">這個範例應用程式會建立一個運行時、建立管線、將兩個命令新增至管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="b6d48-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="b6d48-105">新增至管線的命令是 `Get-Process` 和 `Measure-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b6d48-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="b6d48-106">您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載原始程式檔（runspace07.cs）。</span><span class="sxs-lookup"><span data-stu-id="b6d48-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b6d48-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="b6d48-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="b6d48-108">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="b6d48-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b6d48-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b6d48-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="b6d48-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d48-110">See Also</span></span>

[<span data-ttu-id="b6d48-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="b6d48-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b6d48-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b6d48-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
