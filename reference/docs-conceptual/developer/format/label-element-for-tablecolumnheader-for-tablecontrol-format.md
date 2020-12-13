---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnHeader 的標籤元素 (格式)
description: TableControl 之 TableColumnHeader 的標籤元素 (格式)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667788"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的標籤元素 (格式)

定義顯示在資料行頂端的標籤。 定義資料表視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) TableControl 元素 (format) TableHeaders 元素 for TableControl (Format) 之 tablecolumnheader TableHeaders for TableControl for 之 tablecolumnheader (format) TableControl for (格式) 

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `Label` 。 每個資料行只允許一個標籤。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 TableHeaders 的 TableControl (格式的之 tablecolumnheader 元素) ](./tablecolumnheader-element-format.md)|定義資料表之資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

指定在資料表資料行頂端顯示的文字。 資料行標籤沒有受限的字元。

## <a name="remarks"></a>備註

如果未指定標籤，則會使用其值顯示在資料列中的屬性名稱。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例顯示 `TableColumnHeader` 其標籤為 "Column 1" 的元素。

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
