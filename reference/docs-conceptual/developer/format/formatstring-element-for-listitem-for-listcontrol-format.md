---
title: ListControl 之專案的格式字串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363017"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>ListControl 之 ListItem 的 FormatString 元素 (格式)

指定定義屬性或腳本值顯示方式的格式模式。

ListEntry （格式） ListControl 元素的 ListControl （format） ListItems 元素的設定元素（格式） ViewDefinitions 元素（格式） ListEntries 元素（格式）適用于 ListControl 之專案的 ListControl （格式）格式（格式）元素的專案專案專案

## <a name="syntax"></a>語法

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `FormatString` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定用來格式化資料的模式。 例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。 如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。

如需在清單視圖中使用格式字串的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>另請參閱

[建立清單視圖](./creating-a-list-view.md)

[[專案] 元素（格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
