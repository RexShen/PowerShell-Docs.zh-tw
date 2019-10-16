---
title: TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361807"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)

定義屬性或腳本，其值會顯示在資料列中。

TableRowEntry for TableRowEntries 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableRowEntries 元素（格式）TableControl 之 TableControlEntry 的 TableColumnItems 元素（格式）

## <a name="syntax"></a>語法

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明 `TableColumnItems` 元素的屬性、子專案和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableColumnItems 的之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義屬性或腳本，其值會顯示在資料列的資料行中。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableRowEntries 的 TableRowEntry 元素（格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義在資料表的資料列中顯示的資料。|

## <a name="remarks"></a>備註

資料列的每個資料行都需要 `TableColumnItem` 元素。 第一個專案會顯示在第一個資料行、第二個數據行中的第二個專案，依此類推。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的 `TableColumnItems` 元素會定義[system.servicemodel 物件的](/dotnet/api/System.Diagnostics.Process)三個屬性。

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

[建立資料表視圖](./creating-a-table-view.md)

[之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry 元素（格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
