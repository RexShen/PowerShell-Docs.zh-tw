---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: eac42af069b5d1276105c16dd6e280c7c72cf558
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204579"
---
# Get-Variable

## 概要
取得目前主控台中的變數。

## SYNTAX

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-Variable`Cmdlet 會取得目前主控台中的 PowerShell 變數。
您可以透過指定 **ValueOnly** 參數來只抓取變數的值，而且您可以依名稱篩選傳回的變數。

## 範例

### 範例 1︰依字母取得變數

此命令會取得名稱以字母 m 為開頭的變數。
命令也會取得變數的值。

```powershell
Get-Variable m*
```

### 範例 2︰依字母取得變數值

此命令只會取得名稱以 m 為開頭之變數的值。

```powershell
Get-Variable m* -ValueOnly
```

### 範例 3︰依兩個字母取得變數

此命令會取得以字母 M 或字母 P 為開頭之變數的相關資訊。

```powershell
Get-Variable -Include M*,P*
```

### 範例 4︰依範圍取得變數

第一個命令只會取得本機範圍中定義的變數。
它相當於 `Get-Variable -Scope Local`，並可縮寫成 `gv -s 0`。

第二個命令 `Compare-Object` 會使用 Cmdlet 來尋找 (範圍 1) 的父範圍中定義的變數，但只在區域 (範圍 0) 可見。

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## PARAMETERS

### -Exclude

指定此 Cmdlet 從作業排除之項目的陣列。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

指定 Cmdlet 會在其中作用的項目陣列，不包含其他所有項目。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

指定變數的名稱。
允許使用萬用字元。
您也可以使用管線將變數名稱傳送至 `Get-Variable` 。

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

### -Scope

指定範圍中的變數。此參數可接受的值包括：

- **全球**
- **本機**
- **指令碼**
- 相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。

預設值為 [ **本機** ]。
如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

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

### -ValueOnly

指示此 Cmdlet 只取得變數的值。

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含變數名稱的字串傳送至 `Get-Variable` 。

## 輸出

### System.Management.Automation.PSVariable

此 Cmdlet 會傳回它所取得之每個變數的 **System.Management.AutomationPSVariable** 物件。 物件類型會視變數而定。

### System.object []

當您指定 **ValueOnly** 參數時，如果指定的變數值為集合，則會傳回 `Get-Variable` `[System.Object[]]` 。 此行為可防止正常管線操作一次處理一個變數的值。 強制集合列舉的因應措施是將命令以括弧括住 `Get-Variable` 。

## 注意

- 此 Cmdlet 並不會管理環境變數。 若要管理環境變數，您可以使用環境變數提供者。

## 相關連結

[Clear-Variable](Clear-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
