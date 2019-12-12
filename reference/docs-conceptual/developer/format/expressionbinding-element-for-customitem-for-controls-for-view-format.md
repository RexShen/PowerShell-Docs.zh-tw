---
title: View 之控制項的 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363777"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry 元素 for view （format） ExpressionBinding 的控制項

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
|[View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[View 之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定顯示集合的元素。|
|[View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[View 之控制項的 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[View 之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[View 之控制項的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
