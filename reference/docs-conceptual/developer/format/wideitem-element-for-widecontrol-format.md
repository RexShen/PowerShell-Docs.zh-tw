---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 WideItem 元素 (格式)
description: WideControl 的 WideItem 元素 (格式)
ms.openlocfilehash: b9c416bbe3befcd689b8a2c0b72a8ff1301b9659
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647806"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl 的 WideItem 元素 (格式)

定義顯示其值的屬性或腳本。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 wideitem 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `WideItem` 。 `FormatString` 則是選擇性元素。 不過，您必須指定 `PropertyName` 或 `ScriptBlock` 元素，但不能同時指定兩者。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl 之 WideItem 的 FormatString 元素 (格式)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定格式模式，定義屬性或腳本值在視圖中的顯示方式。|
|[之 wideitem (格式的 PropertyName 元素) ](./propertyname-element-for-wideitem-for-widecontrol-format.md)|指定物件的屬性，其值會顯示在寬視圖中。|
|[之 wideitem (格式的 ScriptBlock 元素) ](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|指定以寬視圖顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

如需廣泛視圖元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。 `WideItem`元素會定義屬性或腳本，其值會顯示在視圖中。

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 之 WideItem 的 FormatString 元素 (格式)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[之 wideitem (格式的 PropertyName 元素) ](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[之 wideitem (格式的 ScriptBlock 元素) ](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
