---
title: AccessDbProviderSample01 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081983"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="110dc-102">AccessDbProviderSample01 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="110dc-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="110dc-103">下列程式碼顯示中所述的 Windows PowerShell 提供者的實作[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="110dc-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="110dc-104">這個實作提供方法來啟動和停止提供者，雖然它不會提供方法來存取資料存放區，或取得或設定資料存放區中的資料，但是它提供基本功能所需的所有提供者。</span><span class="sxs-lookup"><span data-stu-id="110dc-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="110dc-105">您可以下載C#此提供者所使用的 Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的原始程式檔 (AccessDBSampleProvider01.cs)。</span><span class="sxs-lookup"><span data-stu-id="110dc-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="110dc-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="110dc-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="110dc-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="110dc-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="110dc-108">如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="110dc-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="110dc-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="110dc-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="110dc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="110dc-110">See Also</span></span>

[<span data-ttu-id="110dc-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="110dc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="110dc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="110dc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)