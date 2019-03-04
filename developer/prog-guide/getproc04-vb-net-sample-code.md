---
title: GetProc04 (VB.NET) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d22f47b-3679-4587-a559-94454415d2dd
caps.latest.revision: 5
ms.openlocfilehash: 18f9e7a23f8b8c94aae2807a4058cb3a6f18615c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861014"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="dfb6f-102">GetProc04 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="dfb6f-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="dfb6f-103">下列程式碼顯示實作`Get-Process`cmdlet 會報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="dfb6f-104">這個實作會呼叫[System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)報告非終止錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="dfb6f-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dfb6f-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="dfb6f-107">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dfb6f-108">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="dfb6f-109">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="dfb6f-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="dfb6f-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="dfb6f-110">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="dfb6f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfb6f-111">See Also</span></span>

[<span data-ttu-id="dfb6f-112">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="dfb6f-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dfb6f-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dfb6f-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)