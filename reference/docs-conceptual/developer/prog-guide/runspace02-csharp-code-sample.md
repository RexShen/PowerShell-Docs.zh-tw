---
title: 'Runspace02 (c # ) 程式碼範例 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 1e58f035f20baa7443d9031499062a45beae01b9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778457"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="d7b28-102">Runspace02 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d7b28-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="d7b28-103">以下是 Runspace02 範例的 c # 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="d7b28-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="d7b28-104">這個範例會使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別，以同步方式執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d7b28-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="d7b28-105">接著會使用 Windows Forms 和資料系結，在 DataGridView 控制項中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="d7b28-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="d7b28-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d7b28-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="d7b28-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b28-107">See Also</span></span>

[<span data-ttu-id="d7b28-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d7b28-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
