---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655095"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用此清單視圖的定義。 可以針對清單定義指定的選取條件數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) ListEntry 專案 SelectionCondition 的之 entryselectedby (格式) 

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
|[ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[適用于 ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|選擇性項目。<br /><br /> 指定一組觸發條件的 .NET 類型。|
|[ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 TypeName 元素) ](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 型別。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableRowEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此資料表專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="remarks"></a>備註

lWhen 您正在定義選取條件，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md)

[適用于之 entryselectedby 的 ListEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[適用于 ListEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
