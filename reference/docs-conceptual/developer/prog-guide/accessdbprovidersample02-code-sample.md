---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample02 程式碼範例
description: AccessDbProviderSample02 程式碼範例
ms.openlocfilehash: f467ee59b36027e80852ae1f7b2f1af5c9aa8569
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659402"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="f0406-103">AccessDbProviderSample02 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f0406-103">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="f0406-104">下列程式碼顯示 [建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)時所述的 Windows PowerShell 提供者的執行。</span><span class="sxs-lookup"><span data-stu-id="f0406-104">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="f0406-105">這種執行會建立路徑、連接到 Access 資料庫，然後再移除該磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="f0406-105">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="f0406-106">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體開發套件，下載此提供者的 c # 原始程式檔 (AccessDBSampleProvider02.cs) 。</span><span class="sxs-lookup"><span data-stu-id="f0406-106">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f0406-107">如需下載指示，請參閱 [如何安裝 Windows PowerShell 及下載 WINDOWS POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="f0406-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="f0406-108">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="f0406-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="f0406-109">如需其他 Windows PowerShell 提供者實現的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="f0406-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="f0406-110">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f0406-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="f0406-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0406-111">See Also</span></span>

[<span data-ttu-id="f0406-112">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="f0406-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f0406-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f0406-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
