---
title: TableControl 之之 tablecolumnheader 的 Width 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367867"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的寬度元素 (格式)

定義資料行的寬度（以字元為單位）。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素（適用于之 tablecolumnheader （Format））的 TableControl （格式） TableHeaders 元素 TableControlTableControl 的之 tablecolumnheader （格式）

## <a name="syntax"></a>語法

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述在定義資料行標頭時，所使用之 @no__t 0 元素的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableHeaders 的之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)|定義資料表資料行的標籤、寬度和對齊方式。|

## <a name="text-value"></a>文字值

可能的話，請指定大於所顯示內容值長度的寬度（以字元為單位）。

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示其寬度為16個字元的 @no__t 0 元素。

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>另請參閱

[建立資料表視圖](./creating-a-table-view.md)

[TableControl 之 TableHeader 的之 tablecolumnheader 元素（格式）](./tablecolumnheader-element-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
