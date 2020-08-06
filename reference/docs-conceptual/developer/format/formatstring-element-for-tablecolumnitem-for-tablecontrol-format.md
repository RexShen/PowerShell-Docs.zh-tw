---
title: 之 tablecolumnitem for TableControl (Format) 的格式字串元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781540"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 FormatString 元素 (格式)

指定定義如何顯示資料表之屬性或腳本值的格式模式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 專案 (格式) TableRowEntries 專案 (格式) TableRowEntry 專案 (格式) TableColumnItems 元素 (格式) 之 tablecolumnitem 元素 (格式) 之 tablecolumnitem (格式的字串格式) 

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
|[之 tablecolumnitem 元素 (格式) ](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義屬性或腳本，其值會顯示在資料列的資料行中。|

## <a name="text-value"></a>文字值

指定用來格式化資料的模式。 例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。 如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。

如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示如何為屬性的值定義格式化字串 `StartTime` 。

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
