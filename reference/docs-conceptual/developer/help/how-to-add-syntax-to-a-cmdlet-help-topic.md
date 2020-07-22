---
title: 如何新增語法至 Cmdlet 說明主題
ms.date: 09/12/2016
ms.openlocfilehash: 3457341a577b283bf3da5dc010de9bbbb36b78d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893045"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>如何新增語法至 Cmdlet 說明主題

在您開始為 Cmdlet 說明檔中的語法圖表撰寫 XML 的程式碼之前，請先閱讀本節，以清楚瞭解您需要提供的資料類型，例如參數屬性，以及該資料在語法圖表中的顯示方式。

## <a name="parameter-attributes"></a>參數屬性

- 必要
  - 如果為 true，則參數必須出現在所有使用參數集的命令中。
  - 如果為 false，則在使用參數集的所有命令中，參數是選擇性的。
- 位置
  - 如果命名為，則需要參數名稱。
  - 如果是位置，參數名稱是選擇性的。 省略時，參數值必須在命令中指定的位置。 例如，如果值是 position = "1"，則參數值必須是命令中的第一個或唯一未命名的參數值。
- 管線輸入
  - 如果為 true （ByValue），您可以透過管道傳送輸入至參數。 即使屬性名稱和物件類型不符合預期的類型，輸入也會與（「系結至」）參數相關聯。
    PowerShell 參數系結元件會嘗試將輸入轉換成正確的型別，只有在無法轉換型別時，才會使命令失效。 參數集中只有一個參數可以透過 value 來關聯。
  - 如果為 true （ByPropertyName），您可以透過管道傳送輸入至參數。 不過，只有當參數名稱符合輸入物件的屬性名稱時，輸入才會與參數相關聯。 例如，如果參數名稱為，則 `Path` 只有在物件具有名為 path 的屬性時，才會將輸送至 Cmdlet 的物件與該參數相關聯。
  - 如果為 true （ByValue，ByPropertyName），您可以透過屬性名稱或以傳值方式將輸入傳送至參數。 參數集中只有一個參數可以透過 value 來關聯。
  - 如果為 false，則表示您無法透過管道傳送輸入至此參數。
- 通配
  - 若為 true，使用者為參數值輸入的文字可以包含萬用字元。
  - 如果為 false，則使用者為參數值輸入的文字不能包含萬用字元。

### <a name="parameter-value-attributes"></a>參數值屬性

- 必要
  - 若為 true，則在命令中使用參數時，必須使用指定的值。
  - 如果為 false，則表示參數值是選擇性的。 一般來說，只有當值是參數的數個有效值之一時（例如列舉型別），才會是選擇性的。

參數值的**必要**屬性與參數的**必要**屬性不同。

參數的必要屬性會指出叫用 Cmdlet 時，是否必須包含參數（和其值）。 相較之下，只有在命令中包含參數時，才會使用參數值的必要屬性。 它會指出該特定值是否必須與參數搭配使用。

通常是預留位置的參數值，而且不需要常值的參數值，因為它們是可能與參數搭配使用的數個值之一。

### <a name="gathering-syntax-information"></a>正在搜集語法資訊

1. 從 Cmdlet 名稱開始。

   ```
   SYNTAX
       Get-Tech
   ```

1. 列出 Cmdlet 的所有參數。 輸入 `-` 每個參數名稱之前的連字號（）（ASCII 45）。
   將參數分隔成參數集（某些 Cmdlet 只能有一個參數集）。 在此範例中，取得-Tech Cmdlet 有兩個參數集。

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   使用 Cmdlet 名稱啟動每個參數集。

   請先列出預設參數集。 預設參數是由 Cmdlet 類別所指定。

   針對每個參數集，先列出其唯一的參數，除非有位置參數必須先出現。 在上述範例中，Name 和 ID 參數是這兩個參數集的唯一參數（每個參數集都必須有一個參數，而此參數集是唯一的）。 這可讓使用者更輕鬆地識別需要提供給參數集的參數。

   以命令中應該出現的順序列出參數。 如果順序不重要，請將相關的參數列出在一起，或先列出最常使用的參數。

   如果 Cmdlet 支援 ShouldProcess，請務必列出 WhatIf 和 Confirm 參數。

   請勿在您的語法圖表中列出一般參數（例如 Verbose、Debug 和 ErrorAction）。 `Get-Help`Cmdlet 會在顯示說明主題時，為您新增該資訊。

1. 新增參數值。 在 PowerShell 中，參數值會以其 .NET 類型來表示。
   不過，型別名稱可以是縮寫，例如 system.string 的 "string"。

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   縮寫類型（只要其意義很清楚），例如**system.string**的 string**和** **int** （適用于**system.object**）。

   列出列舉的所有值，例如 `-type` 上一個範例中的參數，可以設定為 [**基本**] 或 [**高級**]。

   Switch 參數（如 `-list` 前一個範例所示）沒有值。

1. 將角括弧加入為預留位置的參數值（相較于常值的參數值）。

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. 以方括弧括住選擇性參數和其 missing 值。

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. 以方括弧括住選擇性參數名稱（適用于位置參數）。 位置的參數名稱（例如下列範例中的 Name 參數）不需要包含在命令中。

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. 如果參數值可以包含多個值（例如 Name 參數中的名稱清單），請在參數值後面加上一對方括弧。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. 如果使用者可以從參數或參數值中選擇，例如類型參數，請以大括弧括住選擇，並以獨佔或符號（;) 分隔。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. 如果參數值必須使用特定格式，例如引號或括弧，請在語法中顯示格式。

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>編碼語法圖表 XML

XML 的語法節點會緊接在 [描述] 節點之後，以 `</maml:description>` 標記結尾。 如需有關收集語法圖表中所用資料的詳細資訊，請參閱[收集語法資訊](#gathering-syntax-information)。

### <a name="adding-a-syntax-node"></a>加入語法節點

Cmdlet 說明主題中顯示的語法圖表是從 XML 的語法節點中的資料產生。 語法節點會以成對的標記括住 `<command:syntax>` 。 Cmdlet 的每個參數集都包含在一對 `<command:syntaxitem>` 標記中。 您可以新增的標記數目沒有限制 `<command:syntaxitem>` 。

下列範例顯示語法節點，其中包含兩個參數集的語法專案節點。

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>將 Cmdlet 名稱新增至參數集資料

Cmdlet 的每個參數集都指定于語法專案節點中。 每個語法專案節點的開頭都是一對 `<maml:name>` 包含 Cmdlet 名稱的標記。

下列範例包含語法節點，其中包含兩個參數集的語法專案節點。

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>加入參數

加入至語法專案節點的每個參數都是在一對 `<command:parameter>` 標記內指定。 您需要 `<command:parameter>` 參數集內所包含之每個參數的一對標記，但 PowerShell 所提供的一般參數除外。

開頭標記的屬性 `<command:parameter>` 會決定參數如何出現在語法圖表中。 如需參數屬性的詳細資訊，請參閱[參數屬性](#parameter-attributes)。

> [!NOTE]
> `<command:parameter>`標記支援 `<maml:description>` 內容永遠不會顯示的子項目。 參數描述是在 XML 的參數節點中指定。 若要避免語法專案指日可待和參數節點中的資訊不一致，請省略（ `<maml:description>` 或保留空白。

下列範例包含具有兩個參數之參數集的語法專案節點。

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
