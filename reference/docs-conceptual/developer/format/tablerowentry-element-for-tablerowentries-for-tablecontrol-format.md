---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)
description: TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)
ms.openlocfilehash: 60d64b7c14b40e87825ada36e19f52a66fe8b6cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659762"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)

定義顯示在資料表資料列中的資料。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableRowEntries 元素 for TableControl (Format) TableRowEntry 元素 for TableRowEntries for TableControl (格式) 

## <a name="syntax"></a>語法

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `TableRowEntry` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[適用于 TableRowEntry 的 TableControl (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義其屬性值會顯示在資料列中的物件。|
|[TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義顯示其值的屬性或腳本。|
|[適用于 TableControl (格式的 TableRowEntry Wrap 元素) ](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定在下一行顯示超過欄寬度的文字。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableRowEntries 元素 (格式)](./tablerowentries-element-for-tablecontrol-format.md)|定義資料表的資料列。|

## <a name="remarks"></a>備註

`TableColumnItems`必須指定一個元素和一個 `EntrySelectedBy` 元素。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的專案 `TableRowEntry` 會定義一個資料列，該資料列會顯示 system.string 物件之[](/dotnet/api/System.Diagnostics.Process)兩個屬性的值。

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName> Property for first column</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName> Property for second column</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[適用于 TableRowEntry 的 TableControl (格式的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 的 TableRowEntries 元素 (格式)](./tablerowentries-element-for-tablecontrol-format.md)

[適用于 TableControl (格式的 TableRowEntry Wrap 元素) ](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
