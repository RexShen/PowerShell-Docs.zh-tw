---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
description: ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651540"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定一組觸發條件的 .NET 類型。 當這個集合中的任何類型存在時，就會符合條件，並且使用清單視圖的這項定義來顯示該物件。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) ListEntry 專案的 SelectionCondition (格式) 之 entryselectedby 專案 ListEntry SelectionSetName 的 SelectionCondition 格式

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義必須存在的條件，才能使用此清單視圖的定義。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

選取條件可以指定選擇集或 .NET 類型，但無法同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。 如需有關建立和參考選取集的詳細資訊，請參閱 [定義物件集](./defining-selection-sets.md)。

如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
