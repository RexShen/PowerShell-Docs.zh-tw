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
ms.openlocfilehash: 232b282e366c9fad167686337696ef2ccd8b30d8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734953"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="64368-102">RunSpace07 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="64368-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="64368-103">以下是原始程式碼，Runspace07 範例中所述[建立主控台應用程式，新增命令至管線](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)。</span><span class="sxs-lookup"><span data-stu-id="64368-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="64368-104">此範例應用程式會建立 runspace，會建立管線，到管線中，新增兩個命令，然後執行管線的資料。</span><span class="sxs-lookup"><span data-stu-id="64368-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="64368-105">新增至管線的命令都`Get-Process`和`Measure-Object`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64368-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="64368-106">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (runspace07.cs)。</span><span class="sxs-lookup"><span data-stu-id="64368-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="64368-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="64368-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="64368-108">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="64368-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="64368-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="64368-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="64368-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64368-110">See Also</span></span>

[<span data-ttu-id="64368-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="64368-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="64368-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="64368-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)