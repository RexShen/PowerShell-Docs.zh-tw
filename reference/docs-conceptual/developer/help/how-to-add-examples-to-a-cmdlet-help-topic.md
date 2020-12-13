---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增範例至 Cmdlet 說明主題
description: 如何新增範例至 Cmdlet 說明主題
ms.openlocfilehash: 6b72e29c93740b7953d9b68fc8e68c02eb2f4dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654721"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>如何新增範例至 Cmdlet 說明主題

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Cmdlet 說明中的範例須知事項

- 列出命令中的所有參數名稱，即使參數名稱是選擇性的。 這可協助使用者輕鬆地解讀命令。

- 請避免使用別名和部分參數名稱，即使它們在 PowerShell 中運作也一樣。

- 在 [範例描述] 中，說明命令的有理數。 說明您為何選擇特定參數和值，以及如何使用變數。

- 如果命令使用運算式，請詳細說明它們。

- 如果命令使用物件的屬性和方法，尤其是未出現在預設顯示中的屬性，請使用此範例做為機會告知使用者物件。

## <a name="help-views-that-display-examples"></a>協助視圖顯示範例

範例只會顯示在 [Cmdlet 說明] 的詳細和完整視圖中。

## <a name="adding-an-examples-node"></a>新增範例節點

下列 XML 說明如何加入包含單一 **範例** 節點的 **範例** 節點。 針對您想要包含在主題中的每個範例，新增其他範例節點。

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>新增範例標題

下列 XML 說明如何加入範例的 **標題** 。 **標題** 可用來將範例與其他範例分開。 PowerShell 會使用包含連續範例編號的標準標頭。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>加入前面的字元

下列 XML 會示範如何新增 Windows PowerShell 提示字元，而這些字元會立即顯示在範例命令 (之前，不) 任何中間的空格。 PowerShell 會使用 Windows PowerShell 提示： `C:\PS>` 。

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

下列 XML 說明如何新增範例的實際命令。 新增命令時，請輸入完整名稱 (不要使用 Cmdlet 和參數的別名) 。 此外，請盡可能使用小寫字元。

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

下列 XML 說明如何加入範例的描述。 PowerShell `<maml:para>` 會針對描述使用一組標記，即使可以使用多個標記也是一樣 `<maml:para>` 。

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

下列 XML 說明如何新增命令的輸出。 命令結果資訊是選擇性的，但在某些情況下，示範使用特定參數的效果會很有説明。
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
