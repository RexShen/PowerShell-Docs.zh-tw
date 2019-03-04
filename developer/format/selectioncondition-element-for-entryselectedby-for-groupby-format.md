---
title: GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855164"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在於要使用的控制項定義的條件。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy 的 GroupBy （格式） 的 GroupBy （格式） SelectionCondition 元素的 GroupBy （格式） EntrySelectedBy 元素

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

下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName SelectionCondition 的 GroupBy （格式） 的項目](./propertyname-element-for-selectioncondition-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[GroupBy （格式） 的 SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|
|[GroupBy （格式） 的 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別集。|
|[GroupBy （格式） 的 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-groupby-format.md)|定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。|

## <a name="remarks"></a>備註

在您定義的選取範圍條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[PropertyName SelectionCondition 如 CustomControl 檢視 （格式） 的項目](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName SelectionCondition 檢視 （格式） 的自訂控制項的項目](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[GroupBy （格式） 的 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
