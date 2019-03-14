---
title: AccessDbProviderSample02 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795482"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="675ff-102">AccessDbProviderSample02 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="675ff-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="675ff-103">下列程式碼顯示中所述的 Windows PowerShell 提供者的實作[建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="675ff-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="675ff-104">此實作會建立路徑，會連接到 Access 資料庫，然後移除 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="675ff-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="675ff-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 Runtime Components 這個提供者的原始程式檔 (AccessDBSampleProvider02.cs)。</span><span class="sxs-lookup"><span data-stu-id="675ff-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="675ff-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="675ff-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="675ff-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="675ff-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="675ff-108">如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="675ff-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="675ff-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="675ff-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="675ff-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="675ff-110">See Also</span></span>

[<span data-ttu-id="675ff-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="675ff-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="675ff-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="675ff-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)