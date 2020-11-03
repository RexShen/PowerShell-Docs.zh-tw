---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: ec8d080da133310270d022b00f7f92d08ea3ca41
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203176"
---
# Out-Printer

## 概要
將輸出傳送到印表機。

## SYNTAX

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`Out-Printer`Cmdlet 會將輸出傳送到預設印表機或替代印表機（若有指定）。

> [!NOTE]
> PowerShell 7 中已重新引入此 Cmdlet。 只有支援 Windows 桌面的 Windows 系統才能使用此 Cmdlet。

## 範例

### 範例 1-傳送要列印在預設印表機上的檔案

這個範例會示範如何列印檔案，即使沒有 `Out-Printer` **Path** 參數也是一樣。

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

`Get-Content`取得目前目錄中檔案的內容， `readme.txt` 並將其傳送至 `Out-Printer` 預設印表機，以傳送到預設印表機。

### 範例2：將字串列印到遠端印表機

此範例會列印 `Hello, World` 到 Server01 上的 **Prt 6b 彩色** 印表機。

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

**Name** 參數會選取特定的印表機，而不是預設的。

### 範例 3-將說明主題列印到預設印表機

這個範例會列印的完整版說明主題 `Get-CimInstance` 。

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

`Get-Help` 取得的說明主題的完整版本 `Get-CimInstance` ，並將它儲存在 `$H` 變數中。 **InputObject** 參數會將的值傳遞 `$H` 給 `Out-Printer` 。

## PARAMETERS

### -InputObject

指定要傳送到印表機的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

將輸出傳送到指定的印表機。 參數名稱 **名稱** 是選擇性的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件傳送至 `Out-Printer` 。

## 輸出

### 無

`Out-Printer` 不會傳回任何物件。

## 注意

包含動詞的 Cmdlet `Out` 不會將物件格式化。 它們只會轉譯它們並傳送至指定的顯示目的地。 如果您將未格式化的物件傳送至 `Out` Cmdlet，此 Cmdlet 會將它傳送到格式化 Cmdlet，然後才轉譯它。

`Out-Printer` 將資料傳送至印表機，但不會發出任何輸出物件至管線。 如果您使用管線將的輸出傳送 `Out-Printer` 至，就會 `Get-Member` `Get-Member` 報告未指定任何物件。

## 相關連結

[Out-File](Out-File.md)

[Out-String](Out-String.md)
