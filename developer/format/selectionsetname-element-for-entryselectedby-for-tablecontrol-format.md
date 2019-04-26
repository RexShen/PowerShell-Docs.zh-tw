---
title: TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063916"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組.NET 型別使用 [資料表] 檢視的此項目。 可供指定的項目選取項目集的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 （格式） SelectionSetName 項目TableRowEntry （格式） 的 EntrySelectedBy

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[EntrySelectedBy 項目 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義.NET 型別，使用此項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。 例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。 如需定義選取項目集的詳細資訊，請參閱[檢視的物件的定義設定](./defining-selection-sets.md)。

如果您指定的選取範圍的項目集，您無法指定型別名稱。 如需如何指定.NET 類型的詳細資訊，請參閱[TableRowEntry （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[EntrySelectedBy 項目 （格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[如需檢視定義物件的集合](./defining-selection-sets.md)

[建立資料表檢視](./creating-a-table-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
