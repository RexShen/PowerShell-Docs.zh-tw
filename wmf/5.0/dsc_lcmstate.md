---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="90639-102">LCM 狀態的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="90639-102">Detailed information about LCM state</span></span>

<span data-ttu-id="90639-103">我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。</span><span class="sxs-lookup"><span data-stu-id="90639-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="90639-104">由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰</span><span class="sxs-lookup"><span data-stu-id="90639-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="90639-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="90639-105">**Idle**</span></span>
* <span data-ttu-id="90639-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="90639-106">**Busy**</span></span>
* <span data-ttu-id="90639-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="90639-107">**PendingReboot**</span></span>
* <span data-ttu-id="90639-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="90639-108">**PendingConfiguration**</span></span>

<span data-ttu-id="90639-109">我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="90639-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
