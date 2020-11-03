---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: 4c1c6712966d78f9af4f0c1ff181bf1869c01eea
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208772"
---
# Set-PSReadLineOption

## 概要
自訂 **PSReadLine** 中的命令列編輯行為。

## 語法

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [-PredictionSource <PredictionSource>]
 [<CommonParameters>]
```

## 描述

`Set-PSReadLineOption`當您編輯命令行時，此 Cmdlet 會自訂 **PSReadLine** 模組的行為。 若要查看 **PSReadLine** 設定，請使用 `Get-PSReadLineOption` 。

## 範例

### 範例1：設定前景和背景色彩

此範例會將 **PSReadLine** 設定為以灰色背景顯示具有綠色前景文字的 **批註** 標記。 在範例中使用的 escape 序列中， **32** 代表前景色彩，而 **47** 代表背景色彩。

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

您可以選擇只設定前景文字色彩。 例如， **批註** 標記的淺綠色前景文字色彩： ``"Comment"="`e[92m"`` 。

### 範例2：設定鐘樣式

在此範例中， **PSReadLine** 會回應需要使用者注意的錯誤或狀況。
**BellStyle** 會設定為在 1221 Hz 發出60毫秒的嗶聲。

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> 這項功能可能不適用於平臺上的所有主機。

### 範例3：設定多個選項

`Set-PSReadLineOption` 可以使用雜湊表來設定多個選項。

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

`$PSReadLineOptions`雜湊表會設定索引鍵和值。 `Set-PSReadLineOption` 使用的索引鍵和值 `@PSReadLineOptions` 來更新 **PSReadLine** 選項。

您可以 `$PSReadLineOptions` 在 PowerShell 命令列上，看到輸入雜湊表名稱的索引鍵和值。

### 範例4：設定多個色彩選項

此範例示範如何在單一命令中設定一個以上的色彩值。

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### 範例5：設定多個類型的色彩值

此範例顯示三種不同的方法，說明如何設定 **PSReadLine** 中顯示的權杖色彩。

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### 範例6：使用 ViModeChangeHandler 來顯示 Vi 模式變更

此範例會發出資料指標變更 VT escape，以回應 **Vi** 模式變更。

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

**OnViModeChange** 函數會設定 **Vi** 模式的資料指標選項： insert 和 command。
**ViModeChangeHandler** 會使用 `Function:` 提供者將 **OnViModeChange** 參考為腳本區塊物件。

如需詳細資訊，請參閱 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。

## 參數

### -AddToHistoryHandler

指定 **ScriptBlock** ，以控制要將哪些命令新增至 **PSReadLine** 歷程記錄。

**ScriptBlock** 會接收命令列做為輸入。 如果 **ScriptBlock** 傳回 `$True` ，則會將命令列新增至歷程記錄。

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AnsiEscapeTimeout

當重新導向輸入時（例如，在或下執行時），這個選項是 Windows 專用的 `tmux` `screen` 。

在 Windows 上重新導向的輸入，會以字元序列（開頭為 escape 字元）來傳送許多金鑰。 您無法區分後面接著更多字元和有效 escape 序列的單一 escape 字元。

假設終端機可以比使用者類型更快傳送字元。 **PSReadLine** 會在結束之前等候這個超時，直到它收到完整的 escape 序列。

如果您在輸入時看到隨機或非預期的字元，您可以調整此超時時間。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -BellStyle

指定 **PSReadLine** 如何回應各種錯誤和不明確的狀況。

有效值如下：

- **聲音** ：短暫的嗶聲。
- **視覺效果** ：文字短暫閃爍。
- **無** ：無意見反應。

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### -色彩

**Colors** 參數會指定 **PSReadLine** 所使用的各種色彩。

引數是一個雜湊表，其中的索引鍵會指定哪個元素和值來指定色彩。
如需詳細資訊，請參閱 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。

例如，色彩可以是來自 **ConsoleColor** 的值， `[ConsoleColor]::Red` 或有效的 ANSI escape 序列。 有效的 escape 序列取決於您的終端機。 在 PowerShell 5.0 中，紅色文字的範例 escape 序列是 `$([char]0x1b)[91m` 。 在 PowerShell 6 和更新版本中，相同的 escape 序列是 `` `e[91m`` 。 您可以指定其他的 escape 序列，包括下列類型：

- 256色彩
- 24位色彩
- 前景、背景或兩者
- 反向、粗體

如需 ANSI 色彩代碼的詳細資訊，請參閱維琪百科的 [ansi escape 程式碼](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 。

有效的索引鍵包括：

- **ContinuationPrompt** ：接續提示的色彩。
- **強調** ：強調色彩。 例如，搜尋歷程記錄時的相符文字。
- **錯誤** ：錯誤色彩。 例如，在提示字元中。
- **選取範圍** ：反白顯示功能表選取專案或選取文字的色彩。
- **預設** 值：預設標記色彩。
- **批註** ：註解標記色彩。
- **關鍵字** ：關鍵字標記色彩。
- **字串** ：字串標記色彩。
- **運算子** ：運算子標記色彩。
- **變數** ：變數標記色彩。
- **命令** ：命令標記色彩。
- **參數** ：參數標記色彩。
- **類型** ：類型標記色彩。
- **數位** ：數位標記色彩。
- **成員** ：成員名稱標記色彩。
- **InlinePrediction** ：預測性建議內嵌視圖的色彩。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandValidationHandler

指定從 **ValidateAndAcceptLine** 呼叫的 **ScriptBlock** 。 如果擲回例外狀況，驗證就會失敗，並回報錯誤。

在擲回例外狀況之前，驗證處理常式可以將游標放在錯誤的位置，以便更輕鬆地進行修正。 驗證處理常式也可以變更命令列，例如修正常見的打字錯誤。

**ValidateAndAcceptLine** 是用來避免您的歷程記錄無法運作的命令。

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompletionQueryItems

指定在不提示的情況下顯示的完成專案數目上限。

如果要顯示的專案數大於此值， **PSReadLine** 會在顯示完成專案之前提示 **[是]/[否]** 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContinuationPrompt

指定輸入多行輸入時，在後續行開頭顯示的字串。 預設值為 () 的雙重大於正負號 `>>` 。 空字串是有效的。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingDuration

指定當 **BellStyle** 設定為可 **聽見** 時，嗶聲的持續時間。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### -DingTone

指定當 **BellStyle** 設定為可 **聽見** 時，嗶聲的音調（以赫茲為單位） (Hz) 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### -EditMode

指定命令列編輯模式。 使用這個參數會重設任何由設定的按鍵系結 `Set-PSReadLineKeyHandler` 。

有效值如下：

- **Windows** ：金鑰系結會模擬 PowerShell、cmd 及 Visual Studio。
- **Emacs** ： Key bindings 會模擬 Bash 或 Emacs。
- **Vi** ：金鑰系結會模擬 Vi。

使用 `Get-PSReadLineKeyHandler` 以查看目前設定之 **EditMode** 的索引鍵系結。

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExtraPromptLineCount

指定額外的行數。

如果您的提示橫跨一行以上，請指定此參數的值。 當您想要在顯示某些輸出之後， **PSReadLine** 顯示提示時，可使用額外的行時，請使用此選項。 例如， **PSReadLine** 會傳回完成的清單。

在舊版 **PSReadLine** 中需要此選項，但在使用函式時很有用 `InvokePrompt` 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistoryNoDuplicates

此選項會控制重新叫用行為。 重複的命令仍會新增至歷程記錄檔案。
當設定此選項時，重新叫用命令時只會顯示最新的調用。 重複的命令會新增至歷程記錄，以便在召回期間保留順序。 不過，在重新叫用或搜尋歷程記錄時，您通常不會想要多次看到命令。

根據預設，global **PSConsoleReadLineOptions** 物件的 **HistoryNoDuplicates** 屬性會設定為 `True` 。 使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。 若要變更屬性值，您必須指定 **SwitchParameter** 的值，如下所示： `-HistoryNoDuplicates:$False` 。

您可以使用下列命令，直接設定屬性值：

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySavePath

指定儲存記錄之檔案的路徑。 執行 Windows 或非 Windows 平臺的電腦會將檔案儲存在不同的位置。 例如，檔案名會儲存在變數中 `$($host.Name)_history.txt` `ConsoleHost_history.txt` 。

如果您未使用此參數，預設路徑如下所示：

**Windows**

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

**非 Windows**

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySaveStyle

指定 **PSReadLine** 儲存歷程記錄的方式。

下列是有效值：

- **SaveIncrementally** ：在執行每個命令之後儲存歷程記錄，並在多個 PowerShell 實例之間共用。
- **SaveAtExit** ： PowerShell 結束時附加記錄檔。
- **SaveNothing** ：不使用歷程記錄檔。

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCaseSensitive

指定在 **ReverseSearchHistory** 或 **HistorySearchBackward** 等函式中，記錄搜尋會區分大小寫。

根據預設，global **PSConsoleReadLineOptions** 物件的 **HistorySearchCaseSensitive** 屬性會設定為 `False` 。 使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。 若要將屬性值變更回，您必須指定 **SwitchParameter** 的值，如下所示： `-HistorySearchCaseSensitive:$False` 。

您可以使用下列命令，直接設定屬性值：

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HistorySearchCursorMovesToEnd

指出游標移至您使用搜尋從歷程記錄載入的命令結尾。
當這個參數設定為時 `$False` ，游標會維持在您按下向上鍵或向下箭號時的位置。

根據預設，global **PSConsoleReadLineOptions** 物件的 **HistorySearchCursorMovesToEnd** 屬性會設定為 `False` 。 使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。 若要將屬性值變更回，您必須指定 **SwitchParameter** 的值，如下所示： `-HistorySearchCursorMovesToEnd:$False` 。

您可以使用下列命令，直接設定屬性值：

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumHistoryCount

指定要在 **PSReadLine** 歷程記錄中儲存的命令數目上限。

**PSReadLine** 記錄與 PowerShell 歷程記錄分開。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumKillRingCount

指定儲存在終止環形中的專案數目上限。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -PredictionSource

指定 PSReadLine 的來源，以取得預測性建議。

有效值為：

- **無** ：停用預測性建議功能
- 歷程 **記錄** ：僅從歷程記錄取得預測性建議

```yaml
Type: PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PromptText

發生剖析錯誤時， **PSReadLine** 會將提示的一部分變更為紅色。 **PSReadLine** 會分析您的提示函式，以決定如何只變更部分提示的色彩。 這種分析並不是100% 可靠。

如果 **PSReadLine** 正在以非預期的方式變更您的提示，請使用此選項。 包含任何尾端空白。

例如，如果您的提示函式看起來如下列範例所示：

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

然後設定：

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowToolTips

顯示可能的完成時，工具提示會顯示在完成清單中。

這個選項預設為啟用。 在舊版 **PSReadLine** 中，預設不會啟用此選項。 若要停用，請將此選項設定為 `$False` 。

根據預設，global **PSConsoleReadLineOptions** 物件的 **ShowToolTips** 屬性會設定為 `True` 。 使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。 若要變更屬性值，您必須指定 **SwitchParameter** 的值，如下所示： `-ShowToolTips:$False` 。

您可以使用下列命令，直接設定屬性值：

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeChangeHandler

當 **ViModeIndicator** 設定為時 `Script` ，每次模式變更時，就會叫用提供的腳本區塊。 腳本區塊會提供一個類型的引數 `ViMode` 。

此參數是在 PowerShell 7 中引進。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViModeIndicator

這個選項會設定目前 **Vi** 模式的視覺指示。 請插入模式或命令模式。

有效值如下：

- **無** ：沒有指示。
- **提示** ：提示會變更色彩。
- **Cursor** ：資料指標的大小變更。
- **腳本** ：列印使用者指定的文字。

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WordDelimiters

指定分隔函式（例如 **ForwardWord** 或 **KillWord** ）之單字的字元。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### None

您無法透過管線將物件傳送至 `Set-PSReadLineOption.`

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 備忘稿

## 相關連結

[about_PSReadLine](./About/about_PSReadLine.md)

[PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[PSReadLineOption](Get-PSReadLineOption.md)

[移除-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[設定-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
