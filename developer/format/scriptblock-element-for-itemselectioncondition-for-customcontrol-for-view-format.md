---
title: ItemSelectionCondition CustomControl 檢視 （格式） 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064470"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定的指令碼，就會觸發條件。 此指令碼會評估為`true`、 符合條件，和使用控制項。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry 檢視 （格式） 的檢視 （格式） ItemSelectionCondition 的項目運算式繫結的 ItemSelectionCondition 的檢視 （格式） ScriptBlock 元素 CustomControl CustomControl CustomItem ExpressionBinding 元素CustomControl 檢視 （格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[運算式繫結檢視 （格式） CustomControl ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|定義要使用這個控制項必須存在的條件。|

## <a name="text-value"></a>文字值

指定評估指令碼。

## <a name="remarks"></a>備註

如果會使用這個項目，您無法指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)時定義的選取項目條件的項目。

## <a name="see-also"></a>另請參閱

[PropertyName ItemSelectionCondition 如 CustomControl 檢視 （格式） 的項目](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[運算式繫結檢視 （格式） CustomControl ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
