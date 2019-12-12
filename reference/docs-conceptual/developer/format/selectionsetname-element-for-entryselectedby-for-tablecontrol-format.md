---
title: TableControl 之之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368317"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組 .NET 類型，使用此資料表視圖的專案。 可以為專案指定的選擇集數目沒有限制。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式） SelectionSetName 專案TableRowEntry 的之 entryselectedby （格式）

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[之 entryselectedby 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|定義使用此專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 例如，您可能會想要建立一組相同物件的資料表視圖和清單視圖。 如需定義選取集的詳細資訊，請參閱[定義視圖的物件集合](./defining-selection-sets.md)。

如果您指定專案的選擇集，則無法指定類型名稱。 如需如何指定 .NET 類型的詳細資訊，請參閱[之 entryselectedby For TableRowEntry 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-tablecontrol-format.md)。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[之 entryselectedby 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[定義視圖的物件集合](./defining-selection-sets.md)

[建立資料表視圖](./creating-a-table-view.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
