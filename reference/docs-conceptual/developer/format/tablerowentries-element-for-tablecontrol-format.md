---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 的 TableRowEntries 元素 (格式)
description: TableControl 的 TableRowEntries 元素 (格式)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651469"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableControl 的 TableRowEntries 元素 (格式)

定義資料表的資料列。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (格式) TableControl (格式的 TableRowEntries 元素) 

## <a name="syntax"></a>語法

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `TableRowEntries` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義顯示在資料表資料列中的資料。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 元素 (格式)](./tablecontrol-element-format.md)|定義視圖的資料表格式。|

## <a name="remarks"></a>備註

您必須為數據表視圖指定一個或多個 `TableRowEntry` 元素。 可以加入的專案數目沒有最大限制，也不會影響 `TableRowEntry` 其順序。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的專案 `TableRowEntries` 會定義一個資料列，該資料列會顯示 system.string 物件之[](/dotnet/api/System.Diagnostics.Process)兩個屬性的值。

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
