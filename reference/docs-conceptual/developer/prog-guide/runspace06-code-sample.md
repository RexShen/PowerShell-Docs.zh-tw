---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace06 程式碼範例
description: RunSpace06 程式碼範例
ms.openlocfilehash: 627fa2be51721dd8bfdd63fabdd2e6f286d593be
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667467"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="7f38c-103">RunSpace06 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7f38c-103">RunSpace06 Code Sample</span></span>

<span data-ttu-id="7f38c-104">以下是 [使用 Windows PowerShell 嵌入式管理單元設定運行空間](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83)時所述之 Runspace06 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f38c-104">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="7f38c-105">這個範例應用程式會根據 Windows PowerShell 嵌入式管理單元建立運行空間，然後使用單一命令來執行管線。</span><span class="sxs-lookup"><span data-stu-id="7f38c-105">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="7f38c-106">若要這樣做，應用程式會建立運行空間設定資訊、建立運行空間、使用單一命令建立管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="7f38c-106">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="7f38c-107">您可以使用 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體開發套件， (runspace06.cs) 下載 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="7f38c-107">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7f38c-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="7f38c-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="7f38c-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="7f38c-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7f38c-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7f38c-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="7f38c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f38c-111">See Also</span></span>

[<span data-ttu-id="7f38c-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="7f38c-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7f38c-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7f38c-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
