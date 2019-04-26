---
title: PropertyName ItemSelectionCondition 的 GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064759"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>GroupBy 之 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用控制項。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 用於 GroupBy （格式） PropertyName 元素 ExpressionBinding 的 GroupBy （格式） ItemSelectionCondition 元素的 GroupBy （格式） ExpressionBinding 元素的 GroupBy （格式） CustomItem 元素GroupBy （格式） 的 ItemSelectionCondition

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`PropertyName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|定義要使用這個控制項必須存在的條件。|

## <a name="text-value"></a>文字值

指定.NET 屬性觸發條件的名稱。

## <a name="remarks"></a>備註

如果會使用這個項目，您無法指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)時定義的選取項目條件的項目。

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的 ItemSelectionCondition 的指令碼區塊項目](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[ItemSelectionCondition ExpressionBinding 的 GroupBy （格式） 的項目](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
