---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368607"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。

EnumerableExpansion 的 SelectionCondition （Format）之 entryselectedby 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 EnumerableExpansion （格式） ScriptBlock 元素（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定義必須存在的條件，才能展開這個定義的集合物件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
