---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace08 程式碼範例
description: RunSpace08 程式碼範例
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654230"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="4feba-103">RunSpace08 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4feba-103">RunSpace08 Code Sample</span></span>

<span data-ttu-id="4feba-104">以下是 [建立將參數新增至命令的主控台應用程式](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述之 Runspace08 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="4feba-104">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="4feba-105">這個範例應用程式會建立一個運行空間、建立管線、將兩個命令新增至管線、將兩個參數新增至第二個命令，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="4feba-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="4feba-106">新增至管線的命令為 `Get-Process` 和 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4feba-106">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4feba-107">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="4feba-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="4feba-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4feba-108">See Also</span></span>

[<span data-ttu-id="4feba-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4feba-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
