---
title: ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: ec75945c5517c02fa001f0a38573c045ffcdbfd3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857484"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義要使用此清單檢視的定義必須存在的條件。 選取範圍條件可指定在清單定義的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionCondition 元素ListEntry （格式） 的 EntrySelectedBy

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
|[PropertyName ListEntry （格式） 的 EmtrySelectedBy 的 SelectionCondition 的項目](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|
|[針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|選擇性的項目。<br /><br /> 指定的觸發條件的.NET 型別集。|
|[針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy TableRowEntry （格式） 的項目](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義.NET 型別，使用此資料表項目或要使用此項目必須存在的條件。|

## <a name="remarks"></a>備註

您正在定義的選取範圍條件 lWhen，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

清單檢視的其他元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[ListEntry 項目 （格式）](./listentry-element-for-listcontrol-format.md)

[ListEntry （格式） 的 EnrtySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListEntry （格式） 的 EntrySelectedBy TypeName 項目](http://msdn.microsoft.com/en-us/fcd4daa6-f3fd-43f7-a468-03c582d34533)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
