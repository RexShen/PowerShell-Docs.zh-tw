---
title: TableControl 之之 tablecolumnheader 的對齊元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364377"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的對齊元素 (格式)

定義資料行標頭中的資料顯示方式。

之 tablecolumnheader 的設定元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableHeaders 元素（格式）之 tablecolumnheader 元素（格式）對齊元素

## <a name="syntax"></a>語法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `Alignment` 專案的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|項目|說明|
|-------------|-----------------|
|[之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)|定義資料表資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

指定下列其中一個值。 這些值不會區分大小寫。

靠左對齊資料行中顯示的資料。如果未指定此元素，則為預設值。

靠右對齊右側資料行中顯示的資料。

置中：在資料行中顯示的資料中心。

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示其資料在左側對齊的 `TableColumnHeader` 元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另請參閱

[建立資料表視圖](./creating-a-table-view.md)

[之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
