---
title: 用於檢視 （格式） 的控制項 ItemSelectionCondition 的指令碼區塊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856734"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定的指令碼，就會觸發條件。 此指令碼會評估為`true`、 符合條件，和使用控制項。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） ExpressionBinding 元素的控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素ItemSelectionCondition ExpressionBinding ItemSelectionCondition 用於檢視 （格式） 的控制項的檢視 （格式） ScriptBlock 元素的控制項項目

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`ScriptBlock`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|定義要使用這個控制項必須存在的條件。|

## <a name="text-value"></a>文字值

指定評估指令碼。

## <a name="remarks"></a>備註

如果會使用這個項目，您無法指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)時定義的選取項目條件的項目。

## <a name="see-also"></a>另請參閱

[PropertyName ItemSelectionCondition 用於檢視 （格式） 的控制項的項目](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 ExpressionBinding ItemSelectionCondition 項目](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
