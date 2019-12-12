---
title: GetProc04 （VB.NET）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: f2164b97e4f3b3346e66d00834aa299659b62b33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416100"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="0178e-102">GetProc04 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="0178e-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="0178e-103">下列程式碼示範如何執行 `Get-Process` Cmdlet 來報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="0178e-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="0178e-104">這個執行會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="0178e-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="0178e-105">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov04.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="0178e-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0178e-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="0178e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0178e-107">下載的來源檔案可在**\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="0178e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0178e-108">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="0178e-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="0178e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0178e-109">See Also</span></span>

[<span data-ttu-id="0178e-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="0178e-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0178e-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0178e-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
