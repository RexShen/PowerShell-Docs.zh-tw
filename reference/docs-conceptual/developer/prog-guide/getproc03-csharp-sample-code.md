---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03 (C#) 範例程式碼
description: GetProc03 (C#) 範例程式碼
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355573"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="fb7a5-103">GetProc03 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="fb7a5-103">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="fb7a5-104">下列程式碼顯示 `Get-Process` 可接受管線輸入的 Cmdlet 執行。</span><span class="sxs-lookup"><span data-stu-id="fb7a5-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="fb7a5-105">這個實值會定義一個 `Name` 接受管線輸入的參數、根據提供的名稱抓取本機電腦的處理資訊，然後使用 [WriteObject (system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 方法做為傳送物件至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="fb7a5-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="fb7a5-106">您可以使用適用于 Windows Vista 的 Microsoft Windows 軟體開發套件和 .NET Framework 3.0 執行時間元件，下載此 Get-Proc Cmdlet 的 c # 原始程式檔 (getprov03.cs) 。</span><span class="sxs-lookup"><span data-stu-id="fb7a5-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fb7a5-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="fb7a5-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="fb7a5-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="fb7a5-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fb7a5-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="fb7a5-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="fb7a5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb7a5-110">See Also</span></span>

[<span data-ttu-id="fb7a5-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="fb7a5-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fb7a5-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fb7a5-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
