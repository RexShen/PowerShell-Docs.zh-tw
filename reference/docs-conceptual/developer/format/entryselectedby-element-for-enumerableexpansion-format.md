---
title: EnumerableExpansion 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368797"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EnumerableExpansion 的 EntrySelectedBy 元素 (格式)

定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。

EnumerableExpansion 的設定元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `EntrySelectedBy` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 定義必須存在的條件，才能展開這個定義的集合物件。|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 指定一組 .NET 類型，使用此定義來擴充集合物件的方式。|
|[EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 指定 .NET 類型，其使用此定義來擴充集合物件的方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素（格式）](./enumerableexpansion-element-format.md)|定義特定 .NET 集合物件在視圖中顯示時的擴充方式。|

## <a name="remarks"></a>備註

您必須為定義專案指定至少一個類型、選擇集或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性，或特定屬性值或腳本評估為 `true` 時。 如需選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 元素（格式）](./enumerableexpansion-element-format.md)

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
