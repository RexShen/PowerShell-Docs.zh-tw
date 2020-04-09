---
title: RunSpace06 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d1d5e7f4096288ed09dada8eb8a61773921dc1ce
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978220"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="9d8d9-102">RunSpace06 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9d8d9-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="9d8d9-103">以下是[使用 Windows PowerShell 嵌入式管理單元設定運行](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83)時間中所述之 Runspace06 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d8d9-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span>
<span data-ttu-id="9d8d9-104">這個範例應用程式會根據 Windows PowerShell 嵌入式管理單元建立執行時間，然後使用單一命令來執行管線。</span><span class="sxs-lookup"><span data-stu-id="9d8d9-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="9d8d9-105">若要這樣做，應用程式會建立運行時設定資訊、建立運行空間、使用單一命令建立管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="9d8d9-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="9d8d9-106">您可以使用適用C#于 windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，下載原始程式檔（runspace06.cs）。</span><span class="sxs-lookup"><span data-stu-id="9d8d9-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="9d8d9-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="9d8d9-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="9d8d9-108">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="9d8d9-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9d8d9-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="9d8d9-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs" range="11-85":::

## <a name="see-also"></a><span data-ttu-id="9d8d9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d8d9-110">See Also</span></span>

[<span data-ttu-id="9d8d9-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="9d8d9-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="9d8d9-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9d8d9-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
