---
description: 描述 PowerShell 中的正則運算式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 6112c63b6d0c1018b56df85ec6ae919a0285ffc3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206940"
---
# <a name="about-regular-expressions"></a>關於正則運算式

## <a name="short-description"></a>簡短描述
描述 PowerShell 中的正則運算式。

## <a name="long-description"></a>完整描述

> [!NOTE]
> 本文將說明在 PowerShell 中使用正則運算式的語法和方法，而不會討論所有語法。 如需更完整的參考，請參閱 [正則運算式語言-快速參考](/dotnet/standard/base-types/regular-expression-language-quick-reference)。

正則運算式是用來比對文字的模式。 它可以由常值字元、運算子和其他結構組成。

本文示範 PowerShell 中的正則運算式語法。 PowerShell 有數個使用正則運算式的運算子和 Cmdlet。 您可以在下列連結深入瞭解其語法和用法。

- [Select-String](xref:Microsoft.PowerShell.Utility.Select-String)
- [-match 和-replace 運算子](about_Comparison_Operators.md)
- [-分割](about_Split.md)
- [使用-RegEx 選項的 switch 語句](about_Switch.md)

PowerShell 正則運算式預設為不區分大小寫。 以上顯示的每個方法都有不同的方式來強制區分大小寫。

|       方法       |                      區分大小寫                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | 使用 `-CaseSensitive` 參數                                |
| `switch` 陳述式 | 使用 `-casesensitive` 選項                            |
| 運算子          | 前置詞為 **' c '** (`-cmatch` 、 `-csplit` 或 `-creplace`)  |

### <a name="character-literals"></a>字元常值

正則運算式可以是常值字元或字串。 運算式會使引擎完全符合指定的文字。

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a>字元類別

如果您知道確切的模式，字元常值就會運作，而字元類別可讓您更不特定。

#### <a name="character-groups"></a>字元群組

`[character group]` 可讓您一次比對任意數目的字元，而 `[^character group]` 只會比對不在群組中的字元。

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

如果要比對的字元清單包含連字號字元 (`-`) ，它必須位於清單的開頭或結尾，才能與字元範圍運算式區分。

#### <a name="character-ranges"></a>字元範圍

模式也可以是字元的範圍。 這些字元可以是字母 `[A-Z]` 、數位 `[0-9]` ，甚至是以 ASCII 為基礎 `[ -~]` (所有可列印的字元) 。

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a>數字

`\d`字元類別將會比對任何十進位數。 相反地， `\D` 將會比對任何非十進位數。

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a>單字字元

`\w`字元類別將會比對任何文字字元 `[a-zA-Z_0-9]` 。 若要比對任何非文字字元，請使用 `\W` 。

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a>萬用字元

期間 (`.`) 是正則運算式中的萬用字元。 它會比對任何字元，但不包括分行符號 (`\n`) 。

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a>空白

空白字元會使用字元類別進行比對 `\s` 。 任何非空白字元都會使用進行比對 `\S` 。 也可以使用常值空白字元 `' '` 。

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a>數量詞

數量詞會控制每個專案的實例應該出現在輸入字串中的數目。

以下是 PowerShell 中可用的一些數量詞：

| 數量詞 |                描述                |
| ---------- | ----------------------------------------- |
| `*`        | 零次或多次。                       |
| `+`        | 一或多次。                        |
| `?`        | 零次或一次。                         |
| `{n,m}`    | 至少 `n` ，但不能超過一 `m` 次。 |

星號 (`*`) 比對前一個元素零次或多次。 結果是，即使輸入字串沒有元素，也會是相符專案。

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

加號 (`+`) 比對前一個元素一或多次。

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

問號會 `?` 比對前一個元素零或一次。 就像星號一樣 `*` ，它甚至會比對不存在元素的字串。

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

`{n, m}`數量詞可以使用數種不同的方式來允許對數量詞進行細微的控制。 第二個元素 `m` 和逗號 `,` 是選擇性的。

| 數量詞 |                描述                 |
| ---------- | ------------------------------------------ |
| `{n}`      | 精確比 `n` 對的次數。         |
| `{n,}`     | 至少比 `n` 對次數。        |
| `{n,m}`    | 比 `n` 對和 `m` 次數。 |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a>錨點

錨點可讓您根據輸入字串內的相符位置，使相符專案成功或失敗。

這兩個常用錨點為 `^` 和 `$` 。 插入點會比對字串的 `^` 開頭和 `$` ，後者會符合字串的結尾。 錨點可讓您在特定位置比對文字，同時也會捨棄不需要的字元。

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> 定義包含錨點的 RegEx 時 `$` ，請務必使用單引號來括住 RegEx (`'`) 而不是雙引號 (`"`) 或 PowerShell 會將運算式擴充為變數。

在 PowerShell 中使用錨點時，您應該瞭解 **單行** 和 **多行** 正則運算式選項之間的差異。

- **多** 行：多行模式會強制 `^` 並 `$` 比對每一行的開頭，而不是輸入字串的開頭和結尾。
- **單行** ：單行模式會將輸入字串視為 **單行** 。
  它會強制 `.` 字元符合每個字元 (包括分行符號) ，而不是比對分行符號以外的每個字元 `\n` 。

若要深入瞭解這些選項以及如何使用這些選項，請造訪 [正則運算式語言-快速參考](/dotnet/standard/base-types/regular-expression-language-quick-reference)。

### <a name="escaping-characters"></a>逸出字元

反斜線 (`\`) 用來 escape 字元，因此正則運算式引擎不會剖析它們。

保留下列字元： `[]().\^$|?*+{}` 。

您必須在模式中將這些字元換成符合輸入字串中的字元。

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

Regex 類別的靜態方法可為您 escape 文字。

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> 這會將所有保留的正則運算式字元（包括字元類別中使用的現有反斜線）全部轉義。 請務必只在您需要 escape 的模式部分使用它。

#### <a name="other-character-escapes"></a>其他字元轉義

您也可以使用保留的字元 esc 來比對特殊的字元類型。

以下是一些常用的字元數轉義：

|字元 Escape  |描述  |
|---------|---------|
|`\t`|符合索引標籤|
|`\n`|符合新行|
|`\r`|符合回車|

### <a name="groups-captures-and-substitutions"></a>群組、捕捉和替代

群組結構會將輸入字串分隔成可加以捕獲或忽略的子字串。 群組的子字串稱為子運算式。 依預設，子運算式是在編號群組中捕捉，不過您也可以指派名稱給它們。

群組結構是以括弧括住的正則運算式。 會捕捉任何由包含的正則運算式相符的文字。 下列範例會將輸入文字分成兩個捕獲群組。

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

使用 `$Matches` **Hashtable** 自動變數來取出捕捉的文字。
代表整個相符的文字會儲存在索引鍵 `0` 。

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

捕捉會儲存在由左至右增加的數值 **整數** 索引鍵中。 Capture `1` 包含所有文字，直到使用者名稱，capture `2` 只包含使用者名稱。

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> 索引 `0` 鍵是 **整數** 。 您可以使用任何 **Hashtable** 方法來存取儲存的值。
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a>已命名的捕獲

依預設，會以遞增的數值順序（從左至右）儲存捕獲。
您也可以將 **名稱** 指派給捕捉群組。 這個 **名稱** 會成為 `$Matches` **Hashtable** 自動變數的索引鍵。

在「捕獲群組」內，使用 `?<keyname>` 將已捕捉的資料儲存在名為的金鑰下。

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

下列範例會將最新的記錄專案儲存在 Windows 安全性記錄檔中。
提供的正則運算式會從訊息中解壓縮使用者名稱和網域，並將其儲存在索引鍵的索引鍵上： **N** 代表網域的名稱和 **D** 。

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

如需詳細資訊，請參閱 [正則運算式中的群組結構](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)。

#### <a name="substitutions-in-regular-expressions"></a>在規則運算式中執行替代

使用正則運算式搭配 `-replace` 運算子，可讓您使用已捕捉的文字動態取代文字。

`<input> -replace <original>, <substitute>`

- `<input>`：要搜尋的字串
- `<original>`：用來搜尋輸入字串的正則運算式
- `<substitute>`：用來取代在輸入字串中找到之相符專案的正則運算式替代運算式。

> [!NOTE]
> `<original>`和 `<substitute>` 運算元受限於正則運算式引擎的規則，例如字元轉義。

您可以在字串中參考捕捉群組 `<substitute>` 。 您可以使用 `$` 群組識別碼之前的字元來完成替代。

有兩種方式可以參考捕捉群組，也就是依 **編號** 和 **名稱** 。

- 依 **編號** -捕獲群組是由左至右編號。

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- 依 **名稱-捕獲** 群組也可以依名稱參考。

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

`$&`運算式代表所有符合的文字。

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> 由於 `$` 字元是在字串展開中使用，因此您必須使用常值字串搭配替代，或 `$` 在使用雙引號時將字元換用。
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> 此外，如果您想要將做 `$` 為常值字元，請使用 `$$` 而不是一般的 escape 字元。 使用雙引號時，仍會將的所有實例都換用， `$` 以避免不正確的替代。
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

如需詳細資訊，請參閱 [正則運算式中的替代](/dotnet/standard/base-types/substitutions-in-regular-expressions)。

## <a name="see-also"></a>另請參閱

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Operators](about_Operators.md)
