---
title: RunSpace10 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429579"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="ca67c-102">RunSpace10 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ca67c-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="ca67c-103">以下是 Runspace10 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ca67c-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="ca67c-104">此範例應用程式新增到 cmdlet [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後建立 runspace 中使用修改過的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="ca67c-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="ca67c-105">您可以下載C#使用的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (runspace10.cs)。</span><span class="sxs-lookup"><span data-stu-id="ca67c-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ca67c-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ca67c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ca67c-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="ca67c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ca67c-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ca67c-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="ca67c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca67c-109">See Also</span></span>

[<span data-ttu-id="ca67c-110">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="ca67c-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ca67c-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ca67c-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)