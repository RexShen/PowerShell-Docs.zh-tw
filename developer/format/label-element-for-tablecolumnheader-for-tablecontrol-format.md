---
title: 供 TableColumnHeader 標籤項目，如 TableControl （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054504"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>TableControl 之 TableColumnHeader 的標籤元素 (格式)

定義顯示在資料行頂端的標籤。 定義資料表的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableHeaders 項目 TableHeaders TableControl （格式） 的標籤元素的 TableControl （格式） TableColumnHeader 項目TableControl （格式） 的 TableColumnHeader

## <a name="syntax"></a>語法

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`Label`項目。 每個資料行允許只有一個標籤。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableControl （格式） 的 TableHeaders TableColumnHeader 項目](./tablecolumnheader-element-format.md)|定義標籤、 寬度和資料行的資料表資料的對齊方式。|

## <a name="text-value"></a>文字值

指定顯示在資料表的資料行頂端的文字。 有任何限制的字元資料行標籤。

## <a name="remarks"></a>備註

如果未不指定任何標籤，會使用資料列中顯示其值之屬性的名稱。

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例示範`TableColumnHeader`其標籤是 [資料行 1] 的項目。

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
