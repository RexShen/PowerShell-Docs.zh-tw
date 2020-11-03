---
description: 描述 PowerShell 如何剖析命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: d7b5af8c94ad6370c69773d2bc3796bace60ef7c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207967"
---
# <a name="about-parsing"></a>關於剖析

## <a name="short-description"></a>簡短描述

描述 PowerShell 如何剖析命令。

## <a name="long-description"></a>詳細描述

當您在命令提示字元中輸入命令時，PowerShell 會將命令文字分成一系列稱為 _權杖_ 的區段，然後決定如何解讀每個標記。

例如，如果您輸入：

```powershell
Write-Host book
```

PowerShell 會將命令分成兩個權杖，並 `Write-Host` `book` 使用兩個主要剖析模式的其中一種來個別解釋每個權杖：運算式模式和引數模式。

> [!NOTE]
> 當 PowerShell 剖析命令輸入時，它會嘗試將命令名稱解析為 Cmdlet 或原生可執行檔。 如果命令名稱沒有完全相符的命令名稱，PowerShell 就會在命令前面加上 `Get-` 預設的動詞命令。 例如，PowerShell 會剖析 `Process` 為 `Get-Process` 。 基於下列原因，不建議使用這項功能：
>
> - 效率不佳。 這會導致 PowerShell 多次搜尋。
> - 系統會先解決具有相同名稱的外部程式，因此您可能無法執行預定的 Cmdlet。
> - `Get-Help` 和 `Get-Command` 不辨識動詞命令的名稱。

### <a name="expression-mode"></a>運算式模式

運算式模式適用于結合運算式，這是在指令碼語言中進行值操作的必要項。 運算式是 PowerShell 語法中值的標記法，而且可以是簡單或複合的，例如：

常值運算式是其值的直接標記法：

```powershell
'hello', 32
```

變數運算式會包含它們所參考的變數值：

```powershell
$x, $script:path
```

運算子會合並其他運算式以進行評估：

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- _字元字串常_ 值必須包含在引號中。
- _數位_ 會被視為數值，而不是一系列的字元 (除非是) 的轉義。
- _運算子_ （包括和和等 `-` 二元運算子） `-not` `+` `-gt` 會被視為運算子，並將其引數的各自作業套用至) 的 (運算元。
- _屬性和轉換運算式_ 會剖析為運算式，並套用至從屬運算式（例如） `[int] '7'` 。
- _變數參考_ 會評估為它們的值，但 _展開_ (亦即，將預先填入的參數集貼入) 是禁止的，並導致剖析器錯誤。
- 任何其他將會被視為要叫用的命令。

### <a name="argument-mode"></a>引數模式

剖析時，PowerShell 會先將輸入解讀為運算式。 但是，當遇到命令調用時，剖析作業會繼續處於引數模式。

引數模式的設計是為了剖析 shell 環境中命令的引數和參數。 所有輸入都會被視為可擴充的字串，除非它使用下列其中一個語法：

- 貨幣符號 (`$`) 只會在後面加上有效的變數名稱時才開始變數參考 (，否則會被視為可展開字串) 的一部分。
- 引號 (`'` 和 `"`) 開始字串值
- 括弧 (`(` 和 `)`) 界限新的運算式。
- 子運算式運算子 (`$(` ... `)`) 標示內嵌運算式。
- 括弧 (`{` ，並 `}`) 界限新的腳本區塊。
- 初始 at sign (`@`) 開始運算式語法，例如展開 (`@args`) 、陣列 (`@(1,2,3)`) ，以及雜湊表 () `@{a=1;b=2}` 。
- `,`除非要呼叫的命令是原生應用程式，但在此情況下，會將它們視為可展開字串的一部分，所以逗號 () 引進以陣列形式傳遞的清單。 不支援初始、連續或結尾的逗號。

內嵌運算式的值會轉換成字串。

下表提供數個在運算式模式和引數模式中處理的值範例，以及這些值的評估。 我們假設變數的值 `a` 是 `4` 。

|       範例        |    模式    |      結果       |
| -------------------- | ---------- | ----------------- |
| `2`                  | 運算是 | 2 (整數)        |
| `` `2``              | 運算式 | "2" (命令)      |
| `echo 2`             | 運算式 | 2 (整數)        |
| `2+2`                | 運算式 | 4 (整數)        |
| `echo 2+2`           | 引數   | "2 + 2" (字串)     |
| `echo(2+2)`          | 運算式 | 4 (整數)        |
| `$a`                 | 運算式 | 4 (整數)        |
| `echo $a`            | 運算式 | 4 (整數)        |
| `$a+2`               | 運算式 | 6 (整數)        |
| `echo $a+2`          | 引數   | 4 + 2 (字串)       |
| `$-`                 | 引數   | "$-" (命令)     |
| `echo $-`            | 引數   | "$-" (字串)      |
| `a$a`                | 運算式 | "a $ a" (命令)    |
| `echo a$a`           | 引數   | "a4" (字串)      |
| `a'$a'`              | 運算式 | "a $ a" (命令)    |
| `echo a'$a'`         | 引數   | "a $ a" (字串)     |
| `a"$a"`              | 運算式 | "a $ a" (命令)    |
| `echo a"$a"`         | 引數   | "a4" (字串)      |
| `a$(2)`              | 運算式 | "a $ (2) " (命令)  |
| `echo a$(2)`         | 引數   | "a2" (字串)      |

每個標記都可以解讀為某種類型的物件類型，例如布林值或字串。 PowerShell 會嘗試從運算式判斷物件類型。
物件類型取決於命令所預期的參數類型，以及 PowerShell 是否知道如何將引數轉換成正確的型別。 下表顯示數個指派給運算式所傳回值的類型範例。

|       範例          |    模式    |     結果      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | 引數   | "！ 1" (字串)    |
| `Write-Output (!1)`    | 運算式 | False (布林值)  |
| `Write-Output (2)`     | 運算式 | 2 (整數)      |
| `Set-Variable AB A,B`  | 引數   | ' A '、' B ' (陣列)  |
| `CMD /CECHO A,B`       | 引數   | ' A，B ' (字串)   |
| `CMD /CECHO $AB`       | 運算式 | ' A '、' B ' (陣列)  |
| `CMD /CECHO :$AB`      | 引數   | '： B ' (字串)  |

在 PowerShell 3.0 中引進的停止剖析符號 () ，會 `--%` 指示 powershell 避免將輸入解釋為 powershell 命令或運算式。

在 PowerShell 中呼叫可執行程式時，請在程式引數之前放置停止剖析符號。 這項技術比使用 escape 字元來防止解釋的程式更容易。

當它遇到停止剖析符號時，PowerShell 會將該行中的其餘字元視為常值。 唯一會執行的轉譯是替代使用標準 Windows 標記法的環境變數值，例如 `%USERPROFILE%` 。

停止剖析符號只有在下一個新行或管線字元之後才有效。 您無法使用接續字元 (`` ` ``) 來延伸其效果，或使用命令分隔符號 (`;`) 終止其效果。

例如，下列命令會呼叫 **Icacls** 程式。

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

若要在 PowerShell 2.0 中執行此命令，您必須使用 escape 字元，以防止 PowerShell 錯誤解譯括弧。

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

從 PowerShell 3.0 開始，您可以使用停止剖析符號。

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell 會將下列命令字串傳送至 **Icacls** 程式：

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

## <a name="see-also"></a>另請參閱

[about_Command_Syntax](about_Command_Syntax.md)
