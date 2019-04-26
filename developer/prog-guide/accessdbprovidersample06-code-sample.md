---
title: AccessDbProviderSample06 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081932"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="ccd7b-102">AccessDbProviderSample06 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ccd7b-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="ccd7b-103">下列程式碼顯示的內容提供者中所述的 Windows PowerShell 實作[建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd7b-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="ccd7b-104">此提供者可讓使用者管理的資料存放區中的項目內容。</span><span class="sxs-lookup"><span data-stu-id="ccd7b-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd7b-105">您可以下載C#使用 Microsoft Windows 軟體開發套件的 Windows Vista 和 Microsoft.NET Framework 3.0 執行階段元件的這個提供者的原始程式檔 (AccessDBSampleProvider06.cs)。</span><span class="sxs-lookup"><span data-stu-id="ccd7b-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ccd7b-106">如需下載指示，請參閱[如何安裝 Windows PowerShell 並下載 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ccd7b-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ccd7b-107">已下載的原始程式檔位於 **\<PowerShell 範例 >** 目錄。</span><span class="sxs-lookup"><span data-stu-id="ccd7b-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="ccd7b-108">如需有關其他 Windows PowerShell 提供者實作的詳細資訊，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="ccd7b-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="ccd7b-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ccd7b-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="ccd7b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccd7b-110">See Also</span></span>

[<span data-ttu-id="ccd7b-111">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="ccd7b-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ccd7b-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ccd7b-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)