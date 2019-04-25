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
# <a name="detailed-information-about-lcm-state"></a>LCM 狀態的詳細資訊

我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。 由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。
