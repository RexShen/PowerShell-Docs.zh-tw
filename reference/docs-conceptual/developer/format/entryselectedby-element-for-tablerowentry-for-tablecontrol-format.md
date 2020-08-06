---
title: TableControl (格式) 的 TableRowEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 047a10fb6b38dfa8f78a7741fd50b781d4a14b6d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787694"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 EntrySelectedBy 元素 (格式)

定義使用此資料表視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 元素 (格式) 

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
|[TableControl 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此資料表視圖定義的條件。|
|[TableControl 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定一組使用此資料表視圖定義的 .NET 類型。|
|[TableControl 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定使用此資料表視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl (格式的 TableRowEntry 元素) ](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義在資料表的資料列中顯示的資料。|

## <a name="remarks"></a>備註

您必須為數據表視圖定義指定至少一個類型、選擇集或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義要使用的定義必須存在的條件，例如，當物件具有特定屬性或特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示 `TableRowEntry` 用來顯示 system.servicemodel [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件之屬性的專案。

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
