---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders 元素 (格式)
description: TableHeaders 元素 (格式)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659827"
---
# <a name="tableheaders-element-format"></a>TableHeaders 元素 (格式)

定義資料表之資料行的標頭。

ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableControl (格式的 TableHeaders 元素) 

## <a name="syntax"></a>語法

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `TableHeaders` 。 要顯示之物件的每個屬性都必須要有一個子項目。 資料行標頭資訊會以指定子項目的順序顯示。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素 (格式)](./tablecolumnheader-element-format.md)|選擇性項目。<br /><br /> 定義資料表視圖之資料行的標籤、寬度和對齊方式。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl 元素 (格式)](./tablecontrol-element-format.md)|定義視圖的資料表格式。|

## <a name="remarks"></a>備註

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示 `TableHeaders` 定義兩個數據行標頭的元素。

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

[建立表格檢視](./creating-a-table-view.md)

[TableColumnHeader 元素 (格式)](./tablecolumnheader-element-format.md)

[TableControl 元素 (格式)](./tablecontrol-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
