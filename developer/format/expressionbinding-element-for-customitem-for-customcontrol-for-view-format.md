---
title: ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065915"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） ExpressionBinding 項目，如 CustomControl 檢視 （格式） 的 CustomItem CustomControl CustomEntry CustomItem 項目

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
|[CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定通用控制項的檢視控制項的名稱。|
|[EnumerateCollection CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定集合的項目會顯示。|
|[ItemSelectionCondition CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|選擇性的項目。<br /><br /> 定義要使用這個控制項必須存在的條件。|
|[PropertyName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定其值控制項所顯示的.NET 屬性。|
|[ExpressionBinding CustomCustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定其值控制項所顯示的指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomControl 檢視 （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義自訂的控制項檢視所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomControlName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName CustomControl 檢視 （格式） 的 ExpressionBinding 的項目](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ExpressionBinding CustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControl 檢視 （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
