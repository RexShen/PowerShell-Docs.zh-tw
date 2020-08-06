---
title: WideControl (格式的之 wideitem 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6b2f7c97978c20350caeec894589c5995ae7ccc4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779891"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl 的 WideItem 元素 (格式)

定義顯示其值的屬性或腳本。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 wideitem 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `WideItem` 。 `FormatString` 則是選擇性元素。 不過，您必須指定 `PropertyName` 或專案 `ScriptBlock` ，但不能同時指定這兩個專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl 之 WideItem 的 FormatString 元素 (格式)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定定義屬性或腳本值在視圖中顯示方式的格式模式。|
|[之 wideitem (格式的 PropertyName 元素) ](./propertyname-element-for-wideitem-for-widecontrol-format.md)|指定物件的屬性，其值會顯示在寬視圖中。|
|[之 wideitem (格式的 ScriptBlock 元素) ](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|指定在寬視圖中顯示其值的腳本。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

如需有關寬視圖元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示 `WideEntry` 定義單一專案的元素 `WideItem` 。 `WideItem`元素會定義屬性或腳本，其值會顯示在視圖中。

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 之 WideItem 的 FormatString 元素 (格式)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[之 wideitem (格式的 PropertyName 元素) ](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[之 wideitem (格式的 ScriptBlock 元素) ](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
