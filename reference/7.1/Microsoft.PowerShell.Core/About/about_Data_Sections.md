---
description: 說明資料區段，這些區段會將文字字串和其他唯讀資料與腳本邏輯隔離。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: a5eed0056fe572760415f62537b5a69942d819ae
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207347"
---
# <a name="about-data-sections"></a>關於資料區段

## <a name="short-description"></a>簡短描述
說明資料區段，這些區段會將文字字串和其他唯讀資料與腳本邏輯隔離。

## <a name="long-description"></a>完整描述

專為 PowerShell 設計的腳本可以有一個或多個資料區段只包含資料。 您可以在任何腳本、函數或 advanced 函數中包含一個或多個資料區段。 Data 區段的內容限制為指定的 PowerShell 指令碼語言子集。

分隔資料與程式碼邏輯可讓您更輕鬆地識別及管理邏輯和資料。 它可讓您針對文字使用不同的字串資源檔，例如錯誤訊息和說明字串。 它也會隔離程式碼邏輯，以促進安全性和驗證測試。

在 PowerShell 中，Data 區段可用來支援腳本國際化。
您可以使用資料區段，讓您更輕鬆地隔離、找出及處理將轉譯成許多使用者介面 (UI) 語言的字串。

Data 區段是 PowerShell 2.0 功能。 具有資料區段的腳本不會在沒有修訂的 PowerShell 1.0 中執行。

### <a name="syntax"></a>Syntax

資料區段的語法如下所示：

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

需要資料關鍵字。 不區分大小寫。 允許的內容限制為下列元素：

- 所有 PowerShell 操作員，除了 `-match`
- `If`、 `Else` 和 `ElseIf` 語句
- 下列自動變數如下： `$PsCulture` 、 `$PsUICulture` 、 `$True` 、 `$False` 和。 `$Null`
- 註解
- 管線
- 以分號分隔的語句 (`;`) 
- 常值，如下所示：

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- 資料區段中允許的 Cmdlet。 依預設，只 `ConvertFrom-StringData` 允許 Cmdlet。
- 使用參數在資料區段中允許的 Cmdlet `-SupportedCommand` 。

當您 `ConvertFrom-StringData` 在資料區段中使用 Cmdlet 時，您可以用單引號或雙引號括住的字串，或是以單引號括住或以雙引號括住的字串來括住機碼值組。 不過，包含變數和子運算式的字串必須以單引號括住的字串，或在此以單引號括住的字串括住，如此一來，就不會展開變數，且子運算式無法執行。

### <a name="-supportedcommand"></a>-SupportedCommand

`-SupportedCommand`參數可讓您指出 Cmdlet 或函式只會產生資料。 它的設計目的是讓使用者在其所撰寫或測試的資料區段中包含 Cmdlet 和函數。

的值 `-SupportedCommand` 是一個或多個 Cmdlet 或函式名稱的逗號分隔清單。

例如，下列資料區段包含使用者撰寫的 Cmdlet，其會將 `Format-XML` XML 檔案中的資料格式化：

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a>使用資料區段

若要使用資料區段的內容，請將它指派給變數，並使用變數標記法來存取內容。

例如，下列資料區段包含的 `ConvertFrom-StringData` 命令會將此字串轉換成雜湊表。 雜湊表會指派給 `$TextMsgs` 變數。

`$TextMsgs`變數不是 data 區段的一部分。

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

若要存取雜湊表中的索引鍵和值 `$TextMsgs` ，請使用下列命令。

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

或者，您可以將變數名稱放在 Data 區段的定義中。 例如：

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

結果與上一個範例相同。

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a>範例

簡單的資料字串。

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

包含允許變數的字串。

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

以單引號括住的字串，使用 `ConvertFrom-StringData` Cmdlet：

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

以雙引號括住的字串，使用 `ConvertFrom-StringData` Cmdlet：

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

資料區段，包含可產生資料的使用者撰寫 Cmdlet：

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_If](about_If.md)

[about_Operators](about_Operators.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

