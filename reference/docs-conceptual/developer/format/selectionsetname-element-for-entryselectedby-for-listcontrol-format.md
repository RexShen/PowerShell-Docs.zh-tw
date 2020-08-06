---
title: ListControl (格式) 的之 entryselectedby 的 SelectionSetName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4315d81da4ceeb7a5b171087434ae15fb09e6592
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785263"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

為清單專案指定一組 .NET 物件。 可以為專案指定的選擇集數目沒有限制。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListEntries 專案 (格式) ListEntry 專案 (格式) 之 entryselectedby 元素用於 ListEntry (格式) SelectionSetName 元素 (

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[ListEntry (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定義使用此清單專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個清單專案都必須定義至少一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。 如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。

如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定清單視圖專案的選擇集。

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
