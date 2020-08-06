---
title: CustomControl (格式) 的之 entryselectedby 的 SelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 52858dba5c7a5222b5410835f3374546ce8b88a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785348"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用控制項定義。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl for view (格式的 CustomEntries 專案) 格式 (CustomEntry 專案的 CustomEntries for CustomControl for view) format (CustomItem 元素（CustomEntry for CustomControl for view) format） (之 entryselectedby 專案（適用于 CustomEntry for CustomControl for) format (

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

下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[SelectionCondition 的 SelectionSetName 元素，用於 View (格式的自訂控制項) ](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[檢視之 CustomControl 的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="remarks"></a>備註

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionCondition 的 SelectionSetName 元素，用於 View (格式的自訂控制項) ](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
