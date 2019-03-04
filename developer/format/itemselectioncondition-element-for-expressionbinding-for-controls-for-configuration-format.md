---
title: ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861684"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>設定之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素 (格式)

定義要使用這個控制項必須存在的條件。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry CustomItem 組態 （格式） 的控制項設定 ExpressionBinding 元素的控制項的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目ItemSelectionCondition ExpressionBinding 組態 （格式） 的控制項的項目

## <a name="syntax"></a>語法

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ItemSelectionCondition`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName ItemSelectionCondition 組態 （格式） 的控制項的項目](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[ScriptBlock ItemSelectionCondition 組態 （格式） 的控制項的項目](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|定義控制項所顯示的資料。|

## <a name="remarks"></a>備註

您可以指定一個屬性名稱或用於這種狀況的指令碼，但不能同時指定。

## <a name="see-also"></a>另請參閱

[PropertyName ItemSelectionCondition 組態 （格式） 的控制項的項目](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock ItemSelectionCondition 組態 （格式） 的控制項的項目](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding CustomItem 組態 （格式） 的控制項的項目](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
