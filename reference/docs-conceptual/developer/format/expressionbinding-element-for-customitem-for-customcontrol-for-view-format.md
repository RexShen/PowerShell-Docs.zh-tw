---
title: CustomControl for View (格式) 的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1885a2820c0cb250aa6fda80544f58d06136cfeb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773788"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 for view (format) CustomEntries 專案 for view (格式) CustomEntry 元素 for CustomEntries for CustomControl for view (format) CustomItem 元素，CustomEntry for CustomControl for view (格式) 

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
|[檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[檢視之 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定會顯示集合的元素。|
|[CustomControl for View (格式) 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[檢視之 CustomControl 的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[ExpressionBinding for CustomCustomControl for View (Format 的 ScriptBlock 元素) ](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義自訂控制項視圖顯示的資料，以及顯示的方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl for View (格式) 的 ExpressionBinding 的 ItemSelectionCondition 元素](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[檢視之 CustomControl 的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
