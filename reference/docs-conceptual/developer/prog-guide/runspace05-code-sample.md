---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace05 程式碼範例
description: RunSpace05 程式碼範例
ms.openlocfilehash: f128e09522bdb05cba2c160bce4944c829a5c108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654203"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="e86b8-103">RunSpace05 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e86b8-103">RunSpace05 Code Sample</span></span>

<span data-ttu-id="e86b8-104">以下是 [使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述之 Runspace05 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="e86b8-104">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="e86b8-105">此範例說明如何建立執行時間設定資訊、建立執行時間、使用單一命令建立管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="e86b8-105">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="e86b8-106">執行的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e86b8-106">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e86b8-107">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件， (runspace05.cs) 下載 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="e86b8-107">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e86b8-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="e86b8-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="e86b8-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="e86b8-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e86b8-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e86b8-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="e86b8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e86b8-111">See Also</span></span>

[<span data-ttu-id="e86b8-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="e86b8-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e86b8-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e86b8-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
