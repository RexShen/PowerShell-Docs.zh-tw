---
title: FormatString 元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860934"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>WideControl 之 WideItem 的 FormatString 元素 (格式)

指定之格式模式所定義的屬性或指令碼的值在檢視中的顯示方式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） WideControl 項目 （格式） WideEntries 項目 （格式） WideEntry WideControl （格式） WideItem 元素元素 WideControl （格式） FormatString 元素針對 WideControl （格式） 的 WideItem

## <a name="syntax"></a>語法

```xml
<FormatString>PropertyPattern</FormatString>
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
|[WideItem WideControl （格式） 的項目](./wideitem-element-for-widecontrol-format.md)|定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。|

## <a name="text-value"></a>文字值

指定用來將資料格式化的模式。 例如，您可以使用此模式來格式化任何類型的屬性值[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。

## <a name="remarks"></a>備註

建立資料表檢視、 清單檢視、 寬型檢視或自訂的檢視時，就可以使用格式字串。 如需有關如何格式化顯示在檢視值的詳細資訊，請參閱[格式顯示資料](./formatting-displayed-data.md)。

如需在寬型檢視中使用格式字串的詳細資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例示範如何定義的格式化字串的值，`StartTime`屬性。

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideItem WideControl （格式） 的項目](./wideitem-element-for-widecontrol-format.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
