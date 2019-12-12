---
title: GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368627"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry for groupby （format） ExpressionBinding 元素的 GroupBy （format） CustomItem 元素的 CustomControl

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
|[GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定通用控制項或 view 控制項的名稱。|
|[GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）|選擇性項目。<br /><br /> 指定會顯示集合的元素。|
|[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此控制項的條件。|
|[GroupBy 之 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的 .NET 屬性。|
|[GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項顯示其值的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)|定義自訂控制項視圖顯示的資料，以及顯示的方式。|

## <a name="see-also"></a>另請參閱

[GroupBy 之 ExpressionBinding 的 CustomControlName 元素（格式）](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 EnumerateCollection 元素（格式）](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 ExpressionBinding 的 PropertyName 元素（格式）](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 的 ExpressionBinding 的 ScriptBlock 元素（格式）](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
