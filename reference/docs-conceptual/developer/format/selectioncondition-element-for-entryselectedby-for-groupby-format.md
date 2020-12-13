---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 14c293b6bc6d6accc201de35be9219349079801d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664753"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在才能使用控制項定義的條件。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) CustomEntry 專案用於 CustomControl 的 groupby (格式) 之 entryselectedby 專案適用于 CustomEntry 的 groupby (格式)  (

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
|[GroupBy 之 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[GroupBy (格式的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|選擇性項目。<br /><br /> 指定一組觸發條件的 .NET 類型。|
|[GroupBy (格式的 SelectionCondition TypeName 元素) ](./typename-element-for-selectioncondition-for-groupby-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 型別。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)|定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。|

## <a name="remarks"></a>備註

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[View (Format) 的自訂控制項之 SelectionCondition 的 SelectionSetName 元素 ](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[GroupBy (格式的 SelectionCondition TypeName 元素) ](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
