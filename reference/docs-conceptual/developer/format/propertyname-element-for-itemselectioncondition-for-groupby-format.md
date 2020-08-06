---
title: GroupBy (格式的 ItemSelectionCondition 的 PropertyName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6d671035bfd2ef6323b638fdd951bb020bd6548
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780877"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時 `true` ，就會符合條件，並使用控制項。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素的視圖 (格式) CustomEntries 專案的 groupby (格式) CustomEntry 元素用於 CustomControl 若為 GroupBy (格式) 適用于 GroupBy 的 CustomEntry 的 CustomItem 專案 (格式) CustomItem 的 GroupBy (格式) ItemSelectionCondition 元素的 ExpressionBinding 元素 (格式) ExpressionBinding 的 PropertyName 專案 (格式) 

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

指定觸發條件之 .NET 屬性的名稱。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)元素。

## <a name="see-also"></a>另請參閱

[GroupBy 之 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
