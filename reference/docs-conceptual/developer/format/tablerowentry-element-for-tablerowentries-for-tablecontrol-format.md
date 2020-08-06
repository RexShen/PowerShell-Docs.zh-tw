---
title: TableControl (格式) 的 TableRowEntries 的 TableRowEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 83076ae5b2c48992ce5e621c65fc9937efb68b87
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787405"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)

定義在資料表的資料列中顯示的資料。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) TableRowEntry 元素用於 TableRowEntries 的 TableControl (格式) 

## <a name="syntax"></a>語法

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `TableRowEntry` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl (格式的 TableRowEntry 的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義物件，其屬性值會顯示在資料列中。|
|[TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義要顯示其值的屬性或腳本。|
|[TableControl (格式的 TableRowEntry 的 Wrap 元素) ](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定超過欄寬度的文字會顯示在下一行。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableRowEntries 元素 (格式)](./tablerowentries-element-for-tablecontrol-format.md)|定義資料表的資料列。|

## <a name="remarks"></a>備註

`TableColumnItems`必須指定一個專案和一個 `EntrySelectedBy` 元素。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的專案 `TableRowEntry` 會定義一個資料列，以顯示 system.servicemodel 物件的兩個屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)值。

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

[TableControl (格式的 TableRowEntry 的之 entryselectedby 元素) ](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 的 TableRowEntries 元素 (格式)](./tablerowentries-element-for-tablecontrol-format.md)

[TableControl (格式的 TableRowEntry 的 Wrap 元素) ](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
