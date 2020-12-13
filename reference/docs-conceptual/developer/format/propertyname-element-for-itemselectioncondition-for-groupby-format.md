---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)
description: GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 9667a389ded33d0744f0f7f8d739635a8b21d98b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666105"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用控制項。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy (格式) CustomEntries 元素適用于 CustomEntry 的 CustomControl 專案 (格式) CustomControl 元素針對 groupby (格式) CustomItem 元素，用於 CustomEntry 的 GroupBy (格式) ExpressionBinding 元素（CustomItem 的 groupby (格式）) ItemSelectionCondition 專案（ExpressionBinding 的 groupby (格式) ） (

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
|[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定觸發條件的 .NET 屬性名稱。

## <a name="remarks"></a>備註

如果使用此元素，則在定義選取條件時，不能指定 [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) 元素。

## <a name="see-also"></a>另請參閱

[GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
