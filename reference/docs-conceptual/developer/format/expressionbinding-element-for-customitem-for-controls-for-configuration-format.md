---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
description: 設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)
ms.openlocfilehash: 1abcf2173e18d45839161b4c7e59f1ad238f81a1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655328"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) CustomControl 專案的設定 (格式) CustomItem 專案的設定 (格式) CustomEntry 專案的設定 (格式) 的控制項設定 ExpressionBinding 專案的 CustomItem 元素

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
|[設定之控制項的 ExpressionBinding 的 CustomControlName 元素 (格式)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[設定之控制項的 ExpressionBinding 的 EnumerateCollection 元素 (格式)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定控制項會顯示集合的元素。|
|[設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此通用控制項的條件。|
|[設定之控制項的 ExpressionBinding 的 PropertyName 元素 (格式)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定由通用控制項顯示其值的 .NET 屬性。|
|[設定之控制項的 ExpressionBinding 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定由通用控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于設定之控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義自訂控制項視圖所顯示的資料，以及其顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[適用于設定之控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
