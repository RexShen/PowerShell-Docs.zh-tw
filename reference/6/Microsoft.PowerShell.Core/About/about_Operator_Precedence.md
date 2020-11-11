---
description: 依優先順序列出 PowerShell 操作員。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 62b49476760192386ae2c583fd9b7699e893134c
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483055"
---
# <a name="about-operator-precedence"></a>關於運算子優先順序

## <a name="short-description"></a>簡短描述
依優先順序列出 PowerShell 操作員。

## <a name="long-description"></a>詳細描述

PowerShell 操作員可讓您建立簡單但功能強大的運算式。 本主題依優先順序列出操作員。 優先順序是在相同的運算式中出現多個運算子時，PowerShell 評估運算子的順序。

當運算子的優先順序相等時，PowerShell 會在運算式中出現時，從左至右進行評估。 例外狀況是指派運算子、轉換運算子和負運算子 (`!` 、 `-not` `-bnot`) ，由右至左進行評估。

您可以使用磁片磁碟機（例如括弧）來覆寫標準優先順序，並強制 PowerShell 在 unenclosed 部分之前評估運算式的封閉部分。

在下列清單中，運算子會依照其評估的順序列出。 相同行或相同群組中的運算子具有相等的優先順序。

[運算子] 資料行列出操作員。 參考資料行會列出描述運算子的 PowerShell 說明主題。 若要顯示主題，請輸入 `get-help <topic-name>` 。

|         OPERATOR         |           參考            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | [about_Operators][]            |
| `.` (成員存取)       | [about_Operators][]            |
| `::` (靜態)             | [about_Operators][]            |
| `[0]` (索引運算子)    | [about_Operators][]            |
| `[int]` (轉換運算子)  | [about_Operators][]            |
| `-split` (一元)          | [about_Split][]                |
| `-join` (一元)           | [about_Join][]                 |
| `,` (逗號運算子)      | [about_Operators][]            |
| `++ --`                  | [about_Assignment_Operators][] |
| `! -not`                 | [about_Logical_Operators][]    |
| `..` (範圍運算子)     | [about_Operators][]            |
| `-f` (格式運算子)    | [about_Operators][]            |
| `-` (一元/負)      | [about_Arithmetic_Operators][] |
| `* / %`                  | [about_Arithmetic_Operators][] |
| `+ -`                    | [about_Arithmetic_Operators][] |

下列運算子群組具有相同的優先順序。 其區分大小寫且明確區分大小寫的變數具有相同的優先順序。

|         OPERATOR          |           參考            |
| ------------------------- | ------------------------------ |
| `-split` (二進位)          | [about_Split][]                |
| `-join` (二進位)           | [about_Join][]                 |
| `-is -isnot -as`          | [about_Type_Operators][]       |
| `-eq -ne -gt -gt -lt -le` | [about_Comparison_Operators][] |
| `-like -notlike`          | [about_Comparison_Operators][] |
| `-match -notmatch`        | [about_Comparison_Operators][] |
| `-in -notIn`              | [about_Comparison_Operators][] |
| `-contains -notContains`  | [about_Comparison_Operators][] |
| `-replace`                | [about_Comparison_Operators][] |

清單會依下列順序在這裡繼續：

|                OPERATOR                 |           參考            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | [about_Arithmetic_Operators][] |
| `-and -or -xor`                         | [about_Logical_Operators][]    |

下列專案不是 true 運算子。 它們是 PowerShell 命令語法的一部分，而不是運算式語法的一部分。 指派一律會是最後一個執行的動作。

|                SYNTAX                   |           參考            |
| --------------------------------------- | ------------------------------ |
| `.` (點-來源)                         | [about_Operators][]            |
| `&` (呼叫)                               | [about_Operators][]            |
| <code>&#124;</code> (管線運算子)  | [about_Operators][]            |
| `> >> 2> 2>> 2>&1`                      | [about_Redirection][]          |
| `= += -= *= /= %=`                      | [about_Assignment_Operators][] |

## <a name="examples"></a>範例

下列兩個命令顯示算術運算子，以及使用括弧強制 PowerShell 先評估運算式的封閉部分的效果。

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

下列範例會從本機目錄取得唯讀文字檔，並將它們儲存在 `$read_only` 變數中。

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

它相當於下列範例。

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

因為管線運算子 (`|`) 的優先順序高於指派運算子 (`=`) ，所以 Cmdlet 取得的檔案會在指派給 `Get-ChildItem` 變數之前，傳送至 `Where-Object` Cmdlet 進行篩選 `$read_only` 。

下列範例示範索引運算子的優先順序高於轉換運算子。

此運算式會建立三個字串的陣列。 然後，它會使用具有0值的索引運算子來選取陣列中的第一個物件，也就是第一個字串。 最後，它會將選取的物件轉換為字串。 在此情況下，轉換不會有任何作用。

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

這個運算式會使用括弧來強制在索引選取之前進行轉換作業。 因此，整個陣列會轉換成 (單一) 字串。 然後，索引運算子會選取字串陣列中的第一個專案，也就是第一個字元。

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

在下列範例中，因為 `-gt` (大於) 運算子的優先順序高於 `-and` (邏輯 AND) 運算子，所以運算式的結果為 FALSE。

```powershell
PS> 2 -gt 4 -and 1
False
```

它相當於下列運算式。

```powershell
PS> (2 -gt 4) -and 1
False
```

如果-and 運算子的優先順序較高，則答案會是 TRUE。

```powershell
PS> 2 -gt (4 -and 1)
True
```

不過，此範例示範管理運算子優先順序的重要原則。 當某個運算式不容易解讀時，請使用括弧來強制執行評估順序，即使它強制預設運算子優先順序亦同。 括弧讓讀取和維護腳本的人員清楚明瞭。

## <a name="see-also"></a>另請參閱

[about_Operators][]

[about_Assignment_Operators][]

[about_Comparison_Operators][]

[about_Arithmetic_Operators][]

[about_Join][]

[about_Redirection][]

[about_Scopes][]

[about_Split][]

[about_Type_Operators][]

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
