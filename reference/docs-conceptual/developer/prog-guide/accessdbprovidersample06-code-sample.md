---
title: AccessDbProviderSample06 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f650648320a0a31324af1bd1a112f01bdfc6c599
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787235"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="03d22-102">AccessDbProviderSample06 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="03d22-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="03d22-103">下列程式碼示範如何執行[建立 Windows Powershell 內容提供者](./creating-a-windows-powershell-content-provider.md)中所述的 windows powershell 內容提供者。</span><span class="sxs-lookup"><span data-stu-id="03d22-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span>
<span data-ttu-id="03d22-104">此提供者可讓使用者運算元據存放區中的專案內容。</span><span class="sxs-lookup"><span data-stu-id="03d22-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="03d22-105">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為此提供者下載 c # 原始程式檔 (AccessDBSampleProvider06.cs) 。</span><span class="sxs-lookup"><span data-stu-id="03d22-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="03d22-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="03d22-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="03d22-107">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="03d22-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="03d22-108">如需其他 Windows PowerShell 提供者執行的詳細資訊，請參閱[設計您的 Windows Powershell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="03d22-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="03d22-109">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="03d22-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="03d22-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03d22-110">See Also</span></span>

[<span data-ttu-id="03d22-111">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="03d22-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="03d22-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="03d22-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
