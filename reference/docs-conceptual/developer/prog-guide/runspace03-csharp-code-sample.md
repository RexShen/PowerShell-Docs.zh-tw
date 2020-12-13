---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace03 (C#) 程式碼範例
description: RunSpace03 (C#) 程式碼範例
ms.openlocfilehash: cdb08811de13f8bbf5cd91fcbef552c78594b788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653835"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="49369-103">RunSpace03 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="49369-103">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="49369-104">以下是「建立執行指定腳本的主控台應用程式」中所述之主控台應用程式的 c # 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="49369-104">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="49369-105">這個範例會使用 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 類別來執行腳本，該腳本會使用傳遞至腳本的進程名稱清單來抓取進程資訊。</span><span class="sxs-lookup"><span data-stu-id="49369-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="49369-106">它會示範如何將輸入物件傳遞給腳本，以及如何取出錯誤物件以及輸出物件。</span><span class="sxs-lookup"><span data-stu-id="49369-106">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="49369-107">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件，下載此範例的 c # 原始程式檔 (runspace03.cs) 。</span><span class="sxs-lookup"><span data-stu-id="49369-107">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="49369-108">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="49369-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="49369-109">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="49369-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="49369-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="49369-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="49369-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49369-111">See Also</span></span>

[<span data-ttu-id="49369-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="49369-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="49369-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="49369-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
