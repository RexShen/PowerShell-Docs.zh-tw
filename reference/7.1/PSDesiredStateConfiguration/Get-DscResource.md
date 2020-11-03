---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: a572efd12b35705ebac34d304d2b9ef0a3b1ab60
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205759"
---
# Get-DscResource

## 概要
取得 Desired State Configuration (DSC) 資源存在於電腦上。

## SYNTAX

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-DscResource` Cmdlet 會抓取存在於電腦上的 POWERSHELL DSC 資源。 此 Cmdlet 只會探索安裝在 PSModulePath 中的資源。 它會顯示使用者所建立之內建和自訂提供者的詳細資料。 此 Cmdlet 也會顯示覆合資源的詳細資料，也就是封裝為模組，或在會話的執行時間建立的其他設定。

## 範例

### 範例1：取得本機電腦上的所有資源

```powershell
Get-DscResource
```

此命令會取得本機電腦上的所有資源。

### 範例2：指定名稱以取得資源

```powershell
Get-DscResource -Name "WindowsFeature"
```

此命令會取得 WindowsFeature 資源。

### 範例3：取得模組中的所有資源

```powershell
Get-DscResource -Module "xHyper-V"
```

此命令會從 xHyper-V 模組取得所有資源。

### 範例4：使用萬用字元取得資源

```powershell
Get-DscResource -Name P*,r*
```

此命令會取得符合 **Name** 參數所指定之萬用字元模式的所有資源。

### 範例5：取得資源語法

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

此命令會取得 WindowsFeature 資源，並顯示資源的語法。

### 範例6：取得資源的所有屬性

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

此命令會取得使用者資源，然後使用管線運算子傳回使用者資源的所有屬性。

### 範例7：從指定的模組取得具有指定版本的所有資源

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

此命令會從 xHyper-V 模組取得具有版本3.0.0.0 的所有資源。

## PARAMETERS

### -Module

指定要為其查看 DSC 資源的模組名稱或完整名稱。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

指定要查看之 DSC 資源的名稱陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -語法

指出此 Cmdlet 會傳回指定之 DSC 資源的語法視圖。 傳回的語法說明如何使用 PowerShell 腳本中的資源。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String[]

### System.Object

## 輸出

### DesiredStateConfiguration. DscResourceInfo []

### string[]

## 注意

## 相關連結

[PowerShell Desired State Configuration 總覽](/powershell/scripting/dsc/overview/overview)

[Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)

