---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace10 程式碼範例
description: RunSpace10 程式碼範例
ms.openlocfilehash: d9219ca29ec85b8dd2af19c9eba3ddb49050c25c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659148"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="6a81c-103">RunSpace10 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6a81c-103">RunSpace10 Code Sample</span></span>

<span data-ttu-id="6a81c-104">以下是 Runspace10 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a81c-104">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="6a81c-105">這個範例應用程式會將 Cmdlet 新增至 [Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後使用修改過的設定資訊來建立此執行時間。</span><span class="sxs-lookup"><span data-stu-id="6a81c-105">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="6a81c-106">您可以使用 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體開發套件， (runspace10.cs) 下載 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="6a81c-106">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6a81c-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="6a81c-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6a81c-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="6a81c-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6a81c-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6a81c-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs" range="11-118":::

## <a name="see-also"></a><span data-ttu-id="6a81c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a81c-110">See Also</span></span>

[<span data-ttu-id="6a81c-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="6a81c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6a81c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6a81c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
