---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc04 程式碼範例
description: GetProc04 程式碼範例
ms.openlocfilehash: db94eda2b3aa5fc88a3054df66f54628e1482f56
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659244"
---
# <a name="getproc04-code-samples"></a><span data-ttu-id="b7011-103">GetProc04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b7011-103">GetProc04 Code Samples</span></span>

<span data-ttu-id="b7011-104">以下是 GetProc04 範例 Cmdlet 的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="b7011-104">Here are the code samples for the GetProc04 sample cmdlet.</span></span> <span data-ttu-id="b7011-105">此為[新增持續錯誤報告至 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md) 中所描述 `Get-Process` Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="b7011-105">This is the `Get-Process` cmdlet sample described in [Adding Nonterminating Error Reporting to Your Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md).</span></span> <span data-ttu-id="b7011-106">`Get-Process`每當在抓取處理常式資訊時擲回無效作業例外狀況時，此 Cmdlet 會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。</span><span class="sxs-lookup"><span data-stu-id="b7011-106">This `Get-Process` cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method whenever an invalid operation exception is thrown while retrieving process information.</span></span>

> [!NOTE]
> <span data-ttu-id="b7011-107">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getprov04.cs) 。</span><span class="sxs-lookup"><span data-stu-id="b7011-107">You can download the C# source file (getprov04.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b7011-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="b7011-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="b7011-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="b7011-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="b7011-110">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="b7011-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="b7011-111">語言</span><span class="sxs-lookup"><span data-stu-id="b7011-111">Language</span></span>|<span data-ttu-id="b7011-112">主題</span><span class="sxs-lookup"><span data-stu-id="b7011-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="b7011-113">C#</span><span class="sxs-lookup"><span data-stu-id="b7011-113">C#</span></span>|[<span data-ttu-id="b7011-114">GetProc04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="b7011-114">GetProc04 (C#) Sample Code</span></span>](./getproc04-csharp-sample-code.md)|
|<span data-ttu-id="b7011-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="b7011-115">VB.NET</span></span>|[<span data-ttu-id="b7011-116">GetProc04 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="b7011-116">GetProc04 (VB.NET) Sample Code</span></span>](./getproc04-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="b7011-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7011-117">See Also</span></span>

[<span data-ttu-id="b7011-118">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="b7011-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b7011-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b7011-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
