---
description: 描述控制 PowerShell 如何解讀序列中下一個字元的特殊字元序列。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 875a1c3c63e759151c3c64b5396312b030955cb7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207547"
---
# <a name="about-special-characters"></a>關於特殊字元

## <a name="short-description"></a>簡短描述

描述控制 PowerShell 如何解讀序列中下一個字元的特殊字元序列。

## <a name="long-description"></a>完整描述

PowerShell 支援一組特殊字元序列，用來代表不屬於標準字元集的字元。 這些序列通常稱為「 _escape 序列_ 」。

Escape sequence 的開頭是倒引號字元，也就是字元，稱為「音符號」 (ASCII 96) ，而且會區分大小寫。 倒引號字元也可以稱為「escape 字元」（ _escape character_ ）。

只有在包含于以雙引號括住的 () 字串時，才會解讀 Escape 序列 `"` 。

PowerShell 會辨識這些 escape 序列：

|  順序   |       描述       |
| ----------- | ----------------------- |
| `` `0 ``    | Null                    |
| `` `a ``    | 警示                   |
| `` `b ``    | 退格鍵               |
| `` `f ``    | 換頁字元               |
| `` `n ``    | 新行                |
| `` `r ``    | 歸位字元         |
| `` `t ``    | 水平 Tab 鍵          |
| `` `v ``    | 垂直 Tab 鍵            |

PowerShell 也有特殊標記可標示您想要剖析停止的位置。 緊接在此標記後面的所有字元都是用來做為不會解讀的常值。

特殊剖析權杖：

| 順序 |            描述             |
| -------- | ---------------------------------- |
| `--%`    | 停止剖析下列任何事項 |

## <a name="null-0"></a>Null (' 0) 

Null (`` `0 ``) 字元在 PowerShell 輸出中會顯示為空白空間。
此功能可讓您使用 PowerShell 來讀取和處理使用 null 字元的文字檔，例如字串終止或記錄終止指標。 Null 特殊字元不等於 `$null` 變數，它會儲存 **null** 值。

## <a name="alert-a"></a>警示 (' a) 

警示 (`` `a ``) 字元傳送嗶聲信號給電腦的說話者。
您可以使用此字元來警告使用者即將發生的動作。 下列範例會將兩個嗶聲信號傳送給本機電腦的說話者。

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a>倒退鍵 (' b) 

倒退鍵 (`` `b ``) 字元會將游標移回一個字元，但不會刪除任何字元。

此範例會寫入單字 **備份** ，然後將游標移回兩次。
然後，在新位置寫入一個空格，後面接著 **一個字。**

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="form-feed-f"></a>表單摘要 (' f) 

表單摘要 (`` `f ``) 字元是一種列印指令，可將目前的頁面彈出並繼續在下一頁進行列印。 表單摘要字元只會影響列印的檔。 它不會影響螢幕輸出。

## <a name="new-line-n"></a>新行 (' n) 

新的行 (`` `n ``) 字元會在字元之後插入分行符號。

此範例示範如何使用新的行字元，在命令中建立分行符號 `Write-Host` 。

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a>傳回 (' r) 的回車

「 `` `r `` 換行」 () 字元會將輸出游標移至目前行的開頭，並繼續寫入。 目前行上的任何字元都會遭到覆寫。

在此範例中，會覆寫換行之前的文字。

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

請注意，不會刪除字元之前的文字 `` `r `` ，而是會予以覆寫。

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a>水準索引標籤 (t) 

水準 `` `t `` 索引標籤 () 字元前進到下一個索引標籤，然後在該時間點繼續寫入。 根據預設，PowerShell 主控台在每八個空間都有一個 tab 鍵停止。

此範例會在每個資料行之間插入兩個索引標籤。

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="vertical-tab-v"></a>垂直索引標籤 (' v) 

水準 `` `v `` 索引標籤 () 字元前進到下一個垂直定位停駐點，然後寫入該點的剩餘輸出。 這在預設的 Windows 主控台中沒有任何作用。

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

下列範例顯示您會在印表機或不同主控台主機中取得的輸出。

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a>停止剖析權杖 (--% ) 

停止剖析 (`--%`) token 可防止 powershell 將字串解讀為 powershell 命令和運算式。 這可將這些字串傳遞給其他程式以進行解讀。

將停止剖析標記放在程式名稱之後，以及可能會造成錯誤的程式引數之前。

在此範例中，此 `Icacls` 命令會使用停止剖析權杖。

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

PowerShell 會將下列字串傳送給 `Icacls` 。

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

以下是另一個範例。 **ShowArgs** 函式會輸出傳遞給它的值。 在此範例中，我們會將名 `$HOME` 為的變數傳遞給函式兩次。

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

您可以在輸出中看到，針對第一個參數，變數 `$HOME` 會由 PowerShell 所解釋，以便將變數的值傳遞至函式。 第二種用途是在 `$HOME` 停止剖析 token 之後，因此字串 "$HOME" 會傳遞至函式，而不需解讀。

```Output
$args = C:\Users\username|--%|$HOME
```

如需有關停止剖析權杖的詳細資訊，請參閱 [about_Parsing](about_Parsing.md)。

## <a name="see-also"></a>另請參閱

[about_Quoting_Rules](about_Quoting_Rules.md)
