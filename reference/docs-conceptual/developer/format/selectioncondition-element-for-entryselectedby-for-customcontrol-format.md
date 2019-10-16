---
title: CustomControl 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368437"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>CustomControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用控制項定義。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素，用於 CustomControl for view （format）之 entryselectedby 元素 CustomEntry for CustomControl for view （format） SelectionCondition 元素之 entryselectedby for view （格式）

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionCondition` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[SelectionCondition for CustomControl for View 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[SelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 指定觸發條件的腳本。|
|[View 的自訂控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[SelectionCondition for CustomControl for View 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="remarks"></a>備註

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[SelectionCondition for CustomControl for View 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[View 的自訂控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionCondition for CustomControl for View 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for View 的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
