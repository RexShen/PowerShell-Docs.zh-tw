---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01 (C#) 程式碼範例
description: Runspace01 (C#) 程式碼範例
ms.openlocfilehash: e6121c144e1a4c1a1d9460d01119f44ee5835821
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657145"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="e9142-103">Runspace01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e9142-103">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="e9142-104">以下是 [建立執行指定命令的主控台應用程式](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)中所述之運行空間的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="e9142-104">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="e9142-105">若要這樣做，應用程式會叫用運行空間，然後再叫用命令。</span><span class="sxs-lookup"><span data-stu-id="e9142-105">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="e9142-106"> (請注意，此應用程式不會指定運行時設定資訊，也不會明確建立管線) 。</span><span class="sxs-lookup"><span data-stu-id="e9142-106">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="e9142-107">叫用的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e9142-107">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e9142-108">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件，下載此執行時間的 c # 原始程式檔 (runspace01.cs) 。</span><span class="sxs-lookup"><span data-stu-id="e9142-108">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="e9142-109">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="e9142-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e9142-110">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="e9142-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e9142-111">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e9142-111">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="e9142-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9142-112">See Also</span></span>

[<span data-ttu-id="e9142-113">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="e9142-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e9142-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e9142-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
