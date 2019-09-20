---
title: TableControl 之 TableColumnItems 的之 tablecolumnitem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143572"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)

定義屬性或腳本，其值會顯示在資料列的資料行中。

TableRowEntry for TableRowEntries 之 TableControl （Format） TableControl 元素的 Configuration 元素（格式） ViewDefinitions 元素（格式） TableRowEntries 元素（格式）TableColumnItems for TableControl 之 TableControl （Format）之 tablecolumnitem 元素的 TableControlEntry 的 TableColumnItems 元素（格式）

## <a name="syntax"></a>語法

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述`TableColumnItem`元素的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之之 tablecolumnitem 的對齊元素（格式）](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 定義如何顯示資料列資料行中的資料。|
|[TableControl 之之 tablecolumnitem 的格式字串元素（格式）](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|指定格式模式，用來格式化資料列之資料行中的資料。|
|[TableControl 之之 tablecolumnitem 的 PropertyName 元素（格式）](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定顯示其值的屬性名稱。|
|[TableControl 之之 tablecolumnitem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定其值顯示在資料列資料行中的腳本。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TableControl 之 TableControlEntry 的 TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|定義其值會顯示在資料列中的屬性或腳本。|

## <a name="remarks"></a>備註

您可以在資料列的每個資料行中指定物件的屬性或腳本。 如果未指定任何子項目，則專案為預留位置，而且不會顯示任何資料。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示`TableColumnItem`一個專案，該專案會顯示`Status` [system.webserver](/dotnet/api/System.Diagnostics.Process)物件的屬性值。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另請參閱

[建立資料表視圖](./creating-a-table-view.md)

[TableControl 之之 tablecolumnitem 的對齊元素（格式）](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 元素（格式）](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 之之 tablecolumnitem 的格式字串元素（格式）](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl 之之 tablecolumnitem 的 PropertyName 元素（格式）](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl 之之 tablecolumnitem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
