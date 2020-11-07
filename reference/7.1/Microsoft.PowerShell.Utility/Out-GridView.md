---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 840aa38ff17ceaf7dc65ca838da020c3d8c27952
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344383"
---
# Out-GridView

## 概要
將輸出傳送到另一個視窗中的互動式表格。

## SYNTAX

### PassThru (預設值)

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### 等候

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### OutputMode

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## DESCRIPTION

`Out-GridView`Cmdlet 會將命令的輸出傳送至格線視圖視窗，其中的輸出會顯示在互動式資料表中。

由於此 Cmdlet 需要使用者介面，因此無法在 Windows Server Core 或 Windows Nano Server 上運作。

您可以使用下列表格功能來檢查您的資料：

- 隱藏、顯示及重新排列資料行
- 排序資料列
- 快速篩選器
- 新增準則篩選
- 複製和貼上

如需完整指示，請參閱本文的「 [附注](#notes) 」一節。

> [!NOTE]
> PowerShell 7 中已重新引入此 Cmdlet。 只有支援 Windows 桌面的 Windows 系統才能使用此 Cmdlet。 如需此 Cmdlet 的跨平臺版本，請參閱 PowerShell 資源庫中的 [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) 模組。

## 範例

### 範例1：將進程輸出至方格視圖

這個範例會取得在本機電腦上執行的處理常式，並將它們傳送至方格視圖視窗。

```powershell
Get-Process | Out-GridView
```

### 範例2：使用變數將進程輸出至方格視圖

此範例也會取得在本機電腦上執行的處理常式，並將它們傳送至方格視圖視窗。

```powershell
$P = Get-Process
$P | Out-GridView
```

Cmdlet 的輸出 `Get-Process` 會儲存在 `$P` 變數中。 然後， `$P` 會輸送至 `Out-GridView` 。

### 範例3：在格線視圖中顯示選取的屬性

此範例會在格線視圖中顯示正在執行之進程的已選取屬性。

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

的輸出 `Get-Process` 會以管道傳送至， `Select-Object` 以選取 [ ******名稱** ]、[工作集] 和 [ **PeakWorkingSet** ] 屬性。 另一個管線運算子會將篩選的物件傳送至 `Sort-Object` Cmdlet，以依工作集屬性的值以 **WorkingSet** 遞減順序排序它們。
然後，排序的結果會輸送至 `Out-GridView` 。 您現在已經可以使用資料格檢視的功能來搜尋、排序及篩選資料。

### 範例4：將輸出儲存至變數，然後輸出方格視圖

此範例會將 Cmdlet 輸出儲存在變數中，然後將它傳送至 `Out-GridView` 。

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

`Get-ChildItem` 使用自動變數，取得 PowerShell 安裝目錄及其子目錄中的所有檔案 `$PSHOME` 。 命令中的括號會確立操作的順序。 因此，命令的輸出 `Get-ChildItem` 會先儲存在變數中， `$A` 然後再傳送至 `Out-GridView` 。

### 範例5：將指定電腦的輸出流程輸出至方格視圖

此範例會在格線視圖視窗中顯示在 Server01 電腦上執行的處理常式。

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

範例會使用 `ogv` ，這是 Cmdlet 的別名 `Out-GridView` 。 **Title** 參數指定視窗標題。

### 範例6：將遠端電腦的資料輸出至方格視圖

此範例示範如何將從遠端電腦收集的資料傳送至 `Out-GridView` 。

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

`Invoke-Command` 會 `Get-Culture` 在三部遠端電腦上執行。 產生的資料會以管道傳送至 `Out-GridView` 。 請注意，在遠端電腦上執行的腳本區塊不包含 `Out-GridView` 命令。 如果有包含，當此命令嘗試在每一部遠端電腦上開啟資料格檢視視窗時，將會失敗。

### 範例7：傳遞多個專案至 `Out-GridView`

此範例可讓您從視窗中選取多個進程 `Out-GridView` 。 您選取的進程會傳遞至 `Export-Csv` 命令，並寫入至檔案 `ProcessLog.csv` 。

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

的 **PassThru** 參數 `Out-GridView` 可讓您在管線中傳送多個專案。 **PassThru** 參數等同於使用 **OutputMode** 參數的 **Multiple** 值。

### 範例8：建立 Windows 快捷方式 `Out-GridView`

這個範例會示範如何使用的 **Wait** 參數 `Out-GridView` 來建立視窗的 Windows 快捷方式 `Out-GridView` 。

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

此命令列可以在 Windows 快捷方式中使用。 如果沒有 **Wait** 參數，PowerShell 會在視窗開啟時立即 `Out-GridView` 結束，這會 `Out-GridView` 立即關閉視窗。

## PARAMETERS

### -InputObject

指定 Cmdlet 接受做為輸入的物件 `Out-GridView` 。

當您使用 **InputObject** 參數將物件的集合傳送至時 `Out-GridView` ， `Out-GridView` 會將該集合視為一個集合物件，並且會顯示一個代表集合的資料列。 若要顯示集合中的每個物件，請使用管線運算子 (`|`) 傳送物件至 `Out-GridView` 。

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

### -OutputMode

指定互動式視窗向下傳送管線的專案，做為其他命令的輸入。
根據預設，此 Cmdlet 不會產生任何輸出。 若要從互動式視窗將項目沿著管線向下傳送，請按一下項目來進行選取，然後按一下 [確定]。

這個參數的值會決定您可以沿著管線向下傳送的項目數。

- 無。  沒有項目。 這是預設值。
- 單一。 零個項目或一個項目。 如果下一個命令只能接受一個輸入物件，請使用這個值。
- 多個。 零個、一個或許多個項目。 如果下一個命令可以接受多個輸入物件，請使用這個值。 這個值相當於 **Passthru** 參數。

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

指出此 Cmdlet 會將專案從互動式視窗沿著管線向下傳送，以做為其他命令的輸入。 根據預設，此 Cmdlet 不會產生任何輸出。 這個參數等同於使用 **OutputMode** 參數的 **Multiple** 值。

若要從互動式視窗將項目沿著管線向下傳送，請按一下項目來進行選取，然後按一下 [確定]。 支援按住 Shift 鍵並按一下滑鼠左鍵及按住 Ctrl 鍵並按一下滑鼠左鍵來進行選取。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Title

指定出現在視窗標題列中的文字 `Out-GridView` 。 依預設，標題列會顯示叫用的命令 `Out-GridView` 。

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

### -Wait

指出此 Cmdlet 會抑制命令提示字元，並防止 Windows PowerShell 關閉，直到 `Out-GridView` 視窗關閉為止。 依預設，當視窗開啟時，會傳回命令提示字元 `Out-GridView` 。

這項功能可讓您 `Out-GridView` 在 Windows 快捷方式中使用 Cmdlet。 當 `Out-GridView` 在沒有 **Wait** 參數的快捷方式中使用時， `Out-GridView` 視窗只會在 PowerShell 關閉之前短暫顯示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以將任何物件傳送至此 Cmdlet。

## 輸出

### None

通常 `Out-GridView` 不會傳回任何物件。 使用 **PassThru** 參數時，代表選取資料列的物件會傳回至管線。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

您無法使用遠端命令在另一部電腦上開啟資料格檢視視窗。

您傳送給的命令輸出 `Out-GridView` 無法使用 Cmdlet 來格式化 `Format` ，例如 `Format-Table` 或 `Format-Wide` Cmdlet。 若要選取屬性，請使用 `Select-Object` Cmdlet。

來自遠端命令的已還原序列化輸出在資料格檢視中可能無法正確格式化。

**的鍵盤快速鍵**`Out-GridView`

|              使用此按鍵：              |                                   可執行此動作：                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <kbd>索引標籤</kbd>                          | 將游標從 [ **篩選** ] 方塊移到 [ **新增條件** ] 功能表，再移回資料表。 |
| <kbd>UpArrow</kbd>                      | 上移一列。 從資料的第一個資料列移至資料行標頭。                             |
| <kbd>Download-downarrow-circled</kbd>                    | 向下移動一個資料列。                                                                           |
| <kbd>LeftArrow</kbd>                    | 在資料行標頭資料列中，向左移動一欄。                                                  |
| <kbd>向右鍵</kbd>                   | 在資料行標頭資料列中，向右移動一欄。                                                 |
| <kbd>CoNtextMenuKey</kbd>               | 在 [資料行標頭資料列] 中，顯示 [選取欄位] 選項。                                    |
| <kbd>Enter</kbd> 或 <kbd>空格鍵</kbd> | 在資料行標頭資料列中，將資料行資料排序 (切換 a-z、Z-A) 。                                    |

**如何使用格線視圖視窗功能**

**隱藏或顯示欄位：**

1. 以滑鼠右鍵按一下任何欄標題，然後按一下 [ **選取資料行** ]。
2. 在 [ **選取資料行** ] 對話方塊中，使用方向鍵將選取之資料行之間的資料行移至 [可用的資料行] 方塊。 格線視圖視窗中只會顯示 [ **選取資料行** ] 方塊中的資料行。

**重新排列欄位：**

您可以將資料行拖放到所需的位置。 或者，使用下列步驟：

1. 以滑鼠右鍵按一下任何欄標題，然後按一下 [ **選取資料行** ]。
2. 在 [ **選取資料行** ] 對話方塊中，使用 [ **上移** ] 和 **[下移] 按鈕來** 重新排列資料行。 清單頂端的欄位在資料格檢視視窗中會顯示在清單底部欄位的左邊。

**如何排序表格資料**

- 若要排序資料，請按一下欄標題。
- 若要變更排序順序，請再按一下欄標題。 每次按一下相同的標題，排序順序就會在遞增順序與遞減順序之間切換。 欄標題中的三角形表示目前的順序。

**如何選取表格資料**

- 若要選取資料列，請選取資料列，或使用向上或向下箭號來流覽至資料列。
- 若要選取除了標頭資料列) 以外的所有資料列 (，請按下<kbd>CTRL</kbd> + <kbd>鍵</kbd>。
- 若要選取連續的資料列，請按住 <kbd>SHIFT</kbd> 鍵，同時按一下資料列或使用方向鍵。
- 若要選取不連續的資料列，請按 <kbd>CTRL</kbd> 鍵，然後按一下將資料列加入至選取專案。
- 您無法選取欄位，也無法選取整個欄標題列。

**如何複製列**

- 若要從表格複製一列或多列，請選取那些列，然後按 CTRL+C。

  您可以將資料貼到任何文字或試算表程式中。 您無法複製欄位或或列的部分，也無法複製欄標題列。

**如何在資料表中搜尋 (快速篩選)**

您可以使用 [篩選] 方塊來搜尋資料表中的資料。 在方塊中輸入時，只有包含輸入之文字的項目才會顯示在表格中。

- 搜尋文字。 若要搜尋表格中的文字，請在 [篩選] 方塊中輸入要尋找的文字。
- 搜尋多個字。 若要搜尋表格中的多個字，請輸入文字並以空格分隔。 `Out-GridView` 顯示包含所有文字 (邏輯 AND) 的資料列。
- 搜尋片語。 若要搜尋包含空格或特殊字元的片語，請以引號括住該片語。 `Out-GridView` 顯示包含片語完全相符的資料列。
- 在欄位中搜尋。 若要在一個或多個欄位中搜尋文字，請使用下列格式：

  `<column>:<text> [<column>:<text>] ...`

  例如，若要在 **DisplayName** 欄位中尋找 "Net"，請在 [ **篩選** ] 方塊中輸入：

  `displayname:net`

  若要在 [ **DisplayName** ] 和 [ **名稱** ] 資料行中尋找 "Net" 的資料列，請在 [ **篩選** ] 方塊中輸入：

  `displayname:net name:net`

- 關閉搜尋。 若要再次顯示整份資料表，請按一下 [ **篩選** ] 方塊右上角的 [紅色 X] 按鈕，或從 [ **篩選** ] 方塊中刪除文字。

**使用條件來篩選表格**

您可以使用規則或準則來判斷哪些專案要顯示在資料表中。 只有當專案滿足您所建立的所有條件時，才會出現這些專案。 可用的條件取決於資料格檢視視窗中所顯示之物件的屬性，以及這些屬性的 .NET Framework 類別。

每個條件都具有下列格式：

`<column> <operator> <value>`

不同屬性的準則是由 **和** 連接。 相同屬性的準則是由 **或** 連接。 您無法變更邏輯連接子。

條件只會影響顯示。 它不會將項目從表格中刪除。

**如何新增條件**

1. 若要顯示 [ **新增條件** ] 功能表按鈕，請按一下視窗右上角的展開箭號。
2. 按一下 [ **新增條件** ] 功能表按鈕。
3. 按一下來選取欄位 (屬性)。 您可以選取一個或多個屬性。
4. 當您完成選取 [屬性] 時，按一下 [ **加入** ] 按鈕。
5. 若要取消新增，請按一下 [ **取消** ]。
6. 若要新增更多條件，請再按一下 [ **新增條件** ] 按鈕。

**如何編輯條件**

- 若要變更運算子，請按一下藍色運算子值，然後從下拉式清單中選取不同的運算子。
- 若要輸入或變更某個值，請在值方塊中輸入值。 如果輸入的值無效，就會顯示圓形的 X 圖示。 若要將它移除，請變更該值。
- 若要建立 **或** 語句，請新增具有相同屬性的條件。

**如何刪除條件**

- 若要刪除選取的條件，請按一下每個條件旁邊的紅色 X。
- 若要刪除所有條件，請按一下 [ **全部清除** ] 按鈕。

## 相關連結

[Out-File](Out-File.md)

[Out-Printer](Out-Printer.md)

[Out-String](Out-String.md)

