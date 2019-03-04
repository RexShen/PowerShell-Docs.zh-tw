---
title: TableControl （格式） 的 TableColumnHeader 對齊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853754"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的對齊元素 (格式)

定義資料行標頭中的資料的顯示方式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 （格式） TableColumnHeader 項目 （格式） 對齊項目 TableColumnHeader （格式）

## <a name="syntax"></a>語法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Alignment`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableColumnHeader 項目 （格式）](./tablecolumnheader-element-format.md)|定義標籤、 寬度和資料行的資料表資料的對齊方式。|

## <a name="text-value"></a>文字值

指定下列值之一。 這些值不區分大小寫。

如果未指定這個項目，這是預設值靠左對齊的資料顯示在左邊的資料行。

靠右對齊顯示在右側資料行中的資料。

Center 中心資料行中顯示的資料。

## <a name="remarks"></a>備註

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例示範`TableColumnHeader`其資料靠左項目。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[TableColumnHeader 項目 （格式）](./tablecolumnheader-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
