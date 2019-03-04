---
title: TableColumnHeader 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858594"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader 元素 (格式)

定義標籤，將資料行的寬度和資料表資料行的標籤對齊方式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 TableControl （格式） TableColumnHeader TableHeaders TableControl （格式） 的項目

## <a name="syntax"></a>語法

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TableColumnHeader`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableColumnHeader label 項目](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 定義顯示在資料行頂端的標籤。 如果未不指定任何標籤，會使用資料列中顯示其值之屬性的名稱。|
|[TableControl （格式） 的 TableColumnHeader 的 width 元素](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|必要項目。<br /><br /> 指定的資料行的寬度 （以字元為單位）。|
|[TableControl （格式） 的 TableColumbnHeader 對齊項目](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|選擇性的項目。<br /><br /> 指定資料行的標籤顯示的方式。 如果指定沒有對齊，則標籤會對齊左邊。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableHeaders 項目 （格式）](./tableheaders-element-format.md)|定義資料行的資料表檢視。|

## <a name="remarks"></a>備註

指定資料表的每個資料行的標頭。 資料行所顯示的順序在`TableColumnHeader`項目定義。

資料表必須有相同數目的`TableColumnHeader`項目與`TableRowEntry`項目。 資料行標頭會定義在資料表頂端的文字的顯示方式。 資料列項目會定義哪些資料會顯示在資料表的資料列。

資料表檢視元件的相關資訊，請參閱[資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例示範兩個`TableColumnHeader`項目。 第一個項目會定義資料行，以及其標籤是 [資料行 1]，寬度為 16 個字元，其標籤會對齊左邊。 第二個元素會定義資料行，以及其標籤是 [資料行 2]，寬度為 10 個字元，其標籤會置中的資料行中。

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>另請參閱

[TableColumnHeader TableContrl （格式） 的對齊項目](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[建立資料表檢視](./creating-a-table-view.md)

[TableControl （格式） 的 TableColumnHeader label 項目](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableHeaders TableControl （格式） 的項目](./tableheaders-element-format.md)

[寬度 TableColumnHeader TableControl 項目 （格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
