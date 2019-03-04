---
title: TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861234"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義要用於此 [資料表] 檢視的定義必須存在的條件。 選取範圍可以針對資料表定義指定的條件數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目

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

下列各節說明屬性、 子項目和 SelectionCondition 元素的父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|
|[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定的觸發條件的.NET 型別集。|
|[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy TableRowEntry （格式） 的項目](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義.NET 型別，使用此資料表項目或要使用此項目必須存在的條件。|

## <a name="remarks"></a>備註

每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。

在您定義的選取範圍條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy 項目 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[PropertyName TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
