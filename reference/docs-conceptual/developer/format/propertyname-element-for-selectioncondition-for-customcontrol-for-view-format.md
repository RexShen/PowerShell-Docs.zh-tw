---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)
description: 檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 1dd325a58b29a0f13b1341559c2a7dfe251c6b36
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665850"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomEntries (format) format (format) 元素 for CustomEntry for CustomEntries for CustomControl for CustomItem for for View (format) 元素若為 CustomEntry for CustomControl for View (Format) 之 entryselectedby 元素 for CustomEntry for CustomControl for View (Format) SelectionCondition 之 entryselectedby for CustomControl for SelectionCondition for view (Format) CustomControl for for View (Format 專案) 

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在才能使用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
