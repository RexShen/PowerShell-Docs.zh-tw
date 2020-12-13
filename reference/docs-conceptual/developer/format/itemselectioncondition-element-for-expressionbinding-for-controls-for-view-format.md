---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
description: 檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)
ms.openlocfilehash: adbe747bdb4f6c1d180e5b630247de0fd3d72b85
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648063"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a>檢視之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義必須存在才能使用此控制項的條件。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 () 格式控制項的控制項專案 (格式) CustomEntries 元素用於查看 CustomControl 的視圖 (針對 view (Format 的控制項格式化) CustomEntry 元素) CustomItem 專案 CustomEntry for view 的元素 (格式) ExpressionBinding 專案 CustomItem 的專案 (格式) ItemSelectionCondition 專案的 ExpressionBinding 元素 (格式) 

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
|[檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以為此條件指定一個屬性名稱或腳本，但不能同時指定兩者。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 ItemSelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
