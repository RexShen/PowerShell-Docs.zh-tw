---
title: TableControl （格式） 的 TableRowEntries TableRowEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58059873"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>TableControl （格式） 的 TableRowEntries TableRowEntry 項目

定義會顯示在資料表資料列的資料。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目

## <a name="syntax"></a>語法

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TableRowEntry`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|必要項目。<br /><br /> 定義其屬性值會顯示資料列中的物件。|
|[TableControl （格式） 的 TableRowEntry TableColumnItems 項目](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|必要項目。<br /><br /> 定義屬性或其值會顯示指令碼。|
|[如 TableRowEntry 包裝項目，如 TableControl （格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定超過欄寬度的文字會顯示在下一行。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableRowEntries TableControl （格式） 的項目](./tablerowentries-element-for-tablecontrol-format.md)|定義資料表的資料列。|

## <a name="remarks"></a>備註

一`TableColumnItems`項目和一個`EntrySelectedBy`必須指定項目。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例所示`TableRowEntry`項目，定義會顯示兩個屬性的值的資料列[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

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

[建立資料表檢視](./creating-a-table-view.md)

[TableControl （格式） 的 TableRowEntry EntrySelectedBy 項目](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl （格式） 的 TableRowEntry TableColumnItems 項目](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries TableControl （格式） 的項目](./tablerowentries-element-for-tablecontrol-format.md)

[如 TableRowEntry 包裝項目，如 TableControl （格式）](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
