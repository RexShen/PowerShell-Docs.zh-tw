---
title: View (Format) 的控制項之之 entryselectedby 的 SelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1c14b2638249bdbfe25f7a96e917d66ea10ed239
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787575"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用控制項定義。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 (格式) CustomControl 專案控制項的控制項 () 格式的 CustomEntries 元素 CustomControl for View (Format) CustomEntry 元素 for CustomEntries for view (Format) 之 entryselectedby 元素 for CustomEntry for view (format) SelectionCondition 元素 for view (Format) 的控制項

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
|[檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="remarks"></a>備註

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[檢視之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[檢視之控制項的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
