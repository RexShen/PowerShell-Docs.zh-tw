---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: 檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 839032048739e529057d7066fb3bc6aa2fbc5037
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651606"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定一組觸發條件的 .NET 類型。 當這個集合中的任何類型存在時，就會符合條件，並使用此控制項來顯示該物件。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案格式之 entryselectedby 元素

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
|[適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在才能使用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。 如需有關建立和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍集合](./defining-selection-sets.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
