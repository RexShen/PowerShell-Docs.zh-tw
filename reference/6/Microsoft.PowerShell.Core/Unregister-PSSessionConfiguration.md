---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: f9cc2f83ec0fca1c957c670e13ac7b455c322adb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345336"
---
# Unregister-PSSessionConfiguration

## 概要
從電腦刪除已註冊的工作階段設定。

## SYNTAX

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Unregister-PSSessionConfiguration`Cmdlet 會從電腦刪除已註冊的會話設定。 此 Cmdlet 是專為系統管理員管理使用者的自訂會話設定而設計的。

若要讓變更生效，請 `Unregister-PSSessionConfiguration` 重新開機 **WinRM** 服務。 若要防止重新啟動，請指定 **NoServiceRestart** 參數。

如果您不小心 **刪除預設的** **microsoft.powershell32** 會話設定，請使用 `Enable-PSRemoting` Cmdlet 來還原它們。 如需詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

## 範例

### 範例 1：刪除工作階段設定

此範例會從電腦刪除 **MaintenanceShell** 會話設定。

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### 範例 2︰刪除工作階段設定，並重新啟動 WinRM 服務

在此範例中，我們會刪除 **MaintenanceShell** 設定，並重新啟動 WinRM 服務。 **Force** 參數會抑制所有使用者訊息，以重新開機 **WinRM** 服務而不提示。

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### 範例 3：刪除所有工作階段設定

此範例顯示兩種刪除電腦上所有會話設定的方式。 這兩個命令都有相同的效果，而且可以交換使用。

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### 範例 4︰取消註冊而不重新啟動

此範例顯示使用 **NoServiceRestart** 參數來防止服務重新開機，而導致電腦上的任何會話中斷的效果。

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

會 `Unregister-PSSessionConfiguration` 刪除 **MaintenanceShell** 會話設定。
不過，因為命令使用 **NoServiceRestart** 參數，所以 **WinRM** 服務不會重新啟動，而變更尚未完全生效。

接下來， `Get-PSSessionConfiguration` 嘗試取得 **MaintenanceShell** 會話。 因為會話已經從 WS-Management 資源資料表中移除，所以 `Get-PSSessionConfiguration` 無法將它傳回。

此 `New-PSSession` Cmdlet 會使用 **MaintenanceShell** 設定來建立會話。 命令執行成功。 接下來，我們會重新開機 **WinRM** 服務。

最後， `New-PSSession` Cmdlet 會嘗試建立使用 **MaintenanceShell** 設定的會話。 這次，會話失敗，因為 WinRM 服務重新開機時已刪除 **MaintenanceShell** 設定。

## PARAMETERS

### -Force

指出 Cmdlet 不會提示您進行確認，並會在不提示的情況下重新啟動 **WinRM** 服務。 重新啟動服務可讓設定變更生效。

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

指定要刪除的工作階段設定名稱。 輸入一個工作階段設定名稱或設定名稱模式。 允許使用萬用字元。 這是必要參數。

您也可以使用管線將會話設定傳送至 `Unregister-PSSessionConfiguration` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoServiceRestart

指出此 Cmdlet 不會重新啟動 **WinRM** 服務，且會抑制重新啟動服務的提示。

依預設，當您執行 `Unregister-PSSessionConfiguration` 命令時，系統會提示您重新開機 **WinRM** 服務，讓變更生效。 在 **WinRM** 服務重新開機之前，使用者仍然可以使用未註冊的會話設定，即使找 `Get-PSSessionConfiguration` 不到它也一樣。

若要重新啟動 **WinRM** 服務而不提示，請指定 **Force** 參數。 若要手動重新開機 **WinRM** 服務，請使用 `Restart-Service` Cmdlet。

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

### Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration

您可以使用管線將會話設定物件傳送 `Get-PSSessionConfiguration` 至此 Cmdlet。

## 輸出

### None

此 Cmdlet 不會傳回任何物件。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

若要執行此 Cmdlet，您必須使用 [ **以系統管理員身分執行** ] 選項啟動 PowerShell。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

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
