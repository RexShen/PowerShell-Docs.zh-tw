---
title: TableControl 之 TableRowEntries 的 TableRowEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361797"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableControl 之 TableRowEntries 的 TableRowEntry 元素 (格式)

定義在資料表的資料列中顯示的資料。

TableRowEntry for TableRowEntries 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableRowEntries 元素（格式）

## <a name="syntax"></a>語法

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `TableRowEntry` 元素的屬性、子專案和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義物件，其屬性值會顯示在資料列中。|
|[TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|必要元素。<br /><br /> 定義要顯示其值的屬性或腳本。|
|[TableControl 的 TableRowEntry 的 Wrap 元素（格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|選擇性元素。<br /><br /> 指定超過欄寬度的文字會顯示在下一行。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 的 TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)|定義資料表的資料列。|

## <a name="remarks"></a>備註

必須指定一個 `TableColumnItems` 元素和一個 @no__t 1 元素。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示的 `TableRowEntry` 元素會定義一個資料列，其中會顯示[system.web](/dotnet/api/System.Diagnostics.Process)物件的兩個屬性值。

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

[建立資料表視圖](./creating-a-table-view.md)

[TableControl 之 TableRowEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 之 TableRowEntry 的 TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 的 TableRowEntries 元素（格式）](./tablerowentries-element-for-tablecontrol-format.md)

[TableControl 的 TableRowEntry 的 Wrap 元素（格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
