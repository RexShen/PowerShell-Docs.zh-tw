---
title: 'StopProcessSample04 (c # ) 範例程式碼 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: f7ee58ee8faa95bbd0d3ca2f01fd8e340e08beb6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786963"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="48565-102">StopProcessSample04 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="48565-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="48565-103">以下是 StopProc04 範例 Cmdlet 的完整 c # 範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="48565-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="48565-104">這是 `Stop-Process` [將參數集新增至 Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述之 Cmdlet 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="48565-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="48565-105">此 `Stop-Process` Cmdlet 的設計目的是要使用 ([建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)) 中所述的 Get-Proc Cmdlet 來停止處理常式。</span><span class="sxs-lookup"><span data-stu-id="48565-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="48565-106">您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為這個停止程式 Cmdlet 下載 c # (stopprocesssample04.cs) 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="48565-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="48565-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="48565-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="48565-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="48565-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs" range="11-435":::

## <a name="see-also"></a><span data-ttu-id="48565-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48565-109">See Also</span></span>

[<span data-ttu-id="48565-110">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="48565-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="48565-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="48565-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
