---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
description: 設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 853130da4489e571d7f4026a8d65d029d1889f9b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665219"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並且會使用控制項。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 專案的設定 (格式) CustomEntry 專案的 CustomControl 設定 (格式) 元素，用於 CustomControl 的控制項設定 (格式) CustomItem 元素，適用于 CustomEntry 的設定 ExpressionBinding 專案設定專案 CustomItem 的設定 (格式) ItemSelectionCondition 專案設定 (格式) ScriptBlock 專案的 ExpressionBinding 控制項設定 (格式) 

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用此元素，則在定義選取條件時，不能指定 [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) 元素。

## <a name="see-also"></a>另請參閱

[設定之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
