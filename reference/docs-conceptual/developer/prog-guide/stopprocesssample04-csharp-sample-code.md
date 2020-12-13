---
ms.date: 09/13/2016
ms.topic: reference
title: StopProcessSample04 (C#) 範例程式碼
description: StopProcessSample04 (C#) 範例程式碼
ms.openlocfilehash: ecb3c5b8226a1a9a75b93d215e0579a155fe3662
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667448"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="a2892-103">StopProcessSample04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="a2892-103">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="a2892-104">以下是 StopProc04 範例 Cmdlet 的完整 c # 範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2892-104">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="a2892-105">這是 `Stop-Process` [將參數集新增至 Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述之 Cmdlet 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a2892-105">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="a2892-106">此 `Stop-Process` Cmdlet 的設計目的是要停止使用 Get-Proc Cmdlet 抓取的進程， (在 [建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)) 中所述。</span><span class="sxs-lookup"><span data-stu-id="a2892-106">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="a2892-107">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Stop-Proc Cmdlet 的 c # (stopprocesssample04.cs) 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="a2892-107">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a2892-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a2892-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="a2892-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="a2892-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs" range="11-435":::

## <a name="see-also"></a><span data-ttu-id="a2892-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2892-110">See Also</span></span>

[<span data-ttu-id="a2892-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="a2892-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a2892-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a2892-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
