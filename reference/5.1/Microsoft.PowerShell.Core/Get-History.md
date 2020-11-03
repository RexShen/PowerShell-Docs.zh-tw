---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: ae9cc8b0daf9a3c25d4385fbca156e8a146334da
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "93206364"
---
# Get-History

## 概要
取得目前工作階段期間輸入的命令清單。

## SYNTAX

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-History` Cmdlet 會取得會話歷程記錄，也就是在目前會話期間輸入的命令清單。

PowerShell 會自動維護每個會話的歷程記錄。 會話歷程記錄中的專案數取決於喜好設定變數的值 `$MaximumHistoryCount` 。 從 Windows PowerShell 3.0 開始，預設值為 `4096` 。 根據預設，歷程記錄檔案會儲存在主目錄中，但是您可以將檔案儲存在任何位置。 如需 PowerShell 中歷程記錄功能的詳細資訊，請參閱 [about_History](About/about_History.md)。

會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。
這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。 此 Cmdlet 僅適用于會話歷程記錄。 如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

## 範例

### 範例1：取得會話歷程記錄

這個範例會取得會話歷程記錄中的專案。 預設顯示會顯示每個命令和它的識別碼，指出它們的執行順序。

```powershell
Get-History
```

### 範例2：取得包含字串的專案

此範例會取得命令歷程記錄中包含字串服務的專案。 第一個命令會取得工作階段歷程記錄中所有項目。 管線運算子 () 會將 `|` 結果傳遞至 `Where-Object` Cmdlet，此 Cmdlet 只會選取包含服務的命令。

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### 範例3：將記錄專案匯出至特定識別碼

這個範例會取得以專案7結尾的五個最新歷程記錄專案。 管線運算子會將結果傳遞至 `Export-Csv` Cmdlet，此 Cmdlet 會將歷程記錄格式化為逗點分隔的文字，並將其儲存在 History.csv 檔案中。 檔案包含將歷程記錄格式化為清單時所顯示的資料。 這包括命令的狀態和開始和結束時間。

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### 範例4：顯示最新的命令

此範例會取得命令歷程記錄中的最後一個命令。 最後一個命令是最近輸入的命令。 此命令會使用 **Count** 參數只顯示一個命令。 根據預設，會 `Get-History` 取得最新的命令。 此命令可以縮寫成 "h -c 1"，而且相當於按下向上鍵。

```powershell
Get-History -Count 1
```

### 範例5：顯示歷程記錄中所有專案的屬性

此範例會顯示會話歷程記錄中所有專案的屬性。 管線運算子會將命令的結果傳遞 `Get-History` 給 `Format-List` Cmdlet，以顯示每個歷程記錄專案的所有屬性。 這包括命令的識別碼、狀態和開始與結束時間。

```powershell
Get-History | Format-List -Property *
```

## PARAMETERS

### -Count

指定此 Cmdlet 取得的最新歷程記錄專案數目。 依預設，會 `Get-History` 取得會話歷程記錄中的所有專案。 如果您同時在命令中使用 **Count** 和 **Id** 參數，畫面結尾會是 **Id** 參數所指定的命令。

在 Windows PowerShell 2.0 中，預設會 `Get-History` 取得32的最新專案。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定會話歷程記錄中專案的識別碼陣列。 `Get-History` 只取得指定的專案。 如果您在命令中同時使用 **id** 和 **Count** 參數，會 `Get-History` 取得以 **id** 參數指定的專案結尾的最新專案。

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Int64

您可以使用管線將歷程記錄識別碼傳送至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.HistoryInfo

這個 Cmdlet 會針對它取得的每個歷程記錄專案傳回一個歷程記錄物件。

## 注意

工作階段歷程記錄是工作階段期間輸入的命令清單。 會話歷程記錄代表命令的執行順序、狀態，以及開始和結束時間。 當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。 如需命令歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。

從 Windows PowerShell 3.0 開始，喜好設定變數的預設值 `$MaximumHistoryCount` 為 `4096` 。 在 Windows PowerShell 2.0 中，預設值為 `64` 。 如需變數的詳細資訊 `$MaximumHistoryCount` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

## 相關連結

[Add-History](Add-History.md)

[Clear-History](Clear-History.md)

[Invoke-History](Invoke-History.md)

[about_History](About/about_History.md)
