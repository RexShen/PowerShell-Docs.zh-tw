---
title: TableControl (格式) 的之 entryselectedby 的 SelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4a829f9daef22c4b3fd6b21dfb3af2f8539bdeb3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780282"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能用於這個資料表視圖定義。 可以針對資料表定義指定的選取條件數目沒有限制。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素用於 TableRowEntry (格式) SelectionCondition 元素 (

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

下列各節說明屬性、子專案，以及 SelectionCondition 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[SelectionCondition for 之 entryselectedby for TableRowEntry (Format 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[SelectionCondition for 之 entryselectedby for TableRowEntry (Format 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableRowEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此資料表專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="remarks"></a>備註

每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[SelectionCondition for 之 entryselectedby for TableRowEntry (Format 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素) ](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[SelectionCondition for 之 entryselectedby for TableRowEntry (Format 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
