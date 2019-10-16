---
title: TableControl 之之 tablecolumnitem 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362247"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)

指定屬性，其值會顯示在資料列的資料行中。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式）之 tablecolumnitem 元素（格式）之 tablecolumnitem 的 PropertyName 元素（格式）

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `PropertyName` 元素的屬性、子專案和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義屬性或腳本，其值會顯示在資料列的資料行中。|

## <a name="text-value"></a>文字值

指定顯示其值的屬性名稱。

## <a name="remarks"></a>備註

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示 `TableColumnItem` 元素，這個專案會指定[system.webserver](/dotnet/api/System.Diagnostics.Process)物件的 `Status` 屬性。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另請參閱

[建立資料表視圖](./creating-a-table-view.md)

[之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
