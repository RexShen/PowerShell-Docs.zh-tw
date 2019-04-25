---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085317"
---
# <a name="new-guid"></a><span data-ttu-id="9a868-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="9a868-102">New-Guid</span></span>
<span data-ttu-id="9a868-103">當您需要唯一識別碼時經常使用的指令碼 (或可能會撰寫 DSC 資源)。</span><span class="sxs-lookup"><span data-stu-id="9a868-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="9a868-104">GUID 可順暢運作，而且呼叫 .NET Framework Guid 類別很容易就能產生一個 GUID，但是對還不熟悉 .NET Framework 類別的使用者來說，使用 Cmdlet 可更容易找到 GUID︰</span><span class="sxs-lookup"><span data-stu-id="9a868-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="9a868-105">PS C:\\&gt;New-Guid</span><span class="sxs-lookup"><span data-stu-id="9a868-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="9a868-106">GUID</span><span class="sxs-lookup"><span data-stu-id="9a868-106">Guid</span></span>

----

<span data-ttu-id="9a868-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="9a868-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
