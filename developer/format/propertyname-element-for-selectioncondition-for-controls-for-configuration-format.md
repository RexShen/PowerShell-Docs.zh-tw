---
title: PropertyName SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064722"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和使用的項目。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 的組態 （格式） 的組態 （如 CustomEntry EntrySelectedBy 的 SelectionCondition 項目控制項的組態 （格式） EntrySelectedBy 元素的控制項的格式） CustomEntry 項目針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition 的格式） PropertyName 項目

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
|[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在，要使用的通用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定.NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或指令碼，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
