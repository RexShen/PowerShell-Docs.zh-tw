---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e8bc5bc248eafe479f366397aa947845e94e190c
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206203"
---
# Set-WSManQuickConfig

## 概要
針對遠端管理設定本機電腦。

## SYNTAX

### 全部

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會設定 `Set-WSManQuickConfig` 電腦，以接收使用 Web Services For management (ws-management) 技術傳送的 PowerShell 遠端命令。

`Set-WSManQuickConfig` 會執行下列動作：

- 檢查 WinRM 服務是否正在執行。 如果 WinRM 服務未執行，則會啟動服務。
- 將 WinRM 服務的啟動類型設定為自動。
- 建立接聽程式，以接受有關任何 IP 位址的要求。 預設傳輸為 **HTTP** 。
- 為 WinRM 流量啟用防火牆例外。

若要執行 `Set-WSManQuickConfig` ，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

## 範例

### 範例 1︰透過 HTTP 啟用本機電腦的遠端管理

此範例會設定必要的設定，以啟用本機電腦的遠端系統管理。 根據預設，此命令會在 **HTTP** 上建立 WS-Management 接聽程式。

```powershell
Set-WSManQuickConfig
```

### 範例 2︰透過 HTTPS 啟用本機電腦的遠端管理

此範例會設定必要的設定，以啟用本機電腦的遠端系統管理。 **UseSSL** 參數會指定使用 **HTTPS** 來與電腦通訊。

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> **HTTPS** 需要手動設定。 如需詳細資訊，請參閱 **UseSSL** 參數的描述。

## PARAMETERS

### -Force

強制執行命令而不要求使用者確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

當電腦位於公用網路時，設定 Windows 用戶端版本進行遠端處理。 此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。

此參數不會影響 Windows server 版本，預設為具有公用網路的本機子網防火牆規則。 如果伺服器版本的 Windows 上已停用本機子網防火牆規則， `Enable-PSRemoting` 則不論此參數的值為何，都會重新啟用它。

若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` **NetSecurity** 模組中的 Cmdlet。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。 預設不會使用 SSL。

WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。 **UseSSL** 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。 如果您使用此參數，而且在用於連線的埠上無法使用 SSL，則命令會失敗。

**HTTPS** 需要手動設定 WinRM 和防火牆規則。 如需詳細資訊，請參閱 how [To：設定 WINRM FOR HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

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

此 Cmdlet 不接受任何輸入。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-PSRemoting](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[如何：為 HTTPS 設定 WINRM](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Test-WSMan](Test-WSMan.md)
