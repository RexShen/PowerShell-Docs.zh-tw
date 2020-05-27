---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSCAutomationHostEnabled 登錄機碼
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808328"
---
# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 登錄機碼

> 適用於：Windows PowerShell 5.0

DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** 下的 **DSCAutomationHostEnabled** 登錄機碼，在初始開機時啟用電腦的設定。
**DSCAutomationHostEnabled** 支援三個模式：

|  DSCAutomationHostEnabled 值  |  描述   |
|---|---|
0 | 不允許在開機時設定電腦。 |
1 | 允許在開機時設定電腦。 |
2 | 僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。 這是預設值。 |

## <a name="see-also"></a>另請參閱

如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。
