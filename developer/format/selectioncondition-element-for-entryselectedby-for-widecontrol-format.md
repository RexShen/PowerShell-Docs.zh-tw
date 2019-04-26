---
title: WideControl （格式） 的 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063973"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義要使用此定義必須存在的條件。 選取範圍條件可指定寬的項目定義的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry 項目 （格式） EntrySelectedBy 項目用於 WideEntry （格式） SelectionCondition 元素WideEntry （格式） 的 EntrySelectedBy

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

下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。 您必須指定單一`PropertyName`或`ScriptBlock`項目。 `SelectionSetName`和`TypeName`元素是選擇性的。 您可以指定其中一個可能是項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的指令碼區塊。|
|[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別集。|
|[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)|定義.NET 型別，使用此寬的項目或要使用此項目必須存在的條件。|

## <a name="remarks"></a>備註

每個寬的項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。

在您定義的選取範圍條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。

寬型檢視的其他元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy WideEntry （格式） 的項目](./entryselectedby-element-for-wideentry-format.md)

[PropertyName WideEntry （格式） 的 EntrySelectedBy 的 SelectionCondition 的項目](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[針對 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
