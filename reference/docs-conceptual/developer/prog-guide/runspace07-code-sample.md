---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace07 程式碼範例
description: RunSpace07 程式碼範例
ms.openlocfilehash: 6e8c9f48a6e9c5a642ecf93bca8a85003b3cfbf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647394"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="ced8b-103">RunSpace07 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ced8b-103">RunSpace07 Code Sample</span></span>

<span data-ttu-id="ced8b-104">以下是 [建立可將命令新增至管線的主控台應用程式](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述之 Runspace07 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ced8b-104">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span>
<span data-ttu-id="ced8b-105">這個範例應用程式會建立一個運行空間、建立管線、將兩個命令新增至管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="ced8b-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="ced8b-106">新增至管線的命令為 `Get-Process` 和 `Measure-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ced8b-106">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="ced8b-107">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件， (runspace07.cs) 下載 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ced8b-107">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ced8b-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ced8b-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ced8b-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="ced8b-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ced8b-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ced8b-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs" range="11-108":::

## <a name="see-also"></a><span data-ttu-id="ced8b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ced8b-111">See Also</span></span>

[<span data-ttu-id="ced8b-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="ced8b-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ced8b-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ced8b-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
