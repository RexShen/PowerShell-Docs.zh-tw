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
<a id="detailed-information-about-lcm-state" class="xliff"></a>
# LCM 狀態的詳細資訊

我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。 由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。

