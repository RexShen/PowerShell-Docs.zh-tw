---
title: GetProc01 (VB.NET) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 1f11c89f60aef44905cbce3fe669def26119d12e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856064"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="70f9a-102">GetProc01 (VB.NET) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="70f9a-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="70f9a-103">下列程式碼顯示 GetProc01 cmdlet 範例的實作。</span><span class="sxs-lookup"><span data-stu-id="70f9a-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="70f9a-104">請注意，此 cmdlet 會簡化留下來的程序擷取的實際工作[System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法。</span><span class="sxs-lookup"><span data-stu-id="70f9a-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="70f9a-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="70f9a-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="70f9a-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="70f9a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="70f9a-107">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getproc01.cs)。</span><span class="sxs-lookup"><span data-stu-id="70f9a-107">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="70f9a-108">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="70f9a-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="70f9a-109">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="70f9a-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="70f9a-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="70f9a-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="70f9a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70f9a-111">See Also</span></span>

[<span data-ttu-id="70f9a-112">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="70f9a-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="70f9a-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="70f9a-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)