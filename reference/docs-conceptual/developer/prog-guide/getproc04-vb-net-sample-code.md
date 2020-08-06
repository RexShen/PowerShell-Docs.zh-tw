---
title: GetProc04 (VB.NET) 範例程式碼 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 63fbbb2d6bef4634bf72d4b0f9e429de9ed9deca
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771867"
---
# <a name="getproc04-vbnet-sample-code"></a><span data-ttu-id="5fc3a-102">GetProc04 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5fc3a-102">GetProc04 (VB.NET) Sample Code</span></span>

<span data-ttu-id="5fc3a-103">下列程式碼顯示 `Get-Process` 報告非終止錯誤的 Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="5fc3a-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="5fc3a-104">這個執行會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="5fc3a-104">This implementation calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="5fc3a-105">您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為這個 getprov04.cs) 下載 c # 原始程式檔 (。</span><span class="sxs-lookup"><span data-stu-id="5fc3a-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5fc3a-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="5fc3a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5fc3a-107">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="5fc3a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5fc3a-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="5fc3a-108">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc04#GetProc04vball](Msh_samplesgetproc04#GetProc04vball)]  -->

## <a name="see-also"></a><span data-ttu-id="5fc3a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fc3a-109">See Also</span></span>

[<span data-ttu-id="5fc3a-110">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="5fc3a-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5fc3a-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5fc3a-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
