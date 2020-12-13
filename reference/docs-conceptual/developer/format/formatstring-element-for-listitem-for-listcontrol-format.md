---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 ListItem 的 FormatString 元素 (格式)
description: ListControl 之 ListItem 的 FormatString 元素 (格式)
ms.openlocfilehash: 1c16da92928ea632241942f4f2c63390c4fea706
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667907"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>ListControl 之 ListItem 的 FormatString 元素 (格式)

指定定義屬性或腳本值顯示方式的格式模式。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) ListControl 元素 (format) ListEntries 元素 for ListControl (format) ListEntry 專案 for (format) ListControl 專案 for ListItems (format)  (格式專案的 ListControl) 格式 (

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
|[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定用於格式化資料的模式。 例如，您可以使用此模式來格式化屬於 [system.string： {](/dotnet/api/System.TimeSpan)0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

您可以在建立資料表視圖、清單視圖、寬視圖或自訂視圖時使用格式字串。 如需有關如何將顯示在視圖中的值格式化的詳細資訊，請參閱 [格式化顯示的資料](./formatting-displayed-data.md)。

如需在清單視圖中使用格式字串的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何定義屬性值的格式化字串 `StartTime` 。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ (格式) 的 [專案] 元素 ](./listitem-element-for-listitems-for-listcontrol-format.md)

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
