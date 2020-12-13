---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample06 程式碼範例
description: AccessDbProviderSample06 程式碼範例
ms.openlocfilehash: 401aca7fab86cfbf3fa8d671eab17412dd162a88
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647488"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="dc3c1-103">AccessDbProviderSample06 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="dc3c1-103">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="dc3c1-104">下列程式碼顯示 [建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)時所述的 Windows PowerShell 內容提供者的執行。</span><span class="sxs-lookup"><span data-stu-id="dc3c1-104">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span>
<span data-ttu-id="dc3c1-105">此提供者可讓使用者運算元據存放區中專案的內容。</span><span class="sxs-lookup"><span data-stu-id="dc3c1-105">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="dc3c1-106">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件，為此提供者下載 c # 原始程式檔 (AccessDBSampleProvider06.cs) 。</span><span class="sxs-lookup"><span data-stu-id="dc3c1-106">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dc3c1-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="dc3c1-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="dc3c1-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="dc3c1-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="dc3c1-109">如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3c1-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="dc3c1-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="dc3c1-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="dc3c1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3c1-111">See Also</span></span>

[<span data-ttu-id="dc3c1-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="dc3c1-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dc3c1-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dc3c1-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
