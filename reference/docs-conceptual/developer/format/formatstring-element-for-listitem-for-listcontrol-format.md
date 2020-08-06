---
title: 適用于 ListControl (格式) 的專案格式字串元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9ec73aa1c2e8180258722627e30344de4e67bda5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781574"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>ListControl 之 ListItem 的 FormatString 元素 (格式)

指定定義屬性或腳本值顯示方式的格式模式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 專案 (格式) ListControl (格式) ListEntry 元素 ListControl (格式) ListItems 元素用於 ListControl (格式) ListControl 專案用於 ListControl (格式的顯示專案) 格式的元素

## <a name="syntax"></a>語法

```xml
<FormatString>PropertyPattern</FormatString>
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
|[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定用來格式化資料的模式。 例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。 如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。

如需在清單視圖中使用格式字串的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何為屬性的值定義格式化字串 `StartTime` 。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ (格式的 [專案] 元素) ](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
