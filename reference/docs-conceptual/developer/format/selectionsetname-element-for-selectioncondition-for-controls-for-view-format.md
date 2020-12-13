---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: 檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: b23ee5310d415cf287bf99c73b1173f70ae15f4c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651636"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定一組觸發條件的 .NET 類型。 當這個集合中的任何類型存在時，就會符合條件，並使用此控制項來顯示該物件。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) 控制項控制項的控制項 (格式) CustomEntries 元素，用於控制項的視圖 (格式) 適用于 view 的控制項之 CustomEntries 的 CustomEntry 專案 (格式) 之 entryselectedby 專案 CustomEntry 的控制項視圖 (格式) SelectionCondition 專案的專案 (格式) 之 entryselectedby 專案的 SelectionSetName 專案 (格式) 的控制項

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
|[檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|定義必須存在才能使用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。 如需有關建立和參考選取集的詳細資訊，請參閱 [定義選取集](./defining-selection-sets.md)。

選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍集合](./defining-selection-sets.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
