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
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734908"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="85fe7-102">RunSpace08 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="85fe7-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="85fe7-103">以下是原始程式碼，Runspace08 範例中所述[建立主控台應用程式，將命令參數](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)。</span><span class="sxs-lookup"><span data-stu-id="85fe7-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span> <span data-ttu-id="85fe7-104">此範例應用程式建立 runspace，會建立管線，將兩個命令新增至管線，將兩個參數加入至第二個命令中，，然後執行管線。</span><span class="sxs-lookup"><span data-stu-id="85fe7-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="85fe7-105">新增至管線的命令都`Get-Process`和`Sort-Object`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="85fe7-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="85fe7-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="85fe7-106">Code Sample</span></span>

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a><span data-ttu-id="85fe7-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85fe7-107">See Also</span></span>

[<span data-ttu-id="85fe7-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="85fe7-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)