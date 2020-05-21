---
title: 如何將範例新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 82bee7b7bb0ef49203636f2a293075f3db924ce4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557085"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>如何新增範例至 Cmdlet 說明主題

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Cmdlet 說明中的範例須知事項

- 列出命令中的所有參數名稱，即使參數名稱是選擇性的。 這可協助使用者輕鬆地解讀命令。

- 請避免使用別名和部分參數名稱，即使它們在 Windows PowerShell®中工作也是一樣。

- 在範例描述中，為命令的結構說明有理數。 說明為何選擇特定的參數和值，以及如何使用變數。

- 如果命令使用運算式，請詳細說明它們。

- 如果命令使用物件的屬性和方法，特別是不會出現在預設顯示中的屬性，請使用此範例做為商機，告訴使用者該物件的相關資訊。

## <a name="help-views-that-display-examples"></a>顯示範例的說明視圖

範例只會出現在 Cmdlet 說明的詳細和完整的觀點。

## <a name="adding-an-examples-node"></a>新增範例節點

下列 XML 顯示如何新增包含單一範例節點的範例節點。 針對您想要包含在主題中的每個範例，新增其他範例節點。

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>加入範例標題

下列 XML 示範如何新增範例的標題。 標題是用來設定除了其他範例以外的範例。 Windows PowerShell®使用包含連續範例號碼的標準標頭。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>新增前面的字元

下列 XML 顯示如何新增緊接在範例命令之前顯示的字元（例如 Windows PowerShell 提示）（不含任何空格）。 Windows PowerShell®使用 Windows PowerShell 命令提示字元： C:\PS>。

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

下列 XML 顯示如何新增範例的描述。 Windows PowerShell®會使用一組 \< maml：段落> 標記來進行描述，即使 \< 可以使用多個 maml：段落> 標記。

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

下列 XML 顯示如何新增命令的輸出。 命令結果資訊是選擇性的，但在某些情況下，示範使用特定參數的效果會很有説明。 Windows PowerShell®使用兩組空白的 \< maml：段落> 標記來分隔命令輸出與命令。

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
