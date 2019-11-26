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
ms.openlocfilehash: 8326d1f47ce07698f09ade9ba97154ecc358465a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417448"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="9f3cc-102">GetProc04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9f3cc-102">GetProc04 Code Samples</span></span>

<span data-ttu-id="9f3cc-103">以下是 GetProc04 範例 Cmdlet 的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-103">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="9f3cc-104">這是[將非終止錯誤報表新增至您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 `Get-Process` Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-104">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="9f3cc-105">此 `Get-Process` Cmdlet 會在抓取進程資訊時，每次擲回不正確作業例外狀況時，呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-105">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="9f3cc-106">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov04.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-106">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9f3cc-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="9f3cc-108">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="9f3cc-109">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="9f3cc-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="9f3cc-110">Language</span><span class="sxs-lookup"><span data-stu-id="9f3cc-110">Language</span></span>|<span data-ttu-id="9f3cc-111">主題</span><span class="sxs-lookup"><span data-stu-id="9f3cc-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="9f3cc-112">C#</span><span class="sxs-lookup"><span data-stu-id="9f3cc-112">C#</span></span>|[<span data-ttu-id="9f3cc-113">GetProc04 （C#）範例程式碼</span><span class="sxs-lookup"><span data-stu-id="9f3cc-113">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="9f3cc-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="9f3cc-114">VB.NET</span></span>|[<span data-ttu-id="9f3cc-115">GetProc04 （VB.NET）範例程式碼</span><span class="sxs-lookup"><span data-stu-id="9f3cc-115">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="9f3cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f3cc-116">See Also</span></span>

[<span data-ttu-id="9f3cc-117">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="9f3cc-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9f3cc-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9f3cc-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
