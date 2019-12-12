---
title: ListEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368397"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此清單視圖的定義來顯示該物件。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式）之 entryselectedby 元素（代表的 ListEntry （格式） SelectionCondition 元素）之 entryselectedby for ListEntry （Format） SelectionSetName 元素，用於之 entryselectedby for ListEntry 的 SelectionCondition （格式）

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionSetName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義必須存在才能使用此清單視圖定義的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。 如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。

如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單視圖](./creating-a-list-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[ListEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
