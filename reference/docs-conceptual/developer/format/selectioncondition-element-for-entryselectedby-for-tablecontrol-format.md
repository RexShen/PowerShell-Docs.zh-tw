---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645762"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能用於此資料表視圖的定義。 可以針對資料表定義指定的選取條件數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) TableRowEntry 專案 SelectionCondition 的之 entryselectedby (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案，以及 SelectionCondition 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[適用于 TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[適用于 TableRowEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定一組觸發條件的 .NET 類型。|
|[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 型別。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableRowEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此資料表專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="remarks"></a>備註

每個清單專案都必須定義至少一個類型名稱、選取集或選取條件。

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[適用于 TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[適用于 TableRowEntry 的之 entryselectedby (格式的 SelectionCondition SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
