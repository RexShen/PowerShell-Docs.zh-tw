---
title: WideControl 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368557"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為 `true` 時，就會符合條件，並使用寬專案定義。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 entryselectedby 元素（代表的 WideEntry （格式） SelectionCondition 元素）之 entryselectedby for WideEntry （Format） ScriptBlock 元素 for 之 entryselectedby for WideEntry 的 SelectionCondition （格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|定義必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型視圖](./creating-a-wide-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[WideEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[WideEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
