---
title: 定義用於顯示資料的條件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066323"
---
# <a name="defining-conditions-for-displaying-data"></a>定義用於顯示資料的條件

在定義檢視或控制項所顯示的資料時，您可以指定要顯示的資料必須存在的條件。 可以觸發條件，依特定屬性，或當指令碼或屬性的值評估為`true`。 當符合選取條件時，可檢視或控制項的定義。

## <a name="specifying-a-selection-condition-for-a-definition"></a>指定選取條件的定義

當建立檢視或控制項，定義`EntrySelectedBy`項目用來指定哪些物件會使用定義或何種條件必須存在，要使用的定義。 藉由指定的條件`SelectionCondition`項目。

在下列範例中，選擇條件指定的資料表檢視的定義。 在此範例中，此定義會用來評估指定的指令碼時，才`true`。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

沒有任何限制，選擇條件，您可以檢視或控制項的定義中指定的數目。 唯一的條件如下所示：

- 選取條件必須指定一個屬性名稱或條件，觸發程序的指令碼，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

## <a name="specifying-a-selection-condition-for-an-item"></a>指定選取條件的項目

您也可以指定當使用清單檢視或控制項的項目包括`ItemSelectionCondition`項目定義中的項目。 在下列範例中，選擇條件被指定之清單檢視項目。 在此範例中，項目用來評估指令碼時，才`true`。

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

您可以指定只有一個選擇條件的項目。 與條件必須指定一個屬性名稱或條件，觸發程序的指令碼，但不能同時指定。

## <a name="xml-elements"></a>XML 項目

 下列 XML 元素用來建立選取範圍的條件。

- 下列項目指定檢視定義的選取範圍的條件：

    - [TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [WideControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- 下列項目指定的選取範圍的一般條件並檢視控制定義：

    - [SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- 下列項目會指定擴充集合物件的選取範圍條件：

    - [EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 下列項目會指定選取條件來顯示資料的新群組：

    - [GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- 下列項目會指定清單檢視項目選取項目條件：

    - [ItemSelectionCondition ListControl （格式） 的 ListItem 元素](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- 下列項目會指定控制項的項目選取範圍條件：

    - [ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ItemSelectionCondition CustomControl （格式） 的 ExpressionBinding 的項目](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
