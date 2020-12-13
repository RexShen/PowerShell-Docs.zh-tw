---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)
description: TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667754"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)

定義其值會顯示在資料列中的屬性或腳本。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableRowEntries 元素 for TableControl (Format) TableRowEntry TableRowEntries for TableControl for TableColumnItems (TableControlEntry for TableControl for) format (

## <a name="syntax"></a>語法

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `TableColumnItems` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義其值會顯示在資料列的資料行中的屬性或腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義顯示在資料表資料列中的資料。|

## <a name="remarks"></a>備註

資料 `TableColumnItem` 列的每個資料行都需要元素。 第一個專案會顯示在第一個資料行中，第二個數據行中的第二個專案，依此類推。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的專案 `TableColumnItems` 會定義每個 system.string 物件的[](/dotnet/api/System.Diagnostics.Process)三個屬性。

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry 元素 (格式) ](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
