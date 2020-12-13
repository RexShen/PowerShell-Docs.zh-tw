---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)
description: 設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 5e4368a9546307c5ff223ae42ecaa1d2872bc587
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665952"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並且會使用此專案。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomEntries 專案 CustomControl 的設定 (格式) CustomEntry 專案的適用于設定 (格式的控制項的 CustomControl 格式) 之 entryselectedby 專案 CustomEntry 的設定 (格式) 之 entryselectedby for CustomEntry for SelectionCondition 的 SelectionCondition 專案 (格式) 的之 entryselectedby for ListEntry 的 (屬性) 

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
|[設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在才能使用通用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
