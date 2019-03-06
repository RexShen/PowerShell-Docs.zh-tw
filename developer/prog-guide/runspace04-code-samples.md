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
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429460"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="e26dd-102">RunSpace04 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e26dd-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="e26dd-103">如下的程式碼範例會使用的 runspace [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行指令碼會產生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e26dd-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="e26dd-104">主應用程式負責攔截錯誤和解譯記錄時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e26dd-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="e26dd-105">您可以下載的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件使用此 runspace VB.NET 原始程式檔 (Runspace04.vb)。</span><span class="sxs-lookup"><span data-stu-id="e26dd-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e26dd-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="e26dd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e26dd-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="e26dd-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="e26dd-108">完整的範例程式碼，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="e26dd-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="e26dd-109">語言</span><span class="sxs-lookup"><span data-stu-id="e26dd-109">Language</span></span>|<span data-ttu-id="e26dd-110">主題</span><span class="sxs-lookup"><span data-stu-id="e26dd-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="e26dd-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="e26dd-111">VB.NET</span></span>|[<span data-ttu-id="e26dd-112">Runspace01 (VB.NET) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="e26dd-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="e26dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e26dd-113">See Also</span></span>

[<span data-ttu-id="e26dd-114">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="e26dd-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e26dd-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e26dd-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)