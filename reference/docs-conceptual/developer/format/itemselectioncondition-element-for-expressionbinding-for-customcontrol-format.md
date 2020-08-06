---
title: CustomControl (格式) 的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6a5c66a63c02980b16c2d2d9dd689410c8aec51c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781183"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此控制項的條件。 可以針對控制項專案指定的選取條件數目沒有限制。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素，CustomEntries for view) format (CustomItem 專案（CustomEntry for view) format (ExpressionBinding 元素）) CustomItem 專案（ (CustomControl 的運算式系結

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
|[ItemSelectionCondition for CustomControl for View (格式的 PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定這兩者。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)

[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
