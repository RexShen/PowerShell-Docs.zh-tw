---
title: RunSpace10 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 976df6c36a5f95d17a76dcd31d287a3f064eff24
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784651"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="ea283-102">RunSpace10 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ea283-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="ea283-103">以下是 Runspace10 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea283-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="ea283-104">這個範例應用程式會將 Cmdlet 新增至[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後使用修改過的設定資訊來建立執行時間。</span><span class="sxs-lookup"><span data-stu-id="ea283-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="ea283-105">您可以使用適用于 Windows Vista 和 Microsoft .NET Framework 3.0 執行時間元件的 Windows 軟體發展工具組， (runspace10.cs) 下載 c # 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ea283-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ea283-106">如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ea283-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ea283-107">下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="ea283-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ea283-108">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="ea283-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs" range="11-118":::

## <a name="see-also"></a><span data-ttu-id="ea283-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea283-109">See Also</span></span>

[<span data-ttu-id="ea283-110">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="ea283-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ea283-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ea283-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
