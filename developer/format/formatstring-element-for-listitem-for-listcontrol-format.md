---
title: FormatString 元素 ListControl （格式） 的 ListItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065610"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a>ListControl 之 ListItem 的 FormatString 元素 (格式)

指定之格式模式所定義的屬性或指令碼的值的顯示方式。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries ListControl （格式） ListEntry 元素元素 ListControl （格式） 的 ListControl （格式） ListItems 元素ListItem 項目 ListControl （格式） 的 ListItem ListControl （格式） FormatString 元素

## <a name="syntax"></a>語法

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`FormatString`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ListItem 項目 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)|定義屬性或其值會顯示 [清單] 檢視的資料列中的指令碼。|

## <a name="text-value"></a>文字值

指定用來將資料格式化的模式。 例如，您可以使用此模式來格式化任何類型的屬性值[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。

## <a name="remarks"></a>備註

建立資料表檢視、 清單檢視、 寬型檢視或自訂的檢視時，就可以使用格式字串。 如需有關如何格式化顯示在檢視值的詳細資訊，請參閱[格式顯示資料](./formatting-displayed-data.md)。

如需在清單檢視中使用格式字串的詳細資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="example"></a>範例

下列範例示範如何定義的格式化字串的值，`StartTime`屬性。

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[ListItem 項目 （格式）](./listitem-element-for-listitems-for-listcontrol-format.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
