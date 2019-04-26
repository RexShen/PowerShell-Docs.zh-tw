---
title: Runspace01 (C#) 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081456"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="32db3-102">Runspace01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="32db3-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="32db3-103">如下的程式碼範例中所述的 runspace[建立主控台應用程式，執行指定命令](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)。</span><span class="sxs-lookup"><span data-stu-id="32db3-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="32db3-104">若要這樣做，應用程式會叫用的 runspace，然後再叫用命令。</span><span class="sxs-lookup"><span data-stu-id="32db3-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="32db3-105">（請注意，此應用程式未指定 runspace 組態資訊，也不會它明確地建立管線）。</span><span class="sxs-lookup"><span data-stu-id="32db3-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="32db3-106">叫用的命令是`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="32db3-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="32db3-107">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件此 runspace 的原始程式檔 (runspace01.cs)。</span><span class="sxs-lookup"><span data-stu-id="32db3-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="32db3-108">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="32db3-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="32db3-109">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="32db3-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="32db3-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="32db3-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="32db3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32db3-111">See Also</span></span>

[<span data-ttu-id="32db3-112">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="32db3-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="32db3-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="32db3-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)