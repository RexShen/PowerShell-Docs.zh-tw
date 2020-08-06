---
title: 之 tablecolumnheader 元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6296aea5c567663b1c3c0a2cf0a57b21aa5394de
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785178"
---
# <a name="tablecolumnheader-element-format"></a>TableColumnHeader 元素 (格式)

定義標籤、資料行的寬度，以及資料表資料行的標籤對齊方式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (格式) 之 tablecolumnheader 元素用於 TableHeaders 的 TableControl (格式) 

## <a name="syntax"></a>語法

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TableColumnHeader` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl (格式之之 tablecolumnheader 的 Label 元素) ](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 定義顯示在資料行頂端的標籤。 如果未指定任何標籤，則會使用其值顯示在資料列中的屬性名稱。|
|[TableControl 之 TableColumnHeader 的寬度元素 (格式)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|必要元素。<br /><br /> 指定資料行的字元) 寬度 (。|
|[TableControl 之 TableColumnHeader 的對齊元素 (格式)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定資料行標籤的顯示方式。 如果未指定對齊，標籤會在左邊對齊。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableHeaders 元素 (格式)](./tableheaders-element-format.md)|定義資料表視圖的資料行。|

## <a name="remarks"></a>備註

為數據表的每個資料行指定標頭。 資料行會以定義元素的順序顯示 `TableColumnHeader` 。

資料表必須有相同數目的 `TableColumnHeader` 元素做為專案 `TableRowEntry` 。 資料行標頭會定義如何顯示資料表頂端的文字。 資料列專案會定義要在資料表的資料列中顯示的資料。

如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示兩個 `TableColumnHeader` 元素。 第一個元素定義的資料行的標籤為 "Column 1"，寬度為16個字元，而其標籤在左邊對齊。 第二個元素會定義其標籤為 "Column 2"、寬度為10個字元，且其標籤在資料行中央的資料行。

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

[TableControl 之 TableColumnHeader 的對齊元素 (格式)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[建立表格檢視](./creating-a-table-view.md)

[TableControl 之 TableColumnHeader 的標籤元素 (格式)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableControl (格式的 TableHeaders 元素) ](./tableheaders-element-format.md)

[TableControl 元素的之 tablecolumnheader 寬度 (格式) ](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
