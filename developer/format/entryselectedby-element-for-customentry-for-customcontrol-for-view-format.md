---
title: CustomControl 檢視 （格式） 的 CustomEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066272"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義.NET 型別，使用此自訂的項目或要使用此項目必須存在的條件。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式） 的檢視 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 檢視 （格式） 的項目

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|選擇性的項目。<br /><br /> 定義要使用此定義必須存在的條件。|
|[CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定一組使用的控制項檢視此定義的.NET 型別。|
|[CustomEntry （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定使用的控制項檢視此定義的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomEntry CustomEntries 檢視 （格式） 的項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|定義特定的.NET 物件所使用的控制項。|

## <a name="remarks"></a>備註

您必須指定至少一個型別、 選取項目集或選擇條件的項目。 沒有任何子項目的，您可以使用數字的最大限制。

選擇條件用來定義的條件必須存在於要使用的項目，例如當物件只有特定的屬性時，或特定的屬性值，或指令碼會評估`true`。 如需有關選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。

如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[自訂的控制項檢視](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[CustomEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[CustomEntry （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry CustomEntries 檢視 （格式） 的項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[自訂的控制項檢視](./creating-custom-controls.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
