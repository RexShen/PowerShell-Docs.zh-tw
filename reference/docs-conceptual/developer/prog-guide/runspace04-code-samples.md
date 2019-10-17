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
ms.openlocfilehash: 2a3e7598c433027fdd96343829c0606fc7b1c37c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360157"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="f4f47-102">RunSpace04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f4f47-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="f4f47-103">以下是使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行會產生終止錯誤之腳本的運行時程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="f4f47-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="f4f47-104">主應用程式負責攔截錯誤並解讀錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="f4f47-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="f4f47-105">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，下載此執行時間的 VB.NET 原始程式檔（Runspace04）。</span><span class="sxs-lookup"><span data-stu-id="f4f47-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f4f47-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="f4f47-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="f4f47-107">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="f4f47-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="f4f47-108">如需完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="f4f47-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="f4f47-109">Language</span><span class="sxs-lookup"><span data-stu-id="f4f47-109">Language</span></span>|<span data-ttu-id="f4f47-110">主題</span><span class="sxs-lookup"><span data-stu-id="f4f47-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="f4f47-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="f4f47-111">VB.NET</span></span>|[<span data-ttu-id="f4f47-112">Runspace01 （VB.NET）程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f4f47-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="f4f47-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4f47-113">See Also</span></span>

[<span data-ttu-id="f4f47-114">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="f4f47-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f4f47-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f4f47-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)