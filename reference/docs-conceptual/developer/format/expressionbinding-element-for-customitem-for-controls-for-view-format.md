---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
description: 檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: da87bb26d21dcb051871e67997cc3fba7ce73c74
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649885"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 專案的視圖控制項的控制項 (格式若為 CustomControl for View (格式) CustomEntry 元素，用於 CustomEntries 的控制項 (格式) CustomItem 專案的 CustomEntry 控制項的 ExpressionBinding， () 格式的控制項 CustomItem 的控制項 (的元素) 

## <a name="syntax"></a>語法

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ExpressionBinding` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|選擇性項目。<br /><br /> 定義這個控制項所使用的控制項。|
|[檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定要顯示集合的元素。|
|[View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition ](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項顯示的資料以及其顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[View (Format) 的控制項之 ExpressionBinding 元素 ItemSelectionCondition ](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
