---
title: 如何新增 Cmdlet 說明主題的範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083462"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>如何新增範例至 Cmdlet 說明主題

- [關於指令程式說明中的範例應該知道的事項](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [顯示範例的說明檢視](#Help-Views-that-Display-Examples)

- [新增範例節點](#Adding-an-Examples-Node)

- [新增前置字元](#Adding-Preceding-Characters)

- [加入命令](#Adding-the-Command)

- [加入描述](#Adding-a-Description)

- [新增範例輸出](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>關於指令程式說明中的範例應該知道的事項

- 即使是選擇性的參數名稱，請列出的參數名稱，在命令中，所有選項。 這可協助使用者輕鬆地解譯命令。

- 避免別名和部分參數名稱，即使它們在 Windows PowerShell® 中運作。

- 在範例描述，說明 rational 建構的命令。 說明您為何要選擇特定的參數和值，以及您如何使用變數。

- 如果此命令會使用運算式，它們會詳細說明。

- 如果此命令會使用物件的屬性和方法，特別是不會出現在顯示的預設值的屬性會使用範例，因為有機會告訴使用者關於物件。

## <a name="help-views-that-display-examples"></a>顯示範例的說明檢視

範例只會出現在 cmdlet 說明的詳細資料和完整檢視。

## <a name="adding-an-examples-node"></a>新增範例節點

下列 XML 示範如何新增的範例節點包含單一的範例節點。 新增您想要包含在本主題中的每個範例的其他範例節點。

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>新增範例標題

下列 XML 示範如何加入標題的範例。 標題用來設定範例中的，除了其他範例。 Windows PowerShell® 會使用標準的標頭包含循序的範例編號。

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>新增前置字元

下列 XML 示範如何加入字元，例如 Windows PowerShell 提示字元中，顯示之前範例命令 （不含任何中間的空格）。 Windows PowerShell® 會使用 Windows PowerShell 命令提示字元：C:\PS>.

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

## <a name="adding-the-command"></a>加入命令

下列 XML 示範如何加入實際範例的命令。 當加入命令，輸入完整名稱 （請勿使用別名） 的 cmdlet 和參數。 此外，使用盡可能的小寫字元。

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

## <a name="adding-a-description"></a>加入描述

下列 XML 示範如何加入範例的描述。 Windows PowerShell® 會使用一組\<: para><maml: > 標記描述，即使多個\<: para><maml: > 可以使用標記。

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

下列 XML 示範如何新增命令的輸出。 命令結果的資訊是選擇性的但在某些情況下很有幫助示範使用特定參數的效果。 Windows PowerShell® 會使用兩組空白\<: para><maml: > 標記來分隔命令的命令輸出。

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