---
title: TableRowEntries TableControl （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055728"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>TableControl 的 TableRowEntries 元素 (格式)

定義資料表的資料列。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式）

## <a name="syntax"></a>語法

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TableRowEntries`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableRowEntries TableRowEntry 項目](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|必要項目。<br /><br /> 定義會顯示在資料表資料列的資料。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 項目 （格式）](./tablecontrol-element-format.md)|定義檢視的資料表格式。|

## <a name="remarks"></a>備註

您必須指定一或多個`TableRowEntry`資料表檢視項目。 沒有任何數目的最大限制`TableRowEntry`可以加入的項目也不是重要的順序。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例所示`TableRowEntries`項目，定義會顯示兩個屬性的值的資料列[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

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

[建立資料表檢視](./creating-a-table-view.md)

[TableControl 項目 （格式）](./tablecontrol-element-format.md)

[TableRowEntry 項目 （格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
