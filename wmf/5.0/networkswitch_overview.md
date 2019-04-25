---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085115"
---
# <a name="network-switch-management-with-powershell"></a>使用 PowerShell 管理網路交換器

**Get-NetworkSwitchEthernetPort** Cmdlet 現在會藉執行個體傳回下列其他資訊︰

- IPAddress – 與連接埠相關聯的 IP 位址
- PortMode – 連接埠模式︰存取、路由或主幹
- AccessVLAN – 在存取模式中與這個連接埠相關聯的 VLAN 識別碼
- TrunkedVLANList – 在主幹模式中與這個連接埠相關聯的VLAN 識別碼清單

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>使用 Windows PowerShell 管理基本的網路交換器

網路交換器 Cmdlet，在 WMF 5.0 中引進，可讓您將交換器、虛擬 LAN (VLAN) 和基本層級 2 網路交換器連接埠設定套用至 Windows Server 2012 R2 標誌認證的網路交換器。 Microsoft 努力不懈地支援[資料中心抽象](http://technet.microsoft.com/cloud/dal.aspx)層 (DAL) 的願景，並為我們的客戶和合作夥伴展現這個領域的價值。 使用這些 Cmdlet 可以執行︰

- 全域交換器設定，例如︰
    - 設定主機名稱
    - 設定參數橫幅
    - 保存設定
    - 啟用或停用功能

- VLAN 設定：
    - 建立或移除 VLAN
    - 啟用或停用 VLAN
    - 列舉 VLAN
    - 設定易記的 VLAN 名稱

- 階層 2 連接埠設定：
    - 列舉連接埠
    - 啟用或停用連接埠
    - 設定連接埠模式和屬性
    - 將 VLAN 加入連接埠的主幹或存取或建立關聯性

探索就從尋找所有 NetworkSwitch Cmdlet 開始！

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

詳細資訊請參閱 Jeffrey Snover 的 WMF 5.0 Preview 公告部落格文章：<http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
