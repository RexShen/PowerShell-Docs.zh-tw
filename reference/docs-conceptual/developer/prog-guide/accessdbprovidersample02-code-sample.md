---
title: AccessDbProviderSample02 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 122fc8ec4fc4388cca01f1a7e5014fa875506bb7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360527"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="8dcbb-102">AccessDbProviderSample02 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8dcbb-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="8dcbb-103">下列程式碼示範如何執行[建立 Windows Powershell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)中所述的 windows powershell 提供者。</span><span class="sxs-lookup"><span data-stu-id="8dcbb-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="8dcbb-104">此執行會建立路徑、連接到 Access 資料庫，然後移除磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="8dcbb-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="8dcbb-105">您可以使用適用C#于 Windows Vista 和 microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider02.cs）。</span><span class="sxs-lookup"><span data-stu-id="8dcbb-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8dcbb-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="8dcbb-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="8dcbb-107">下載的來源檔案可在 **@no__t 1PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="8dcbb-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="8dcbb-108">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="8dcbb-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="8dcbb-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="8dcbb-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="8dcbb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dcbb-110">See Also</span></span>

[<span data-ttu-id="8dcbb-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="8dcbb-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8dcbb-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8dcbb-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
