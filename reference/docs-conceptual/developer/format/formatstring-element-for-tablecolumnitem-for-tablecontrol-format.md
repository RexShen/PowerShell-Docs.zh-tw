---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl 之 TableColumnItem 的 FormatString 元素 (格式)
description: TableControl 之 TableColumnItem 的 FormatString 元素 (格式)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667890"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 FormatString 元素 (格式)

指定格式模式，定義資料表的屬性或腳本值的顯示方式。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式)  (格式專案) 格式 () 

## <a name="syntax"></a>語法

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `FormatString` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義其值會顯示在資料列的資料行中的屬性或腳本。|

## <a name="text-value"></a>文字值

指定用於格式化資料的模式。 例如，您可以使用此模式來格式化 [任何類型為](/dotnet/api/System.TimeSpan)system.string： {0： MMM} {0： dd} {0： HH}： {0： mm} 的屬性值。

## <a name="remarks"></a>備註

您可以在建立資料表視圖、清單視圖、寬視圖或自訂視圖時使用格式字串。 如需有關如何將顯示在視圖中的值格式化的詳細資訊，請參閱 [格式化顯示的資料](./formatting-displayed-data.md)。

如需有關資料表視圖元件的詳細資訊，請參閱 [資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[設定已顯示之資料的格式](./formatting-displayed-data.md)

[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
