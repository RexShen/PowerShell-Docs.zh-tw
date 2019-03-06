---
title: GetProc01 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430072"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="e32de-102">GetProc01 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e32de-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="e32de-103">下列程式碼顯示 GetProc01 cmdlet 範例的實作。</span><span class="sxs-lookup"><span data-stu-id="e32de-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="e32de-104">請注意，此 cmdlet 會簡化留下來的程序擷取的實際工作[System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法。</span><span class="sxs-lookup"><span data-stu-id="e32de-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="e32de-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="e32de-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e32de-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="e32de-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e32de-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="e32de-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e32de-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e32de-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="e32de-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e32de-109">See Also</span></span>

[<span data-ttu-id="e32de-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="e32de-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e32de-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e32de-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)