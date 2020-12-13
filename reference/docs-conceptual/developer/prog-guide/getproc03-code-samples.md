---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03 程式碼範例
description: GetProc03 程式碼範例
ms.openlocfilehash: 2866f3652072e1d89780c818543dbfc72a0606f0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659277"
---
# <a name="getproc03-code-samples"></a><span data-ttu-id="8ae0d-103">GetProc03 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8ae0d-103">GetProc03 Code Samples</span></span>

<span data-ttu-id="8ae0d-104">以下是 GetProc03 範例 Cmdlet 的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-104">Here are the code samples for the GetProc03 sample cmdlet.</span></span> <span data-ttu-id="8ae0d-105">此為[新增可處理管線輸入的參數](../cmdlet/adding-parameters-that-process-pipeline-input.md)中所描述 `Get-Process` Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-105">This is the `Get-Process` cmdlet sample described in [Adding Parameters that Process Pipeline Input](../cmdlet/adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="8ae0d-106">此 `Get-Process` Cmdlet 會使用 `Name` 接受來自管線物件之輸入的參數、根據提供的名稱從本機電腦抓取處理資訊，然後在命令列上顯示處理常式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-106">This `Get-Process` cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="8ae0d-107">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getprov03.cs) 。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-107">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8ae0d-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8ae0d-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="8ae0d-110">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="8ae0d-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="8ae0d-111">語言</span><span class="sxs-lookup"><span data-stu-id="8ae0d-111">Language</span></span>|<span data-ttu-id="8ae0d-112">主題</span><span class="sxs-lookup"><span data-stu-id="8ae0d-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="8ae0d-113">C#</span><span class="sxs-lookup"><span data-stu-id="8ae0d-113">C#</span></span>|[<span data-ttu-id="8ae0d-114">GetProc03 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="8ae0d-114">GetProc03 (C#) Sample Code</span></span>](./getproc03-csharp-sample-code.md)|
|<span data-ttu-id="8ae0d-115">VB.NET</span><span class="sxs-lookup"><span data-stu-id="8ae0d-115">VB.NET</span></span>|[<span data-ttu-id="8ae0d-116">GetProc03 (VB.NET) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="8ae0d-116">GetProc03 (VB.NET) Sample Code</span></span>](./getproc03-vb-net-sample-code.md)|

## <a name="see-also"></a><span data-ttu-id="8ae0d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ae0d-117">See Also</span></span>

[<span data-ttu-id="8ae0d-118">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="8ae0d-118">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8ae0d-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8ae0d-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
