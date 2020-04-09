---
title: RunSpace10 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 25201200eb437c58a38c88feb1e4c17c974d3e24
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977568"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="590c1-102">RunSpace10 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="590c1-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="590c1-103">以下是 Runspace10 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="590c1-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="590c1-104">這個範例應用程式會將 Cmdlet 新增至[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後使用修改過的設定資訊來建立執行時間。</span><span class="sxs-lookup"><span data-stu-id="590c1-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="590c1-105">您可以使用適用C#于 windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，下載原始程式檔（runspace10.cs）。</span><span class="sxs-lookup"><span data-stu-id="590c1-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="590c1-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="590c1-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="590c1-107">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="590c1-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="590c1-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="590c1-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs" range="11-118":::

## <a name="see-also"></a><span data-ttu-id="590c1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="590c1-109">See Also</span></span>

[<span data-ttu-id="590c1-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="590c1-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="590c1-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="590c1-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
