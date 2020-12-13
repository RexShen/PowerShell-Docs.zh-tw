---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)
description: 檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 5687bb781ce2db27b875f829147ee8b436f04adc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666122"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (格式) CustomEntries 元素 (格式)  (格式) CustomEntry 元素 CustomEntry for View (Format) ExpressionBinding 元素 for CustomItem for CustomControl for View (Format) ItemSelectionCondition 元素用於 CustomControl for View 的運算式系結 (Format) ItemSelectionCondition for CustomControl for View (

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
|[適用于 CustomControl 之 ItemSelectionCondition 運算式系結的元素 (格式) ](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定觸發條件的 .NET 屬性名稱。

## <a name="remarks"></a>備註

如果使用此元素，則在定義選取條件時，不能指定 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) 元素。

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[適用于 CustomControl 之 ItemSelectionCondition 運算式系結的元素 (格式) ](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
