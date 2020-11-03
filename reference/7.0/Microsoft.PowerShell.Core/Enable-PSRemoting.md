---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: f74fe88cfb1d89e2f21d3f85e5c604d75f8ac55d
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "93205303"
---
# Enable-PSRemoting

## 概要
設定電腦接收遠端命令。

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會設定 `Enable-PSRemoting` 電腦以接收使用 WS-Management 技術傳送的 PowerShell 遠端命令。 目前只有在 Windows 平臺上才支援以 WS-Management 為基礎的 PowerShell 遠端處理。

預設會在 Windows Server 平臺上啟用 PowerShell 遠端功能。 您可以使用在 `Enable-PSRemoting` 其他支援的 Windows 版本上啟用 PowerShell 遠端功能，並在停用時重新啟用遠端功能。

您只需在每一部將接收命令的電腦上執行此命令一次。 您不需要在只傳送命令的電腦上執行它。 由於設定會啟動接聽程式以接受遠端連線，因此最好只在需要時才執行。

當電腦位於公用網路上時，通常不允許在用戶端版本的 Windows 上啟用 PowerShell 遠端功能，但您可以使用 **SkipNetworkProfileCheck** 參數略過這項限制。 如需詳細資訊，請參閱 **SkipNetworkProfileCheck** 參數的描述。

多個 PowerShell 安裝可以並存存在於單一電腦上。 `Enable-PSRemoting`執行會針對您在中執行 Cmdlet 的特定安裝版本，設定遠端端點。 因此，如果您在執行 `Enable-PSRemoting` powershell 6.2 時執行，將會設定執行 powershell 6.2 的遠端端點。 如果您在執行 `Enable-PSRemoting` powershell 7-preview 時執行，將會設定執行 powershell 7-preview 的遠端端點。

`Enable-PSRemoting` 視需要建立兩個遠端端點設定。 如果端點設定已經存在，則只會確保已啟用。 建立的設定完全相同，但有不同的名稱。 其中一個會有一個簡單的名稱，對應至裝載會話的 PowerShell 版本。 另一個設定名稱包含裝載會話之 PowerShell 版本的詳細資訊。 例如， `Enable-PSRemoting` 在 PowerShell 6.2 中執行時，您會取得名為 **6.2.2** 的 **PowerShell.6** 兩個已設定端點。
這可讓您使用簡單名稱 **powershell** 來建立最新 powershell 6 主機版本的連接。 或者，您可以使用較長的 **6.2.2** 名稱來連接到特定的 powershell 主機版本。

若要使用新啟用的遠端端點，您必須在使用 **ConfigurationName** `Invoke-Command` 、 `New-PSSession` 、Cmdlet 建立遠端連線時，使用 ConfigurationName 參數來指定它們 `Enter-PSSession` 。 如需詳細資訊，請參閱範例4。

此 `Enable-PSRemoting` Cmdlet 會執行下列作業：

- 執行 [>set-wsmanquickconfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) Cmdlet，此 Cmdlet 會執行下列工作：
  - 啟動 WinRM 服務。
  - 將 WinRM 服務上的啟動類型設定為 [自動]。
  - 建立接聽程式，以接受有關任何 IP 位址的要求。
  - 針對 WS-Management 通訊啟用防火牆例外。
  - 視需要建立簡單和完整名稱交談端點設定。
  - 啟用所有會話設定。
  - 變更所有會話設定的安全描述項，以允許遠端存取。
- 重新開機 WinRM 服務，讓前述變更生效。

若要在 Windows 平臺上執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。 Linux 或 MacOS 版本的 PowerShell 無法使用此 Cmdlet。

> [!CAUTION]
> 此 Cmdlet 不會影響 Windows PowerShell 所建立的遠端端點設定。
> 它只會影響以 PowerShell 第6版和更新版本建立的端點。 若要啟用和停用 Windows PowerShell 所裝載的 PowerShell 遠端端點，請 `Enable-PSRemoting` 從 Windows PowerShell 會話內執行 Cmdlet。

## 範例

### 範例1：設定要接收遠端命令的電腦

這個命令會設定電腦接收遠端命令。

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### 範例2：在沒有確認提示的情況下，設定電腦接收遠端命令

這個命令會設定電腦接收遠端命令。
**Force** 參數會抑制使用者提示。

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
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

### 範例4：建立新啟用端點設定的遠端會話

此範例說明如何在電腦上啟用 PowerShell 遠端功能、尋找已設定的端點名稱，以及建立指向其中一個端點的遠端會話。

第一個命令會在電腦上啟用 PowerShell 遠端功能。

第二個命令會列出端點設定。

第三個命令會在同一部電腦上建立遠端 PowerShell 會話，並依名稱指定 **PowerShell 6** 端點。 遠端會話將使用最新的 PowerShell 6 版 (6.2.2) 來裝載。

最後一個命令會存取 `$PSVersionTable` 遠端會話中的變數，以顯示裝載會話的 PowerShell 版本。

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

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

在伺服器版本的 Windows 作業系統上， `Enable-PSRemoting` 會針對允許遠端存取的私人和網域網路建立防火牆規則，並為公用網路建立防火牆規則，以允許從相同本機子網的電腦進行遠端存取。

在用戶端版本的 Windows 作業系統上， `Enable-PSRemoting` 會針對允許不受限制的遠端存取的私人和網域網路建立防火牆規則。 若要針對允許從同一個本機子網路進行遠端存取的公用網路建立防火牆規則，請使用 **SkipNetworkProfileCheck** 參數。

在用戶端或伺服器版本的 Windows 作業系統上，若要針對移除本機子網限制並允許遠端存取的公用網路建立防火牆規則，請使用 `Set-NetFirewallRule` NetSecurity 模組中的 Cmdlet 來執行下列命令： `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

`Enable-PSRemoting` 藉由將所有會話設定的 **Enabled** 屬性值設定為，以啟用所有會話設定 `$True` 。

`Enable-PSRemoting` 移除 **Deny_All** 並 **Network_Deny_All** 設定。 這可讓您從遠端存取保留給本機使用的會話設定。

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
