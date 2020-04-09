---
title: RunSpace09 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: d7fa39485eea833483682c91c96417a76e5d770f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977534"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="78985-102">RunSpace09 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="78985-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="78985-103">以下是[建立可非同步叫用管線之主控台應用程式](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)中所述 Runspace09 範例的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="78985-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="78985-104">這個範例應用程式會建立並開啟一個運行時、建立和非同步叫用管線，然後使用管線事件以非同步方式處理腳本。</span><span class="sxs-lookup"><span data-stu-id="78985-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="78985-105">此應用程式所執行的腳本會在0.5 秒的間隔（500毫秒）內建立整數1到10。</span><span class="sxs-lookup"><span data-stu-id="78985-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="78985-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="78985-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="78985-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78985-107">See Also</span></span>

[<span data-ttu-id="78985-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="78985-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
