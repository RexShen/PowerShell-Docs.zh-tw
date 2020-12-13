---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnHeader 的寬度元素 (格式)
description: TableControl 之 TableColumnHeader 的寬度元素 (格式)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658258"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的寬度元素 (格式)

定義資料行) 字元 (的寬度。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 for TableControl (Format) 之 tablecolumnheader Element TableHeaders for TableControl (format) 之 tablecolumnheader for TableControl 的 (Width 元素) 格式

## <a name="syntax"></a>語法

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述定義資料行標頭時所使用專案的屬性、子項目和父元素 `Width` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 TableHeaders 的 TableControl (格式的之 tablecolumnheader 元素) ](./tablecolumnheader-element-format.md)|定義資料表之資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

如果有可能的話，請將寬度 (指定為大於所顯示內容值長度的字元) 。

## <a name="remarks"></a>備註

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例 `TableColumnHeader` 會顯示其寬度為16個字元的元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[適用于 TableHeader 的 TableControl (格式的之 tablecolumnheader 元素) ](./tablecolumnheader-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
