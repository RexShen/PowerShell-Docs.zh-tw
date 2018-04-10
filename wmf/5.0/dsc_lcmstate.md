---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="9ce1c-102">LCM 狀態的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="9ce1c-102">Detailed information about LCM state</span></span>

<span data-ttu-id="9ce1c-103">我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。</span><span class="sxs-lookup"><span data-stu-id="9ce1c-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="9ce1c-104">由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰</span><span class="sxs-lookup"><span data-stu-id="9ce1c-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="9ce1c-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="9ce1c-105">**Idle**</span></span>
* <span data-ttu-id="9ce1c-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="9ce1c-106">**Busy**</span></span>
* <span data-ttu-id="9ce1c-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="9ce1c-107">**PendingReboot**</span></span>
* <span data-ttu-id="9ce1c-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9ce1c-108">**PendingConfiguration**</span></span>

<span data-ttu-id="9ce1c-109">我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9ce1c-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>