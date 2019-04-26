---
title: EntrySelectedBy EnumerableExpansion （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066204"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EnumerableExpansion 的 EntrySelectedBy 元素 (格式)

定義.NET 類型使用這個定義或必須存在於要使用此定義的條件。

組態項目 （格式） DefaultSettings 項目 （格式） EnumerableExpansions 項目 （格式） EnumerableExpansion 項目 （格式） EntrySelectedBy 項目 EnumerableExpansion （格式）

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
|[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性的項目。<br /><br /> 定義必須存在以展開此定義的集合物件的條件。|
|[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性的項目。<br /><br /> 指定一組.NET 型別，使用此定義的集合物件擴充的方式。|
|[EnumerableExpansion （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性的項目。<br /><br /> 指定的.NET 型別會使用這個定義的集合物件擴充的方式。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[EnumerableExpansion 項目 （格式）](./enumerableexpansion-element-format.md)|定義在檢視中顯示時，會展開物件的特定.NET 集合。|

## <a name="remarks"></a>備註

您必須指定至少一個型別、 選取項目集或選擇條件的定義項目。 沒有任何子項目的，您可以使用數字的最大限制。

選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼會評估為`true`。 如需有關選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[定義用於顯示資料的條件](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 項目 （格式）](./enumerableexpansion-element-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
