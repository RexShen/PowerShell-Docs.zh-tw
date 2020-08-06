---
title: RunSpace08 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67172a0f8d6daf2f5b9965d1a18f7698daddbe1a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784685"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="40e3c-102">RunSpace08 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="40e3c-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="40e3c-103">以下是[建立可將參數新增至命令的主控台應用程式](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述之 Runspace08 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="40e3c-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="40e3c-104">這個範例應用程式會建立一個執行空間、建立管線、將兩個命令新增至管線、將兩個參數新增至第二個命令，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="40e3c-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="40e3c-105">新增至管線的命令是 `Get-Process` 和 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40e3c-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="40e3c-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="40e3c-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="40e3c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40e3c-107">See Also</span></span>

[<span data-ttu-id="40e3c-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="40e3c-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
