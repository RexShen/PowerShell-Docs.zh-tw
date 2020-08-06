---
title: ItemSelectionCondition for CustomControl for View (Format) 的 ScriptBlock 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 31873e886af04f8eedaf859af1d6bc1d5bcfdbf7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772870"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，會符合條件，並使用控制項。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (format) CustomEntries 元素 for CustomControl for view (format) CustomEntry 元素 for CustomEntries element for CustomEntry for View (格式) CustomItem for CustomControl for View 的 ExpressionBinding 元素 (Format) ItemSelectionCondition 元素用於 CustomControl for ItemSelectionCondition for view (格式) ScriptBlock 元素， (

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
|[CustomControl for View (格式之運算式系結的 ItemSelectionCondition 元素) ](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for View (格式之運算式系結的 ItemSelectionCondition 元素) ](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
