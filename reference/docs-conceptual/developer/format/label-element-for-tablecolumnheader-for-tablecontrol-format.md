---
title: TableControl 之之 tablecolumnheader 的標籤元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365167"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的標籤元素 (格式)

定義顯示在資料行頂端的標籤。 定義資料表視圖時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素（適用于之 tablecolumnheader for TableHeaders （Format） Label 元素的 TableControl （format） TableControl 元素）TableControl 的之 tablecolumnheader （格式）

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Label` 專案的父元素。 每個資料行只允許一個標籤。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableHeaders 的之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)|定義資料表資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

指定在資料表的資料行頂端顯示的文字。 資料行標籤沒有受限制的字元。

## <a name="remarks"></a>備註

如果未指定任何標籤，則會使用其值顯示在資料列中的屬性名稱。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示其標籤為 "Column 1" 的 `TableColumnHeader` 元素。

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
