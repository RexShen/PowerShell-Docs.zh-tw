---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/publish-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-DscConfiguration
ms.openlocfilehash: 139de2bfdb88c443e7bc48d36e37e95644556bf5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203939"
---
# Publish-DscConfiguration

## 概要
將 DSC 設定發佈到一組電腦。

## SYNTAX

### ComputerNameSet (預設值)

```
Publish-DscConfiguration [-Path] <String> [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Publish-DscConfiguration [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Publish-DscConfiguration** Cmdlet 會在一組電腦上發佈 Windows PowerShell 預期狀態設定 (DSC) 的設定文件。
此 Cmdlet 不會套用設定。
設定是由 Start-DscConfiguration Cmdlet 搭配 *UseExisting* 參數搭配使用時所套用，或 DSC 引擎執行其一致性循環時所套用。
DSC 引擎也稱為「本機設定管理員 (LCM)」。

傳遞多個設定文件的片段時，此 Cmdlet 特別有用。
傳遞多個設定文件片段時，它們會覆寫較舊的設定文件片段。

## 範例

### 範例 1︰將設定發佈到遠端電腦

```
PS C:\> Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

此命令會將設定發佈到遠端電腦。
執行此 Cmdlet 的使用者應為遠端電腦上的系統管理員。

## PARAMETERS

### -CimSession
在遠端工作階段或遠端電腦上執行 Cmdlet。
輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。
預設為本機電腦上的目前工作階段。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
指定此 Cmdlet 在其中發佈組態的一或多部電腦。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
指定用來存取目標裝置的認證。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
強制此 Cmdlet 完成。
如果「本機設定管理員」重新整理模式設為「提取」，使用此參數會將其變更為「推入」，並會發佈 DSC 設定。
此外，如果有擱置中的 DSC 設定，使用此參數會覆寫該擱置中設定。

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

### -Path
指定一個路徑，其中包含要發佈到目標電腦的設定。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
指定為執行 Cmdlet 可建立的最大並行作業數。
如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。
節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。

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

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
