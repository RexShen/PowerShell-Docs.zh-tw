---
title: TableControl （格式） 的 TableColumnItem 的 FormatString 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854324"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a>TableControl 之 TableColumnItem 的 FormatString 元素 (格式)

指定之格式模式所定義的屬性或指令碼的值之資料表的顯示方式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） TableColumnItems 項目 （格式） TableColumnItem 項目 （格式）TableColumnItem （格式） 的 FormatString 元素

## <a name="syntax"></a>語法

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`FormatString`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|定義屬性或其值會顯示在資料列的資料行的指令碼。|

## <a name="text-value"></a>文字值

指定用來將資料格式化的模式。 例如，此模式可以用來格式化類型的任何屬性的值[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。

## <a name="remarks"></a>備註

建立資料表檢視、 清單檢視、 寬型檢視或自訂的檢視時，就可以使用格式字串。 如需有關如何格式化顯示在檢視值的詳細資訊，請參閱[格式顯示資料](./formatting-displayed-data.md)。

資料表檢視元件的相關資訊，請參閱[資料表檢視](./creating-a-table-view.md)。

## <a name="example"></a>範例

下列範例示範如何定義的格式化字串的值，`StartTime`屬性。

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[格式化顯示資料](./formatting-displayed-data.md)

[TableColumnItem 項目 （格式）](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
