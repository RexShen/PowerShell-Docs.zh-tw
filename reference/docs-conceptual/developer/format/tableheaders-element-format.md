---
title: TableHeaders 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361817"
---
# <a name="tableheaders-element-format"></a>TableHeaders 元素 (格式)

定義資料表之資料行的標頭。

TableControl 的 ViewDefinitions 元素（格式） View 元素（Format） TableControl 元素（格式） TableHeaders 元素（格式）

## <a name="syntax"></a>語法

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `TableHeaders` 專案的屬性、子專案和父項目。 要顯示之物件的每個屬性都必須要有一個子項目。 資料行標頭資訊會以指定子項目的順序顯示。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)|選擇性項目。<br /><br /> 定義資料表視圖之資料行的標籤、寬度和對齊方式。|

### <a name="parent-elements"></a>父元素

|項目|說明|
|-------------|-----------------|
|[TableControl 元素（格式）](./tablecontrol-element-format.md)|定義視圖的資料表格式。|

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示定義兩個數據行標頭的 `TableHeaders` 元素。

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

[建立資料表視圖](./creating-a-table-view.md)

[之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)

[TableControl 元素（格式）](./tablecontrol-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
