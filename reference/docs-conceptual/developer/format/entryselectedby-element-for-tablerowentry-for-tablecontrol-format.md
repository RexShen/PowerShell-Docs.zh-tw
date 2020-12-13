---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)
description: TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645897"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)

定義 .NET 型別，這些型別會使用資料表視圖的這個定義或必須存在才能使用此定義的條件。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用此資料表視圖定義。|
|[TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定一組使用此資料表視圖定義的 .NET 類型。|
|[TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定使用此資料表視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl (格式的 TableRowEntry 元素) ](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義顯示在資料表資料列中的資料。|

## <a name="remarks"></a>備註

您必須為數據表視圖定義指定至少一個類型、選取集或選取條件。 您可以使用的子項目數目沒有最大限制。

選取條件是用來定義必須存在才能使用定義的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例 `TableRowEntry` 會顯示用來顯示 system.string [](/dotnet/api/System.Diagnostics.Process)物件屬性的專案。

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

[建立表格檢視](./creating-a-table-view.md)

[TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableControl (格式的 TableRowEntry 元素) ](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
