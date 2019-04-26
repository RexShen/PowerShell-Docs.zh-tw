---
title: TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066153"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)

定義使用此定義的資料表檢視或條件必須存在於要使用此定義的.NET 類型。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 （格式）

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`EntrySelectedBy`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 定義要使用此表格檢視定義必須存在的條件。|
|[TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定一組使用這個資料表的檢視定義的.NET 型別。|
|[TableControl （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定使用此資料表的檢視定義的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TableRowEntry TableControl （格式） 的項目](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義會顯示在資料表資料列的資料。|

## <a name="remarks"></a>備註

您必須指定至少一個型別、 選取項目集或資料表的檢視定義的選取範圍條件。 沒有任何子項目的，您可以使用數字的最大限制。

選擇條件用來定義要使用，例如當物件具有特定屬性的定義必須存在的條件，或特定的屬性值或指令碼會評估為`true`。 如需有關選擇條件的詳細資訊，請參閱[定義條件時檢視項目或項目用](./defining-conditions-for-displaying-data.md)。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例所示`TableRowEntry`用來顯示屬性的項目[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[TableControl （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl （格式） 的 EntrySelectedBy SelectionSetName 項目](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry TableControl （格式） 的項目](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TableControl （格式） 的 EntrySelectedBy TypeName 項目](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
