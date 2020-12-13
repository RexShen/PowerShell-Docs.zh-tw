---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 WideEntries 元素 (格式)
description: WideControl 的 WideEntries 元素 (格式)
ms.openlocfilehash: 567b8acdd0d2e8d5daaef2c31b4fe4ce38c23a47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651230"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl 的 WideEntries 元素 (格式)

提供寬視圖的定義。 寬型視圖必須指定一或多個定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideEntries 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `WideEntries` 。 至少必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideControl 元素 (格式)](./widecontrol-element-format.md)|為視圖定義寬 (單一值) 清單格式。|

## <a name="remarks"></a>備註

寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。 如需廣泛視圖元件的詳細資訊，請參閱 [Wide View 元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示 `WideEntries` 定義單一專案的元素 `WideEntry` 。 `WideEntry`元素包含單一 `WideItem` 元素，可定義顯示在視圖中的屬性或腳本值。

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

如需完整的完整範例，請參閱 [ (基本) 的寬量視圖 ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideControl 元素 (格式)](./widecontrol-element-format.md)

[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
