---
ms.date: 09/13/2016
ms.topic: reference
title: 定義用於顯示資料的條件
description: 定義用於顯示資料的條件
ms.openlocfilehash: 9a8b7a618da8c64de978c13b527435a2d7793677
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660314"
---
# <a name="defining-conditions-for-displaying-data"></a>定義用於顯示資料的條件

定義 view 或控制項所顯示的資料時，您可以指定必須存在才能顯示資料的條件。 條件可以由特定屬性觸發，或當腳本或屬性值評估為時 `true` 。 當符合選取條件時，就會使用 view 或 control 的定義。

## <a name="specifying-a-selection-condition-for-a-definition"></a>指定定義的選取條件

當您建立 view 或 control 的定義時， `EntrySelectedBy` 會使用元素來指定哪些物件將使用定義，或必須有何種條件存在，才能使用定義。 條件是由元素所指定 `SelectionCondition` 。

在下列範例中，會針對資料表視圖的定義指定選取條件。 在此範例中，只有在指定的腳本評估為時，才會使用定義 `true` 。

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

您可以針對視圖或控制項的定義指定的選取條件數目沒有任何限制。 唯一的需求如下：

- 選取條件必須指定一個屬性名稱或腳本來觸發條件，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。

## <a name="specifying-a-selection-condition-for-an-item"></a>指定專案的選取條件

您也可以在專案定義中包含元素，以指定何時使用清單視圖或控制項的專案 `ItemSelectionCondition` 。 在下列範例中，會針對清單視圖的專案指定選取條件。 在此範例中，只有在將腳本評估為時，才會使用此專案 `true` 。

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

您只能為專案指定一個選取條件。 而且條件必須指定一個屬性名稱或腳本來觸發條件，但不能同時指定兩者。

## <a name="xml-elements"></a>XML 元素

 下列 XML 元素可用來建立選取條件。

- 下列元素會指定視圖定義的選取條件：

  - [TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- 下列元素會指定通用和 view 控制項定義的選取條件：

  - [設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- 下列元素會指定展開集合物件的選取條件：

  - [EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 下列元素會指定用於顯示新資料群組的選取條件：

  - [GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- 下列元素會指定清單視圖的專案選取條件：

  - [ListControl 之 ListItem 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- 下列元素會指定控制項的專案選取條件：

  - [設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
