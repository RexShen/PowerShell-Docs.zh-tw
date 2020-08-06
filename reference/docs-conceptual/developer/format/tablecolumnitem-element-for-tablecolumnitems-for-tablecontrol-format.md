---
title: TableControl (格式) 的 TableColumnItems 的之 tablecolumnitem 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: beadf771f02519394d799a03db374050e3302321
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785161"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>TableControl 之 TableColumnItems 的 TableColumnItem 元素 (格式)

定義屬性或腳本，其值會顯示在資料列的資料行中。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableControl (Format) TableRowEntry 元素（TableRowEntries for TableControl 的 TableColumnItems (format) TableControlEntry 元素，TableControl for 之 tablecolumnitem (format) TableColumnItems 專案 (

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

下列各節描述元素的屬性、子專案和父項目 `TableColumnItem` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TableControl 之 TableColumnItem 的對齊元素 (格式)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 定義如何顯示資料列資料行中的資料。|
|[TableControl 之 TableColumnItem 的 FormatString 元素 (格式)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|指定格式模式，用來格式化資料列之資料行中的資料。|
|[TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定顯示其值的屬性名稱。|
|[TableControl 之 TableColumnItem 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|選擇性項目。<br /><br /> 指定其值顯示在資料列資料行中的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[TableControl (格式的 TableControlEntry 的 TableColumnItems 元素) ](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|定義其值會顯示在資料列中的屬性或腳本。|

## <a name="remarks"></a>備註

您可以在資料列的每個資料行中指定物件的屬性或腳本。 如果未指定任何子項目，則專案為預留位置，而且不會顯示任何資料。

如需有關資料表視圖之元件的詳細資訊，請參閱[建立資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

這個範例會顯示一個專案 `TableColumnItem` ，該專案會顯示 `Status` [system.webserver](/dotnet/api/System.Diagnostics.Process)物件的屬性值。

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[TableControl 之 TableColumnItem 的對齊元素 (格式)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems 元素 (格式) ](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableControl 之 TableColumnItem 的 FormatString 元素 (格式)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl 之 TableColumnItem 的 PropertyName 元素 (格式)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableControl 之 TableColumnItem 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
