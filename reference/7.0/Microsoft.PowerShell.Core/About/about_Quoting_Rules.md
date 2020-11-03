---
description: 描述在 PowerShell 中使用單引號和雙引號的規則。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 8e30640c74976ac79634f5f7f648aafc16977f31
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207820"
---
# <a name="about-quoting-rules"></a>關於引號規則

## <a name="short-description"></a>簡短描述
描述在 PowerShell 中使用單引號和雙引號的規則。

## <a name="long-description"></a>詳細描述

用引號來指定常值字串。 您可以用單引號括住字串 (的 `'`) 或雙引號 (`"`) 。

引號也用來建立這個字串。 這裡的字串是以單引號括住的單引號或雙引號括住的字串，其中的引號會以字面方式來解讀。 在此，字串可以橫跨多行。 在此字串中的所有行都會被視為字串，即使它們不是以引號括住也是一樣。

在 [遠端電腦的命令] 中，引號會定義在遠端電腦上執行之命令的部分。 在遠端會話中，引號也會決定是否要先在本機電腦或遠端電腦上解釋命令中的變數。

### <a name="single-and-double-quoted-strings"></a>單引號和雙引號括住的字串

當您以雙引號括住字串， (以雙引號括住的字串) 時，會以變數的值取代前面加上貨幣符號 () 的變數名稱， `$` 然後將字串傳遞給命令進行處理。

例如：

```powershell
$i = 5
"The value of $i is $i."
```

此命令的輸出為：

```Output
The value of 5 is 5.
```

此外，在以雙引號括住的字串中，會評估運算式，並在字串中插入結果。 例如：

```powershell
"The value of $(2+3) is 5."
```

此命令的輸出為：

```Output
The value of 5 is 5.
```

當您以單引號括住字串 (單引號字串) 時，字串就會與您輸入時完全一樣地傳遞至命令。 不會執行任何替代。 例如：

```powershell
$i = 5
'The value of $i is $i.'
```

此命令的輸出為：

```Output
The value $i is $i.
```

同樣地，不會評估以單引號括住的字串中的運算式。 它們會被視為常值。 例如：

```powershell
'The value of $(2+3) is 5.'
```

此命令的輸出為：

```Output
The value of $(2+3) is 5.
```

若要避免在以雙引號括住的字串中替換變數值，請使用倒引號字元 (`` ` ``) # B2 ASCII 96) ，也就是 PowerShell escape 字元。

在下列範例中，第一個 $i 變數之前的倒引號字元會防止 PowerShell 以其值取代變數名稱。
例如：

```powershell
$i = 5
"The value of `$i is $i."
```

此命令的輸出為：

```Output
The value $i is 5.
```

若要讓雙引號出現在字串中，請使用單引號括住整個字串。 例如：

```powershell
'As they say, "live and learn."'
```

此命令的輸出為：

```Output
As they say, "live and learn."
```

您也可以用雙引號括住的字串括住單引號字串。 例如：

```powershell
"As they say, 'live and learn.'"
```

此命令的輸出為：

```Output
As they say, 'live and learn.'
```

或者，以雙引號括住雙引號的雙引號。 例如：

```powershell
"As they say, ""live and learn."""
```

此命令的輸出為：

```Output
As they say, "live and learn."
```

若要在單引號字串中加入單引號，請使用第二個連續單引號。 例如：

```powershell
'don''t'
```

此命令的輸出為：

```Output
don't
```

若要強制 PowerShell 逐字解讀雙引號，請使用倒引號字元。 這可防止 PowerShell 將引號解讀為字串分隔符號。 例如：

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

因為單引號字串的內容是以字面方式解讀，所以您會將倒引號字元視為常值字元，並顯示在輸出中。

### <a name="here-strings"></a>這裡-字串

這裡的引號規則-字串略有不同。

這裡的字串是以單引號括住的單引號或雙引號括住的字串，其中的引號會以字面方式來解讀。 在此，字串可以橫跨多行。 在此字串中的所有行都會被視為字串，即使它們不是以引號括住。

如同一般字串，變數會以雙引號括住的值取代。 在這裡以單引號括住的字串中，不會以變數的值取代變數。

您可以在這裡使用任何文字的字串，但它們對下列種類的文字特別有用：

- 包含常值引號的文字
- 多行文字，例如 HTML 或 XML 中的文字
- 腳本或函數檔的解說文字

這裡的字串可以是下列其中一種格式，其中 `<Enter>` 代表當您按下 <kbd>enter</kbd> 鍵時加入的換行字元或分行符號。

雙引號：

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

單引號：

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

無論是哪一種格式，右引號都必須是該行中的第一個字元。

這裡的字串包含兩個隱藏字元之間的所有文字。 在此字串中，所有引號都會以字面方式來解讀。 例如：

```powershell
@"
For help, type "get-help"
"@
```

此命令的輸出為：

```Output
For help, type "get-help"
```

使用這裡的字串可以簡化在命令中使用字串的方式。 例如：

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

此命令的輸出為：

```Output
Use a quotation mark (') to begin a string.
```

在這裡以單引號括住的字串中，變數會完全解讀和重現。 例如：

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

此命令的輸出為：

```Output
The $profile variable contains the path
of your PowerShell profile.
```

以雙引號括住的字串，變數會以其值取代。 例如：

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

此命令的輸出為：

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

這裡-字串通常用來將多行指派給變數。 例如，下列字串會將 XML 頁面指派給 $page 變數。

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

在此，字串也是對 Cmdlet 輸入的便利格式 `ConvertFrom-StringData` ，會將這裡的字串轉換成雜湊表。
如需詳細資訊，請參閱`ConvertFrom-StringData`。

## <a name="see-also"></a>另請參閱

[about_Special_Characters](about_Special_Characters.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
