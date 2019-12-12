---
title: WideControl 之之 wideitem 的格式字串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363027"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 FormatString 元素 (格式)

指定定義屬性或腳本值在視圖中顯示方式的格式模式。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 專案（格式） WideEntry 元素（適用于 WideControl 的之 wideitem 元素（格式）適用于 WideControl 的之 wideitem （格式）

## <a name="syntax"></a>語法

```xml
<FormatString>PropertyPattern</FormatString>
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
|[WideControl 的之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)|定義屬性或腳本，其值會顯示在清單視圖的資料列中。|

## <a name="text-value"></a>文字值

指定用來格式化資料的模式。 例如，您可以使用此模式來格式化[System. Timespan](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 類型之任何屬性的值。

## <a name="remarks"></a>備註

建立資料表視圖、清單視圖、寬視圖或自訂視圖時，可以使用格式字串。 如需有關格式化顯示在視圖中之值的詳細資訊，請參閱[格式化顯示的資料](./formatting-displayed-data.md)。

如需在寬視圖中使用格式字串的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示如何為 `StartTime` 屬性的值定義格式字串。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[建立寬型視圖](./creating-a-wide-view.md)

[WideControl 的之 wideitem 元素（格式）](./wideitem-element-for-widecontrol-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
