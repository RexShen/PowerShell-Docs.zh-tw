---
title: CustomControl for View (格式) 的 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7fdd92475ba24d27e61371d1c6b54fa1a55647c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787507"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素（CustomEntries for view) 之 entryselectedby 元素的 CustomEntry for view (格式) 

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
|[CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。 如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。

選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[CustomControl for View (格式) 的之 entryselectedby 的 SelectionCondition 元素](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍集合](./defining-selection-sets.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
