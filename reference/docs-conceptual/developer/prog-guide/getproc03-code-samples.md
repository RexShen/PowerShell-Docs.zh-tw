---
title: GetProc03 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad39c7d-2f64-49d1-9be0-d2295e4302b3
caps.latest.revision: 5
ms.openlocfilehash: 833ff1c37ee025e9cd9d2760bc63695534dd69ff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360377"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="03408-102">GetProc03 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="03408-102">GetProc03 Code Samples</span></span>

<span data-ttu-id="03408-103">以下是 GetProc03 範例 Cmdlet 的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="03408-103">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="03408-104">這是[新增處理管線輸入的參數](../cmdlet/adding-parameters-that-process-pipeline-input.md)中所述的 `Get-Process` Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="03408-104">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="03408-105">這個 `Get-Process` Cmdlet 使用可接受管線物件輸入的 `Name` 參數，根據提供的名稱從本機電腦上抓取進程資訊，然後在命令列顯示進程的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="03408-105">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="03408-106">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov03.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="03408-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="03408-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="03408-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="03408-108">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="03408-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="03408-109">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="03408-109">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="03408-110">Language</span><span class="sxs-lookup"><span data-stu-id="03408-110">Language</span></span>|<span data-ttu-id="03408-111">主題</span><span class="sxs-lookup"><span data-stu-id="03408-111">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="03408-112">C#</span><span class="sxs-lookup"><span data-stu-id="03408-112">C#</span></span>|[<span data-ttu-id="03408-113">GetProc03 （C#）範例程式碼</span><span class="sxs-lookup"><span data-stu-id="03408-113">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="03408-114">VB.NET</span><span class="sxs-lookup"><span data-stu-id="03408-114">VB.NET</span></span>|[<span data-ttu-id="03408-115">GetProc03 （VB.NET）範例程式碼</span><span class="sxs-lookup"><span data-stu-id="03408-115">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="03408-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03408-116">See Also</span></span>

[<span data-ttu-id="03408-117">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="03408-117">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="03408-118">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="03408-118">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)