---
title: ListEntry (格式) 的之 entryselectedby 之 SelectionCondition 的 SelectionSetName 元素Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3666888f149f176126d9a19bdbad62469ca9f064
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787473"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定觸發條件的 .NET 類型集合。 當此集合中的任何類型都存在時，就會符合條件，並使用此清單視圖的定義來顯示該物件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素（ListEntry 的 SelectionCondition (format) 之 entryselectedby 元素，ListEntry for SelectionSetName for SelectionCondition (format) 

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
|[ListEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義必須存在才能使用此清單視圖定義的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

選取條件可以指定選擇集或 .NET 類型，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

選取範圍是一組通用的 .NET 物件，可供格式設定檔案定義的任何視圖使用。 如需建立和參考選取集的詳細資訊，請參閱[定義物件集合](./defining-selection-sets.md)。

如需清單視圖之其他元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[ListEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
