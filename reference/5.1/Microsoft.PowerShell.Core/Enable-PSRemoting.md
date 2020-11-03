---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "93205307"
---
# Enable-PSRemoting

## 概要
設定電腦接收遠端命令。

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會設定 `Enable-PSRemoting` 電腦以接收使用 WS-Management 技術傳送的 PowerShell 遠端命令。

Windows Server 2012 上預設會啟用 PowerShell 遠端功能。 您可以使用在 `Enable-PSRemoting` 其他支援的 windows 版本上啟用 PowerShell 遠端功能，並在 Windows Server 2012 上重新啟用遠端功能（如果已停用）。

您只需在每一部將接收命令的電腦上執行此命令一次。 您不需要在只傳送命令的電腦上執行它。 因為設定會啟動接聽程式，所以最好只在需要時才執行。

從 PowerShell 3.0 開始， `Enable-PSRemoting` 當電腦位於公用網路上時，此 Cmdlet 可以在用戶端版本的 Windows 上啟用 PowerShell 遠端功能。 如需詳細資訊，請參閱 **SkipNetworkProfileCheck** 參數的描述。

此 `Enable-PSRemoting` Cmdlet 會執行下列作業：

- 執行 [>set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) Cmdlet，此 Cmdlet 會執行下列工作：
  - 啟動 WinRM 服務。
  - 將 WinRM 服務上的啟動類型設定為 [自動]。
  - 建立接聽程式，以接受有關任何 IP 位址的要求。
  - 針對 WS-Management 通訊啟用防火牆例外。
  - 註冊 **Microsoft powershell** 和 **microsoft. powershell** 會話設定（如果尚未註冊）。
  - 註冊64位電腦上的 **microsoft.powershell32** 會話設定（如果尚未登錄）。
  - 啟用所有會話設定。
  - 變更所有會話設定的安全描述項，以允許遠端存取。
- 重新開機 WinRM 服務，讓前述變更生效。

若要在 Windows 平臺上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。 這並不適用于 Linux 或 MacOS 版本的 PowerShell。

> [!CAUTION]
> 在同時具有 PowerShell 3.0 和 PowerShell 2.0 的系統上，請勿使用 PowerShell 2.0 來執行 `Enable-PSRemoting` 和 `Disable-PSRemoting` Cmdlet。 命令可能會顯示成功，但並未正確設定遠端功能。 遠端命令及稍後嘗試啟用和停用遠端處理的作業可能會失敗。

## 範例

### 範例1：設定要接收遠端命令的電腦

這個命令會設定電腦接收遠端命令。

```powershell
Enable-PSRemoting
```

### 範例2：在沒有確認提示的情況下，設定電腦接收遠端命令

這個命令會設定電腦接收遠端命令。
**Force** 參數會抑制使用者提示。

```powershell
Enable-PSRemoting -Force
```

### 範例3：允許用戶端上的遠端存取

此範例示範如何在用戶端版本的 Windows 作業系統上允許從公用網路進行遠端存取。 不同版本的 Windows 可能會有不同的防火牆規則名稱。
使用 `Get-NetFirewallRule` 以查看規則清單。 啟用防火牆規則之前，請先查看規則中的安全性設定，確認設定適用于您的環境。

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

根據預設， `Enable-PSRemoting` 會建立允許從私人和網域網路進行遠端存取的網路規則。 這個命令使用 **SkipNetworkProfileCheck** 參數，允許從同一個本機子網路中的公用網路進行遠端存取。 此命令會指定 **Force** 參數來抑制確認訊息。

**SkipNetworkProfileCheck** 參數不會影響伺服器版本的 Windows 作業系統，因此預設允許從同一個本機子網中的公用網路進行遠端存取。

`Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet 會加入防火牆規則，允許從任何遠端位置從公用網路進行遠端存取。 這包括不同子網中的位置。

> [!NOTE]
> 根據 Windows 版本而定，防火牆規則的名稱可能會不同。 使用 `Get-NetFirewallRule` Cmdlet 來列出您系統上的規則名稱。

## PARAMETERS

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

指出當電腦位於公用網路時，此 Cmdlet 會在用戶端版本的 Windows 作業系統上啟用遠端功能。 此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。

此參數不會影響伺服器版本的 Windows 作業系統，其預設會有公用網路的本機子網防火牆規則。 如果伺服器版本上的本機子網防火牆規則已停用， `Enable-PSRemoting` 不論此參數的值為何，都會重新啟用它。

若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.String

此 Cmdlet 會傳回描述其結果的字串。

## 注意

在 PowerShell 3.0 中，會 `Enable-PSRemoting` 為 WS-Management 通訊建立下列防火牆例外。

在伺服器版本的 Windows 作業系統上， `Enable-PSRemoting` 會針對允許遠端存取的私人和網域網路建立防火牆規則，並為公用網路建立防火牆規則，以允許從相同本機子網的電腦進行遠端存取。

在用戶端版本的 Windows 作業系統上， `Enable-PSRemoting` PowerShell 3.0 會為允許不受限制的遠端存取的私人和網域網路建立防火牆規則。 若要針對允許從同一個本機子網路進行遠端存取的公用網路建立防火牆規則，請使用 **SkipNetworkProfileCheck** 參數。

在用戶端或伺服器版本的 Windows 作業系統上，若要針對移除本機子網限制並允許遠端存取的公用網路建立防火牆規則，請使用 `Set-NetFirewallRule` NetSecurity 模組中的 Cmdlet 來執行下列命令： `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

在 PowerShell 2.0 中，會 `Enable-PSRemoting` 為 WS-Management 通訊建立下列防火牆例外。

在伺服器版本的 Windows 作業系統上，它會針對允許遠端存取的所有網路建立防火牆規則。

在用戶端版本的 Windows 作業系統上， `Enable-PSRemoting` PowerShell 2.0 僅針對網域和私人網路位置建立防火牆例外。 為了將安全性風險降至最低，不 `Enable-PSRemoting` 會在用戶端版本的 Windows 上建立公用網路的防火牆規則。 當目前的網路位置是公用時，會傳回 `Enable-PSRemoting` 下列訊息：無法檢查防火牆的狀態。

從 PowerShell 3.0 開始，會 `Enable-PSRemoting` 將所有會話設定的 **Enabled** 屬性值設定為，以啟用所有會話設定 `$True` 。

在 PowerShell 2.0 中， `Enable-PSRemoting` 從會話設定的安全描述項中移除 **Deny_All** 設定。 在 PowerShell 3.0 中， `Enable-PSRemoting` 移除 **Deny_All** ，並 **Network_Deny_All** 設定。 這可讓您從遠端存取保留給本機使用的會話設定。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Disable-PSRemoting](Disable-PSRemoting.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Remote](About/about_Remote.md)

[about_Session_Configurations](About/about_Session_Configurations.md)
