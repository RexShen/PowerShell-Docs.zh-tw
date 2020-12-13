---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 (VB.NET) 範例程式碼
description: GetProc04 (VB.NET) 範例程式碼
ms.openlocfilehash: c46a374ab9d77f343b5ac6f45be1711eaec6dd75
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659229"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="179ea-103">GetProc04 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="179ea-103">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="179ea-104">下列程式碼顯示 `Get-Process` 會報告非終止錯誤的 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="179ea-104">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="179ea-105">此實 WriteError 會呼叫[](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="179ea-105">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="179ea-106">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getprov04.cs) 。</span><span class="sxs-lookup"><span data-stu-id="179ea-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="179ea-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="179ea-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="179ea-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="179ea-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="179ea-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="179ea-109">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="179ea-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="179ea-110">See Also</span></span>

[<span data-ttu-id="179ea-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="179ea-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="179ea-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="179ea-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
