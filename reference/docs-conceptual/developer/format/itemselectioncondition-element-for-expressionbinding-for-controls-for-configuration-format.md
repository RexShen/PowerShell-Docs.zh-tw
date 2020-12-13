---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: 設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 6bd3d386ba64b33a1744fcc9e602cf13404765a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648089"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此控制項的條件。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) CustomEntry 元素針對 configuration (格式的控制項的 CustomControl 格式) CustomItem 元素，用於 CustomEntry 的控制項，以設定 (格式的控制項之 CustomItem 的 ItemSelectionCondition 專案) ExpressionBinding 元素)  (

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ItemSelectionCondition` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[ (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
