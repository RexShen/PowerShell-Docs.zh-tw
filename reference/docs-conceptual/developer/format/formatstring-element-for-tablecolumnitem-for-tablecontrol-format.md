---
title: TableControl 之之 tablecolumnitem 的格式字串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363707"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 FormatString 元素 (格式)

指定定義如何顯示資料表之屬性或腳本值的格式模式。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式）之 tablecolumnitem 元素（格式）之 tablecolumnitem 的格式字串元素（格式）

## <a name="syntax"></a>語法

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `FormatString` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義屬性或腳本，其值會顯示在資料列的資料行中。|

## <a name="text-value"></a>文字值

指定用來格式化資料的模式。 例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。 如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。

如需有關資料表視圖之元件的詳細資訊，請參閱[資料表視圖](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>另請參閱

[建立資料表視圖](./creating-a-table-view.md)

[格式化顯示的資料](./formatting-displayed-data.md)

[之 tablecolumnitem 元素（格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
