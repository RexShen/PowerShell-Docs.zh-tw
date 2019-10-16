---
title: GetProc01 （VB.NET）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ee87f67-6d2c-48cc-b300-3ae917c6dc88
caps.latest.revision: 5
ms.openlocfilehash: 2411642c39737e7dc03bd0bb4ea753ed27783732
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360437"
---
# <a name="getproc01-vbnet-sample-code"></a><span data-ttu-id="7fa04-102">GetProc01 (VB.NET) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7fa04-102">GetProc01 (VB.NET) Sample Code</span></span>

<span data-ttu-id="7fa04-103">下列程式碼顯示 GetProc01 範例 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="7fa04-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="7fa04-104">請注意，藉由將處理常式抓取的實際工作保留到[system.diagnostics.process.getprocesses \*](/dotnet/api/System.Diagnostics.Process.GetProcesses)方法，即可簡化此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7fa04-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="7fa04-105">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getproc01.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="7fa04-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7fa04-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="7fa04-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7fa04-107">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="7fa04-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7fa04-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7fa04-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [msh_samplesgetproc01#getproc01vball](msh_samplesgetproc01#getproc01vball)]  -->

## <a name="see-also"></a><span data-ttu-id="7fa04-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fa04-109">See Also</span></span>

[<span data-ttu-id="7fa04-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="7fa04-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7fa04-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7fa04-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)