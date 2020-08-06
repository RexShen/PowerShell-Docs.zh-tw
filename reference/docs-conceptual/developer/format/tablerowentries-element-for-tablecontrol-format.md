---
title: TableControl (格式的 TableRowEntries 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4cc5d354df3e552e181a95148caa020f0041db92
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785110"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableControl 的 TableRowEntries 元素 (格式)

定義資料表的資料列。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableControl (格式的 TableRowEntries 元素) 

## <a name="syntax"></a>語法

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `TableRowEntries` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義在資料表的資料列中顯示的資料。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 元素 (格式)](./tablecontrol-element-format.md)|定義視圖的資料表格式。|

## <a name="remarks"></a>備註

您必須為數據表視圖指定一個或多個 `TableRowEntry` 元素。 可以新增的專案數沒有最大限制， `TableRowEntry` 也沒有順序重要性。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的專案 `TableRowEntries` 會定義一個資料列，以顯示 system.servicemodel 物件的兩個屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)值。

```xml
<TableRowEntries>
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
</TableRowEntries>

```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[TableControl 元素 (格式)](./tablecontrol-element-format.md)

[TableRowEntry 元素 (格式) ](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
