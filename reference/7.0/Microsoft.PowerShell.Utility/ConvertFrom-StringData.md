---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: a5f65a70ccb97db5338456cca50309b593b900c1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201747"
---
# ConvertFrom-StringData

## 概要
將包含一或多個索引鍵與值組的字串轉換成雜湊表。

## SYNTAX

### 全部

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-StringData`Cmdlet 會將包含一或多個索引鍵和值組的字串轉換成雜湊表。 因為每個索引鍵/值組都必須位於不同的行上，所以此處的字串通常會用來做為輸入格式。 根據預設，索引 **鍵** 必須以等號 () 字元來與 **值** 分隔 `=` 。

此 `ConvertFrom-StringData` Cmdlet 會被視為安全的 Cmdlet，可以在腳本或函式的區段中使用 `DATA` 。 在區段中使用時 `DATA` ，字串的內容必須符合 DATA 區段的規則。 如需詳細資訊，請參閱 [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)。

`ConvertFrom-StringData` 支援傳統機器翻譯工具所允許的 escape 字元序列。 也就是說，此 Cmdlet 可以 `\` 使用 [Unescape 方法](/dotnet/api/system.text.regularexpressions.regex.unescape)將反斜線 () 為字串資料中的 escape 字元，而不是 \` 通常會在腳本中發出行結尾的 PowerShell 倒引號字元 () 。 在 here-string 內部，倒單引號字元沒有作用。 您也可以使用前面的反斜線（如下所示）將常值反斜線保留在結果中 `\\` 。 未逸出的反斜線字元 (例如通常在檔案路徑中使用的反斜線)，可能會在您的結果中轉譯為無效的逸出序列。

PowerShell 7 會新增 **分隔符號** 參數。

## 範例

### 範例1：將以單引號括住的字串轉換成雜湊表

此範例會將以單引號括住的使用者訊息字串轉換成雜湊表。 在單引號字串中，值不會被變數取代，而且不會評估運算式。
`ConvertFrom-StringData`Cmdlet 會將變數中的值轉換 `$Here` 成雜湊表。

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### 範例2：使用不同的分隔符號來轉換字串資料

此範例示範如何轉換使用不同字元做為分隔符號的字串資料。 在此範例中，字串資料會使用管道字元 (`|`) 作為分隔符號。

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### 範例3：在此轉換包含批註的字串

此範例會將包含批註和多個索引鍵/值組的字串轉換成雜湊表。

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

**至 convertfrom-stringdata** 參數的值是此處的字串，而不是包含此處字串的變數。 任一格式都有效。 here-string 包括一個與其中一個字串有關的註解。
`ConvertFrom-StringData` 忽略單行批註，但 `#` 字元必須是該行的第一個非空白字元。 中的行上的所有字元 `#` 都會被忽略。

### 範例4：將字串轉換成雜湊表

此範例會將正則雙引號的字串 (不是此處的字串) 轉換成雜湊表，並將它儲存在 `$A` 變數中。

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

為了滿足每個索引鍵/值組都必須位於不同行的條件，此字串會使用 PowerShell 分行符號 (\` n) 來分隔配對。

### 範例5：在腳本的 DATA 區段中使用 ConvertFrom-StringData

此範例顯示 `ConvertFrom-StringData` 在腳本的 DATA 區段中使用的命令。
DATA 區段下方的陳述式會向使用者顯示文字。

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

因為文字包括變數名稱，必須在單引號字串中將它括住，才能將變數解譯為常值且不會展開。 **DATA** 區段中不允許使用變數。

### 範例6：使用管線運算子來傳遞字串

此範例顯示您可以使用管線運算子 () 將 `|` 字串傳送至 `ConvertFrom-StringData` 。 變數的值 `$Here` 會以管道傳送至 `ConvertFrom-StringData` 變數中的結果，並產生結果 `$Hash` 。

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### 範例7：使用 escape 字元加入新行和傳回字元

此範例示範如何使用 escape 字元來建立新的行，並傳回來源資料中的字元。 Escape 序列 `\n` 是用來在與產生的雜湊表中的名稱或專案相關聯的文字區塊內建立新的行。

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### 範例8：使用反斜線 escape 字元正確轉譯檔案路徑

此範例示範如何在字串資料中使用反斜線 escape 字元，以允許在產生的雜湊表中正確轉譯檔案路徑 `ConvertFrom-StringData` 。 雙反斜線可確保能夠在雜湊表輸出中正確轉譯常值反斜線字元。

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## PARAMETERS

### -StringData

指定要轉換的字串。 您可以使用這個參數或使用管線將字串傳送至 `ConvertFrom-StringData` 。 參數名稱為選擇性。

此參數的值必須是包含一或多個索引鍵/值組的字串。 每個索引鍵/值組都必須位於不同的行上，否則每個配對必須以分行符號分隔 (\` n) 。

您可以在字串中包括批註，但是批註不能和索引鍵/值組位於同一行。 `ConvertFrom-StringData` 忽略單行批註。 `#`字元必須是該行的第一個非空白字元。 中的行上的所有字元 `#` 都會被忽略。 註解不會包括在雜湊表中。

這裡的字串是由一或多行組成的字串。 在此字串內的引號會當做字串資料的一部分來解讀。 如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Delimiter

用來將索引 **鍵** 與要轉換的字串中的 **值** 資料分隔的字元。
預設分隔符號是 () 字元的等號 `=` 。 此參數是在 PowerShell 7 中新增的。

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含機碼值組的字串傳送至 `ConvertFrom-StringData` 。

## 輸出

### System.Collections.Hashtable

這個 Cmdlet 會傳回雜湊表，它會從索引鍵/值組建立。

## 注意

here-string 是由一或多行組成的字串，其中的引號會解譯為常值。

在以多種語言顯示使用者訊息的腳本中，此 Cmdlet 會很有用。 您可以使用字典樣式雜湊表來隔離文字字串與程式碼 (例如在資源檔案中)，以及將文字字串格式化以在翻譯工具中使用。

## 相關連結
