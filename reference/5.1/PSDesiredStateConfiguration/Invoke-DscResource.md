---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203943"
---
# Invoke-DscResource

## 概要
執行指定 DSC 資源的方法。

## SYNTAX

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## DESCRIPTION
**DscResource 指令程式** 會執行指定 Windows PowerShell DESIRED STATE CONFIGURATION (DSC) 資源的方法。
執行此 Cmdlet 之前，請將本機 Configuration Manager (LCM) 的重新整理模式設定為停用。

此 Cmdlet 會直接叫用 DSC 資源，而不需建立設定文件。
使用此 Cmdlet，設定管理產品可以使用 DSC 資源來管理 windows。
當 DSC 引擎或 LCM 在啟用偵錯工具的情況下執行時，此 Cmdlet 也會啟用資源的偵錯工具。

## 範例

### 範例1：指定資源的必要屬性來叫用資源的 Set 方法

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

此命令會叫用名為 Log 的資源的 **Set** 方法，並為其指定 **訊息** 屬性。

### 範例2：叫用指定模組之資源的測試方法

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

此命令會叫用名為 WindowsProcess 之資源的 **測試** 方法，該資源位於名為 PSDesiredStateConfiguration 的模組中。

## PARAMETERS

### -Method
指定此 Cmdlet 叫用之資源的方法。 此參數可接受的值為： Get、Set 和 Test。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ModuleName
指定此 Cmdlet 用來叫用指定之資源的模組名稱。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
指定要啟動之 DSC 資源的名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Property
在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。 使用 **Get-DscResource** Cmdlet，探索資源的屬性和其類型。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### CimInstance，system.string. 布林值

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Get-DscResource](Get-DscResource.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
