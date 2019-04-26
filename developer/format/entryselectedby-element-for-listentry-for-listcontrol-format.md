---
title: ListControl （格式） 的 ListEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066187"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>ListControl 之 ListEntry 的 EntrySelectedBy 元素 (格式)

定義.NET 型別，使用這個清單檢視的定義或必須存在於要使用此定義的條件。 在大部分情況下只有一個定義所需的清單檢視。 不過，您可以提供多個定義清單檢視，如果您想要使用相同的清單檢視來顯示不同的資料，針對不同物件中。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目用於 ListControl （格式） EntrySelectedBy 元素 ListEntry ListControl （格式） ListEntry 項目ListControl （格式） 的 ListEntry

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
|[ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 定義要使用此清單檢視定義必須存在的條件。|
|[ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定一組使用此清單檢視定義的.NET 型別。|
|[ListControl （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-listcontrol-format.md)|選擇性的項目。<br /><br /> 指定使用此清單的檢視定義的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ListEntry ListControl （格式） 的項目](./listentry-element-for-listcontrol-format.md)|定義清單的資料列的顯示方式。|

## <a name="remarks"></a>備註

您必須指定至少一個型別、 選取項目集或選取項目在清單檢視定義的條件。 沒有任何子項目的，您可以使用數字的最大限制。

選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼會評估為`true`。 如需有關選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何定義使用他們的.NET 型別名稱的清單檢視的物件。

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>另請參閱

[ListEntry ListControl （格式） 的項目](./listentry-element-for-listcontrol-format.md)

[ListControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[ListControl （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[建立清單檢視](./creating-a-list-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
