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
ms.openlocfilehash: 4d921dd62999bc68b80838bafa2a3da8d4df3ebb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057513"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="3f4c3-102">GetProc03 (C#) 範例程式碼</span><span class="sxs-lookup"><span data-stu-id="3f4c3-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="3f4c3-103">下列程式碼顯示實作`Get-Process`cmdlet 可接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="3f4c3-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="3f4c3-104">此實作會定義`Name`接受管線輸入參數會從本機電腦，根據提供的名稱，擷取程序資訊，然後使用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29)方法，將物件傳送至管線的輸出機制。</span><span class="sxs-lookup"><span data-stu-id="3f4c3-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="3f4c3-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和.NET Framework 3.0 執行階段元件這個 Get-proc cmdlet 的原始程式檔 (getprov03.cs)。</span><span class="sxs-lookup"><span data-stu-id="3f4c3-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="3f4c3-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="3f4c3-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="3f4c3-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="3f4c3-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3f4c3-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="3f4c3-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="3f4c3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f4c3-109">See Also</span></span>

[<span data-ttu-id="3f4c3-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="3f4c3-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="3f4c3-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3f4c3-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)