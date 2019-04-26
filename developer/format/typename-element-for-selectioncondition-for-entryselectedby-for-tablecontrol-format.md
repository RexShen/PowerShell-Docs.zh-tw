---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition TypeName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083836"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的.NET 型別。 有這種類型時，符合條件，並用資料表資料列。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） 類型名稱元素的項目

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`TypeName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定義必須存在於要使用這個資料表資料列的條件。|

## <a name="text-value"></a>文字值

指定完整的.NET 型別名稱，例如`System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
