---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 的 EntrySelectedBy 元素 (格式)
description: EnumerableExpansion 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652321"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>EnumerableExpansion 的 EntrySelectedBy 元素 (格式)

定義使用此定義的 .NET 類型或必須存在的條件，才能使用這個定義。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案的 EnumerableExpansion (格式) 

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 定義必須存在才能展開這個定義之集合物件的條件。|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 指定一組 .NET 型別，這些型別會使用此定義來擴充集合物件的方式。|
|[EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 指定 .NET 型別，此型別會使用此定義來擴充集合物件的方式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 元素 (格式)](./enumerableexpansion-element-format.md)|定義當特定 .NET 集合物件顯示在視圖中時，如何展開這些物件。|

## <a name="remarks"></a>備註

您必須為定義專案指定至少一個類型、選取集或選取條件。 您可以使用的子項目數目沒有最大限制。

選取條件是用來定義必須存在才能使用定義的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[定義用於顯示資料的條件](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 元素 (格式)](./enumerableexpansion-element-format.md)

[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
