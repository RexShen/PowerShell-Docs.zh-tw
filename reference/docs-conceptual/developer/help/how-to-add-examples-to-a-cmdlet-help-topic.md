---
title: 如何新增範例至 Cmdlet 說明主題
ms.date: 09/12/2016
ms.openlocfilehash: 33a1726f9d52b5a368d5df7962cc17ba9c45246a
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893436"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>如何新增範例至 Cmdlet 說明主題

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Cmdlet 說明中的範例須知事項

- 列出命令中的所有參數名稱，即使參數名稱是選擇性的。 這可協助使用者輕鬆地解讀命令。

- 請避免別名和部分參數名稱，即使它們在 PowerShell 中工作也是一樣。

- 在範例描述中，為命令的結構說明有理數。 說明為何選擇特定的參數和值，以及如何使用變數。

- 如果命令使用運算式，請詳細說明它們。

- 如果命令使用物件的屬性和方法，特別是不會出現在預設顯示中的屬性，請使用此範例做為商機，告訴使用者該物件的相關資訊。

## <a name="help-views-that-display-examples"></a>顯示範例的說明視圖

範例只會出現在 Cmdlet 說明的詳細和完整的觀點。

## <a name="adding-an-examples-node"></a>新增範例節點

下列 XML 顯示如何新增包含單一**範例**節點的**範例**節點。 針對您想要包含在主題中的每個範例，新增其他範例節點。

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>加入範例標題

下列 XML 示範如何新增範例的**標題**。 **標題**是用來設定除了其他範例以外的範例。 PowerShell 會使用包含連續範例號碼的標準標頭。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>新增前面的字元

下列 XML 顯示如何新增緊接在範例命令之前顯示的字元（例如 Windows PowerShell 提示）（不含任何空格）。 PowerShell 會使用 Windows PowerShell 命令提示字元： `C:\PS>` 。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>新增命令

下列 XML 顯示如何新增範例的實際命令。 新增命令時，請輸入 Cmdlet 和參數的完整名稱（請勿使用 alias）。 此外，盡可能使用小寫字元。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>新增描述

下列 XML 顯示如何新增範例的描述。 PowerShell `<maml:para>` 會針對描述使用一組標記，即使可以使用多個 `<maml:para>` 標記也一樣。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>新增範例輸出

下列 XML 顯示如何新增命令的輸出。 命令結果資訊是選擇性的，但在某些情況下，示範使用特定參數的效果會很有説明。
PowerShell 會使用兩組空白 `<maml:para>` 標記來分隔命令輸出與命令。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
