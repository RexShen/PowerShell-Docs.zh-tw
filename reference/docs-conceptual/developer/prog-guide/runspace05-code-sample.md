---
title: RunSpace05 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31a73f965a6e38dceec740a2f7d4adead3e2a3f9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784736"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="7969e-102">RunSpace05 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7969e-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="7969e-103">以下是[使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述 Runspace05 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7969e-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="7969e-104">這個範例示範如何建立執行時間設定資訊、建立執行時間、使用單一命令建立管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="7969e-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="7969e-105">執行的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7969e-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="7969e-106">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組， (runspace05.cs) 下載 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="7969e-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7969e-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="7969e-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="7969e-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="7969e-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7969e-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7969e-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="7969e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7969e-110">See Also</span></span>

[<span data-ttu-id="7969e-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="7969e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7969e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7969e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
