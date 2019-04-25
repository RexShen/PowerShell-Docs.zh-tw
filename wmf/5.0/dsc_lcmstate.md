---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085791"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="d7e79-102">LCM 狀態的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d7e79-102">Detailed information about LCM state</span></span>

<span data-ttu-id="d7e79-103">我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。</span><span class="sxs-lookup"><span data-stu-id="d7e79-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="d7e79-104">由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰</span><span class="sxs-lookup"><span data-stu-id="d7e79-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="d7e79-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="d7e79-105">**Idle**</span></span>
* <span data-ttu-id="d7e79-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="d7e79-106">**Busy**</span></span>
* <span data-ttu-id="d7e79-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="d7e79-107">**PendingReboot**</span></span>
* <span data-ttu-id="d7e79-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="d7e79-108">**PendingConfiguration**</span></span>

<span data-ttu-id="d7e79-109">我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d7e79-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
