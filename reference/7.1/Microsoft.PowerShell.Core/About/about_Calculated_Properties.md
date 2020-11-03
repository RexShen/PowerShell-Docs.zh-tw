---
description: PowerShell 可讓您以動態方式加入新的屬性，以及改變輸出到管線的物件格式。
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1ecc621d05cb340f6792481df483249095ed63a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208359"
---
# <a name="about-calculated-properties"></a>關於計算屬性

## <a name="short-description"></a>簡短描述

PowerShell 可讓您以動態方式加入新的屬性，以及改變輸出到管線的物件格式。

## <a name="long-description"></a>完整描述

許多 PowerShell Cmdlet 會使用允許將新屬性新增至這些輸出物件的參數，以轉換、匯總或處理輸入物件到輸出物件中。 這些參數可以用來根據輸入物件的值，在輸出物件上產生新的計算屬性。
匯出屬性是由 [雜湊表](about_hash_tables.md) 定義，其中包含指定新屬性名稱的索引鍵/值組、用於計算值的運算式，以及選用的格式設定資訊。

## <a name="supported-cmdlets"></a>支援的 Cmdlet

下列 Cmdlet 支援 **property** 參數的計算屬性值。 `Format-*`Cmdlet 也支援 **GroupBy** 參數的計算值。

下列清單逐項列出 Cmdlet，這些 Cmdlet 支援每個 Cmdlet 所支援的計算屬性和機碼值組。

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - `name`/`label` -PowerShell 6.x 中新增的選擇性 () 
  - `expression`
  - `width` -選擇性
  - `alignment` -選擇性

- `Format-Custom`
  - `expression`
  - `depth` -選擇性

- `Format-List`
  - `name`/`label` -選擇性
  - `expression`
  - `formatstring` -選擇性

  這組相同的索引鍵/值組也適用于傳遞給所有 Cmdlet 之 **GroupBy** 參數的計算屬性值 `Format-*` 。

- `Format-Table`
  - `name`/`label` -選擇性
  - `expression`
  - `formatstring` -選擇性
  - `width` -選擇性
  - `alignment` -選擇性

- `Format-Wide`
  - `expression`
  - `formatstring` -選擇性

- `Group-Object`
  - `expression`

- `Measure-Object`
  - 只支援運算式的腳本區塊，而不支援雜湊表。
  - PowerShell 5.1 及更舊版本不支援。

- `Select-Object`
  - `name`/`label` -選擇性
  - `expression`

- `Sort-Object`
  - `expression`
  - `ascending`/`descending` -選擇性

> [!NOTE]
> 的值 `expression` 可以是腳本區塊，而不是雜湊表。 如需詳細資訊，請參閱 [附注](#notes) 一節。

## <a name="hashtable-key-definitions"></a>雜湊表索引鍵定義

- `name`/`label` -指定要建立之屬性的名稱。 您可以使用 `name` 或其別名（可 `label` 交換）。
- `expression` -用來計算新屬性值的腳本區塊。
- `alignment` -由產生表格式輸出的指令程式使用，以定義值在資料行中的顯示方式。 值必須是 `'left'` 、 `'center'` 或 `'right'` 。
- `formatstring` -指定格式字串，以定義值格式化輸出的方式。 如需格式字串的詳細資訊，請參閱 [.net 中的格式類型](/dotnet/standard/base-types/formatting-types)。
- `width` -在顯示值時，指定資料表中的最大寬度資料行。 值必須大於 `0` 。
- `depth` -的 **depth** 參數會 `Format-Custom` 為所有屬性指定擴充的深度。 此索引 `depth` 鍵可讓您指定每個屬性的展開深度。
- `ascending` / `descending` -可讓您指定一或多個屬性的排序次序。 這些是布林值。

只要指定的名稱前置詞不明確，雜湊表索引鍵不需要拼出。 例如， `n` 可以用來代替 `Name` ，而且 `e` 可以用來代替 `Expression` 。

## <a name="examples"></a>範例

### <a name="compare-object"></a>Compare-Object

您可以使用 [計算屬性] 來控制如何比較輸入物件的屬性。 在此範例中，您不會直接比較值，而是比較值與算數運算的結果 (2) 的模數。

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a>ConvertTo-Html

`ConvertTo-Html` 可以將物件的集合轉換成 HTML 資料表。
計算屬性可讓您控制資料表的呈現方式。

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

這個範例會建立 HTML 表格，其中包含 PowerShell 別名清單和每個別名命令的數位參數。 **ParameterCount** 資料行的值會置中。

### <a name="format-custom"></a>Format-Custom

`Format-Custom` 以類似于類別定義的格式，提供物件的自訂視圖。 更複雜的物件可以包含以複雜型別進行深層嵌套的成員。 的 **depth** 參數會 `Format-Custom` 為所有屬性指定擴充的深度。 此索引 `depth` 鍵可讓您指定每個屬性的展開深度。

在此範例中， `depth` 金鑰可簡化 Cmdlet 的自訂輸出 `Get-Date` 。 `Get-Date` 傳回 **DateTime** 物件。 這個物件的 **Date** 屬性也是 **DateTime** 物件，因此物件是嵌套的。

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a>Format-List

在此範例中，我們使用計算屬性來變更輸出的名稱和格式 `Get-ChildItem` 。

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a>Format-Table

在此範例中，計算屬性會加入用來依內容類型分類檔案的 **型** 別屬性。

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a>Format-Wide

此 `Format-Wide` Cmdlet 可讓您將集合中物件的某個屬性值顯示為多資料行清單。

在此範例中，我們想要以 kb 的形式來查看檔案名和大小 (（以 kb 為單位）) 。 由於不 `Format-Wide` 會顯示多個屬性，因此我們會使用計算屬性，將兩個屬性的值結合成單一值。

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a>Group-Object

此 `Group-Object` Cmdlet 會根據指定屬性的值，在群組中顯示物件。 在此範例中，計算屬性會計算每個內容類型的檔案數目。

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a>Measure-Object

`Measure-Object`Cmdlet 會計算物件的數值屬性。 在此範例中，我們會使用計算屬性來取得計數 (加) **總** 值（介於1到10之間），並可平均地除以3。

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> 與其他 Cmdlet 不同的 `Measure-Object` 是，不接受計算屬性的雜湊表。 您必須使用腳本區塊。

### <a name="select-object"></a>Select-Object

您可以使用計算屬性，將其他成員新增至使用此 Cmdlet 的輸出物件 `Select-Object` 。 在此範例中，我們會列出以字母開頭的 PowerShell 別名 `C` 。 使用 `Select-Object` 時，我們會輸出別名、其所對應的 Cmdlet，以及針對 Cmdlet 定義的參數數目計數。 使用計算屬性，我們可以建立 **ParameterCount** 屬性。

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a>Sort-Object

您可以使用計算屬性，依每個屬性的不同順序來排序資料。 此範例會依 **日期** 以遞增順序排序 CSV 檔案中的資料。 但是在每個日期內，它會依 **UnitsSold** 以遞減順序排序資料列。

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a>備忘稿

- 您可以 _直接_ 指定運算式腳本區塊做為引數，而不是將它指定為 `Expression` 雜湊表中的專案。 例如：

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  這個範例很方便不需要 (或支援) 透過 `Name` 金鑰（例如、和）命名屬性的 Cmdlet `Sort-Object` `Group-Object` `Measure-Object` 。

  針對支援命名屬性的 Cmdlet，腳本區塊會轉換成字串，並當做輸出中屬性的名稱使用。

- `Expression` 腳本區塊會在 _子_ 範圍中執行，這表示呼叫端的變數無法直接修改。

- 管線邏輯會套用至 `Expression` 腳本區塊的輸出。 這表示，輸出單一元素陣列會導致該陣列解除包裝。

- 在大部分的 Cmdlet 中，運算式腳本區塊內的錯誤會以安靜的形式忽略。
  針對 `Sort-Object` ，語句終止和腳本結束錯誤是 _輸出_ ，但不會終止語句。

## <a name="see-also"></a>另請參閱

[about_Hash_Tables](about_hash_tables.md)

[Compare-Object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[Format-Custom](xref:Microsoft.PowerShell.Utility.Format-Custom)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Format-Wide](xref:Microsoft.PowerShell.Utility.Format-Wide)

[Group-Object](xref:Microsoft.PowerShell.Utility.Group-Object)

[Measure-Object](xref:Microsoft.PowerShell.Utility.Measure-Object)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Sort-Object](xref:Microsoft.PowerShell.Utility.Sort-Object)

[.NET 中的格式類型](/dotnet/standard/base-types/formatting-types)
