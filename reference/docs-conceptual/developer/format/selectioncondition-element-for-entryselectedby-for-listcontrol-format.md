---
title: ListControl 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: 7150b29ad84dfb587215ee3e64c356adbd5a6305
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417549"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在才能使用此清單視圖定義的條件。 可以為清單定義指定的選取條件數目沒有限制。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionCondition 元素）ListEntry 的之 entryselectedby （格式）

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
|[ListEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[ListEntry 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[ListEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[ListEntry 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此資料表專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="remarks"></a>備註

lWhen 您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單視圖](./creating-a-list-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListEntry 之之 entryselectedby 的 TypeName 元素（格式）](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
