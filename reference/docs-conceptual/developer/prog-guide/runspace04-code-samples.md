---
title: RunSpace04 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9a9b7e02358cdf9018199046c938c699aff8681c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787055"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="d76d9-102">RunSpace04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d76d9-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="d76d9-103">以下是使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行會產生終止錯誤之腳本的運行時程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d76d9-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="d76d9-104">主應用程式負責攔截錯誤並解讀錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="d76d9-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="d76d9-105">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，下載此執行時間的 VB.NET 原始程式檔 (Runspace04) 。</span><span class="sxs-lookup"><span data-stu-id="d76d9-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d76d9-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="d76d9-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d76d9-107">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="d76d9-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="d76d9-108">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="d76d9-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="d76d9-109">語言</span><span class="sxs-lookup"><span data-stu-id="d76d9-109">Language</span></span>|<span data-ttu-id="d76d9-110">主題</span><span class="sxs-lookup"><span data-stu-id="d76d9-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="d76d9-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="d76d9-111">VB.NET</span></span>|[<span data-ttu-id="d76d9-112">Runspace01 (VB.NET) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d76d9-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="d76d9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d76d9-113">See Also</span></span>

[<span data-ttu-id="d76d9-114">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="d76d9-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d76d9-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d76d9-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
