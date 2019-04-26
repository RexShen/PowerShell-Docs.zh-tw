---
title: PropertyName SelectionCondition 如 CustomControl 檢視 （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064691"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的.NET 屬性。 當這個屬性是存在，或當其評估結果為`true`、 符合條件，和在使用定義。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目進行檢視 （格式） 的檢視 （如 CustomControl CustomEntries CustomEntry 元素 CustomControl 的檢視 （格式） CustomEntries 項目格式） 的檢視 （格式） 的檢視 （格式） 的檢視 （格式） m CustomControl EntrySelectedBy SelectionCondition 元素 CustomControl CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry CustomItem 項目SelectionCondition CustomControl 檢視 （格式） 的項目

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
|[CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在，要使用的控制項定義的條件。|

## <a name="text-value"></a>文字值

指定.NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或指令碼，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
