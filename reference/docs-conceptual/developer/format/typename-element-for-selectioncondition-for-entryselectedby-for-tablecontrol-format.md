---
title: TableControl 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361467"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 類型。 當此型別存在時，就會符合條件，並使用資料表資料列。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式）之 entryselectedby 元素（格式）SelectionCondition for 之 entryselectedby for TableRowEntry 的 TableRowEntry （Format） TypeName 元素之 entryselectedby 的 SelectionCondition 元素（格式）

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定義必須存在才能使用此資料表資料列的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立資料表視圖](./creating-a-table-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
