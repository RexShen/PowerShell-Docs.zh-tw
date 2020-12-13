---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample01 程式碼範例
description: AccessDbProviderSample01 程式碼範例
ms.openlocfilehash: 5be593b9e86347b2f55de156fe4d9b44cfab5b78
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659406"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="412a8-103">AccessDbProviderSample01 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="412a8-103">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="412a8-104">下列程式碼顯示 [建立基本 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)中所述之 Windows PowerShell 提供者的執行。</span><span class="sxs-lookup"><span data-stu-id="412a8-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="412a8-105">這項實行提供啟動和停止提供者的方法，雖然它不提供存取資料存放區的方法，或是在資料存放區中取得或設定資料，但它確實提供了所有提供者所需的基本功能。</span><span class="sxs-lookup"><span data-stu-id="412a8-105">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="412a8-106">您可以使用 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體開發套件，下載此提供者 (AccessDBSampleProvider01.cs) 的 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="412a8-106">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="412a8-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="412a8-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="412a8-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="412a8-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="412a8-109">如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="412a8-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="412a8-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="412a8-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="412a8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="412a8-111">See Also</span></span>

[<span data-ttu-id="412a8-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="412a8-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="412a8-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="412a8-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
