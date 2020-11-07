---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 075071f83e8443d186dcc99e13fa102504dc23af
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345522"
---
# Disable-PSSessionConfiguration

## 概要
停用本機電腦上的工作階段設定。

## SYNTAX

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Disable-PSSessionConfiguration` Cmdlet 會停用本機電腦上的會話設定，以防止所有使用者使用會話設定，在本機電腦上 ( **pssession** ) 建立使用者管理的會話。 這是一個進階的 Cmdlet，專門設計給系統管理員用於管理其使用者的自訂工作階段設定。

從 PowerShell 3.0 開始，此 `Disable-PSSessionConfiguration` Cmdlet 會將會話設定的 **啟用** 設定 (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) 設定為 False。

在 PowerShell 2.0 中，此 `Disable-PSSessionConfiguration` Cmdlet 會將 **Deny_All** 專案新增至一或多個已註冊之會話設定的安全描述項。

如果沒有參數，則會 `Disable-PSSessionConfiguration` 停用 **Microsoft PowerShell** 設定，這是用於會話的預設設定。 除非使用者指定不同的設定，否則本機和遠端使用者都無法建立任何連線到電腦的工作階段。

若要停用電腦上的所有會話設定，請使用 `Disable-PSRemoting` 。

## 範例

### 範例 1：停用預設設定

此範例會停用 Microsoft PowerShell 會話設定。

```powershell
Disable-PSSessionConfiguration
```

### 範例 2︰停用所有已註冊的工作階段設定

此範例會停用電腦上所有已註冊的會話設定。

```powershell
Disable-PSSessionConfiguration -Name *
```

### 範例 3︰依名稱停用工作階段設定

此範例會停用所有名稱開頭為 Microsoft 的會話設定。 **Force** 參數會抑制 Cmdlet 中的所有使用者提示。

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### 範例 4︰使用管線停用工作階段設定

此範例會停用 **MaintenanceShell** 和 **AdminShell** 會話設定。 管線運算子 (|) 將的結果傳送 `Get-PSSessionConfiguration` 至 `Disable-PSSessionConfiguration` 。

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### 範例 5︰停用工作階段設定的效果

此範例顯示執行之前和之後的許可權 `Disable-PSSessionConfiguration` ，以及停用會話設定的影響。

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> 停用此設定並不會讓您無法使用 Cmdlet 來變更設定 `Set-PSSessionConfiguration` 。 它只會防止使用設定。

## PARAMETERS

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

### -Name

指定要停用之工作階段設定名稱的陣列。 輸入一或多個設定名稱。 允許使用萬用字元。 您也可以使用管線將包含設定名稱的字串或會話設定物件傳送至 `Disable-PSSessionConfiguration` 。

如果您省略此參數，則會 `Disable-PSSessionConfiguration` 停用 Microsoft PowerShell 會話設定。

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

用來防止重新開機 WSMan 服務。 不需要重新開機服務來停用設定。

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

若要執行此 Cmdlet，您必須使用 [ **以系統管理員身分執行** ] 選項啟動 PowerShell。

## 相關連結

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
