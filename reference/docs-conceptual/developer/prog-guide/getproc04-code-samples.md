---
title: GetProc04 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c00afd46-758a-4aec-b865-2c9d8f6a17ad
caps.latest.revision: 5
ms.openlocfilehash: 67081528ebe14fbb082091c1b9500de82069b48f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360317"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="d65d6-102">GetProc04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d65d6-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="d65d6-103">以下是 GetProc04 範例 Cmdlet 的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d65d6-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="d65d6-104">這是[將非終止錯誤報表新增至您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 `Get-Process` Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="d65d6-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="d65d6-105">當抓取程式資訊時，如果擲回不正確作業例外狀況，此 `Get-Process` Cmdlet 會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="d65d6-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="d65d6-106">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov04.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="d65d6-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d65d6-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="d65d6-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d65d6-108">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="d65d6-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="d65d6-109">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="d65d6-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="d65d6-110">Language</span><span class="sxs-lookup"><span data-stu-id="d65d6-110">Language</span></span>|<span data-ttu-id="d65d6-111">主題</span><span class="sxs-lookup"><span data-stu-id="d65d6-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="d65d6-112">C#</span><span class="sxs-lookup"><span data-stu-id="d65d6-112">C#</span></span>|[<span data-ttu-id="d65d6-113">GetProc04 （C#）範例程式碼</span><span class="sxs-lookup"><span data-stu-id="d65d6-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="d65d6-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="d65d6-114">VB.NET</span></span>|[<span data-ttu-id="d65d6-115">GetProc04 （VB.NET）範例程式碼</span><span class="sxs-lookup"><span data-stu-id="d65d6-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="d65d6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d65d6-116">See Also</span></span>

[<span data-ttu-id="d65d6-117">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="d65d6-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d65d6-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d65d6-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)