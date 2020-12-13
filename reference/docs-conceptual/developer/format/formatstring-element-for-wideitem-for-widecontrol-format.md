---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 之 WideItem 的 FormatString 元素 (格式)
description: WideControl 之 WideItem 的 FormatString 元素 (格式)
ms.openlocfilehash: f67a18e3ec4f1323e7f9be8904db518c679d53e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667873"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 FormatString 元素 (格式)

指定格式模式，定義屬性或腳本值在視圖中的顯示方式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (format) WideEntries 元素 (format) WideControl (format) format 元素 (format 專案) 格式 (之 wideitem 的 WideControl) 格式

## <a name="syntax"></a>語法

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `FormatString` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideControl 的 WideItem 元素 (格式)](./wideitem-element-for-widecontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定用於格式化資料的模式。 例如，您可以使用此模式來格式化屬於 [system.string： {](/dotnet/api/System.TimeSpan)0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

您可以在建立資料表視圖、清單視圖、寬視圖或自訂視圖時使用格式字串。 如需有關如何將顯示在視圖中的值格式化的詳細資訊，請參閱 [格式化顯示的資料](./formatting-displayed-data.md)。

如需在寬型視圖中使用格式字串的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideControl 的 WideItem 元素 (格式)](./wideitem-element-for-widecontrol-format.md)

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
