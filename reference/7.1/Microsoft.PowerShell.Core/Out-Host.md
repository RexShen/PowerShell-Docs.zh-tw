---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 9f53f137ecdd415e0185e380cba6ff817972b82e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205003"
---
# Out-Host

## 概要
將輸出傳送至命令列。

## SYNTAX

### 全部

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

`Out-Host`Cmdlet 會將輸出傳送至 PowerShell 主機以供顯示。 主機會在命令列中顯示輸出。 因為 `Out-Host` 是預設值，除非您想要使用其參數，否則不需要指定它。

`Out-Host` 會自動附加至每個執行的命令。 它會將管線的輸出傳遞給執行命令的主機。 `Out-Host` 忽略 ANSI escape 序列。 Escape 序列是由主機處理。 `Out-Host` 將 ANSI escape 序列傳遞給主機，而不嘗試解讀或變更它們。

## 範例

### 範例1：一次顯示一個頁面的輸出

此範例會顯示一次一個頁面的系統處理。

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

`Get-Process` 取得系統進程，並將物件沿著管線向下傳送。 `Out-Host` 使用 **分頁** 參數，一次顯示一頁數據。

### 範例2：使用變數作為輸入

這個範例會使用儲存在變數中的物件做為的輸入 `Out-Host` 。

```powershell
$io = Get-History
Out-Host -InputObject $io
```

`Get-History` 取得 PowerShell 會話的歷程記錄，並將物件儲存在 `$io` 變數中。
`Out-Host` 使用 **InputObject** 參數來指定 `$io` 變數並顯示歷程記錄。

## PARAMETERS

### -InputObject

指定寫入主控台的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

### -Paging

指出 `Out-Host` 一次會顯示一頁的輸出，並等待使用者輸入再顯示其餘的頁面。 依預設，所有輸出都會顯示在單一頁面上。 頁面大小取決於主機特性。

按 <kbd>空格鍵</kbd> 以顯示下一頁的輸出，或按 <kbd>Enter</kbd> 鍵來查看下一行輸出。 按 <kbd>Q</kbd> 鍵結束。

**分頁** 類似于 **更多** 命令。

> [!NOTE]
> PowerShell ISE 主機不支援 **分頁** 參數。

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

### System.Management.Automation.PSObject

您可以將物件沿著管線向下傳送至 `Out-Host` 。

## 輸出

### 無

`Out-Host` 不會產生任何輸出。 它會將物件傳送至主控制項以供顯示。

## 注意

所有 PowerShell 主機都不支援 **分頁** 參數。 例如，如果您在 PowerShell ISE 中使用 **分頁** 參數，則會顯示下列錯誤： `out-lineoutput : The method or operation is not implemented.`

包含 **Out** 動詞的 Cmdlet 不會將 `Out-` 物件格式化。 它們會轉譯物件，並將它們傳送至指定的顯示目的地。 如果您將未格式化的物件傳送至 `Out-` Cmdlet，此 Cmdlet 會將它傳送到格式化 Cmdlet，然後才轉譯它。

`Out-`Cmdlet 沒有名稱或檔案路徑的參數。 若要將資料傳送至 `Out-` Cmdlet，請使用管線將 PowerShell 命令的輸出傳送至 Cmdlet。 或者，您可以將資料儲存在變數中，然後使用 **InputObject** 參數將資料傳遞給 Cmdlet。

`Out-Host` 傳送資料，但不會產生任何輸出物件。 如果您將的輸出管線 `Out-Host` 至 `Get-Member` Cmdlet，則會 `Get-Member` 報告未指定任何物件。

## 相關連結

[Clear-Host](Clear-Host.md)

[Out-Default](Out-Default.md)

[Out-File](../Microsoft.PowerShell.Utility/Out-File.md)

[Out-Null](Out-Null.md)

[Out-Printer](../Microsoft.PowerShell.Utility/Out-Printer.md)

[Out-String](../Microsoft.PowerShell.Utility/Out-String.md)

[Write-Host](../Microsoft.PowerShell.Utility/Write-Host.md)

