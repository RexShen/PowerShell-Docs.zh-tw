---
title: ItemSelectionCondition CustomControl （格式） 的 ExpressionBinding 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065812"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>CustomControl 之 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義要使用這個控制項必須存在的條件。 沒有任何限制，選擇條件，您可以指定的控制項項目數目。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CustomControl CustomControl 的檢視 （格式） 的運算式繫結的檢視 （格式） ItemSelectionCondition 項目的的 CustomItem 的檢視 （格式） ExpressionBinding 元素

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName ItemSelectionCondition CustomControl 檢視 （格式為的項目](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[ItemSelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)

[ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
