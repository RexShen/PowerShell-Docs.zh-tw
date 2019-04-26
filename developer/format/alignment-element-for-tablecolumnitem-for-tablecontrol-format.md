---
title: TableControl （格式） 的 TableColumnItem 對齊項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066935"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的對齊元素 (格式)

定義資料列的資料行中資料的顯示方式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） TableColumnItems 項目 （格式） TableColumnItem 項目 （格式）TableColumnItem （格式） 的對齊項目

## <a name="syntax"></a>語法

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`Alignment`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義標籤、 寬度和資料行的資料表資料的對齊方式。|

## <a name="text-value"></a>文字值

指定下列值之一。 （這些值都不區分大小寫）。

左的移位左邊資料行中顯示的資料。 （這是預設值如果不指定這個元素。）

右移位右側資料行中顯示的資料。

Center 中心資料行中顯示的資料。

## <a name="remarks"></a>備註

資料表檢視元件的相關資訊，請參閱[資料表檢視](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[資料表檢視](./creating-a-table-view.md)

[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
