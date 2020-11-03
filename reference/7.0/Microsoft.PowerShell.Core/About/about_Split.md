---
description: 說明如何使用 Split 運算子將一或多個字串分割成子字串。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: ed57cec30577fbd02f7aa317460bf1a73b006685
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206556"
---
# <a name="about-split"></a>關於分割

## <a name="short-description"></a>簡短描述
說明如何使用 Split 運算子將一或多個字串分割成子字串。

## <a name="long-description"></a>詳細描述

Split 運算子會將一個或多個字串分割成子字串。 您可以變更分割作業的下列元素：

- 分隔符號。 預設值為空白，但您可以指定字元、字串、模式或指定分隔符號的腳本區塊。 PowerShell 中的 Split 運算子會在分隔符號中使用正則運算式，而不是使用簡單字元。
- 子字串的最大數目。 預設值是傳回所有子字串。 如果您指定的數位小於子字串的數目，則會在最後一個子字串串連其餘的子字串。
- 選項，可指定符合分隔符號的條件，例如 SimpleMatch 和多行。

## <a name="syntax"></a>SYNTAX

下圖顯示-split 運算子的語法。

參數名稱不會出現在命令中。 只包含參數值。 這些值必須以語法圖表中指定的順序顯示。

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

您可以 `-iSplit` `-cSplit` `-split` 在任何二元分割語句中替代或， (包含分隔符號或腳本區塊) 的 split 語句。 `-iSplit`和 `-split` 運算子不區分大小寫。 `-cSplit`運算子會區分大小寫，這表示套用分隔符號規則時，會考慮大小寫。

## <a name="parameters"></a>PARAMETERS

### <a name="string-or-string"></a>\<String\> 或 \<String[]\>

指定要分割的一或多個字串。 如果您提交多個字串，則會使用相同的分隔符號規則來分割所有字串。

範例：

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

識別子字串結尾的字元。 預設分隔符號是空白字元，包括空格和不可列印的字元，例如分行符號 (\` n) 和 tab (\` t) 。 分割字串時，會省略所有子字串中的分隔符號。 範例：

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

根據預設，會從結果中省略分隔符號。 若要保留全部或部分的分隔符號，請以括弧括住您想要保留的部分。
如果已 \<Max-substrings\> 加入參數，則當您的命令分割集合時，會優先使用此參數。 如果您選擇包含分隔符號作為輸出的一部分，此命令會傳回分隔符號作為輸出的一部分;但是，將字串分割以傳回分隔符號作為輸出的一部分，並不會被視為分割。

範例：

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

在下列範例中， \<Max-substrings\> 會設為3。 這會產生三個字串值的分割，但產生的輸出中總共有五個字串：分隔符號會包含在分割之後，直到達到三個子字串的最大值為止。 最後一個子字串中的其他分隔符號會成為子字串的一部分。

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

指定分割字串的最大次數。 預設值是依分隔符號分割的所有子字串。 如果有更多的子字串，它們會串連到最後一個子字串。 如果有較少的子字串，則會傳回所有子字串。 值為0會傳回所有子字串。 負數值會傳回從輸入字串結尾開始要求的子字串數量。

> [!NOTE]
> 已在 PowerShell 7 中新增對負值的支援。

**Max-子字串** 不會指定傳回的最大物件數目。 其值等於分割字串的最大次數。
如果您將一個以上的字串 (的字串陣列提交) 給 `-split` 運算子，則 **最大的子** 字串限制會分別套用至每個字串。

範例：

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

運算式，指定套用分隔符號的規則。 運算式必須評估為 $true 或 $false。 以大括弧括住腳本區塊。

範例：

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

將選項名稱括在引號中。 只有在 \<Max-substrings\> 語句中使用參數時，選項才有效。

Options 參數的語法為：

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

SimpleMatch 選項如下：

- **SimpleMatch** ：評估分隔符號時，請使用簡單的字串比較。 無法與 RegexMatch 搭配使用。
- **IgnoreCase** ：強制比對不區分大小寫，即使已指定-cSplit 運算子也是如此。

RegexMatch 選項如下：

- **RegexMatch** ：使用正則運算式比對來評估分隔符號。 此為預設行為。 無法與 SimpleMatch 搭配使用。
- **IgnoreCase** ：強制比對不區分大小寫，即使已指定-cSplit 運算子也是如此。
- **>RegExoptions.cultureinvariant** ：評估分隔符號時，會忽略語言的文化差異。 僅適用于 RegexMatch。
- **Regexoptions.ignorepatternwhitespace** ：忽略以數位正負號 ( # ) 標記的非轉義空白字元和批註。 僅適用于 RegexMatch。
- **多** 行：多行模式會強制 `^` 並 `$` 比對每一行的開頭，而不是輸入字串的開頭和結尾。
- **單行** ：單行模式會將輸入字串視為 *單行* 。
  它會強制 `.` 字元符合每個字元 (包括分行符號) ，而不是比對分行符號以外的每個字元 `\n` 。
- **>RegExoptions.explicitcapture** ：忽略非命名的比對群組，以便只傳回結果清單中的明確 capture 群組。 僅適用于 RegexMatch。

## <a name="unary-and-binary-split-operators"></a>一元和二元分割運算子

一元分割運算子 (`-split <string>`) 的優先順序高於逗號。 如此一來，如果您將以逗號分隔的字串清單提交給一元分割運算子，則只有第一個字串在第一個逗號) 之前 (會被分割。

您可以使用下列其中一種模式來分割一個以上的字串：

- 使用二元分割運算子 (\<string[]\> 分割 \<delimiter\>) 
- 將所有字串括在括弧中
- 將字串儲存在變數中，然後將變數提交給分割運算子

請考慮下列範例：

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a>範例

下列語句會將字串分割為空格。

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

下列語句會以任何逗號分隔字串。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

下列語句會將字串分割為 "er" 模式。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

下列語句會以字母 "N" 執行區分大小寫的分割。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

下列語句會將字串分割為 "e" 和 "t"。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

下列語句會在 "e" 和 "r" 分割字串，但會將產生的子字串限制為六個子字串。

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

下列語句會將字串分割成三個子字串。

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

下列語句會從字串結尾開始，將字串分割成三個子字串。

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

下列語句會將兩個字串分割成三個子字串。
 (限制會個別套用至每個字串。 ) 

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

下列語句會在第一個數位分割此處的每一行。 它會使用多行選項來辨識每一行和字串的開頭。

0代表最大子字串參數的 "return all" 值。 只有在指定最大的子字串值時，您才能使用選項，例如多行。

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

下列語句會使用反斜線字元來將點 ( ) 分隔符號。

使用預設值 RegexMatch 時，以引號括住的點 ( ".") 會被解讀來比對分行符號以外的任何字元。 因此，Split 語句會針對分行符號以外的每個字元傳回空白行。

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

下列語句會使用 SimpleMatch 選項來指示-split 運算子，將點 (。 ) 分隔符號。

0代表最大子字串參數的 "return all" 值。 只有在指定最大的子字串值時，您才能使用選項（例如 SimpleMatch）。

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

下列語句會根據變數的值，將字串分割成兩個分隔符號的其中一個。

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a>另請參閱

[Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Join](about_Join.md)
