---
title: ExpressionBinding 之控制項的 ItemSelectionCondition 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3bfd3efe916b4d88c024de8f959482cab515f777
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781217"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此控制項的條件。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomEntries 元素) CustomEntry 元素如需設定 (格式的控制項的 CustomControl) CustomItem 元素用於 CustomEntry 的 configuration ExpressionBinding 元素) CustomItem 的 ItemSelectionCondition 元素設定 (格式的控制項)  (

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
|[設定 (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[設定 (格式之控制項的 ItemSelectionCondition 的 PropertyName 元素) ](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[設定 (格式之控制項的 ItemSelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
