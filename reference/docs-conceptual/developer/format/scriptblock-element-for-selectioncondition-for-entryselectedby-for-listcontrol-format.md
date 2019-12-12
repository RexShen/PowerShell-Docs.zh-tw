---
title: ListControl 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368587"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用清單專案。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionCondition 元素）之 entryselectedby for ListEntry （Format） ScriptBlock 元素 for 之 entryselectedby for ListEntry 的 SelectionCondition （格式）

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
|[ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義必須存在才能使用此清單專案的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。 （如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)）。

如需清單視圖之其他元件的詳細資訊，請參閱[清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[ListEntry 元素（格式）](./listentry-element-for-listcontrol-format.md)

[ListEntry 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[清單檢視](./creating-a-list-view.md)

[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
