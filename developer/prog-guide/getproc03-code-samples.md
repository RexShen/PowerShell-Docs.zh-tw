---
title: GetProc03 Code Samples | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 8cb02b9f2510b90f405651deaf551e9622f5a298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857304"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="4e7f5-102">GetProc03 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4e7f5-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="4e7f5-103">以下是 GetProc03 cmdlet 範例的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="4e7f5-104">這是`Get-Process`cmdlet 的範例中所述[加入參數，該程序管線輸入](../cmdlet/adding-parameters-that-process-pipeline-input.md)。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="4e7f5-105">這`Get-Process`cmdlet 會使用`Name`接受來自管線的物件中，輸入的參數會從本機電腦，根據提供的名稱，擷取程序資訊，並接著會處理序的相關資訊顯示在命令列。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="4e7f5-106">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4e7f5-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="4e7f5-108">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-108">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="4e7f5-109">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="4e7f5-110">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="4e7f5-111">完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="4e7f5-111">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="4e7f5-112">語言</span><span class="sxs-lookup"><span data-stu-id="4e7f5-112">Language</span></span>|<span data-ttu-id="4e7f5-113">主題</span><span class="sxs-lookup"><span data-stu-id="4e7f5-113">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="4e7f5-114">C#</span><span class="sxs-lookup"><span data-stu-id="4e7f5-114">C#</span></span>|[<span data-ttu-id="4e7f5-115">GetProc03 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4e7f5-115">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="4e7f5-116">VB.NET</span><span class="sxs-lookup"><span data-stu-id="4e7f5-116">VB.NET</span></span>|[<span data-ttu-id="4e7f5-117">GetProc03 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="4e7f5-117">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="4e7f5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e7f5-118">See Also</span></span>

[<span data-ttu-id="4e7f5-119">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="4e7f5-119">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="4e7f5-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4e7f5-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)