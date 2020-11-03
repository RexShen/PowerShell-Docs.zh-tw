---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 2a66f906025f7a25609080e0b8da7f01755cd2fa
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201327"
---
# New-DscChecksum

## 概要
建立 DSC 檔和 DSC 資源的總和檢查碼檔案。

## SYNTAX

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**>new-dscchecksum 指令程式** 會為 PowerShell DESIRED STATE CONFIGURATION (DSC) 檔和壓縮的 dsc 資源產生總和檢查碼檔案。
這個 Cmdlet 會針對要在提取模式中使用的每個設定和資源，產生總和檢查碼檔案。
DSC 服務會使用總和檢查碼來確定目標節點上有正確的設定和資源。
將總和檢查碼與 dsc 服務存放區中相關聯的 DSC 檔和壓縮的 DSC 資源放在一起。

## 範例

### 範例1：為特定路徑中的所有設定建立總和檢查碼檔案

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

此命令會在路徑 C:\DSC\Configurations 中建立所有設定的總和檢查碼檔案。
系統會略過已存在的任何總和檢查碼檔案。

### 範例2：為特定路徑中的所有設定建立總和檢查碼檔案，並覆寫現有的總和檢查碼檔案

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

此命令會在路徑 C:\DSC\Configurations 中建立所有設定的新總和檢查碼檔案。
指定 *Force* 參數會導致命令覆寫已存在的任何總和檢查碼檔案。

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

指出此 Cmdlet 會覆寫指定的輸出檔案 (如果該檔案已存在)。

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

### -OutPath

指定輸出總和檢查碼檔案的路徑和檔案名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定輸入檔的路徑。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
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

## 輸出

### System.Object

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)
