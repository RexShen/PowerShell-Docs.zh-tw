---
title: View (Format) 之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74b3e23005f595c4c550320849cac5b196e9d479
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787660"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，會符合條件，並使用控制項。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 專案) 格式的控制項 (CustomEntry 元素的 CustomEntries 專案針對 View 的控制項 (格式) CustomItem 元素以用於 view (Format) ExpressionBinding 專案 CustomItem for view (format) ItemSelectionCondition 元素 for view (format) ScriptBlock 元素 for view (format 的控制項的 ExpressionBinding 專案) 

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
|[View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
