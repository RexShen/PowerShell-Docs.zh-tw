---
title: 'GetProc01 (c # ) 範例程式碼 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 883beb9dd1328a1897b9b61656a98cf515a21be7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778891"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="b13bd-102">GetProc01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b13bd-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="b13bd-103">下列程式碼顯示 GetProc01 範例 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="b13bd-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="b13bd-104">請注意，藉由將處理常式抓取的實際工作保留到[system.diagnostics.process.getprocesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法，即可簡化此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b13bd-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="b13bd-105">您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為這個 getproc01.cs) 下載 c # 原始程式檔 (。</span><span class="sxs-lookup"><span data-stu-id="b13bd-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b13bd-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="b13bd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="b13bd-107">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="b13bd-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b13bd-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b13bd-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="11-126":::

## <a name="see-also"></a><span data-ttu-id="b13bd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b13bd-109">See Also</span></span>

[<span data-ttu-id="b13bd-110">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="b13bd-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b13bd-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b13bd-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
