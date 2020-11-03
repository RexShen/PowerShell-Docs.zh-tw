---
description: PowerShell 可讓您以動態方式加入新的屬性，以及改變輸出到管線的物件格式。
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 7937d4e59f2e73c8b52e9957dd143b6d48eeae57
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206664"
---
# <a name="about-calculated-properties"></a><span data-ttu-id="16642-103">關於計算屬性</span><span class="sxs-lookup"><span data-stu-id="16642-103">About calculated properties</span></span>

## <a name="short-description"></a><span data-ttu-id="16642-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="16642-104">Short Description</span></span>

<span data-ttu-id="16642-105">PowerShell 可讓您以動態方式加入新的屬性，以及改變輸出到管線的物件格式。</span><span class="sxs-lookup"><span data-stu-id="16642-105">PowerShell provides the ability to dynamically add new properties and alter the formatting of objects output to the pipeline.</span></span>

## <a name="long-description"></a><span data-ttu-id="16642-106">完整描述</span><span class="sxs-lookup"><span data-stu-id="16642-106">Long Description</span></span>

<span data-ttu-id="16642-107">許多 PowerShell Cmdlet 會使用允許將新屬性新增至這些輸出物件的參數，以轉換、匯總或處理輸入物件到輸出物件中。</span><span class="sxs-lookup"><span data-stu-id="16642-107">A number of PowerShell cmdlets transform, aggregate, or process input objects into output objects using parameters that allow the addition of new properties to those output objects.</span></span> <span data-ttu-id="16642-108">這些參數可以用來根據輸入物件的值，在輸出物件上產生新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="16642-108">These parameters can be used to generate new, calculated properties on output objects based on the values of input objects.</span></span>
<span data-ttu-id="16642-109">匯出屬性是由 [雜湊表](about_hash_tables.md) 定義，其中包含指定新屬性名稱的索引鍵/值組、用於計算值的運算式，以及選用的格式設定資訊。</span><span class="sxs-lookup"><span data-stu-id="16642-109">The calculated property is defined by a [hashtable](about_hash_tables.md) containing key-value pairs that specify the name of the new property, an expression to calculate the value, and optional formatting information.</span></span>

## <a name="supported-cmdlets"></a><span data-ttu-id="16642-110">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="16642-110">Supported cmdlets</span></span>

<span data-ttu-id="16642-111">下列 Cmdlet 支援 **property** 參數的計算屬性值。</span><span class="sxs-lookup"><span data-stu-id="16642-111">The following cmdlets support calculated property values for the **Property** parameter.</span></span> <span data-ttu-id="16642-112">`Format-*`Cmdlet 也支援 **GroupBy** 參數的計算值。</span><span class="sxs-lookup"><span data-stu-id="16642-112">The `Format-*` cmdlets also support calculated values for the **GroupBy** parameter.</span></span>

<span data-ttu-id="16642-113">下列清單逐項列出 Cmdlet，這些 Cmdlet 支援每個 Cmdlet 所支援的計算屬性和機碼值組。</span><span class="sxs-lookup"><span data-stu-id="16642-113">The following list itemizes the cmdlets that support calculated properties and the key-value pairs that are supported by each cmdlet.</span></span>

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - <span data-ttu-id="16642-114">`name`/`label` -PowerShell 6.x 中新增的選擇性 () </span><span class="sxs-lookup"><span data-stu-id="16642-114">`name`/`label` - optional (added in PowerShell 6.x)</span></span>
  - `expression`
  - <span data-ttu-id="16642-115">`width` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-115">`width` - optional</span></span>
  - <span data-ttu-id="16642-116">`alignment` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-116">`alignment` - optional</span></span>

- `Format-Custom`
  - `expression`
  - <span data-ttu-id="16642-117">`depth` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-117">`depth` - optional</span></span>

- `Format-List`
  - <span data-ttu-id="16642-118">`name`/`label` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-118">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="16642-119">`formatstring` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-119">`formatstring` - optional</span></span>

  <span data-ttu-id="16642-120">這組相同的索引鍵/值組也適用于傳遞給所有 Cmdlet 之 **GroupBy** 參數的計算屬性值 `Format-*` 。</span><span class="sxs-lookup"><span data-stu-id="16642-120">This same set of key-value pairs also apply to calculated property values passed to the **GroupBy** parameter for all `Format-*` cmdlets.</span></span>

- `Format-Table`
  - <span data-ttu-id="16642-121">`name`/`label` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-121">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="16642-122">`formatstring` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-122">`formatstring` - optional</span></span>
  - <span data-ttu-id="16642-123">`width` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-123">`width` - optional</span></span>
  - <span data-ttu-id="16642-124">`alignment` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-124">`alignment` - optional</span></span>

- `Format-Wide`
  - `expression`
  - <span data-ttu-id="16642-125">`formatstring` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-125">`formatstring` - optional</span></span>

- `Group-Object`
  - `expression`

- `Measure-Object`
  - <span data-ttu-id="16642-126">只支援運算式的腳本區塊，而不支援雜湊表。</span><span class="sxs-lookup"><span data-stu-id="16642-126">Only supports a script block for the expression, not a hashtable.</span></span>
  - <span data-ttu-id="16642-127">PowerShell 5.1 及更舊版本不支援。</span><span class="sxs-lookup"><span data-stu-id="16642-127">Not supported in PowerShell 5.1 and older.</span></span>

- `Select-Object`
  - <span data-ttu-id="16642-128">`name`/`label` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-128">`name`/`label` - optional</span></span>
  - `expression`

- `Sort-Object`
  - `expression`
  - <span data-ttu-id="16642-129">`ascending`/`descending` -選擇性</span><span class="sxs-lookup"><span data-stu-id="16642-129">`ascending`/`descending` - optional</span></span>

> [!NOTE]
> <span data-ttu-id="16642-130">的值 `expression` 可以是腳本區塊，而不是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="16642-130">The value of the `expression` can be a script block instead of a hashtable.</span></span> <span data-ttu-id="16642-131">如需詳細資訊，請參閱 [附注](#notes) 一節。</span><span class="sxs-lookup"><span data-stu-id="16642-131">For more information, see the [Notes](#notes) section.</span></span>

## <a name="hashtable-key-definitions"></a><span data-ttu-id="16642-132">雜湊表索引鍵定義</span><span class="sxs-lookup"><span data-stu-id="16642-132">Hashtable key definitions</span></span>

- <span data-ttu-id="16642-133">`name`/`label` -指定要建立之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="16642-133">`name`/`label` - Specifies the name of the property being created.</span></span> <span data-ttu-id="16642-134">您可以使用 `name` 或其別名（可 `label` 交換）。</span><span class="sxs-lookup"><span data-stu-id="16642-134">You can use `name` or its alias, `label`, interchangeably.</span></span>
- <span data-ttu-id="16642-135">`expression` -用來計算新屬性值的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="16642-135">`expression` - A script block used to calculate the value of the new property.</span></span>
- <span data-ttu-id="16642-136">`alignment` -由產生表格式輸出的指令程式使用，以定義值在資料行中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="16642-136">`alignment` - Used by cmdlets that produce tabular output to define how the values are displayed in a column.</span></span> <span data-ttu-id="16642-137">值必須是 `'left'` 、 `'center'` 或 `'right'` 。</span><span class="sxs-lookup"><span data-stu-id="16642-137">The value must be `'left'`, `'center'`, or `'right'`.</span></span>
- <span data-ttu-id="16642-138">`formatstring` -指定格式字串，以定義值格式化輸出的方式。</span><span class="sxs-lookup"><span data-stu-id="16642-138">`formatstring` - Specifies a format string that defines how the value is formatted for output.</span></span> <span data-ttu-id="16642-139">如需格式字串的詳細資訊，請參閱 [.net 中的格式類型](/dotnet/standard/base-types/formatting-types)。</span><span class="sxs-lookup"><span data-stu-id="16642-139">For more information about format strings, see [Format types in .NET](/dotnet/standard/base-types/formatting-types).</span></span>
- <span data-ttu-id="16642-140">`width` -在顯示值時，指定資料表中的最大寬度資料行。</span><span class="sxs-lookup"><span data-stu-id="16642-140">`width` - Specifies the maximum width column in a table when the value is displayed.</span></span> <span data-ttu-id="16642-141">值必須大於 `0` 。</span><span class="sxs-lookup"><span data-stu-id="16642-141">The value must be greater than `0`.</span></span>
- <span data-ttu-id="16642-142">`depth` -的 **depth** 參數會 `Format-Custom` 為所有屬性指定擴充的深度。</span><span class="sxs-lookup"><span data-stu-id="16642-142">`depth` - The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="16642-143">此索引 `depth` 鍵可讓您指定每個屬性的展開深度。</span><span class="sxs-lookup"><span data-stu-id="16642-143">The `depth` key allows you to specify the depth of expansion per property.</span></span>
- <span data-ttu-id="16642-144">`ascending` / `descending` -可讓您指定一或多個屬性的排序次序。</span><span class="sxs-lookup"><span data-stu-id="16642-144">`ascending` / `descending` - Allows you to specify the order of sorting for one or more properties.</span></span> <span data-ttu-id="16642-145">這些是布林值。</span><span class="sxs-lookup"><span data-stu-id="16642-145">These are boolean values.</span></span>

<span data-ttu-id="16642-146">只要指定的名稱前置詞不明確，雜湊表索引鍵不需要拼出。</span><span class="sxs-lookup"><span data-stu-id="16642-146">The hashtable keys need not be spelled out as long as the specified name prefix is unambiguous.</span></span> <span data-ttu-id="16642-147">例如， `n` 可以用來代替 `Name` ，而且 `e` 可以用來代替 `Expression` 。</span><span class="sxs-lookup"><span data-stu-id="16642-147">For example, `n` can be used in lieu of `Name` and `e` can be used in lieu of `Expression`.</span></span>

## <a name="examples"></a><span data-ttu-id="16642-148">範例</span><span class="sxs-lookup"><span data-stu-id="16642-148">Examples</span></span>

### <a name="compare-object"></a><span data-ttu-id="16642-149">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="16642-149">Compare-Object</span></span>

<span data-ttu-id="16642-150">您可以使用 [計算屬性] 來控制如何比較輸入物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="16642-150">With calculated properties, you can control how the properties of the input objects are compared.</span></span> <span data-ttu-id="16642-151">在此範例中，您不會直接比較值，而是比較值與算數運算的結果 (2) 的模數。</span><span class="sxs-lookup"><span data-stu-id="16642-151">In this example, rather than comparing the values directly, the values are compared to the result of the arithmetic operation (modulus of 2).</span></span>

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a><span data-ttu-id="16642-152">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="16642-152">ConvertTo-Html</span></span>

<span data-ttu-id="16642-153">`ConvertTo-Html` 可以將物件的集合轉換成 HTML 資料表。</span><span class="sxs-lookup"><span data-stu-id="16642-153">`ConvertTo-Html` can convert a collection of objects to an HTML table.</span></span>
<span data-ttu-id="16642-154">計算屬性可讓您控制資料表的呈現方式。</span><span class="sxs-lookup"><span data-stu-id="16642-154">Calculated properties allow you to control how the table is presented.</span></span>

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

<span data-ttu-id="16642-155">這個範例會建立 HTML 表格，其中包含 PowerShell 別名清單和每個別名命令的數位參數。</span><span class="sxs-lookup"><span data-stu-id="16642-155">This example creates an HTML table containing a list of PowerShell aliases and the number parameters for each aliased command.</span></span> <span data-ttu-id="16642-156">**ParameterCount** 資料行的值會置中。</span><span class="sxs-lookup"><span data-stu-id="16642-156">The values of **ParameterCount** column are centered.</span></span>

### <a name="format-custom"></a><span data-ttu-id="16642-157">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="16642-157">Format-Custom</span></span>

<span data-ttu-id="16642-158">`Format-Custom` 以類似于類別定義的格式，提供物件的自訂視圖。</span><span class="sxs-lookup"><span data-stu-id="16642-158">`Format-Custom` provides a custom view of an object in a format similar to a class definition.</span></span> <span data-ttu-id="16642-159">更複雜的物件可以包含以複雜型別進行深層嵌套的成員。</span><span class="sxs-lookup"><span data-stu-id="16642-159">More complex objects can contain members that are deeply nested with complex types.</span></span> <span data-ttu-id="16642-160">的 **depth** 參數會 `Format-Custom` 為所有屬性指定擴充的深度。</span><span class="sxs-lookup"><span data-stu-id="16642-160">The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="16642-161">此索引 `depth` 鍵可讓您指定每個屬性的展開深度。</span><span class="sxs-lookup"><span data-stu-id="16642-161">The `depth` key allows you to specify the depth of expansion per property.</span></span>

<span data-ttu-id="16642-162">在此範例中， `depth` 金鑰可簡化 Cmdlet 的自訂輸出 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="16642-162">In this example, the `depth` key simplifies the custom output for the `Get-Date` cmdlet.</span></span> <span data-ttu-id="16642-163">`Get-Date` 傳回 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="16642-163">`Get-Date` returns a **DateTime** object.</span></span> <span data-ttu-id="16642-164">這個物件的 **Date** 屬性也是 **DateTime** 物件，因此物件是嵌套的。</span><span class="sxs-lookup"><span data-stu-id="16642-164">The **Date** property of this object is also a **DateTime** object, so the object is nested.</span></span>

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

### <a name="format-list"></a><span data-ttu-id="16642-165">Format-List</span><span class="sxs-lookup"><span data-stu-id="16642-165">Format-List</span></span>

<span data-ttu-id="16642-166">在此範例中，我們使用計算屬性來變更輸出的名稱和格式 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="16642-166">In this example, we use calculated properties to change the name and format of the output from `Get-ChildItem`.</span></span>

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

### <a name="format-table"></a><span data-ttu-id="16642-167">Format-Table</span><span class="sxs-lookup"><span data-stu-id="16642-167">Format-Table</span></span>

<span data-ttu-id="16642-168">在此範例中，計算屬性會加入用來依內容類型分類檔案的 **型** 別屬性。</span><span class="sxs-lookup"><span data-stu-id="16642-168">In this example, the calculated property adds a **Type** property used to classify the files by the content type.</span></span>

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

### <a name="format-wide"></a><span data-ttu-id="16642-169">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="16642-169">Format-Wide</span></span>

<span data-ttu-id="16642-170">此 `Format-Wide` Cmdlet 可讓您將集合中物件的某個屬性值顯示為多資料行清單。</span><span class="sxs-lookup"><span data-stu-id="16642-170">The `Format-Wide` cmdlet allows you to display the value of one property for objects in a collection as a multi-column list.</span></span>

<span data-ttu-id="16642-171">在此範例中，我們想要以 kb 的形式來查看檔案名和大小 (（以 kb 為單位）) 。</span><span class="sxs-lookup"><span data-stu-id="16642-171">For this example, we want to see the filename and the size (in kilobytes) as a wide listing.</span></span> <span data-ttu-id="16642-172">由於不 `Format-Wide` 會顯示多個屬性，因此我們會使用計算屬性，將兩個屬性的值結合成單一值。</span><span class="sxs-lookup"><span data-stu-id="16642-172">Since `Format-Wide` does not display more than one property, we use a calculated property to combine the value of two properties into a single value.</span></span>

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

### <a name="group-object"></a><span data-ttu-id="16642-173">Group-Object</span><span class="sxs-lookup"><span data-stu-id="16642-173">Group-Object</span></span>

<span data-ttu-id="16642-174">此 `Group-Object` Cmdlet 會根據指定屬性的值，在群組中顯示物件。</span><span class="sxs-lookup"><span data-stu-id="16642-174">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span> <span data-ttu-id="16642-175">在此範例中，計算屬性會計算每個內容類型的檔案數目。</span><span class="sxs-lookup"><span data-stu-id="16642-175">In this example, the calculated property counts the number of files of each content type.</span></span>

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

### <a name="measure-object"></a><span data-ttu-id="16642-176">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="16642-176">Measure-Object</span></span>

<span data-ttu-id="16642-177">`Measure-Object`Cmdlet 會計算物件的數值屬性。</span><span class="sxs-lookup"><span data-stu-id="16642-177">The `Measure-Object` cmdlet calculates the numeric properties of objects.</span></span> <span data-ttu-id="16642-178">在此範例中，我們會使用計算屬性來取得計數 (加) **總** 值（介於1到10之間），並可平均地除以3。</span><span class="sxs-lookup"><span data-stu-id="16642-178">In this example, we use a calculated property to get the count ( **Sum** ) of the numbers, between 1 and 10, that are evenly divisible by 3.</span></span>

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
> <span data-ttu-id="16642-179">與其他 Cmdlet 不同的 `Measure-Object` 是，不接受計算屬性的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="16642-179">Unlike the other cmdlets, `Measure-Object` does not accept a hashtable for calculated properties.</span></span> <span data-ttu-id="16642-180">您必須使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="16642-180">You must use a script block.</span></span>

### <a name="select-object"></a><span data-ttu-id="16642-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="16642-181">Select-Object</span></span>

<span data-ttu-id="16642-182">您可以使用計算屬性，將其他成員新增至使用此 Cmdlet 的輸出物件 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="16642-182">You can use calculated properties to add additional members to the objects output with the `Select-Object` cmdlet.</span></span> <span data-ttu-id="16642-183">在此範例中，我們會列出以字母開頭的 PowerShell 別名 `C` 。</span><span class="sxs-lookup"><span data-stu-id="16642-183">In this example, we are listing the PowerShell aliases that begin with the letter `C`.</span></span> <span data-ttu-id="16642-184">使用 `Select-Object` 時，我們會輸出別名、其所對應的 Cmdlet，以及針對 Cmdlet 定義的參數數目計數。</span><span class="sxs-lookup"><span data-stu-id="16642-184">Using `Select-Object`, we output the alias, the cmdlet it's mapped to, and a count for the number of parameters defined for the cmdlet.</span></span> <span data-ttu-id="16642-185">使用計算屬性，我們可以建立 **ParameterCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="16642-185">Using a calculated property, we can create the **ParameterCount** property.</span></span>

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

### <a name="sort-object"></a><span data-ttu-id="16642-186">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="16642-186">Sort-Object</span></span>

<span data-ttu-id="16642-187">您可以使用計算屬性，依每個屬性的不同順序來排序資料。</span><span class="sxs-lookup"><span data-stu-id="16642-187">Using the calculated properties, you can sort data in different orders per property.</span></span> <span data-ttu-id="16642-188">此範例會依 **日期** 以遞增順序排序 CSV 檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="16642-188">This example sorts data from a CSV file in ascending order by **Date** .</span></span> <span data-ttu-id="16642-189">但是在每個日期內，它會依 **UnitsSold** 以遞減順序排序資料列。</span><span class="sxs-lookup"><span data-stu-id="16642-189">But within each date, it sorts the rows in descending order by **UnitsSold** .</span></span>

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

## <a name="notes"></a><span data-ttu-id="16642-190">備忘稿</span><span class="sxs-lookup"><span data-stu-id="16642-190">Notes</span></span>

- <span data-ttu-id="16642-191">您可以 _直接_ 指定運算式腳本區塊做為引數，而不是將它指定為 `Expression` 雜湊表中的專案。</span><span class="sxs-lookup"><span data-stu-id="16642-191">You may specify the expression script block _directly_ , as an argument, rather than specifying it as the `Expression` entry in a hashtable.</span></span> <span data-ttu-id="16642-192">例如：</span><span class="sxs-lookup"><span data-stu-id="16642-192">For example:</span></span>

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  <span data-ttu-id="16642-193">這個範例很方便不需要 (或支援) 透過 `Name` 金鑰（例如、和）命名屬性的 Cmdlet `Sort-Object` `Group-Object` `Measure-Object` 。</span><span class="sxs-lookup"><span data-stu-id="16642-193">This example is convenient for cmdlets that do not require (or support) naming a property via the `Name` key, such as `Sort-Object`, `Group-Object`, and `Measure-Object`.</span></span>

  <span data-ttu-id="16642-194">針對支援命名屬性的 Cmdlet，腳本區塊會轉換成字串，並當做輸出中屬性的名稱使用。</span><span class="sxs-lookup"><span data-stu-id="16642-194">For cmdlets that support naming the property, the script block is converted to a string and used as the name of the property in the output.</span></span>

- <span data-ttu-id="16642-195">`Expression` 腳本區塊會在 _子_ 範圍中執行，這表示呼叫端的變數無法直接修改。</span><span class="sxs-lookup"><span data-stu-id="16642-195">`Expression` script blocks run in _child_ scopes, meaning that the caller's variables cannot be directly modified.</span></span>

- <span data-ttu-id="16642-196">管線邏輯會套用至 `Expression` 腳本區塊的輸出。</span><span class="sxs-lookup"><span data-stu-id="16642-196">Pipeline logic is applied to the output from `Expression` script blocks.</span></span> <span data-ttu-id="16642-197">這表示，輸出單一元素陣列會導致該陣列解除包裝。</span><span class="sxs-lookup"><span data-stu-id="16642-197">This means that outputting a single-element array causes that array to be unwrapped.</span></span>

- <span data-ttu-id="16642-198">在大部分的 Cmdlet 中，運算式腳本區塊內的錯誤會以安靜的形式忽略。</span><span class="sxs-lookup"><span data-stu-id="16642-198">For most cmdlets, errors inside expression script blocks are quietly ignored.</span></span>
  <span data-ttu-id="16642-199">針對 `Sort-Object` ，語句終止和腳本結束錯誤是 _輸出_ ，但不會終止語句。</span><span class="sxs-lookup"><span data-stu-id="16642-199">For `Sort-Object`, statement-terminating and script-terminating errors are _output_ but they do not terminate the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="16642-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16642-200">See Also</span></span>

[<span data-ttu-id="16642-201">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="16642-201">about_Hash_Tables</span></span>](about_hash_tables.md)

[<span data-ttu-id="16642-202">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="16642-202">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="16642-203">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="16642-203">ConvertTo-Html</span></span>](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[<span data-ttu-id="16642-204">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="16642-204">Format-Custom</span></span>](xref:Microsoft.PowerShell.Utility.Format-Custom)

[<span data-ttu-id="16642-205">Format-List</span><span class="sxs-lookup"><span data-stu-id="16642-205">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

[<span data-ttu-id="16642-206">Format-Table</span><span class="sxs-lookup"><span data-stu-id="16642-206">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="16642-207">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="16642-207">Format-Wide</span></span>](xref:Microsoft.PowerShell.Utility.Format-Wide)

[<span data-ttu-id="16642-208">Group-Object</span><span class="sxs-lookup"><span data-stu-id="16642-208">Group-Object</span></span>](xref:Microsoft.PowerShell.Utility.Group-Object)

[<span data-ttu-id="16642-209">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="16642-209">Measure-Object</span></span>](xref:Microsoft.PowerShell.Utility.Measure-Object)

[<span data-ttu-id="16642-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="16642-210">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="16642-211">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="16642-211">Sort-Object</span></span>](xref:Microsoft.PowerShell.Utility.Sort-Object)

[<span data-ttu-id="16642-212">.NET 中的格式類型</span><span class="sxs-lookup"><span data-stu-id="16642-212">Format types in .NET</span></span>](/dotnet/standard/base-types/formatting-types)
