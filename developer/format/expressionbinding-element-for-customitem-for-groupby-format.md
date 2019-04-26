---
title: ExpressionBinding CustomItem 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065898"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)

定義控制項所顯示的資料。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 的 GroupBy （格式） 的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素

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
|[CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定通用控制項的檢視控制項的名稱。|
|[EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目|選擇性的項目。<br /><br /> 指定集合的項目會顯示。|
|[ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|選擇性的項目。<br /><br /> 定義要使用這個控制項必須存在的條件。|
|[PropertyName ExpressionBinding 的 GroupBy （格式） 的項目](./propertyname-element-for-expressionbinding-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定其值控制項所顯示的.NET 屬性。|
|[ExpressionBinding 的 GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定其值控制項所顯示的指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-groupby-format.md)|定義自訂的控制項檢視所顯示的資料和顯示方式。|

## <a name="see-also"></a>另請參閱

[CustomControlName ExpressionBinding 的 GroupBy （格式） 的項目](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[EnumerateCollection ExpressionBinding 的 GroupBy （格式） 的項目](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName ExpressionBinding 的 GroupBy （格式） 的項目](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ExpressionBinding 的 GroupBy （格式） 的指令碼區塊項目](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
