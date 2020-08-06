---
title: EnumerableExpansion (格式) 的之 entryselectedby 之 SelectionCondition 的 SelectionSetName 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e18c74bb95c658f2c3e7b7454628f78d523f7609
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787490"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件。

Configuration 元素 DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion (格式) SelectionCondition 元素，之 entryselectedby 的 EnumerableExpansion (格式) SelectionSetName 元素 (

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定義必須存在的條件，才能展開這個定義的集合物件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。 如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[定義選取範圍集合](./defining-selection-sets.md)

[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
