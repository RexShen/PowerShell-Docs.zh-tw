---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651781"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定使用此資料表視圖專案的一組 .NET 類型。 可以針對專案指定的選取範圍數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) SelectionSetName 專案之 entryselectedby 的 TableRowEntry (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。 例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。 如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。

如果您指定專案的選取範圍，就不能指定型別名稱。 如需如何指定 .NET 類型的詳細資訊，請參閱適用于 [TableRowEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[定義視圖的物件集](./defining-selection-sets.md)

[建立表格檢視](./creating-a-table-view.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
