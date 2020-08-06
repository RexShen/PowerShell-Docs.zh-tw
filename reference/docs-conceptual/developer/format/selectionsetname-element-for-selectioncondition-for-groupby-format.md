---
title: 適用于 SelectionCondition 之 GroupBy (格式的 SelectionSetName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6d0263aa335287f20be5b94a8eb65696d06d82a8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772615"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)

指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) GroupBy 元素以取得 (格式) CustomEntries 專案（適用于 groupby (format）) CustomEntry 元素（適用于 CustomControl 的 groupby (格式) 之 entryselectedby 元素，適用于 groupby (格式的 CustomEntry) SelectionCondition 專案 (]

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。 如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。

當指定此元素時，您無法指定[TypeName](./typename-element-for-selectioncondition-for-groupby-format.md)元素。 如需定義選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍集合](./defining-selection-sets.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
