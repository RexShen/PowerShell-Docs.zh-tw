---
title: GetProc04 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: d679bc8cbdb026e072628d3e0c5704de2eec7af9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855444"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="0b59a-102">GetProc04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="0b59a-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="0b59a-103">以下是 GetProc04 cmdlet 範例的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="0b59a-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="0b59a-104">這是`Get-Process`cmdlet 的範例中所述[新增非終止錯誤報告，您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="0b59a-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="0b59a-105">這`Get-Process`cmdlet 會呼叫[System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)時擷取程序資訊時擲回無效作業例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="0b59a-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="0b59a-106">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="0b59a-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0b59a-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="0b59a-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0b59a-108">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov04.cs)。</span><span class="sxs-lookup"><span data-stu-id="0b59a-108">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0b59a-109">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="0b59a-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0b59a-110">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="0b59a-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="0b59a-111">完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="0b59a-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="0b59a-112">語言</span><span class="sxs-lookup"><span data-stu-id="0b59a-112">Language</span></span>|<span data-ttu-id="0b59a-113">主題</span><span class="sxs-lookup"><span data-stu-id="0b59a-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="0b59a-114">C#</span><span class="sxs-lookup"><span data-stu-id="0b59a-114">C#</span></span>|[<span data-ttu-id="0b59a-115">GetProc04 (C#) Sample Code</span><span class="sxs-lookup"><span data-stu-id="0b59a-115">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="0b59a-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="0b59a-116">VB.NET</span></span>|[<span data-ttu-id="0b59a-117">GetProc04 (VB.NET) Sample Code</span><span class="sxs-lookup"><span data-stu-id="0b59a-117">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="0b59a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b59a-118">See Also</span></span>

[<span data-ttu-id="0b59a-119">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="0b59a-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0b59a-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0b59a-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)