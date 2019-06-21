---
title: GetProc03 (C#) 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 116a116a5ba5b81a77b4432a81f001cc999fe46d
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301364"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="a6e64-102">GetProc03 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="a6e64-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="a6e64-103">下列程式碼顯示實作`Get-Process`cmdlet 可接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="a6e64-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="a6e64-104">此實作會定義`Name`接受管線輸入參數會從本機電腦，根據提供的名稱，擷取程序資訊，然後使用[WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法，將物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="a6e64-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="a6e64-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="a6e64-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a6e64-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a6e64-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="a6e64-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="a6e64-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a6e64-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="a6e64-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="a6e64-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6e64-109">See Also</span></span>

[<span data-ttu-id="a6e64-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="a6e64-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a6e64-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a6e64-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
