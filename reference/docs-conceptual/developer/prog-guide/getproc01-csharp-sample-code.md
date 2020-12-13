---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc01 (C#) 程式碼範例
description: GetProc01 (C#) 程式碼範例
ms.openlocfilehash: 79509ff12afb32c907058f4ddb0c707f3823857a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654489"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="4256d-103">GetProc01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4256d-103">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="4256d-104">下列程式碼顯示 GetProc01 範例 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="4256d-104">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="4256d-105">請注意，透過將進程抓取的實際工作保留給 [system.diagnostics.process.getprocesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses) 方法，即可簡化此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4256d-105">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="4256d-106">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getproc01.cs) 。</span><span class="sxs-lookup"><span data-stu-id="4256d-106">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4256d-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="4256d-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4256d-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="4256d-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4256d-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4256d-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="4256d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4256d-110">See Also</span></span>

[<span data-ttu-id="4256d-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="4256d-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4256d-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4256d-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
