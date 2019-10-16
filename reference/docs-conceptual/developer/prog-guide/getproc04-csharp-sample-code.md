---
title: GetProc04 （C#）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: e8d9ae69c0d9da23b3e9a807e30ee76ba83af604
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366777"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="51980-102">GetProc04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="51980-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="51980-103">下列程式碼示範如何執行 `Get-Process` Cmdlet 來報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="51980-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="51980-104">這個執行會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="51980-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="51980-105">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov04.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="51980-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="51980-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="51980-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="51980-107">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="51980-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="51980-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="51980-108">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="51980-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51980-109">See Also</span></span>

[<span data-ttu-id="51980-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="51980-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="51980-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="51980-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
