---
title: RunSpace05 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 8802e308712be93992ead5ef77b97d8c21b137f7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870637"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="82aa0-102">RunSpace05 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="82aa0-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="82aa0-103">以下是[使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述 Runspace05 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="82aa0-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="82aa0-104">這個範例示範如何建立執行時間設定資訊、建立執行時間、使用單一命令建立管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="82aa0-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="82aa0-105">執行的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82aa0-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="82aa0-106">您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載原始程式檔（runspace05.cs）。</span><span class="sxs-lookup"><span data-stu-id="82aa0-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="82aa0-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="82aa0-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="82aa0-108">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="82aa0-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="82aa0-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="82aa0-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="82aa0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82aa0-110">See Also</span></span>

[<span data-ttu-id="82aa0-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="82aa0-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="82aa0-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82aa0-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
