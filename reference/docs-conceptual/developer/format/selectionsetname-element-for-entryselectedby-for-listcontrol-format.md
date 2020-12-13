---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651827"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定清單專案的一組 .NET 物件。 可以針對專案指定的選取範圍數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) ListEntry 專案 SelectionSetName 的之 entryselectedby (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定義使用此清單專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

每個清單專案都必須定義至少一個類型名稱、選取集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取集。 例如，您可能會想要為相同的物件集建立資料表視圖和清單視圖。 如需定義選擇集的詳細資訊，請參閱 [定義視圖的物件集](./defining-selection-sets.md)。

如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何為清單視圖的專案指定選取集。

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
