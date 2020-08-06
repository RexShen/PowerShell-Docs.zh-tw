---
title: 適用于 CustomItem 之 GroupBy (格式的 ExpressionBinding 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5b0017e487aab4ffcbf901cd44aad9b275b22832
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773720"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式) CustomControl 專案 (CustomItem 元素（適用于 groupby) 格式的 CustomEntry） (ExpressionBinding 元素

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
|`CustomControl Element`|選擇性項目。<br /><br /> 定義此控制項所使用的控制項。|
|[GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[GroupBy (格式的 ExpressionBinding 的 EnumerateCollection 元素) ](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy (格式的 ExpressionBinding 的 EnumerateCollection 元素) |選擇性項目。<br /><br /> 指定會顯示集合的元素。|
|[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[GroupBy 之 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)|定義自訂控制項視圖顯示的資料，以及顯示的方式。|

## <a name="see-also"></a>另請參閱

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
