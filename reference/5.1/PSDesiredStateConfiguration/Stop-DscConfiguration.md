---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203087"
---
# Stop-DscConfiguration

## 概要
停止正在執行的設定工作。

## SYNTAX

### 全部

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Stop-DscConfiguration` Cmdlet 會停止執行中的設定工作。 使用通用訊息模型 (CIM) 工作階段，來指定要將此 Cmdlet 套用至哪些電腦。 如果沒有執行中的設定作業，此 Cmdlet 會傳回一則警告訊息。

`Stop-DscConfiguration` 僅適用于2014年11月更新彙總套件的一部分，可從 Microsoft 支援服務程式庫 [Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) 。 使用這個 Cmdlet 之前，請先複習[Windows PowerShell 5.0 的新功能](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)中的資訊。

## 範例

### 範例 1︰停止設定工作

在此範例中，會使用 Cmdlet 建立 CIM 會話 `New-CimSession` 。 **CimSession** 物件是用來停止執行中的設定工作。

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

`New-CimSession` 使用 **ComputerName** 參數來指定 Server01 電腦。 **Credential** 參數會指定使用者帳戶。 **CimSession** 物件儲存在 `$Session` 變數中。 當命令執行時，系統會提示您輸入使用者帳戶的密碼。

`Stop-DscConfiguration` 使用 **CimSession** 參數和儲存在中的物件 `$Session` 來停止設定工作。

## PARAMETERS

### -AsJob

指出此 Cmdlet 會以背景工作方式執行命令。 如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)。

若要使用 **AsJob** 參數，必須設定本機和遠端電腦以進行遠端處理。 在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。 如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。

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

### -CimSession

在遠端工作階段或遠端電腦上執行 Cmdlet。 輸入電腦名稱稱或會話物件，例如或的輸出 `New-CimSession` `Get-CimSession` 。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

`Stop-DscConfiguration` 不支援 **Confirm** 參數。 如果使用 **Confirm** 參數，則會顯示錯誤。

針對支援 **確認** 的 PowerShell Cmdlet，使用參數會在執行命令之前提示您進行驗證。

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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行 Cmdlet 可建立的最大並行作業數。

如果省略此參數或輸入的值 `0` ，則 PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算最佳的節流限制。 節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

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

## 輸出

### 無

## 注意

## 相關連結

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/overview)
