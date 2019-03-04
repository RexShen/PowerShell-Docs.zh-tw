---
title: GetProc04 (C#) Sample Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 02b692047294879f885ca86d4598b0b0ab81808a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863284"
---
# <a name="getproc04-c-sample-code"></a><span data-ttu-id="bc3be-102">GetProc04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="bc3be-102">GetProc04 (C#) Sample Code</span></span>

<span data-ttu-id="bc3be-103">下列程式碼顯示實作`Get-Process`cmdlet 會報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc3be-103">The following code shows the implementation of a `Get-Process` cmdlet that reports nonterminating errors.</span></span> <span data-ttu-id="bc3be-104">這個實作會呼叫[System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)報告非終止錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="bc3be-104">This implementation calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report nonterminating errors.</span></span>

> [!NOTE]
> <span data-ttu-id="bc3be-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="bc3be-105">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bc3be-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="bc3be-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="bc3be-107">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="bc3be-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bc3be-108">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="bc3be-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bc3be-109">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="bc3be-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bc3be-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="bc3be-110">Code Sample</span></span>

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="bc3be-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc3be-111">See Also</span></span>

[<span data-ttu-id="bc3be-112">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="bc3be-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bc3be-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bc3be-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)