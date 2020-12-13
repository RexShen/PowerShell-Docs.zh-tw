---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)
description: GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: 742d9f081a674dc3ee4c84d600933aaf57b2aa6b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655307"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) CustomEntry 專案用於 CustomControl 的 groupby (格式) CustomItem 專案適用于 CustomEntry 的 groupby (格式)  (

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
|[GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[GroupBy (格式之 ExpressionBinding 的 EnumerateCollection 元素) ](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy (格式之 ExpressionBinding 的 EnumerateCollection 元素) |選擇性項目。<br /><br /> 指定會顯示集合的元素。|
|[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[GroupBy 之 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)|定義自訂控制項視圖所顯示的資料，以及其顯示方式。|

## <a name="see-also"></a>另請參閱

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
