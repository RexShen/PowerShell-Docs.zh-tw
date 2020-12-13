---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 6d4cc5a2d5fef0445d586e320b3729d3a7044063
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649772"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在才能使用控制項定義的條件。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomEntries 元素 for View (Format) 元素 for CustomControl for View (format) 元素 for CustomEntry for CustomEntries for view (format) CustomControl 元素 for CustomItem for CustomEntry for view (format) CustomControl 專案 for 之 entryselectedby for CustomEntry for view (格式) 

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
|[View (Format) 的自訂控制項之 SelectionCondition 的 SelectionSetName 元素 ](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定一組觸發條件的 .NET 類型。|
|[檢視之 CustomControl 的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 型別。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。|

## <a name="remarks"></a>備註

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[View (Format) 的自訂控制項之 SelectionCondition 的 SelectionSetName 元素 ](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
