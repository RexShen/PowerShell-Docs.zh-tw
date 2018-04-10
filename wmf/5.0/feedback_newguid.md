---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="10028-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="10028-102">New-Guid</span></span>
<span data-ttu-id="10028-103">當您需要唯一識別碼時經常使用的指令碼 (或可能會撰寫 DSC 資源)。</span><span class="sxs-lookup"><span data-stu-id="10028-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="10028-104">GUID 可順暢運作，而且呼叫 .NET Framework Guid 類別很容易就能產生一個 GUID，但是對還不熟悉 .NET Framework 類別的使用者來說，使用 Cmdlet 可更容易找到 GUID︰</span><span class="sxs-lookup"><span data-stu-id="10028-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="10028-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="10028-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="10028-106">GUID</span><span class="sxs-lookup"><span data-stu-id="10028-106">Guid</span></span>

----

<span data-ttu-id="10028-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="10028-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>