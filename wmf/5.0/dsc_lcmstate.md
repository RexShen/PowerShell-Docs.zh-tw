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
# <a name="detailed-information-about-lcm-state"></a>LCM 狀態的詳細資訊

我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。 由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。