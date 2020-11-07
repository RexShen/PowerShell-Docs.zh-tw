---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 5bc167bdffee4ae7f75d4c18e31110d9291cc53e
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342190"
---
# Enable-PSSessionConfiguration

## 概要
啟用本機電腦上的工作階段設定。

## SYNTAX

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Enable-PSSessionConfiguration`Cmdlet 會啟用已停用的已註冊會話設定，例如使用 `Disable-PSSessionConfiguration` 或 `Disable-PSRemoting` Cmdlet，或的 **AccessMode** 參數 `Register-PSSessionConfiguration` 。 這是一個進階的 Cmdlet，專門設計給系統管理員用於管理其使用者的自訂工作階段設定。

如果沒有參數，則會 `Enable-PSSessionConfiguration` 啟用 **Microsoft PowerShell** 設定，這是用於會話的預設設定。

`Enable-PSSessionConfiguration` 從受影響之會話設定的安全描述項中移除 **Deny_All** 設定、開啟接受任何 IP 位址要求的接聽程式，然後重新開機 WinRM 服務。 從 PowerShell 3.0 開始， `Enable-PSSessionConfiguration` 也會將會話設定的 **Enabled** 屬性值 (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) 設定為 True。 但是，不 `Enable-PSSessionConfiguration` 會移除或變更 **Network_Deny_All** (`AccessMode=Local`) 安全描述項設定，只允許本機電腦的使用者使用會話設定。

## 範例

### 範例1：重新啟用預設會話

此範例會重新啟用電腦上的 **Microsoft PowerShell** 預設會話設定。

```powershell
Enable-PSSessionConfiguration
```

### 範例2：重新啟用指定的會話

此範例會重新啟用電腦上的 **MaintenanceShell** 和 **AdminShell** 會話設定。

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### 範例3：重新啟用所有會話

此範例會重新啟用電腦上的所有會話設定。 這些命令是相等的。
因此，您可以使用其中一種。

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

`Enable-PSSessionConfiguration` 如果您啟用已經啟用的會話設定，則不會產生錯誤。

### 範例4：重新啟用會話，並指定新的安全描述項

此範例會重新啟用 **MaintenanceShell** 會話設定，並為設定指定新的安全描述項。

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## PARAMETERS

### -Force

指出 Cmdlet 不會提示您進行確認，並會在不提示的情況下重新啟動 WinRM 服務。 重新啟動服務可讓設定變更生效。

若要避免重新啟動並抑制重新啟動提示，請使用 **NoServiceRestart** 參數。

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

### -Name

指定要啟用之工作階段設定的名稱。 輸入一或多個設定名稱。
允許使用萬用字元。

您也可以使用管線將包含設定名稱的字串或會話設定物件傳送至 `Enable-PSSessionConfiguration` 。

如果您省略此參數，則會 `Enable-PSSessionConfiguration` 啟用 **Microsoft PowerShell** 會話設定。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NoServiceRestart

指出 Cmdlet 不會重新開機服務。

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

### -SecurityDescriptorSddl

指定此 Cmdlet 用來取代會話設定之安全描述項的安全描述項。

如果您省略此參數，則 `Enable-PSSessionConfiguration` 只會從安全描述項中刪除 [拒絕所有專案]。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipNetworkProfileCheck

指出當電腦位於公用網路時，此 Cmdlet 會啟用會話設定。 此參數會針對公用網路啟用防火牆規則，以便只允許從位於相同本機子網路的電腦進行遠端存取。 依預設， `Enable-PSSessionConfiguration` 在公用網路上會失敗。

此參數是針對用戶端版本的 Windows 作業系統所設計。 伺服器版本的 Windows 作業系統具有公用網路的本機子網防火牆規則。 但是，如果在伺服器版本的 Windows 作業系統上停用本機子網防火牆規則，此參數便會重新啟用。

若要移除本機子網限制，並允許從公用網路上的所有位置進行遠端存取，請使用 `Set-NetFirewallRule` NetSecurity 模組中的 Cmdlet。 如需詳細資訊，請參閱`Enable-PSRemoting`。

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

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration、System.String

您可以使用管線將工作階段設定物件或包含工作階段設定名稱的字串傳送至此 Cmdlet。

## 輸出

### None

此 Cmdlet 不會傳回任何物件。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

若要使用此 Cmdlet，您必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
