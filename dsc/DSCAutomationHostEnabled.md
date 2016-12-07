
---
標題：DSCAutomationHostEnabled 登錄金鑰 ms.date:  2016-05-16 關鍵字： powershell,DSC 描述：  
ms.topic:  article author:  eslesar manager:  dongill ms.prod:  powershell
---

>適用對象：Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>DSCAutomationHostEnabled 登錄機碼

DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies ** 下的 **DSCAutomationHostEnabled** 登錄機碼在初始開機時自動設定電腦。
DSCAutomationHostEnabled 支援三種模式︰

|  DSCAutomationHostEnabled 值  |  描述   | 
|---|---| 
0 | 不允許在開機時設定電腦。 |
1 | 允許在開機時設定電腦。 |
2 | 僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。 這是預設值。 |

## <a name="see-also"></a>另請參閱

如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。


