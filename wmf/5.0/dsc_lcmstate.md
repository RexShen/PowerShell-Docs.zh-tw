---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="b797a-102">LCM 狀態的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="b797a-102">Detailed information about LCM state</span></span>

<span data-ttu-id="b797a-103">我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。</span><span class="sxs-lookup"><span data-stu-id="b797a-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="b797a-104">由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰</span><span class="sxs-lookup"><span data-stu-id="b797a-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="b797a-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="b797a-105">**Idle**</span></span>
* <span data-ttu-id="b797a-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="b797a-106">**Busy**</span></span>
* <span data-ttu-id="b797a-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="b797a-107">**PendingReboot**</span></span>
* <span data-ttu-id="b797a-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="b797a-108">**PendingConfiguration**</span></span>

<span data-ttu-id="b797a-109">我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b797a-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

