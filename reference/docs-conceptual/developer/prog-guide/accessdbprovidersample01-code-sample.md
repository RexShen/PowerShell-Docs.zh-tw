---
title: AccessDbProviderSample01 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 22cfbc63bd369ebcb2fd8a0d0e8d1995941bbb0f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417998"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="6ce01-102">AccessDbProviderSample01 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6ce01-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="6ce01-103">下列程式碼示範如何執行[建立基本 Windows Powershell 提供者](./creating-a-basic-windows-powershell-provider.md)中所述的 Windows powershell 提供者。</span><span class="sxs-lookup"><span data-stu-id="6ce01-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="6ce01-104">此實作為提供啟動和停止提供者的方法，雖然它並未提供存取資料存放區或取得或設定資料存放區中資料的方式，但它確實提供了所有提供者所需的基本功能。</span><span class="sxs-lookup"><span data-stu-id="6ce01-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="6ce01-105">您可以使用適用C#于 windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組，下載此提供者的原始程式檔（AccessDBSampleProvider01.cs）。</span><span class="sxs-lookup"><span data-stu-id="6ce01-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6ce01-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="6ce01-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6ce01-107">下載的來源檔案可在 **\<PowerShell 範例 >** 目錄中取得。</span><span class="sxs-lookup"><span data-stu-id="6ce01-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="6ce01-108">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6ce01-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="6ce01-109">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="6ce01-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="6ce01-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ce01-110">See Also</span></span>

[<span data-ttu-id="6ce01-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="6ce01-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6ce01-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6ce01-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
