---
title: RunSpace05 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429562"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="d7b48-102">RunSpace05 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d7b48-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="d7b48-103">以下是 Runspace05 範例中所述的原始程式碼[設定 Runspace 使用 RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)。</span><span class="sxs-lookup"><span data-stu-id="d7b48-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="d7b48-104">此範例示範如何建立 runspace 的組態資訊、 建立 runspace，建立具有單一命令的管線，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="d7b48-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="d7b48-105">執行此命令為`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d7b48-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d7b48-106">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (runspace05.cs)。</span><span class="sxs-lookup"><span data-stu-id="d7b48-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d7b48-107">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="d7b48-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d7b48-108">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="d7b48-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d7b48-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d7b48-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="d7b48-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b48-110">See Also</span></span>

[<span data-ttu-id="d7b48-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="d7b48-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d7b48-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d7b48-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)