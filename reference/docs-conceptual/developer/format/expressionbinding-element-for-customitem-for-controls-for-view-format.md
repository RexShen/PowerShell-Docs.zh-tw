---
title: View (Format) 的控制項之 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6760bf17be58411948ecb3437bf18bce40073954
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773805"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 (格式) CustomEntries 專案的控制項的控制項 (的 CustomControl 元素針對 CustomControl for View (格式) 的 CustomEntries for 控制項的 CustomEntry 專案， (格式]) CustomItem 元素（針對 view (格式的控制項，CustomEntry 的 ExpressionBinding 元素）) 

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
|[檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定顯示集合的元素。|
|[View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[View (Format) 的控制項之 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[檢視之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
