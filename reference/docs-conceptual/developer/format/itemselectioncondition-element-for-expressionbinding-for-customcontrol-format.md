---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: 38c88ad47e57cd20902c6b8aabdb0b8e8b682ba4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648032"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此控制項的條件。 可以針對控制項專案指定的選取條件數目沒有任何限制。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 專案 (格式) CustomEntries 專案 (格式) 元素 (格式) 專案 (格式) CustomEntry 專案 for CustomEntries for view (format) CustomItem 專案 for CustomEntry for view (格式) ExpressionBinding 專案 CustomItem 的運算式系結 CustomControl 元素

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
|[View (格式之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)

[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
