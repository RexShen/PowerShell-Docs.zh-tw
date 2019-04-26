---
title: TableControl （格式） 的 TableRowEntry TableColumnItems 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075387"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>TableControl 之 TableRowEntry 的 TableColumnItems 元素 (格式)

定義屬性或其值會顯示資料列中的指令碼。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 TableControl （格式） TableRowEntry TableRowEntries TableControl （格式） 的項目TableControl （格式） 的 TableControlEntry TableColumnItems 項目

## <a name="syntax"></a>語法

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`TableColumnItems`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableColumnItems TableColumnItem 項目](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|必要項目。<br /><br /> 定義屬性或其值會顯示資料列的資料行中的指令碼。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableRowEntries TableRowEntry 項目](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|定義會顯示在資料表資料列的資料。|

## <a name="remarks"></a>備註

A `TableColumnItem` ，則需要每個資料行的資料列元素。 第一個項目會顯示在第一個資料行，第二個項目，在第二個資料行，依此類推。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例所示`TableColumnItems`定義的三個屬性的項目[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

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

[建立資料表檢視](./creating-a-table-view.md)

[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry 項目 （格式）](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
