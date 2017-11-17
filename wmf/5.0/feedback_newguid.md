---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a><span data-ttu-id="f712e-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="f712e-102">New-Guid</span></span>
<span data-ttu-id="f712e-103">當您需要唯一識別碼時經常使用的指令碼 (或可能會撰寫 DSC 資源)。</span><span class="sxs-lookup"><span data-stu-id="f712e-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="f712e-104">GUID 可順暢運作，而且呼叫 .NET Framework Guid 類別很容易就能產生一個 GUID，但是對還不熟悉 .NET Framework 類別的使用者來說，使用 Cmdlet 可更容易找到 GUID︰</span><span class="sxs-lookup"><span data-stu-id="f712e-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="f712e-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="f712e-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="f712e-106">GUID</span><span class="sxs-lookup"><span data-stu-id="f712e-106">Guid</span></span>

----

<span data-ttu-id="f712e-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="f712e-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>

