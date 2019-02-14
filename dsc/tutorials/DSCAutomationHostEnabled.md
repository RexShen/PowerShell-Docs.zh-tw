---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSCAutomationHostEnabled 登錄機碼
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676682"
---
>適用對象：Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 登錄機碼

使用 DSC **DSCAutomationHostEnabled**登錄機碼下的**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System**啟用初始的機器組態啟動。
**DSCAutomationHostEnabled** 支援三個模式：

|  DSCAutomationHostEnabled 值  |  描述   |
|---|---|
0 | 不允許在開機時設定電腦。 |
1 | 允許在開機時設定電腦。 |
2 | 僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。 這是預設值。 |

## <a name="see-also"></a>另請參閱

如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。
