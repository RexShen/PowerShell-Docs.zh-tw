---
title: WideControl 的之 wideitem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361397"
---
# <a name="wideitem-element-for-widecontrol-format"></a>WideControl 的 WideItem 元素 (格式)

定義顯示其值的屬性或腳本。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式）之 wideitem 元素（格式）

## <a name="syntax"></a>語法

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `WideItem` 專案的父元素。 `FormatString` 元素為選擇性。 不過，您必須指定 `PropertyName` 或 `ScriptBlock` 元素，但不能同時指定這兩個專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideControl 之之 wideitem 的格式字串元素（格式）](./formatstring-element-for-wideitem-for-widecontrol-format.md)|選擇性項目。<br /><br /> 指定定義屬性或腳本值在視圖中顯示方式的格式模式。|
|[之 wideitem 的 PropertyName 元素（格式）](./propertyname-element-for-wideitem-for-widecontrol-format.md)|指定物件的屬性，其值會顯示在寬視圖中。|
|[之 wideitem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|指定在寬視圖中顯示其值的腳本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

## <a name="remarks"></a>備註

如需有關寬視圖元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示定義單一 `WideItem` 元素的 `WideEntry` 專案。 `WideItem` 元素會定義屬性或腳本，其值會顯示在視圖中。

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 之之 wideitem 的格式字串元素（格式）](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[之 wideitem 的 PropertyName 元素（格式）](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[之 wideitem 的 ScriptBlock 元素（格式）](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
