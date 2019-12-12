---
title: RunSpace08 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366477"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="5a7de-102">RunSpace08 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="5a7de-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="5a7de-103">以下是[建立可將參數新增至命令的主控台應用程式](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述之 Runspace08 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a7de-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="5a7de-104">這個範例應用程式會建立一個執行空間、建立管線、將兩個命令新增至管線、將兩個參數新增至第二個命令，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="5a7de-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="5a7de-105">新增至管線的命令是 `Get-Process` 和 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a7de-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a7de-106">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5a7de-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="5a7de-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a7de-107">See Also</span></span>

[<span data-ttu-id="5a7de-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5a7de-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
