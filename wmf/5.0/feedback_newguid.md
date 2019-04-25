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
# <a name="new-guid"></a>New-Guid
當您需要唯一識別碼時經常使用的指令碼 (或可能會撰寫 DSC 資源)。 GUID 可順暢運作，而且呼叫 .NET Framework Guid 類別很容易就能產生一個 GUID，但是對還不熟悉 .NET Framework 類別的使用者來說，使用 Cmdlet 可更容易找到 GUID︰

PS C:\\&gt;New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
