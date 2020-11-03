---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 6208e9c1b7124c8faec1e3e87a6e815540d2b962
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201995"
---
# Clear-Variable

## 概要
刪除變數的值。

## SYNTAX

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**清除變數** Cmdlet 會刪除儲存在變數中的資料，但不會刪除變數。
因此，變數的值是 NULL (空白)。
如果變數具有指定的資料或物件類型，這個 Cmdlet 會保留變數中所儲存之物件的類型。

## 範例

### 範例1：移除以搜尋字串開頭之全域變數的值

```
PS C:\> Clear-Variable my* -Scope Global
```

此命令會移除名稱開頭為 my 的全域變數值。

### 範例2：清除子範圍中的變數，但不清除父範圍中的變數

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

這些命令示範清除子系範圍中的變數不會清除父系範圍中的值。
第一個命令將變數 $A 值設定為3。
第二個命令使用叫用運算子 ( # A0) 在新的範圍中執行 **清除變數** 命令。
子系範圍內的變數會被清除 (雖然它不存在)，但本機範圍內的變數不會被清除。
第三個命令會取得 $A 的值，顯示值3不受影響。

### 範例3：刪除指定之變數的值

```
PS C:\> Clear-Variable -Name "Processes"
```

此命令會刪除名為「進程」的變數值。
當 Cmdlet 完成作業之後，名為進程的變數仍然存在，但值為 null。

## PARAMETERS

### -Exclude

指定此 Cmdlet 在作業中省略的專案陣列。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 "s*"。
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

### -Force

允許 Cmdlet 清除變數，即使它是唯讀的。
即使使用 Force 參數，Cmdlet 仍然無法清除常數。

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

### -Include

指定此 Cmdlet 在作業中納入之項目的陣列。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 "s*"。
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

指定要清除之變數的名稱。
允許使用萬用字元。
此為必要參數，但是參數名稱 ("Name") 為選擇性。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Scope

指定別名的有效範圍。

此參數可接受的值為：

- 全球
- 本機
- 指令碼

您也可以使用相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父) 。
Local 為預設值。
如需詳細資訊，請參閱 about_Scopes。

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

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無或 System.Management.Automation.PSVariable

當您使用 *PassThru* 參數時，此 Cmdlet 會產生代表已清除變數的 **system.management.automation.psvariable** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 若要刪除變數與其值，請使用 Remove-Variable 或 Remove-Item。

  此 Cmdlet 不會刪除設定為常數或系統所擁有的變數值，即使您使用 *Force* 參數也是如此。

  如果您清除的變數不存在，Cmdlet 不會有任何作用。
它不會建立具有 null 值的變數。

  您也可以使用內建的別名 clv 來參考 **清除變數** 。
如需詳細資訊，請參閱 about_Aliases。

*

## 相關連結

[Get-Variable](Get-Variable.md)

[New-Variable](New-Variable.md)

[Remove-Variable](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
