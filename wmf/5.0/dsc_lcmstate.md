---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219856"
---
# <a name="detailed-information-about-lcm-state"></a>LCM 狀態的詳細資訊

我們在公開有關 LCM 狀態詳細資料的方面上進行了改善。 由 Get-DscLocalConfigurationManager 傳回的 LCMState 現在可包含下列值︰

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

我們也加入了 LCMStateDetail 屬性，其中包含狀態的詳細資訊。
