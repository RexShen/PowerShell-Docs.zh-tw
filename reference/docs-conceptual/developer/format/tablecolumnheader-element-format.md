---
title: 之 tablecolumnheader 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361847"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader 元素 (格式)

定義標籤、資料行的寬度，以及資料表資料行的標籤對齊方式。

之 tablecolumnheader for TableHeaders 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableHeaders 元素（格式）

## <a name="syntax"></a>語法

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `TableColumnHeader` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之之 tablecolumnheader 的標籤元素（格式）](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|選擇性元素。<br /><br /> 定義顯示在資料行頂端的標籤。 如果未指定任何標籤，則會使用其值顯示在資料列中的屬性名稱。|
|[TableControl 之之 tablecolumnheader 的 Width 元素（格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|必要元素。<br /><br /> 指定資料行的寬度（以字元為單位）。|
|[TableControl 之之 tablecolumnheader 的對齊元素（格式）](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|選擇性元素。<br /><br /> 指定資料行標籤的顯示方式。 如果未指定對齊，標籤會在左邊對齊。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableHeaders 元素（格式）](./tableheaders-element-format.md)|定義資料表視圖的資料行。|

## <a name="remarks"></a>備註

為數據表的每個資料行指定標頭。 資料行會以定義 `TableColumnHeader` 元素的順序顯示。

資料表的 `TableColumnHeader` 元素數目必須與 `TableRowEntry` 個元素相同。 資料行標頭會定義如何顯示資料表頂端的文字。 資料列專案會定義要在資料表的資料列中顯示的資料。

如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示兩個 @no__t 0 個元素。 第一個元素定義的資料行的標籤為 "Column 1"，寬度為16個字元，而其標籤在左邊對齊。 第二個元素會定義其標籤為 "Column 2"、寬度為10個字元，且其標籤在資料行中央的資料行。

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

[TableControl 之之 tablecolumnheader 的對齊元素（格式）](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[建立資料表視圖](./creating-a-table-view.md)

[TableControl 之之 tablecolumnheader 的標籤元素（格式）](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl 的 TableHeaders 元素（格式）](./tableheaders-element-format.md)

[TableControl 元素的之 tablecolumnheader 寬度（格式）](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
