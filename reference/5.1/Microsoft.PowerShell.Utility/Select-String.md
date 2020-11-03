---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 95601a4f5f42700c4de7d6ad721ee898b22bab84
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206107"
---
# Select-String

## 概要
尋找字串和檔案中的文字。

## SYNTAX

### File (預設值)

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### Object

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFile

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

## DESCRIPTION

此 `Select-String` Cmdlet 會搜尋輸入字串和檔案中的文字和文字模式。 您可以使用 `Select-String` 類似于 UNIX 中的 **Grep** 或 Windows 中的 **findstr.exe** 。

`Select-String` 以文字行為基礎。 依預設， `Select-String` 會在每一行中尋找第一個相符項，而且每個相符項都會顯示檔案名、行號，以及行中包含相符項的所有文字。 您可以導向 `Select-String` 找出每行的多個相符專案、顯示相符專案之前和之後的文字，或是顯示 (True 或 False 的布林值) 指出是否找到相符專案。

`Select-String` 使用正則運算式比對，但它也可以執行比對，在輸入中搜尋您所指定的文字。

`Select-String` 可以顯示所有文字相符專案，或在每個輸入檔案中的第一個相符專案之後停止。
`Select-String` 可以用來顯示所有不符合指定模式的文字。

您也可以指定 `Select-String` 應該預期特定字元編碼，例如當您搜尋 Unicode 文字的檔案時。 `Select-String` 使用位元組順序標記 (BOM) 來偵測檔案的編碼格式。 如果檔案沒有 BOM，則會假設編碼為 UTF8。

## 範例

### 範例1：尋找區分大小寫的相符項

此範例會對從管線傳送到 Cmdlet 的文字進行區分大小寫的比對 `Select-String` 。

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

文字字串 **Hello** 和 **Hello** 會向下傳送至 `Select-String` Cmdlet。
`Select-String` 使用 **Pattern** 參數指定 **HELLO** 。 **CaseSensitive** 參數指定案例必須僅符合大寫模式。 **SimpleMatch** 是選擇性參數，可指定模式中的字串不會被視為正則運算式。
`Select-String` 在 PowerShell 主控台中顯示 **HELLO** 。

### 範例2：在文字檔中尋找相符專案

此命令會 `.txt` 在目前目錄中搜尋副檔名為的所有檔案。 輸出會顯示這些檔案中包含指定字串的行。

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

在此範例中， `Get-Alias` 和 `Get-Command` 會與 Cmdlet 搭配使用 `Out-File` ，以在目前的目錄中建立兩個文字檔， **Alias.txt** 和 **Command.txt** 。

`Select-String` 使用 **Path** 參數搭配星號 (`*`) 萬用字元來搜尋目前目錄中副檔名為的所有檔案 `.txt` 。 **Pattern** 參數指定要與 **Get** 相符的文字。 `Select-String` 在 PowerShell 主控台中顯示輸出。 檔案名和行號會在包含 **模式** 參數相符項的每一行內容前面。

### 範例3：尋找模式相符

在此範例中，會搜尋多個檔案，以尋找指定模式的相符專案。 此模式會使用正則運算式數量詞。 如需詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)。

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

此 `Select-String` Cmdlet 會使用兩個參數： **路徑** 和 **模式** 。 **Path** 參數 `$PSHOME` 會使用指定 PowerShell 目錄的變數。 路徑的其餘部分包含子目錄 **en-us** ，並指定目錄中的每個檔案 `*.txt` 。 **Pattern** 參數指定要符合每個檔案中的問號 (`?`) 。 使用反斜線 (`\`) 作為 escape 字元，而且是必要的，因為問號 (`?`) 是正則運算式數量詞。 `Select-String` 在 PowerShell 主控台中顯示輸出。 檔案名和行號會在包含 **模式** 參數相符項的每一行內容前面。

### 範例4：在函式中使用 Select-String

這個範例會建立一個函式，以搜尋 PowerShell 說明檔中的模式。 在此範例中，此函式只存在於 PowerShell 會話中。 當 PowerShell 會話關閉時，就會刪除該函式。 如需詳細資訊，請參閱 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)。

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:2:   about_ActivityCommonParameters
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:31:  see about_WorkflowCommonParameters.
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:33:  about_CommonParameters.
```

函式會建立在 PowerShell 命令列上。 此 `Function` 命令會使用名稱 **搜尋-Help** 。 按 **enter** 鍵，開始將語句新增至函式。 從 `>>` 提示字元加入每個語句，然後按下 **enter** ，如範例所示。 新增右括弧之後，您會回到 PowerShell 提示字元。

函數包含兩個命令。 `$PSHelp`變數會儲存 PowerShell 說明檔的路徑。 `$PSHOME` 是具有子目錄 **en-us** 的 PowerShell 安裝目錄，指定目錄中的每個檔案 `*.txt` 。

`Select-String`函數中的命令會使用 **路徑** 和 **模式** 參數。 **Path** 參數會使用 `$PSHelp` 變數來取得路徑。 **Pattern** 參數會使用字串 **About_** 作為搜尋準則。

若要執行函數，請輸入 `Search-Help` 。 函數的 `Select-String` 命令會在 PowerShell 主控台中顯示輸出。

### 範例5：在 Windows 事件記錄檔中搜尋字串

此範例會在 Windows 事件記錄檔中搜尋字串。 變數 `$_` 代表管線中的目前物件。 如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

此 `Get-WinEvent` Cmdlet 會使用 **LogName** 參數來指定應用程式記錄檔。 **MaxEvents** 參數會從記錄檔中取得50最新的事件。 記錄內容會儲存在名為的變數中 `$Events` 。

此 `$Events` 變數會向下傳送至 `Select-String` Cmdlet。 `Select-String` 使用 **InputObject** 參數。 `$_`變數代表目前的物件，而且 `message` 是事件的屬性。 **Pattern** 參數物種字串 **失敗** ，並在中搜尋相符專案 `$_.message` 。 `Select-String` 在 PowerShell 主控台中顯示輸出。

### 範例6：在子目錄中尋找字串

此範例會在目錄及其所有子目錄中搜尋特定的文字字串。

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

`Get-ChildItem` 使用 **Path** 參數來指定 **C:\Windows\System32 \* .txt** 。 **遞迴** 參數包含子目錄。 物件會向下傳送到管線 `Select-String` 。

`Select-String` 使用 **Pattern** 參數，並指定 **Microsoft** 字串。 **CaseSensitive** 參數是用來符合字串的確切大小寫。 `Select-String` 在 PowerShell 主控台中顯示輸出。

> [!NOTE]
> 根據您的許可權，您可能會在輸出中看到 **拒絕存取** 訊息。

### 範例7：尋找不符合模式的字串

此範例顯示如何排除不符合模式的資料行。

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

`Get-Command`Cmdlet 會將物件沿著管線向下傳送至， `Out-File` 以在目前的目錄中建立 **Command.txt** 檔案。 `Select-String` 使用 **Path** 參數來指定 **Command.txt** 檔。 **Pattern** 參數會指定 **Get** 和 **Set** 做為搜尋模式。 **NotMatch** 參數會將 **Get** 和 **Set** 從結果中排除。
`Select-String` 在 PowerShell 主控台中顯示未包含 **Get** 或 **Set** 的輸出。

### 範例8：在相符的前後尋找行

此範例示範如何取得相符模式前後的行。

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:1186:Cmdlet          Get-CmsMessage            3.0.0.0    Microsoft.PowerShell.Security
  Command.txt:1187:Cmdlet          Get-Command               3.0.0.0    Microsoft.PowerShell.Core
> Command.txt:1188:Cmdlet          Get-ComputerInfo          3.1.0.0    Microsoft.PowerShell.Management
> Command.txt:1189:Cmdlet          Get-ComputerRestorePoint  3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1190:Cmdlet          Get-Content               3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1191:Cmdlet          Get-ControlPanelItem      3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1192:Cmdlet          Get-Counter               3.0.0.0    Microsoft.PowerShell.Diagnostics
```

`Get-Command`Cmdlet 會將物件沿著管線向下傳送至， `Out-File` 以在目前的目錄中建立 **Command.txt** 檔案。 `Select-String` 使用 **Path** 參數來指定 **Command.txt** 檔。 **Pattern** 參數會將 **Get 電腦** 指定為搜尋模式。 **內容** 參數會使用兩個值，前後都有兩個值，並以角括弧 () 來標記輸出中的模式相符 `>` 。 **CoNtext** 參數會輸出第一個模式比對之前的兩行，並在最後一個模式相符之後輸出三行。

### 範例9：尋找所有模式相符專案

此範例示範 **AllMatches** 參數如何在文字行中尋找每個模式相符。 依預設， `Select-String` 只會在文字行中尋找第一次出現的模式。 這個範例會使用以 Cmdlet 找到的物件屬性 `Get-Member` 。

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:5:    Describes the parameters that Windows PowerShell
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:9:    Windows PowerShell Workflow adds the activity common

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

2073

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

2200
```

此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數。 **Path** 參數 `$PSHOME` 會使用指定 PowerShell 目錄的變數。 路徑的其餘部分包含子目錄 **en-us** ，並指定目錄中的每個檔案 `*.txt` 。 `Get-ChildItem`物件會儲存在變數中 `$A` 。 此 `$A` 變數會向下傳送至 `Select-String` Cmdlet。 `Select-String` 使用 **Pattern** 參數來搜尋字串 **PowerShell** 的每個檔案。

從 PowerShell 命令列中， `$A` 會顯示變數內容。 有一個包含兩次字串 **PowerShell** 的行。

`$A.Matches`屬性會列出每一行上第一次出現的模式 **PowerShell** 。

`$A.Matches.Length`屬性會計算每一行上第一次出現的模式 **PowerShell** 。

`$B`變數使用相同的 `Get-ChildItem` 和 `Select-String` Cmdlet，但會新增 **AllMatches** 參數。 **AllMatches** 會在每一行找出每個出現的模式 **PowerShell** 。 和變數中所儲存的物件 `$A` `$B` 是相同的。

`$B.Matches.Length`屬性會增加，因為每一行都會計算模式 **PowerShell** 的每個出現次數。

## PARAMETERS

### -AllMatches

指出此 Cmdlet 會在每一行文字中搜尋一個以上的相符項。 如果沒有這個參數， `Select-String` 只會在每一行文字中尋找第一個相符的內容。

當 `Select-String` 在一行文字中找到一個以上的相符專案時，它仍然只會為該行發出一個 **MatchInfo** 物件，但是 **Matches** 物件的 match 屬性會包含所有相符專案。

> [!NOTE]
> 搭配 **SimpleMatch** 參數使用時，會忽略這個參數。 如果您想要傳回所有相符專案，以及您要搜尋的模式包含正則運算式字元，您必須將這些字元轉義，而不是使用 **SimpleMatch** 。 如需有關如何轉義正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 。

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

### -CaseSensitive

指出 Cmdlet 相符專案區分大小寫。 依預設，相符專案不區分大小寫。

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

### -Context

在符合模式的行之前和之後捕獲指定的行數。

如果您輸入一個數字做為此參數的值，該數字會決定相符項目之前與之後擷取的行數。 如果您輸入兩個數字做為該值，第一個數字會決定相符項目之前的行數，而第二個數字會決定相符項目之後的行數。 例如： `-Context 2,3` 。

在預設顯示中，具有相符的行會以右角括弧表示， (`>`) 在顯示的第一個資料行中 (ASCII 62) 。 未標記的行是上下文。

**CoNtext** 參數不會變更所產生的物件數目 `Select-String` 。
`Select-String` 針對每個相符各產生一個 [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 物件。 內容會以字串陣列的形式儲存在物件的 **coNtext** 屬性中。

當命令的輸出向 `Select-String` 下傳送到另一個 `Select-String` 命令時，接收命令只會搜尋相符行中的文字。 符合的行是 **MatchInfo** 物件的 **line** 屬性值，而不是內容行中的文字。 因此， **內容** 參數在接收命令上無效 `Select-String` 。

當內容包含比對時，每個相符項的 **MatchInfo** 物件都會包含所有內容行，但是重迭行只會在顯示中出現一次。

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定目標檔案的編碼類型。 預設值是 `default`。

此參數可接受的值如下：

- `ascii` 使用 ASCII (7 位) 字元集。
- `bigendianunicode` 以位元組由大到小的順序使用 UTF-16。
- `default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。
- `oem` 使用對應至系統目前 OEM 字碼頁的編碼方式。
- `unicode` 使用 UTF-16 和位元組由小到小的位元組順序。
- `utf7` 使用 UTF-7。
- `utf8` 使用 UTF-8。
- `utf32` 以位元組由小到大的位元組順序使用 UTF-32。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

排除指定的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。

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

包含指定的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。

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

### -InputObject

指定要搜尋的文字。 輸入包含文字的變數，或輸入可取得文字的命令或運算式。

使用 **InputObject** 參數和將字串向下傳送至時不同 `Select-String` 。

當您將多個字串輸送至 `Select-String` Cmdlet 時，它會在每個字串中搜尋指定的文字，並傳回包含搜尋文字的每個字串。

當您使用 **InputObject** 參數提交字串集合時，會 `Select-String` 將集合視為單一合併字串。 `Select-String` 如果在任何字串中找到搜尋文字，則會以單位形式傳回字串。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -List

每個輸入檔只會傳回相符文字的第一個實例。 這是取得具有符合正則運算式之內容的檔案清單最有效率的方式。

根據預設， `Select-String` 會針對找到的每個相符項傳回 **MatchInfo** 物件。

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

### -LiteralPath

指定要搜尋之檔案的路徑。 **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。 如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NotMatch

**NotMatch** 參數會尋找不符合指定模式的文字。

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

### -Path

指定要搜尋之檔案的路徑。 允許使用萬用字元。 預設位置是本機目錄。

指定目錄中的檔案，例如 `log1.txt` 、 `*.doc` 或 `*.*` 。 如果您只指定目錄，則命令會失敗。

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Pattern

指定要在每一行上尋找的文字。 模式值會被視為正則運算式。

若要深入瞭解正則運算式，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

指出此 Cmdlet 會傳回布林值 (True 或 False) ，而不是 **MatchInfo** 物件。 如果找到模式，則值為 True。否則，此值為 False。

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

### -SimpleMatch

指出此 Cmdlet 會使用簡單比對，而不是正則運算式相符項。 在簡單的比對中，會在 `Select-String` 輸入中搜尋 **Pattern** 參數的文字。 它不會將 **Pattern** 參數的值解讀為正則運算式語句。

此外，當使用 **SimpleMatch** 時，所傳回之 **MatchInfo** 物件的 [ **符合** ] 屬性會是空的。

> [!NOTE]
> 當此參數搭配 **AllMatches** 參數使用時，會忽略 **AllMatches** 。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以使用管線將具有 **ToString** 方法的任何物件傳送至 `Select-String` 。

## 輸出

### Microsoft.PowerShell.Commands.MatchInfo 或 System.Boolean

根據預設，輸出是一組 **MatchInfo** 物件，每個找到的相符項都有一個物件。 如果您使用 **Quiet** 參數，則輸出會是布林值，指出是否已找到模式。

## 注意

`Select-String` 類似于 UNIX 中的 **grep** 或 Windows 中的 **findstr.exe** 。

Cmdlet 的 **sls** 別名 `Select-String` 是在 PowerShell 3.0 中引進。

> [!NOTE]
> 根據 [PowerShell 命令的已核准動詞](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)，Cmdlet 的官方別名前置詞 `Select-*` 為 `sc` ，而不是 `sl` 。 因此，適當的別名 `Select-String` 應該是 `scs` ，而不是 `sls` 。 這是此規則的例外狀況。

若要使用 `Select-String` ，請輸入您想要尋找的文字做為 **Pattern** 參數的值。 若要指定要搜尋的文字，請使用下列準則：

- 在加上引號的字串中輸入文字，然後使用管線將它傳送至 `Select-String` 。
- 在變數中儲存文字字串，然後將變數指定為 **InputObject** 參數的值。
- 如果文字儲存在檔案中，請使用 **path** 參數來指定檔案的路徑。

依預設，會將 `Select-String` **Pattern** 參數的值解釋為正則運算式。 如需詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。 您可以使用 **SimpleMatch** 參數來覆寫正則運算式比對。 **SimpleMatch** 參數會尋找輸入中 **Pattern** 參數值的實例。

的預設輸出 `Select-String` 是 **MatchInfo** 物件，其中包含相符專案的詳細資訊。 當您搜尋檔案中的文字時，物件中的資訊會很有用，因為 **MatchInfo** 物件具有像是 **Filename** 與 **Line** 等屬性。 當輸入不是來自檔案時，這些參數的值會是 **InputStream** 。

如果您不需要 **MatchInfo** 物件中的資訊，請使用 **Quiet** 參數。 **Quiet** 參數會傳回布林值 (True 或 False) 來指出它是否找到相符的，而不是 **MatchInfo** 物件。

當比對片語時， `Select-String` 會使用針對系統所設定的目前文化特性。 若要尋找目前的文化特性，請使用 `Get-Culture` Cmdlet。

若要尋找 **MatchInfo** 物件的屬性，請輸入下列命令：

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## 相關連結

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[Get-Alias](Get-Alias.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-Command](../Microsoft.PowerShell.Core/Get-Command.md)

[Get-Member](Get-Member.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Out-File](Out-File.md)
