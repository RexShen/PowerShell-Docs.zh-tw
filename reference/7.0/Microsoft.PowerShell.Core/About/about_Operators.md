---
description: 描述 PowerShell 所支援的運算子。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: d442a64be77934cef4636e905c098d9630451b8f
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208939"
---
# <a name="about-operators"></a>關於運算子

## <a name="short-description"></a>簡短描述
描述 PowerShell 所支援的運算子。

## <a name="long-description"></a>完整描述

操作員是可在命令或運算式中使用的語言元素。
PowerShell 支援數種可協助您操作值的運算子類型。

### <a name="arithmetic-operators"></a>算術運算子

使用算術運算子 (`+` 、 `-` 、 `*` 、 `/` `%`) 來計算命令或運算式中的值。 您可以使用這些運算子來加、減、乘或除值，並計算除法運算 (模數) 的餘數。

加法運算子串連元素。 乘法運算子會傳回每個專案的指定複本數目。 您可以將算術運算子用於任何執行它們的 .net 型別，例如： `Int` 、 `String` 、 `DateTime` 、 `Hashtable` 和陣列。

位運算子 (`-band` 、 `-bor` 、 `-bxor` 、 `-bnot` 、 `-shl` `-shr`) 操作值中的位模式。

如需詳細資訊，請參閱 [about_Arithmetic_Operators](about_Arithmetic_Operators.md)。

### <a name="assignment-operators"></a>指派運算子

使用指派運算子 (`=` 、 `+=` 、 `-=` 、 `*=` 、 `/=` `%=`) ，將值指派、變更或附加到變數。 您可以結合算術運算子與指派，將算數運算的結果指派給變數。

如需詳細資訊，請參閱 [about_Assignment_Operators](about_Assignment_Operators.md)。

### <a name="comparison-operators"></a>比較運算子

使用比較運算子 (`-eq` 、 `-ne` 、 `-gt` 、 `-lt` 、 `-le` `-ge`) 來比較值和測試條件。 例如，您可以比較兩個字串值，判斷它們是否相等。

比較運算子也包含尋找或取代文字中之模式的運算子。  (`-match` 、 `-notmatch` 、 `-replace`) 運算子會使用正則運算式，並 `-like` (`-notlike`) 使用萬用字元 `*` 。

內含專案比較運算子會判斷測試值是否出現在參考集 (`-in` 、 `-notin` 、 `-contains` `-notcontains`) 。

類型比較運算子 (`-is` ， `-isnot`) 判斷物件是否為指定的類型。

如需詳細資訊，請參閱 [about_Comparison_Operators](about_Comparison_Operators.md)。

### <a name="logical-operators"></a>邏輯運算子

使用邏輯運算子 (`-and` 、 `-or` 、 `-xor` 、) ，將 `-not` `!` 條件陳述式連接到單一複雜的條件。 例如，您可以使用邏輯 `-and` 運算子來建立具有兩個不同條件的物件篩選。

如需詳細資訊，請參閱 [about_Logical_Operators](about_logical_operators.md)。

### <a name="redirection-operators"></a>重新導向運算子

使用重新導向運算子 (`>` 、、 `>>` `2>` 、和) ，將 `2>>` `2>&1` 命令或運算式的輸出傳送至文字檔。 重新導向運算子的運作方式就像 `Out-File` Cmdlet (沒有參數) 但也可讓您將錯誤輸出重新導向至指定的檔案。 您也可以使用 `Tee-Object` Cmdlet 來重新導向輸出。

如需詳細資訊，請參閱 [about_Redirection](about_Redirection.md)

### <a name="split-and-join-operators"></a>分割和聯結運算子

`-split`和運算子會將 `-join` 子字串相除併合並。 運算子會將 `-split` 字串分割成子字串。 運算子會將 `-join` 多個字串串連成單一字串。

如需詳細資訊，請參閱 [about_Split](about_Split.md) 和 [about_Join](about_Join.md)。

### <a name="type-operators"></a>運算子型別

使用類型運算子 (`-is` 、 `-isnot` 、 `-as`) 來尋找或變更物件的 .NET Framework 類型。

如需詳細資訊，請參閱 [about_Type_Operators](about_Type_Operators.md)。

### <a name="unary-operators"></a>一元運算子

您可以使用一元運算子來遞增或遞減變數或物件屬性，以及將整數設定為正數或負數。 例如，若要將變數 `$a` 從遞增 `9` 到 `10` ，請輸入 `$a++` 。

### <a name="special-operators"></a>特殊運算子

特殊運算子具有不符合任何其他操作員群組的特定使用案例。 例如，特殊運算子可讓您執行命令、變更值的資料類型，或從陣列中取出元素。

#### <a name="grouping-operator--"></a>群組運算子 `( )`

在其他語言中，則是用 `(...)` 來覆寫運算式中的運算子優先順序。 例如：`(1 + 2) / 3`

不過，在 PowerShell 中還有其他行為。

- `(...)` 允許您讓 _命令_ 的輸出參與運算式。 例如：

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- 當做管線的第一個區段使用時，以括弧括住命令或運算式，會造成運算式結果的 _列舉_ 。 如果括弧包裝一個 _命令_ ，則會使用 _記憶體中收集_ 到的所有輸出來執行完成，然後才會透過管線傳送結果。

#### <a name="subexpression-operator--"></a>子運算式運算子 `$( )`

傳回一或多個語句的結果。 針對單一結果，會傳回純量。 針對多個結果，會傳回陣列。 當您想要在另一個運算式中使用運算式時，請使用此語句。 例如，將命令的結果內嵌在字串運算式中。

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a>陣列子運算式運算子 `@( )`

傳回一個或多個語句的結果做為陣列。 如果只有一個專案，則陣列只有一個成員。

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a>呼叫運算子 `&`

執行命令、腳本或腳本區塊。 呼叫運算子也稱為「調用運算子」，可讓您執行儲存在變數中，並以字串或腳本區塊表示的命令。 呼叫運算子會在子範圍中執行。 如需範圍的詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。

此範例會將命令儲存在字串中，並使用 call 運算子來執行它。

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

呼叫運算子不會剖析字串。 這表示當您使用呼叫運算子時，不能在字串中使用命令參數。

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
```

叫用 [運算式](xref:Microsoft.PowerShell.Utility.Invoke-Expression) Cmdlet 可以執行程式碼，以在使用呼叫運算子時產生剖析錯誤。

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

您可以使用呼叫運算子來執行使用其檔案名的腳本。 下列範例顯示包含空格的指令檔名。 當您嘗試執行腳本時，PowerShell 會改為顯示包含檔案名之加上引號的字串內容。 呼叫運算子可讓您執行包含檔案名的字串內容。

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

如需腳本區塊的詳細資訊，請參閱 [about_Script_Blocks](about_Script_Blocks.md)。

#### <a name="background-operator-"></a>背景運算子 `&`

在 PowerShell 作業中，于背景執行管線。 這個運算子的運作方式類似于 UNIX 控制運算子符號 (`&`) ，它會在 subshell 中以非同步方式執行命令，以做為作業。

這個運算子在功能上相當於 `Start-Job` 。 根據預設，背景運算子會啟動啟動平行工作之呼叫端的目前工作目錄中的工作。 下列範例示範背景工作運算子的基本使用方式。

```powershell
Get-Process -Name pwsh &
```

該命令的功能相當於下列用途 `Start-Job` ：

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

就像 `Start-Job` ， `&` background 運算子會傳回 `Job` 物件。 這個物件可以與和一起 `Receive-Job` 使用 `Remove-Job` ，就像您用 `Start-Job` 來啟動作業一樣。

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

`&`背景運算子也是語句結束字元，就像 UNIX 控制運算子符號 (`&`) 一樣。 這可讓您在背景運算子之後叫用其他命令 `&` 。 下列範例示範如何在背景運算子之後叫用其他命令 `&` 。

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

這相當於下列腳本：

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

如果您想要執行多個命令，每個命令都在各自的背景進程中，但全都在同一行，只要在 `&` 每個命令的前後放置。

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

如需 PowerShell 工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。

#### <a name="cast-operator--"></a>Cast 運算子 `[ ]`

將物件轉換或限制為指定的類型。 如果無法轉換物件，PowerShell 會產生錯誤。

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

當指派變數給使用 [cast 標記法](about_Variables.md)時，也可以執行轉換。

#### <a name="comma-operator-"></a>逗點運算子 `,`

作為二元運算子，逗號會建立陣列或附加至所建立的陣列。 在運算式模式中，以一元運算子的形式，逗號會建立只包含一個成員的陣列。 將逗號放在成員前面。

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

由於 `Write-Object` 需要引數，因此您必須將運算式放在括弧中。

#### <a name="dot-sourcing-operator-"></a>點來源運算子 `.`

在目前的範圍中執行腳本，以便將腳本所建立的任何函式、別名和變數新增至目前的範圍，並覆寫現有的範圍。 腳本所宣告的參數會成為變數。 未指定任何值的參數會成為沒有值的變數。 不過，自動變數 `$args` 會保留下來。

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> 點來源運算子後面接著空格。 使用空格來區分點與 `.` 代表目前的目錄的點 () 符號。
>
> 在下列範例中，目前目錄中的 Sample.ps1 腳本會在目前的範圍中執行。
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a>格式運算子 `-f`

使用 string 物件的 format 方法來格式化字串。 輸入運算子左邊的格式字串，以及要在運算子右邊格式化的物件。

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

如果您需要 `{}` 在格式化的字串中保留大括弧 () ，您可以將大括弧換成一倍來將其取消。

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

如需詳細資訊，請參閱 [字串。格式](/dotnet/api/system.string.format) 方法和 [複合格式](/dotnet/standard/base-types/composite-formatting)。

#### <a name="index-operator--"></a>索引運算子 `[ ]`

從索引集合中選取物件，例如陣列和雜湊表。 陣列索引是以零為基底，因此第一個物件的索引為 `[0]` 。 針對僅) 的陣列 (，您也可以使用負索引來取得最後的值。 雜湊表是依索引鍵值來編制索引。

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a>管線運算子 `|`

傳送 ( "pipe" ) 命令前面的命令輸出到其後的命令。 當輸出包含一個以上的物件 ("collection" ) 時，管線運算子會一次傳送一個物件。

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="pipeline-chain-operators--and-"></a>管線鏈運算子 `&&` 和 `||`

根據左側管線的成功與否，有條件地執行右手邊的管線。

```powershell
# If Get-Process successfully finds a process called notepad,
# Stop-Process -Name notepad is called
Get-Process notepad && Stop-Process -Name notepad
```

```powershell
# If npm install fails, the node_modules directory is removed
npm install || Remove-Item -Recurse ./node_modules
```

如需詳細資訊，請參閱 [About_Pipeline_Chain_Operators](About_Pipeline_Chain_Operators.md)。

#### <a name="range-operator-"></a>範圍運算子 `..`

表示整數陣列中的連續整數，指定上限和下限。

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

您也可以依相反順序建立範圍。

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

從 PowerShell 6 開始，範圍運算子適用于 **字元** 和 **整數** 。

若要建立字元範圍，請將界限字元括在引號中。

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a>成員存取運算子 `.`

存取物件的屬性和方法。 成員名稱可以是運算式。

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a>靜態成員運算子 `::`

呼叫 .NET Framework 類別的靜態屬性和方法。 若要尋找物件的靜態屬性和方法，請使用 Cmdlet 的靜態參數 `Get-Member` 。  成員名稱可以是運算式。

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

#### <a name="ternary-operator--if-true--if-false"></a>三元運算子 `? <if-true> : <if-false>`

您可以使用三元運算子來取代簡單的條件式 `if-else` 案例中的語句。

如需詳細資訊，請參閱 [about_If](about_If.md)。

#### <a name="null-coalescing-operator-"></a>Null 聯合運算子 `??`

Null 聯合運算子 `??` 會傳回其左側運算元的值 (如果不是 Null)。 否則會評估右側運算元，並傳回其結果。 如果左側運算元評估為非 Null，則 `??` 運算子不會評估右側運算元。

```powershell
$x = $null
$x ?? 100
```

```Output
100
```

在下列範例中，將不會評估右側運算元。

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-coalescing-assignment-operator-"></a>Null 聯合指派運算子 `??=`

Null 聯合指派運算子只有在 `??=` 左運算元評估為 null 時，才會將右邊運算元的值指派給其左邊運算元。 如果左側運算元評估為非 Null，則 `??=` 運算子不會評估右側運算元。

```powershell
$x = $null
$x ??= 100
$x
```

```Output
100
```

在下列範例中，將不會評估右側運算元。

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
```

```Output
1/10/2020
```

#### <a name="null-conditional-operators--and-"></a>Null 條件運算子 `?.` 和 `?[]`

> [!NOTE]
> 這是實驗性的功能。 如需詳細資訊，請參閱 [about_Experimental_Features](about_Experimental_Features.md)。

Null 條件運算子會在運算元評估為非 null 的情況下，將成員存取、 `?.` 或專案存取權套用 `?[]` 至其運算元; 否則，它會傳回 null。

由於 PowerShell 允許 `?` 作為變數名稱的一部分，因此，使用這些運算子時需要變數名稱的型式規格。 因此，必須在 `${a}` 之類的變數名稱前後，或是當 `?` 為變數名稱 `${a?}` 的一部分時，使用 `{}`。

在下列範例中，會傳回 **PropName** 的值。

```powershell
$a = @{ PropName = 100 }
${a}?.PropName
```

```Output
100
```

下列範例將會傳回 null，而不會嘗試存取成員名稱 **PropName** 。

```powershell
$a = $null
${a}?.PropName
```

同樣地，將會傳回元素的值。

```powershell
$a = 1..10
${a}?[0]
```

```Output
1
```

當運算元為 null 時，就不會存取元素，而且會傳回 null。

```PowerShell
$a = $null
${a}?[0]
```

## <a name="see-also"></a>另請參閱

[about_Arithmetic_Operators](about_Arithmetic_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Logical_Operators](about_logical_operators.md)

[about_Operator_Precedence](about_operator_precedence.md)

[about_Type_Operators](about_Type_Operators.md)

[about_Pipeline_Chain_Operators](about_Pipeline_Chain_Operators.md)

[about_Split](about_Split.md)

[about_Join](about_Join.md)

[about_Redirection](about_Redirection.md)
