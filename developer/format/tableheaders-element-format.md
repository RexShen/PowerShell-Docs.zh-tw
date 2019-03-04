---
title: TableHeaders 項目 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856874"
---
# <a name="tableheaders-element-format"></a>TableHeaders 元素 (格式)

定義資料表的資料行的標頭。

ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 元素 TableControl （格式）

## <a name="syntax"></a>語法

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`TableHeaders`項目。 必須為每個屬性之物件的顯示，則為子項目。 資料行標頭資訊會顯示子項目所指定的順序。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 項目 （格式）](./tablecolumnheader-element-format.md)|選擇性的項目。<br /><br /> 定義標籤、 寬度和資料行的資料表檢視資料的對齊方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 項目 （格式）](./tablecontrol-element-format.md)|定義檢視的資料表格式。|

## <a name="remarks"></a>備註

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例示範`TableHeaders`定義兩個資料行的標頭項目。

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

[建立資料表檢視](./creating-a-table-view.md)

[TableColumnHeader 項目 （格式）](./tablecolumnheader-element-format.md)

[TableControl 項目 （格式）](./tablecontrol-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
