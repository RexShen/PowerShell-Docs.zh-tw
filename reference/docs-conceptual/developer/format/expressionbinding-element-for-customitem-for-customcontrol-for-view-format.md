---
title: CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363147"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素 for CustomControl for View （Format） ExpressionBinding 元素 for CustomItem for View （格式）

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

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ExpressionBinding` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|選擇性項目。<br /><br /> 定義此控制項所使用的控制項。|
|[CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[CustomControl for View 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定會顯示集合的元素。|
|[CustomControl for View 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[ExpressionBinding for CustomControl for View 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[ExpressionBinding for CustomCustomControl for View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義自訂控制項視圖顯示的資料，以及顯示的方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomControl for View 的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl for View 的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl for View 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[ExpressionBinding for CustomControl for View 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ExpressionBinding for CustomControl for View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl for View 的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
