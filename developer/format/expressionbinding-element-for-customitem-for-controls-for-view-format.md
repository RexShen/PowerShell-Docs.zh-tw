---
title: ExpressionBinding CustomItem 用於檢視 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065937"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素

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

下列各節說明屬性、 子項目和父項目`ExpressionBinding`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomControl Element`|選擇性的項目。<br /><br /> 定義會使用這個控制項的控制項。|
|[用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定通用控制項的檢視控制項的名稱。|
|[用於檢視 （格式） 的控制項 ExpressionBinding EnumerateCollection 項目](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定要顯示集合的項目。|
|[用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 定義要使用這個控制項必須存在的條件。|
|[PropertyName ExpressionBinding 的控制項檢視 （格式） 的項目](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定其值控制項所顯示的.NET 屬性。|
|[ExpressionBinding 的控制項檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定其值控制項所顯示的指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 ExpressionBinding CustomControlName 項目](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 ExpressionBinding EnumerateCollection 項目](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName ExpressionBinding 的控制項檢視 （格式） 的項目](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ExpressionBinding 的控制項檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
