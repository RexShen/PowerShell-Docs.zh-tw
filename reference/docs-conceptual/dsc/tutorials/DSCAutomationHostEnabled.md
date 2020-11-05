---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSCAutomationHostEnabled 登錄機碼
description: 此文章定義可在 DSCAutomationHostEnabled 登錄機碼中設定的值
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656189"
---
# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 登錄機碼

> 適用於：Windows PowerShell 5.0

DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** 下的 **DSCAutomationHostEnabled** 登錄機碼，在初始開機時啟用電腦的設定。 **DSCAutomationHostEnabled** 支援三個模式：

| DSCAutomationHostEnabled 值 |                                              描述                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 0                              | 不允許在開機時設定電腦。                                                           |
| 1                              | 允許在開機時設定電腦。                                                            |
| 2                              | 僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。 這是預設值。 |

## <a name="see-also"></a>另請參閱

如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。
