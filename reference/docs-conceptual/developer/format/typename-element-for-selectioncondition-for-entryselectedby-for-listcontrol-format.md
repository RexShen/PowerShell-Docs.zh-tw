---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)
ms.openlocfilehash: 2e8246e3ef2cba38824d8f8004acfffc3236df13
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645565"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 型別。 當這個型別存在時，就會使用清單專案。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (Format) ListEntry ListEntries for ListControl for 之 entryselectedby (format) ListEntry for ListControl for SelectionCondition 的之 entryselectedby 專案 (格式) ListControl 的 SelectionCondition 專案之 entryselectedby (格式) 

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義必須存在才能使用此清單專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[ListControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
