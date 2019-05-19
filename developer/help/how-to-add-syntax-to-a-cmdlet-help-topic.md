---
title: 如何將 Cmdlet 說明主題中的語法 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855141"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>如何新增語法至 Cmdlet 說明主題

您開始撰寫程式碼的 XML 語法圖表中的 cmdlet 說明檔之前，請閱讀本節以取得清楚類型，您必須提供的資料，例如參數屬性和語法圖表中顯示該資料的方式了解...

### <a name="parameter-attributes"></a>參數屬性

- 必要

  - 如果為 true，參數必須出現在使用參數集的所有命令。

  - 如果為 false，參數是選擇性的所有命令的參數集。

- 位置

  - 如果名稱，參數名稱為必要。

  - 如果位置，參數名稱是選擇性的。 省略時，參數值必須在命令中指定的位置。 例如，如果值為位置 ="1"的參數值必須是第一個或唯一未命名的命令中的參數值。

- 管線輸入

  - 如果為 true (ByValue)，您可以使用管線傳送輸入至參數。 輸入是相關聯 （「 繫結至"） 與即使屬性名稱和物件型別不符合預期的類型參數。 Windows PowerShell 中？參數繫結元件，嘗試將輸入轉換成正確的型別，並讓命令失敗，無法將類型轉換時，才而不同。 參數集合中的只有一個參數可以傳值產生關聯。

  - 如果為 true (ByPropertyName)，您可以使用管線傳送輸入至參數。 不過，輸入是屬性的與參數相關聯的參數名稱相符的輸入物件名稱時，才。 比方說，如果參數名稱為`Path`，物件具有名為路徑的屬性時，才傳送至 cmdlet 的物件都是與該參數相關聯。

  - 如果您可以透過管道傳送至參數的輸入屬性名稱或值為 true （ByValue、 ByPropertyName）。 參數集合中的只有一個參數可以傳值產生關聯。

  - 如果為 false，您無法使用管線傳送輸入至這個參數。

- 萬用字元

  - 如果為 true，使用者輸入參數值的文字可以包含萬用字元。

  - 如果為 false，使用者輸入參數值的文字不能包含萬用字元。

### <a name="parameter-value-attributes"></a>參數值屬性

- 必要

  - 如果為 true，只要在命令中使用的參數必須使用指定的值。

  - 如果為 false，參數值是選擇性的。 一般而言，值是選擇性，它是其中一個的數個有效的值是參數，例如在列舉型別時，才。

必要的參數值的屬性與不同參數的必要的屬性。

參數的必要的屬性表示是否參數 （和其值） 必須包含叫用 cmdlet 時。 相較之下，已在命令中包含參數時，才可以使用的參數值的必要的屬性。 指出是否必須搭配參數使用該特定的值。

一般而言，是預留位置的參數值是必要值，並屬於常值的參數值不是必要的因為它們可能會與參數搭配使用的數個值的其中一個。

### <a name="gathering-syntax-information"></a>正在蒐集的語法資訊

1. Cmdlet 名稱的開頭。

   ```
   SYNTAX
       Get-Tech
   ```

2. 列出所有 cmdlet 的參數。 輸入以連字號 （也稱為 「 虛線 」 或 「 負號"(ASCII 45) 在每個參數名稱之前。 參數分成 （某些 cmdlet 可能會有只有一個參數設定） 的參數集。 在此範例中取得科技 cmdlet 有兩個參數集。

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   開始使用的 cmdlet 名稱設定每個參數。

   列出的預設參數集的第一次。 在 cmdlet 類別所指定的預設參數。

   每個參數集，其唯一參數先列出，除非有必須第一個出現的位置參數。 在上述範例中，名稱和識別碼的參數都是兩個參數集的唯一參數 （每個參數集必須是唯一的參數集的一個參數）。 這可讓使用者更輕鬆地識別所需的參數提供哪些參數集。

   列出的順序，它們應該會出現在命令中的參數。 如果順序並不重要，放在一起，列出相關的參數，或先列出最常使用的參數。

   請務必如果 cmdlet 支援 ShouldProcess 時，請列出 WhatIf 和 Confirm 參數。

   待辦事項清單 （例如 Verbose、 Debug 和 ErrorAction） 語法圖表中的一般參數。 `Get-Help` Cmdlet 會顯示 [說明] 主題時，將新增您該資訊。

3. 新增參數的值。 在 Windows PowerShell？，參數值都由它們的.NET 型別。 不過，在型別名稱可以縮寫，例如"string"的 System.String。

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   只要它們的意義明確，例如"string"的 System.String 和 System.Int32 的 「 int 」，將類型縮寫。

   列出所有值的列舉型別，例如在先前的範例中，可以設定為 「 基本 」 或 「 進階 」-型別參數。

   切換參數，例如-在上述範例中的清單，並沒有值。

4. 角括號加入預留位置，相較於是常值的參數值的參數值。

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. 將選擇性參數，而且其值括在方括號中。

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. 方括號括住選擇性參數名稱 （適用於位置的參數）。 要包含在命令中沒有參數的位置，例如在下列範例中，名稱參數的名稱。

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. 如果參數值可以包含多個值，例如在 Name 參數，名稱的清單加入 方括號後面的參數值的配對。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. 如果使用者可以選擇從參數或參數值，型別參數，例如將選擇括在大括號，並使用 exclusive OR symbol(;) 隔開。

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. 如果參數值必須使用特定的格式，例如引號或大括號，請在語法中顯示的格式。

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>撰寫程式碼的語法圖 XML

XML 的語法節點開始，[描述] 節點，以結束後立即\</maml:description > 標記。 如需收集的語法圖表中使用的資料，請參閱[蒐集的語法資訊](#gathering-syntax-information)。

### <a name="adding-a-syntax-node"></a>新增的語法節點

顯示 cmdlet 說明主題中的語法圖表就會產生從 XML 的語法節點中的資料。 語法節點住一組，如果\<命令語法： > 標記。 使用一組括住此指令程式的每個參數集\<命令： syntaxitem > 標記。 數目沒有限制\<命令： syntaxitem > 您可以新增的標記。

下列範例示範具有兩個參數集的語法項目節點的語法節點。

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>將資料加入至參數的 Cmdlet 名稱設定

此 cmdlet 的每個參數集的語法項目節點中指定。 每個語法項目節點開始的一組\<maml:name > 包含的 cmdlet 名稱的標籤。

下列範例包含具有兩個參數集的語法項目節點的語法節點。

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

加入的語法項目節點的每個參數指定一組\<命令： 參數 > 標記。 您需要一對\<命令： 參數 > 針對每個集合中包含參數，除了一般參數所提供的 Windows PowerShell 的參數標記？。

屬性的開頭\<命令： 參數 > 標記可讓您決定參數語法圖表中顯示的方式。 在 參數屬性的資訊，請參閱[參數屬性](#parameter-attributes)。

> [!NOTE]
> \<命令： 參數 > 標記支援子項目\<maml:description > 永遠不會顯示其內容。 參數描述指定之 xml 的 [參數] 節點中。 若要避免不一致的語法項目中的資訊 bodes 和 [參數] 節點中，省略 (\<maml:description >，或保持空白。

下列範例包含具有兩個參數設定為參數的語法項目節點。

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
