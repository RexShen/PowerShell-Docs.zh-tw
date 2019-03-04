---
title: RunSpace04 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: 10f236b201920d2d456af41328c7a62a9e14b571
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861094"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="7e857-102">RunSpace04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7e857-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="7e857-103">如下的程式碼範例會使用的 runspace [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行指令碼會產生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e857-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="7e857-104">主應用程式負責攔截錯誤和解譯記錄時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e857-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="7e857-105">您可以下載的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件使用此 runspace VB.NET 原始程式檔 (Runspace04.vb)。</span><span class="sxs-lookup"><span data-stu-id="7e857-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7e857-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="7e857-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="7e857-107">您可以下載的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件使用此 runspace VB.NET 原始程式檔 (Runspace04.vb)。</span><span class="sxs-lookup"><span data-stu-id="7e857-107">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7e857-108">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="7e857-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7e857-109">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="7e857-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="7e857-110">完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="7e857-110">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="7e857-111">語言</span><span class="sxs-lookup"><span data-stu-id="7e857-111">Language</span></span>|<span data-ttu-id="7e857-112">主題</span><span class="sxs-lookup"><span data-stu-id="7e857-112">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="7e857-113">VB.NET</span><span class="sxs-lookup"><span data-stu-id="7e857-113">VB.NET</span></span>|[<span data-ttu-id="7e857-114">Runspace01 (VB.NET) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="7e857-114">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="7e857-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e857-115">See Also</span></span>

[<span data-ttu-id="7e857-116">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="7e857-116">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7e857-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7e857-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)