---
description: 描述在 PowerShell 中比較值的運算子。
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: ea48d5928f71983f6d035f0e5e6074ce36754d80
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090506"
---
# <a name="about-comparison-operators"></a>關於比較運算子

## <a name="short-description"></a>簡短描述
描述在 PowerShell 中比較值的運算子。

## <a name="long-description"></a>完整描述

比較運算子可讓您指定比較值的條件，並尋找符合指定模式的值。 若要使用比較運算子，請指定要與分隔這些值的運算子一起比較的值。

PowerShell 包含下列比較運算子：

| 類型        | 運算子    | 說明                                 |
| ----------- | ------------ | --------------------------------------------|
| 等式    | -eq          | equals                                      |
|             | -ne          | 不等於                                  |
|             | -gt          | 大於                                |
|             | -ge          | 大於或等於                       |
|             | -lt          | 小於                                   |
|             | -le          | 小於或等於                          |
|             |              |                                             |
| Matching    | -like        | 當字串符合萬用字元時傳回 true   |
|             |              | 模式                                     |
|             | -notlike     | 當字串不相符時傳回 true     |
|             |              | 萬用字元模式                            |
|             | -match       | 當字串符合 RegEx 時傳回 true      |
|             |              | 方式$matches 包含相符的字串 |
|             | -notmatch    | 當字串不相符時傳回 true     |
|             |              | RegEx 模式;$matches 包含相符的   |
|             |              | 字串                                     |
|             |              |                                             |
| Containment | -contains    | 當參考值包含時傳回 true |
|             |              | 在集合中                             |
|             | -notcontains | 如果參考值不是，則傳回 true       |
|             |              | 包含在集合中                   |
|             | -in          | 當包含在中的測試值時傳回 true |
|             |              | collection                                  |
|             | -notin       | 當測試值不包含時傳回 true  |
|             |              | 在集合中                             |
|             |              |                                             |
| 取代 | -取代     | 取代字串模式                   |
|             |              |                                             |
| 類型        | -是          | 如果兩個物件相同，則傳回 true    |
|             |              | 類型                                        |
|             | -isnot       | 如果物件相同，則傳回 true|
|             |              | 類型                                        |

依預設，所有比較運算子都不區分大小寫。 若要讓比較運算子區分大小寫，請在運算子名稱之前加上 `c` 。 例如，區分大小寫的版本 `-eq` 是 `-ceq` 。 若要進行不區分大小寫的明確，請在運算子前面加上 `i` 。 例如，明確的不區分大小寫版本 `-eq` 為 `-ieq` 。

當運算子的輸入是純量值時，比較運算子會傳回布林值。 當輸入是值的集合時，比較運算子會傳回任何相符的值。 如果集合中沒有相符專案，比較運算子會傳回空陣列。

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

例外狀況是內含專案運算子、In 運算子和型別運算子，這些運算子一律會傳回 **布林** 值。

> [!NOTE]
> 如果您需要比較值與 `$null` ，應該放 `$null` 在比較的左邊。 當您比較 `$null` **物件 []** 時，結果為 **False** ，因為比較物件是陣列。 當您比較陣列與時 `$null` ，比較會篩選出任何 `$null` 儲存在陣列中的值。 例如：
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a>等號比較運算子

`-eq` `-ne` 當一或多個輸入值相同于指定的模式時，相等運算子 (，) 會傳回 TRUE 或相符專案的值。 整個模式必須符合整個值。

範例：

### <a name="-eq"></a>-eq

描述：等於。 包含相同的值。

範例：

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

### <a name="-ne"></a>-ne

描述：不等於。 包含不同的值。

範例：

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

### <a name="-gt"></a>-gt

描述：大於。

範例：

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> 這應該不會與 `>` 其他許多程式設計語言中的大於運算子混淆。 在 PowerShell 中， `>` 是用來重新導向。 如需詳細資訊，請參閱 [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)。

### <a name="-ge"></a>-ge

描述：大於或等於。

範例：

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a>-lt

描述：小於。

範例：

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a>-le

描述：小於或等於。

範例：

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a>相符運算子

Like 運算子 (`-like` 和 `-notlike`) 使用萬用字元運算式來尋找符合或不符合指定模式的元素。

語法為：

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

符合運算子 (`-match` 和 `-notmatch`) 使用正則運算式來尋找符合或不符合指定模式的元素。

`$Matches`當運算子的左邊引數)  (的輸入是單一純量物件時，比對運算子會填入自動變數。 當輸入是純量時， `-match` 和 `-notmatch` 運算子會傳回布林值，並將自動變數的值設定 `$Matches` 為引數的相符元件。

語法為：

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a>-like

描述：使用萬用字元 () 比對 \* 。

範例：

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a>-notlike

描述：不符合使用萬用字元 (\*) 。

範例：

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a>-match

描述：使用正則運算式比對字串。 當輸入是純量時，會填入 `$Matches` 自動變數。

如果輸入是集合， `-match` 和運算子會傳回 `-notmatch` 該集合的相符成員，但是運算子不會填入 `$Matches` 變數。

例如，下列命令會將字串的集合提交給 `-match` 運算子。 `-match`運算子會傳回集合中符合的專案。 它不會填入 `$Matches` 自動變數。

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

相反地，下列命令會將單一字串提交給 `-match` 運算子。 運算子會傳回 `-match` 布林值，並填入 `$Matches` 自動變數。 `$Matches`自動變數是 **雜湊表**。 如果未使用群組或捕捉，則只會填入一個金鑰。
機 `0` 碼代表所有相符的文字。 如需使用正則運算式進行群組和捕捉的詳細資訊，請參閱 [about_Regular_Expressions](about_Regular_Expressions.md)。

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

請務必注意， `$Matches` 雜湊表只會包含第一次出現的任何相符模式。

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> 索引 `0` 鍵是 **整數**。 您可以使用任何 **Hashtable** 方法來存取儲存的值。
>
> ```powershell
> PS> "Good Dog" -match "Dog"
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

`-notmatch`當輸入是純量時，運算子會填入 `$Matches` 自動變數，而當它偵測到相符時，結果會是 False。

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

### <a name="-notmatch"></a>-notmatch

描述：不符合字串。 使用正則運算式。 當輸入是純量時，會填入 `$Matches` 自動變數。

範例：

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

## <a name="containment-operators"></a>內含專案運算子

內含專案運算子 (`-contains` 和 `-notcontains`) 類似于等號比較運算子。 不過，內含專案運算子一律會傳回布林值，即使輸入是集合也一樣。

此外，和等號比較運算子不同的是，內含專案運算子會在偵測到第一個相符專案時，立即傳回值。 等號比較運算子會評估所有輸入，然後傳回集合中的所有相符專案。

### <a name="-contains"></a>-contains

描述：內含專案運算子。 指出參考值的集合是否包含單一測試值。 一律傳回布林值。 只有當測試值完全符合至少一個參考值時，才會傳回 TRUE。

當測試值為集合時，Contains 運算子會使用參考相等。 只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。

在非常大的集合中， `-contains` 運算子會傳回比等於運算子更快的結果。

語法：

`<Reference-values> -contains <Test-value>`

範例：

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

### <a name="-notcontains"></a>-notcontains

描述：內含專案運算子。 指出參考值的集合是否包含單一測試值。 一律傳回布林值。 當測試值與至少一個參考值的完全相符時，就會傳回 TRUE。

當測試值為集合時，NotContains 運算子會使用參考相等。

語法：

`<Reference-values> -notcontains <Test-value>`

範例：

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

### <a name="-in"></a>-in

描述： In 運算子。 告知測試值是否出現在參考值的集合中。 一律傳回為布林值。 只有當測試值完全符合至少一個參考值時，才會傳回 TRUE。

當測試值為集合時，In 運算子會使用參考相等。
只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。

`-in`操作員是在 PowerShell 3.0 中引進。

語法：

`<Test-value> -in <Reference-values>`

範例：

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

### <a name="-notin"></a>-notin

描述：告知測試值是否出現在參考值的集合中。 一律傳回布林值。 當測試值與至少一個參考值完全相符時，就會傳回 TRUE。

當測試值為集合時，In 運算子會使用參考相等。
只有當其中一個參考值是測試值物件的相同實例時，才會傳回 TRUE。

`-notin`操作員是在 PowerShell 3.0 中引進。

語法：

`<Test-value> -notin <Reference-values>`

範例：

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

## <a name="replacement-operator"></a>取代運算子

`-replace`運算子具有下列語法：

`<input> -replace <original>, <substitute>`

`<original>`預留位置是符合要取代之字元的正則運算式。 `<substitute>`預留位置是取代它們的常值字串。

運算子會使用正則運算式來取代具有指定值的所有或部分值。 您可以使用運算子進行許多系統管理工作，例如重新命名檔案。 例如，下列命令會將所有檔案的副檔名變更 `.txt` 為 `.log` ：

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a>區分大小寫的相符專案

依預設， `-replace` 運算子不區分大小寫。 若要區分大小寫，請使用 `-creplace` 。 若要讓它明確不區分大小寫，請使用 `-ireplace` 。

請參考下列範例：

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a>規則運算式中的替代項目

您也可以使用正則運算式，以動態方式使用捕捉群組和替代來取代文字。 您可以 `<substitute>` 使用群組識別碼之前的貨幣符號 () 字元，在字串中參考 Capture 群組 `$` 。

您可以依 **編號** 或 **名稱** 參考 Capture 群組

- 依 **編號** -捕獲群組是由左至右編號。

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- 依 **名稱-捕獲** 群組也可以依名稱參考。

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> 由於 `$` 字元是在字串展開中使用，因此您必須使用常值字串或將 `$` 字元換用。
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> 此外，因為在 `$` 替代中使用字元，所以您必須將字串中的任何實例都換用。
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

若要深入瞭解，請參閱[正則運算式中的](/dotnet/standard/base-types/substitutions-in-regular-expressions) [about_Regular_Expressions](about_Regular_Expressions.md)和替代

### <a name="substituting-in-a-collection"></a>以集合取代

當 `<input>` `-replace` 運算子為集合時，PowerShell 會將取代套用至集合中的每個值。 例如：

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="scriptblock-substitutions"></a>ScriptBlock 替代

從 PowerShell 6 開始，您可以使用 **ScriptBlock** 引數做為 _替代_ 文字。 在 _輸入_ 字串中找到的每個相符項都會執行 **ScriptBlock** 。

在 **ScriptBlock** 內，使用 `$_` 自動變數來參考目前的 **>system.text.regularexpressions 相符** 物件。 **Match** 物件可讓您存取目前所要取代的輸入文字，以及其他有用的資訊。

此範例會以對等字元取代三個小數點的每個序列。 每一組需要取代的三個小數位數都會執行 **ScriptBlock** 。

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

## <a name="type-comparison"></a>類型比較

類型比較運算子 (`-is` 和 `-isnot`) 用來判斷物件是否為特定類型。

### <a name="-is"></a>-是

語法：

`<object> -is <type reference>`

範例：

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a>-isnot

語法：

`<object> -isnot <type reference>`

範例：

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a>請參閱

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [Foreach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
