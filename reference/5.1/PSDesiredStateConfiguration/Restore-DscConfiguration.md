---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203935"
---
# Restore-DscConfiguration

## 概要
重新套用先前的節點設定。

## SYNTAX

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**Restore-DscConfiguration** Cmdlet 會還原先前的節點設定 (如果先前的設定已存在)。
使用通用訊息模型 (CIM) 工作階段指定電腦。
如果您沒有指定目標電腦，此 Cmdlet 會還原本機電腦的設定。
如果先前沒有針對特定節點的設定，此 Cmdlet 會傳回錯誤訊息。

此 Cmdlet 不支援 **Confirm** 參數。

## 範例

### 範例 1：還原本機電腦的設定

```
PS C:\> Restore-DscConfiguration
```

此命令會還原本機電腦的設定。

### 範例 2：還原指定電腦的設定

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

這個範例會還原 CIM 工作階段所指定之電腦上的設定。
這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。
或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。

第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。
此命令會提示您輸入密碼。
如需詳細資訊，請鍵入 `Get-Help New-CimSession`。

第二個命令會還原以 $Session 變數儲存的 **CimSession** 物件所識別之電腦的設定，在此案例中為名為 Server01 的電腦。

## PARAMETERS

### -AsJob
指出此 Cmdlet 會以背景工作方式執行命令。

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

### -CimSession
在遠端工作階段或遠端電腦上執行 Cmdlet。
輸入電腦名稱稱或會話物件，例如 **CimSession** 或 **CimSession** Cmdlet 的輸出。

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

### -ThrottleLimit
指定為執行 Cmdlet 可建立的最大並行作業數。

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

## 輸出

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
