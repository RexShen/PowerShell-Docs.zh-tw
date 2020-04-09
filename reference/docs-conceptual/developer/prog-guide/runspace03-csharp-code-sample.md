---
title: RunSpace03 （C#）程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 28cef037f56f2a101f631d3a234974a8868b4ef9
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978316"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="c48ee-102">RunSpace03 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c48ee-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="c48ee-103">以下是主控台C#應用程式的原始程式碼，如「建立執行指定腳本的主控台應用程式」中所述。</span><span class="sxs-lookup"><span data-stu-id="c48ee-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="c48ee-104">這個範例會使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行腳本，藉由使用傳入腳本的進程名稱清單來抓取進程資訊。</span><span class="sxs-lookup"><span data-stu-id="c48ee-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="c48ee-105">它會示範如何將輸入物件傳遞至腳本，以及如何抓取錯誤物件以及輸出物件。</span><span class="sxs-lookup"><span data-stu-id="c48ee-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="c48ee-106">您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此範例的原始程式檔（runspace03.cs）。</span><span class="sxs-lookup"><span data-stu-id="c48ee-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c48ee-107">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="c48ee-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="c48ee-108">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="c48ee-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c48ee-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c48ee-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="c48ee-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c48ee-110">See Also</span></span>

[<span data-ttu-id="c48ee-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="c48ee-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c48ee-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c48ee-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
