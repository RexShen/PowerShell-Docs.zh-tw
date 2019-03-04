---
title: ListControl （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860154"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組.NET 物件清單項目。 可供指定的項目選取項目集的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionSetName 元素ListEntry （格式） 的 EntrySelectedBy

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy ListEntry （格式） 的項目](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|定義.NET 型別，使用此清單項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

每個清單項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。

您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。 例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。 如需定義選取項目集的詳細資訊，請參閱[檢視的物件的定義設定](./defining-selection-sets.md)。

清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何指定設定項目清單檢視的選取範圍。

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

[EntrySelectedBy ListEntry （格式） 的項目](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
