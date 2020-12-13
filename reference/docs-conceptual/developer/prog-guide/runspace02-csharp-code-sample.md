---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace02 (C#) 程式碼範例
description: Runspace02 (C#) 程式碼範例
ms.openlocfilehash: 9e2c0cf37d1bf12a92f4fbf781928c0241202915
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647437"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="b1218-103">Runspace02 (C#) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b1218-103">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="b1218-104">以下是 Runspace02 範例的 c # 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1218-104">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="b1218-105">此範例使用 [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 類別來同步執行 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b1218-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="b1218-106">然後使用 Windows Forms 和資料系結，在 DataGridView 控制項中顯示結果</span><span class="sxs-lookup"><span data-stu-id="b1218-106">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="b1218-107">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="b1218-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="b1218-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1218-108">See Also</span></span>

[<span data-ttu-id="b1218-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b1218-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
