---
title: View (Format) 的控制項之 SelectionCondition 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0feb23f860487952344680f75ee674e9e0e6dcc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787524"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此控制項來顯示該物件。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於 view 的控制項)  ( (格式) 的控制項適用于 CustomEntries 的 CustomEntry 元素，用於 view (Format) 之 entryselectedby 專案 CustomEntry for view (format) SelectionCondition 元素 for view (format) 之 entryselectedby 專案 for SelectionSetName for Controls 的控制項

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
|[檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。 如需建立和參考選取集的詳細資訊，請參閱[定義選取範圍](./defining-selection-sets.md)。

選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍集合](./defining-selection-sets.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
