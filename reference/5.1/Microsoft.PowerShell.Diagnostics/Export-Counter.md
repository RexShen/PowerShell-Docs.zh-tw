---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206675"
---
# Export-Counter

## 概要
將效能計數器資料匯出至記錄檔。

## SYNTAX

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## DESCRIPTION

此 `Export-Counter` Cmdlet 會將效能計數器資料匯出 (PerformanceCounterSampleSet 物件) 至二進位效能記錄檔中的記錄檔 ( .blg) 、逗點分隔值 ( .csv) 或定位字元分隔值 ( tsv) 格式。 您可以使用這個 Cmdlet 來記錄效能計數器資料。

此 `Export-Counter` Cmdlet 是設計用來匯出和 Cmdlet 所傳回的 `Get-Counter` 資料 `Import-Counter` 。

此 Cmdlet 只能在 Windows 7、Windows Server 2008 R2 及更新版本的 Windows 上執行。

## 範例

### 範例1：將計數器資料匯出至檔案

此範例會將計數器資料匯出至 .BLG 檔案。

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

此命令會使用 `Get-Counter` Cmdlet 來收集處理器時間資料。 它使用管線運算子 (|) 將資料傳送至 `Export-Counter` Cmdlet。 此 `Export-Counter` 命令會使用 **Path** 變數來指定輸出檔。

因為資料集可能非常大，所以此範例會透過管線將資料傳送至 `Export-Counter` 。 如果資料儲存在變數中，您可能會使用不相稱的記憶體量。

### 範例 2︰將檔案匯出至計數器檔案格式

此範例會將 CSV 檔案轉換成計數器資料的 .BLG 格式。

此 `Import-Counter` Cmdlet 會從檔案匯入效能計數器資料 `Threads.csv` 。 此範例假設先前使用指令程式匯出此檔案 `Export-Counter` 。 管線運算子 (`|`) 將匯入的資料傳送至 `Export-Counter` Cmdlet。 命令使用 **Path** 參數指定輸出檔案的位置。 它會使用 **迴圈** 和 **MaxSize** 參數，指示 `Export-Counter` CMDLET 建立包裝在 1 GB 的迴圈記錄檔。 **MaxSize** 參數以 mb 表示。

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### 範例 3︰從遠端電腦取得計數器資料，並將資料儲存至檔案

此範例說明如何從遠端電腦取得效能計數器資料，並將資料儲存在遠端電腦上的檔案中。

第一個命令會使用 `Get-Counter` Cmdlet 從遠端電腦的 Server01 收集工作集計數器資料。 此命令會將資料儲存在 `$C` 變數中。

第二個命令會使用管線運算子 (`|`) 將資料傳送 `$C` 至 Cmdlet，以將它儲存 `Export-Counter` 在 `Workingset.blg` Server01 電腦的效能共用中的檔案。

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### 範例 4︰重新記錄現有的資料

此範例示範如何使用 `Import-Counter` 和 `Export-Counter` Cmdlet 重新記錄現有的資料。

第一個命令會使用 `Import-Counter` Cmdlet，從磁碟空間 .blg 記錄檔匯入效能計數器資料。 它會將資料儲存在 `$All` 變數中。 此檔案包含 \% 企業中超過200部遠端電腦上的「LogicalDisk 可用空間」計數器範例。

第二個命令會使用 `Where-Object` Cmdlet 來選取 **CookedValue** 小於 15 (%) 的物件。 命令會將結果儲存在 `$LowSpace` 變數中。

第三個命令會使用管線運算子 (`|`) 將變數中的資料傳送 `$LowSpace` 至 `Export-Counter` Cmdlet。 命令使用 **Path** 參數，指示選取的資料應記錄到 LowDiskSpace.blg 檔案中。

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## PARAMETERS

### -Circular

指出輸出檔為先進先出 (FIFO) 格式的循環記錄檔。
當您包括此參數時， **MaxSize** 是必要參數。

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

### -FileFormat

指定輸出記錄檔的輸出格式。

此參數可接受的值為：

- CSV
- TSV
- BLG

預設值為 BLG。

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

### -Force

若 **Path** 參數所指定的位置已有檔案存在，就會覆寫並取代現有檔案。

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

### -InputObject

以陣列格式指定要匯出的計數器資料。 輸入包含資料的變數，或輸入可取得資料的命令，例如 `Get-Counter` 或 `Import-Counter` Cmdlet。

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaxSize

指定輸出檔案的大小上限，以 mb (MB) 。

若指定 **Circular** 參數，則會在記錄檔達到指定的大小上限時，於較新的項目加入時刪除最舊的項目。 若未指定 **Circular** 參數，則會在記錄檔達到指定的大小上限時，停止加入任何新資料，且此 Cmdlet 會產生一個非終止錯誤。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定輸出檔案的路徑和檔案名稱。 請在本機電腦上輸入相對或絕對路徑，或在遠端電腦上輸入統一命名慣例 (UNC) 路徑，例如 `\\Computer\Share\file.blg` 。 這是必要參數。

檔案格式是由 **FileFormat** 參數的值來決定，而不是由路徑中的副檔名所決定。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet

您可以透過管線將效能計數器資料從 `Get-Counter` 或傳送 `Import-Counter` 至此 Cmdlet。

## 輸出

### 無

## 注意

記錄檔產生器會預期所有輸入物件都具有相同的計數器路徑，並且物件會依時間以遞增順序排列。

計數器類別和第一個輸入物件的路徑會決定記錄檔中記錄的屬性。 若其他輸入物件沒有記錄之屬性的值，屬性欄位就會是空的。 若物件具有未記錄的屬性值，則會忽略額外的屬性值。

效能監視器可能無法讀取產生的所有記錄 `Export-Counter` 。 例如，效能監視器要求所有物件都要有相同的路徑，而且所有物件都以相同的時間間隔分隔。

`Import-Counter`Cmdlet 沒有 **ComputerName** 參數。 但是，如果電腦設定為遠端 Windows PowerShell Windows PowerShell，您可以使用 `Invoke-Command` Cmdlet `Import-Counter` 在遠端電腦上執行命令。

## 相關連結

[Get-Counter](Get-Counter.md)

[Import-Counter](Import-Counter.md)
