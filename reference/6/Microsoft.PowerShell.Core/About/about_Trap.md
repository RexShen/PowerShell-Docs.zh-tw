---
description: 描述可處理終止錯誤的關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 88c16066b96912faf38fd48a3bd2f84572707e4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206836"
---
# <a name="about-trap"></a>關於陷阱

## <a name="short-description"></a>簡短描述

描述可處理終止錯誤的關鍵字。

## <a name="long-description"></a>完整描述

終止錯誤會停止執行語句。 如果 PowerShell 沒有以某種方式處理終止錯誤，PowerShell 也會停止在目前的管線中執行函式或腳本。 在其他語言中（例如 c #），終止錯誤稱為例外狀況。

`trap`關鍵字會指定在終止錯誤發生時要執行的語句清單。 `trap` 語句會以下列方式處理終止錯誤：

- 在處理語句區塊之後顯示錯誤 `trap` ，並繼續執行包含的腳本或函式 `trap` 。 此為預設行為。

- 顯示錯誤，並中止執行語句中包含 using 的腳本或 `trap` 函數 `break` `trap` 。

- 將錯誤靜音，但是 `trap` `continue` 在語句中使用，繼續執行包含的腳本或函數 `trap` 。

的語句清單 `trap` 可以包含多個條件或函式呼叫。 `trap`可以撰寫記錄檔、測試條件，或甚至執行另一個程式。

### <a name="syntax"></a>Syntax

`trap`語句具有下列語法：

```powershell
trap [[<error type>]] {<statement list>}
```

`trap`語句包含終止錯誤發生時要執行的語句清單。 `trap`語句是由 `trap` 關鍵字（選擇性地接著型別運算式），以及包含在發生錯誤時所要執行之語句清單的語句區塊所組成。 型別運算式會調整捕捉的錯誤類型 `trap` 。

腳本或命令可以有多個 `trap` 語句。 `trap` 語句可以出現在腳本或命令中的任何位置。

### <a name="trapping-all-terminating-errors"></a>將所有終止錯誤全部捕獲

當在腳本或命令中未以另一種方式處理的終止錯誤發生時，PowerShell 會檢查 `trap` 處理錯誤的語句。 如果有 `trap` 語句，則 PowerShell 會繼續執行語句中的腳本或命令 `trap` 。

下列範例是非常簡單的 `trap` 語句：

```powershell
trap {"Error found."}
```

此 `trap` 語句會捕捉任何終止錯誤。

在下列範例中，函式包含會造成執行階段錯誤的不實用字串。

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

執行此函數會傳回下列各項：

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

下列範例包含 `trap` 使用自動變數顯示錯誤的語句 `$_` ：

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

執行此版本的函式會傳回下列各項：

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> `trap` 語句可以定義于指定範圍內的任何位置，但一律會套用至該範圍內的所有語句。 在執行時間， `trap` 區塊中的語句會在執行任何其他語句之前定義。 在 JavaScript 中，這就是所謂的 [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting)。 這表示語句會套用 `trap` 至該區塊中的所有語句，即使執行尚未事先定義的時間點也一樣。 例如， `trap` 在腳本結尾定義，並在第一個語句中擲回錯誤，仍然會觸發該 `trap` 。

### <a name="trapping-specific-errors"></a>捕捉特定錯誤

腳本或命令可以有多個 `trap` 語句。 `trap`可以定義來處理特定的錯誤。

下列範例是會將 `trap` 特定錯誤 **system.management.automation.commandnotfoundexception** 陷阱的語句：

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

當函數或腳本遇到不符合已知命令的字串時，此語句會顯示「命令錯誤被攔截」 `trap` 字串。
執行 `trap` 語句清單之後，PowerShell 會將錯誤物件寫入錯誤資料流程，然後繼續執行腳本。

PowerShell 使用 .NET 例外狀況類型。 下列範例會指定 **system.object** 錯誤類型：

```powershell
trap [System.Exception] {"An error trapped"}
```

**System.management.automation.commandnotfoundexception** **錯誤類型繼承自 system.string 類型。** 此語句會攔截由未知命令所建立的錯誤。 它也會捕捉其他錯誤類型。

腳本中可以有一個以上的 `trap` 語句。 每個錯誤類型只能由一個語句來攔截 `trap` 。 當結束錯誤發生時，PowerShell 會搜尋 `trap` 具有最特定相符的，從目前的執行範圍開始。

下列腳本範例包含錯誤。 腳本包含的一般 `trap` 語句會將任何終止錯誤和 `trap` 指定 **system.management.automation.commandnotfoundexception** 類型的特定語句進行陷阱。

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

執行此腳本會產生下列結果：

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

因為 PowerShell 無法辨識 "nonsenseString" 作為 Cmdlet 或其他專案，所以會傳回 **system.management.automation.commandnotfoundexception** 錯誤。 特定語句會攔截這個終止錯誤 `trap` 。

下列腳本範例包含 `trap` 具有不同錯誤的相同語句：

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

執行此腳本會產生下列結果：

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

嘗試零除不會產生 **system.management.automation.commandnotfoundexception** 錯誤。 相反地，這個錯誤會被另一個語句所攔截，而此語句會攔截 `trap` 任何終止錯誤。

### <a name="trapping-errors-and-scope"></a>陷印錯誤和範圍

如果終止錯誤發生在與語句相同的範圍中 `trap` ，則 PowerShell 會執行所定義的語句清單 `trap` 。 執行會在錯誤之後的語句繼續執行。 如果 `trap` 語句與錯誤的範圍不同，則會在與語句相同範圍中的下一個語句繼續執行 `trap` 。

例如，如果函式中發生錯誤，且 `trap` 語句在函式中，則腳本會繼續執行下一個語句。 下列腳本包含錯誤和 `trap` 語句：

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

執行此腳本會產生下列結果：

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

`trap`函數中的語句會攔截錯誤。 顯示訊息之後，PowerShell 會繼續執行函式。 請注意， `Function1` 已完成。

將這個範例與下列範例（具有相同的錯誤和語句）進行比較 `trap` 。 在此範例中， `trap` 語句會出現在函式之外：

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

`Function2`執行函數會產生下列結果：

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

在此範例中，「function2 已完成」命令未執行。 在這兩個範例中，函式內都會發生終止錯誤。 不過，在這個範例中， `trap` 語句是在函式之外。 PowerShell 不會在語句執行之後回到函式 `trap` 。

> [!CAUTION]
> 針對相同的錯誤狀況定義多個陷阱時， `trap` 會使用範圍) 中第一個定義的詞法 (最高。

在下列範例中，只 `trap` 會執行 "唉啊 1"。

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> Trap 語句的範圍設定為編譯的位置。 如果您在函式 `trap` 或點式的來源腳本內有語句，則當函式或點出的腳本結束時，內的所有 `trap` 語句都會被移除。

### <a name="using-the-break-and-continue-keywords"></a>使用 break 和 continue 關鍵字

您可以 `break` `continue` 在語句中使用和關鍵字 `trap` ，判斷腳本或命令是否會在終止錯誤之後繼續執行。

如果您 `break` 在語句清單中包含語句 `trap` ，則 PowerShell 會停止函數或腳本。 下列範例函數會 `break` 在語句中使用關鍵字 `trap` ：

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

因為 `trap` 語句包含關鍵字，所以函式不 `break` 會繼續執行，且不會執行「函式已完成」行。

如果您 `continue` 在語句中包含關鍵字 `trap` ，PowerShell 會在造成錯誤的語句之後繼續執行，就如同沒有或一樣 `break` `continue` 。 `continue`不過，使用關鍵字時，PowerShell 不會將錯誤寫入錯誤串流。

下列範例函數會 `continue` 在語句中使用關鍵字 `trap` ：

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

函數會在攔截到錯誤之後繼續執行，並執行 "Function completed" 語句。 錯誤資料流程未寫入錯誤。

## <a name="notes"></a>備忘稿

`trap` 語句提供了一種簡單的方式，可廣泛確保處理範圍內的所有終止錯誤。 如需更細微的錯誤處理，請使用使用 `try` / `catch` 語句定義陷阱的區塊 `catch` 。 `catch`語句只適用于相關語句內的程式碼 `try` 。 如需詳細資訊，請參閱 [about_Try_Catch_Finally](about_Try_Catch_Finally.md)。

## <a name="see-also"></a>另請參閱

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
