---
title: TableControl (格式的之 tablecolumnheader 的對齊元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1bf395b84af90d725c14b2f0ef569f72b5fcc613
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783920"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的對齊元素 (格式)

定義資料行標頭中的資料顯示方式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableHeaders 專案 (格式) 之 tablecolumnheader 專案 (格式) 之 tablecolumnheader (格式的對齊元素) 

## <a name="syntax"></a>語法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `Alignment` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 元素 (格式)](./tablecolumnheader-element-format.md)|定義資料表資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

指定下列其中一個值。 這些值不會區分大小寫。

靠左對齊資料行中顯示的資料。如果未指定此元素，則為預設值。

靠右對齊右側資料行中顯示的資料。

置中：在資料行中顯示的資料中心。

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示 `TableColumnHeader` 其資料在左側對齊的元素。

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
