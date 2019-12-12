---
title: View 之控制項的之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362047"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用控制項定義。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionCondition 元素 for controls 的控制項（格式）編排

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

下列各節說明屬性、子專案，以及 `SelectionCondition` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[View 之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[View 之控制項的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="remarks"></a>備註

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[View 之控制項的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[View 之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[View 之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[View 之控制項的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
