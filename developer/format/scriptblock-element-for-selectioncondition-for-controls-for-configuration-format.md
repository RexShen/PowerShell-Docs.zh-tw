---
title: ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853214"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定的指令碼，就會觸發條件。 此指令碼會評估為`true`、 符合條件，和在使用定義。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry EntrySelectedBy 控制項組態 （格式） 的組態 （格式） SelectionCondition 元素的控制項的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目

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
|[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在通用控制項定義要使用的條件。|

## <a name="text-value"></a>文字值

指定評估指令碼。

## <a name="remarks"></a>備註

選取條件必須指定至少一個指令碼或屬性名稱來評估，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
