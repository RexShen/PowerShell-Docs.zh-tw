---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 1c0a4c958ae60ab6bde170a71f6bc69e09079074
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201696"
---
# Add-History

## 概要
將項目附加至工作階段歷程記錄。

## SYNTAX

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## DESCRIPTION

`Add-History`Cmdlet 會將專案新增至會話歷程記錄的結尾，也就是在目前會話期間輸入的命令清單。

工作階段歷程記錄是工作階段期間輸入的命令清單。 工作階段歷程記錄代表命令的執行順序、狀態及開始和結束時間。 當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。 如需會話歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。

會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。
這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。 此 Cmdlet 僅適用于會話歷程記錄。 如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。

您可以使用 `Get-History` 指令程式取得命令，並將它們傳遞給 `Add-History` ，也可以將命令匯出至 CSV 或 XML 檔案，然後匯入命令，並將匯入的檔案傳遞至 `Add-History` 。 您可以使用此 Cmdlet 將特定的命令新增至歷程記錄，或建立包含來自多個工作階段之命令的單一歷程記錄檔案。

## 範例

### 範例1：將命令新增至不同會話的歷程記錄

此範例會將在一個 PowerShell 會話中輸入的命令新增至不同 PowerShell 會話的歷程記錄。

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

第一個命令會取得代表歷程記錄中之命令的物件，並將其匯出至檔案 `History.csv` 。

第二個命令是在不同工作階段的命令列中輸入。 它會使用 `Import-Csv` Cmdlet 匯入檔案中的物件 `History.csv` 。 管線運算子 (`|`) 會將物件傳遞至 `Add-History` Cmdlet，此 Cmdlet 會將代表檔案中命令的物件新增 `History.csv` 至目前的會話歷程記錄。

### 範例2：匯入和執行命令

此範例會從檔案匯入命令 `History.xml` ，將它們新增至目前的會話歷程記錄，然後執行合併歷程記錄中的命令。

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

第一個命令會使用 `Import-Clixml` Cmdlet 匯入已匯出至檔案的命令歷程記錄 `History.xml` 。 管線運算子會將命令傳遞至 `Add-History` Cmdlet，此 Cmdlet 會將命令新增至目前的會話歷程記錄。 **PassThru** 參數會將代表新增之命令的物件傳遞至管線。

然後，此命令會使用 `ForEach-Object` Cmdlet 將 `Invoke-History` 命令套用至合併歷程記錄中的每個命令。 此 `Invoke-History` 命令會格式化為腳本區塊，並以大括弧 (`{}`) 括住，如 Cmdlet 的 **Process** 參數所要求 `ForEach-Object` 。

### 範例3：將歷程記錄中的命令新增至歷程記錄的結尾

此範例會將歷程記錄中的前五個命令新增至歷程記錄清單的結尾。

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

此 `Get-History` Cmdlet 會取得五個命令，並以命令5結尾。 管線運算子會將它們傳遞給 `Add-History` Cmdlet，以將它們附加至目前的歷程記錄。 此 `Add-History` 命令不包含任何參數，但 PowerShell 會將透過管線傳遞的物件與的 **InputObject** 參數產生關聯 `Add-History` 。

### 範例4：將 .csv 檔案中的命令新增至目前的歷程記錄

此範例會將檔案中的命令新增 `History.csv` 至目前的會話歷程記錄。

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

Cmdlet 會匯 `Import-Csv` 入檔案中的命令 `History.csv` ，並將其內容儲存在變數中 `$a` 。

第二個命令會使用 `Add-History` Cmdlet，將中的命令新增 `History.csv` 至目前的會話歷程記錄。 它會使用 **InputObject** 參數來指定 `$a` 變數和 **PassThru** 參數，以產生要在命令列中顯示的物件。 如果沒有 **PassThru** 參數，此 `Add-History` Cmdlet 就不會產生任何輸出。

### 範例5：將 .xml 檔案中的命令新增至目前的歷程記錄

此範例會將檔案中的命令新增 `history.xml` 至目前的會話歷程記錄。

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

**InputObject** 參數會將命令的結果以括弧傳遞給 `Add-History` Cmdlet。 括弧中的命令會先執行，然後將檔案匯入 `history.xml` PowerShell。 `Add-History`Cmdlet 接著會將檔案中的命令新增至會話歷程記錄。

## PARAMETERS

### -InputObject

指定要新增至歷程記錄的專案陣列，做為會話歷程記錄的 **HistoryInfo** 物件。
您可以使用此參數將 **HistoryInfo** 物件（例如、或 Cmdlet 所傳回的物件）提交 `Get-History` `Import-Clixml` `Import-Csv` 至 `Add-History` 。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Passthru

指出此 Cmdlet 會傳回每個歷程記錄專案的 **HistoryInfo** 物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### Microsoft.PowerShell.Commands.HistoryInfo

您可以使用管線將 **HistoryInfo** 物件傳送至此 Cmdlet。

## 輸出

### 無或 Microsoft.PowerShell.Commands.HistoryInfo

如果您指定 **PassThru** 參數，此 Cmdlet 會傳回 **HistoryInfo** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

會話歷程記錄是會話期間輸入的命令及其識別碼的清單。 工作階段歷程記錄代表命令的執行順序、狀態及開始和結束時間。 當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。 如需會話歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。

如果要指定要新增至歷程記錄的命令，請使用 **InputObject** 參數。 此 `Add-History` 命令只會接受 **HistoryInfo** 物件，例如 Cmdlet 針對每個命令所傳回的物件 `Get-History` 。 您無法傳送路徑和檔案名稱或命令清單給它。

您可以使用 **InputObject** 參數將 **HistoryInfo** 物件的檔案傳遞至 `Add-History` 。 若要這樣做，請 `Get-History` 使用或 Cmdlet 將命令的結果匯出至檔案 `Export-Csv` ， `Export-Clixml` 然後使用或 Cmdlet 匯入檔案 `Import-Csv` `Import-Clixml` 。 然後，您可以 **HistoryInfo** `Add-History` 透過管線或變數，將匯入的 HistoryInfo 物件的檔案傳遞至。 如需詳細資訊，請參閱範例。

您傳遞給 Cmdlet 的 **HistoryInfo** 物件檔案 `Add-History` 必須包含類型資訊、資料行標題，以及 **HistoryInfo** 物件的所有屬性。 如果您想要將物件傳遞回 `Add-History` ，請不要使用 Cmdlet 的 **NoTypeInformation** 參數，也不 `Export-Csv` 會刪除檔案中的類型資訊、欄標題或任何欄位。

若要修改會話歷程記錄，請將會話匯出至 CSV 或 XML 檔案、修改檔案、匯入檔案，然後使用 `Add-History` 將它附加至目前的會話歷程記錄。

## 相關連結

[Clear-History](Clear-History.md)

[Get-History](Get-History.md)

[Invoke-History](Invoke-History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[設定-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)
