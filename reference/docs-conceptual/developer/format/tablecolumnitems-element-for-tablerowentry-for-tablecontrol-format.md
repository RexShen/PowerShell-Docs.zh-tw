---
title: TableControl (格式) 的 TableRowEntry 的 TableColumnItems 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785144"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)

定義屬性或腳本，其值會顯示在資料列中。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) TableRowEntry 元素，TableRowEntries 的 TableControl (格式) TableColumnItems 元素 (

## <a name="syntax"></a>語法

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `TableColumnItems` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義屬性或腳本，其值會顯示在資料列的資料行中。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義在資料表的資料列中顯示的資料。|

## <a name="remarks"></a>備註

資料 `TableColumnItem` 列的每個資料行都需要一個元素。 第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的 `TableColumnItems` 元素會定義一個 system.servicemodel 物件的三[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)個屬性。

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
