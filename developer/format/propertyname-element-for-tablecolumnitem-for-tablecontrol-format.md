---
title: TableControl （格式） 的 TableColumnItem PropertyName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064600"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)

指定其值會顯示在資料列的資料行的屬性。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） TableColumnItems 項目 （格式） TableColumnItem 項目 （格式）PropertyName TableColumnItem （格式） 的項目

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`PropertyName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義屬性或其值會顯示在資料列的資料行的指令碼。|

## <a name="text-value"></a>文字值

指定其值會顯示屬性的名稱。

## <a name="remarks"></a>備註

資料表檢視元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

此範例示範`TableColumnItem`項目，指定`Status`屬性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)物件。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
