---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnHeader 的對齊元素 (格式)
description: TableControl 之 TableColumnHeader 的對齊元素 (格式)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666819"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的對齊元素 (格式)

定義如何顯示資料行標題中的資料。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 (format) 之 tablecolumnheader 專案 (格式)  (的對齊元素) 格式

## <a name="syntax"></a>語法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `Alignment` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素 (格式)](./tablecolumnheader-element-format.md)|定義資料表之資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

指定下列其中一個值。 這些值不會區分大小寫。

如果未指定這個元素，則靠左對齊資料行中顯示的資料，這是預設值。

靠右對齊資料行中顯示的資料。

置中：將資料行中顯示的資料置中。

## <a name="remarks"></a>備註

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示 `TableColumnHeader` 其資料在左邊對齊的元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[TableColumnHeader 元素 (格式)](./tablecolumnheader-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
