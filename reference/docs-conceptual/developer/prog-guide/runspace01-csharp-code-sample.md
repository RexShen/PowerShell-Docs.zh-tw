---
title: 'Runspace01 (c # ) 程式碼範例 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 418162731b4a98989642e1c61c655fdb0f002698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787049"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="c8f02-102">Runspace01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c8f02-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="c8f02-103">以下是[建立主控台應用程式（可執行指定的命令](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)）中所述之運行空間的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="c8f02-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="c8f02-104">若要這樣做，應用程式會叫用運行空間，然後叫用命令。</span><span class="sxs-lookup"><span data-stu-id="c8f02-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="c8f02-105"> (請注意，此應用程式不會指定執行空間設定資訊，也不會明確地建立管線) 。</span><span class="sxs-lookup"><span data-stu-id="c8f02-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="c8f02-106">所叫用的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8f02-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c8f02-107">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為此執行時間下載 c # 原始程式檔 (runspace01.cs) 。</span><span class="sxs-lookup"><span data-stu-id="c8f02-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="c8f02-108">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="c8f02-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="c8f02-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="c8f02-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c8f02-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c8f02-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="c8f02-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8f02-111">See Also</span></span>

[<span data-ttu-id="c8f02-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="c8f02-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c8f02-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c8f02-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
