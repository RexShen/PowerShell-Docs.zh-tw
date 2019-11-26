---
title: GetProc03 （C#）範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 126df3092c0722b0fc9d02cb61d3faf0578b8e97
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416137"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="7933e-102">GetProc03 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="7933e-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="7933e-103">下列程式碼顯示可接受管線輸入的 `Get-Process` Cmdlet 的執行。</span><span class="sxs-lookup"><span data-stu-id="7933e-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="7933e-104">這個實作為定義一個接受管線輸入的 `Name` 參數，根據提供的名稱從本機電腦抓取進程資訊，然後使用[WriteObject （system.object，system.string）](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="7933e-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="7933e-105">您可以使用適用C#于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載這個 getprov03.cs 的原始程式檔（）。</span><span class="sxs-lookup"><span data-stu-id="7933e-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7933e-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="7933e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7933e-107">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="7933e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7933e-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7933e-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="7933e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7933e-109">See Also</span></span>

[<span data-ttu-id="7933e-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="7933e-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7933e-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7933e-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
