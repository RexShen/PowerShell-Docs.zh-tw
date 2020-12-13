---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace09 程式碼範例
description: RunSpace09 程式碼範例
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654200"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="c7285-103">RunSpace09 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c7285-103">RunSpace09 Code Sample</span></span>

<span data-ttu-id="c7285-104">以下是 [建立以非同步方式叫用管線的主控台應用程式](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)中所述之 Runspace09 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7285-104">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="c7285-105">這個範例應用程式會建立並開啟運行空間、建立和非同步叫用管線，然後使用管線事件以非同步方式處理腳本。</span><span class="sxs-lookup"><span data-stu-id="c7285-105">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="c7285-106">此應用程式所執行的腳本會在0.5 秒的間隔內建立整數1到10， (500 ms) 。</span><span class="sxs-lookup"><span data-stu-id="c7285-106">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="c7285-107">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="c7285-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="c7285-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7285-108">See Also</span></span>

[<span data-ttu-id="c7285-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c7285-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
