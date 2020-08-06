---
title: WideControl (格式的 WideEntries 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785042"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl 的 WideEntries 元素 (格式)

提供寬視圖的定義。 寬視圖必須指定一或多個定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `WideEntries` 。 至少必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideControl 元素 (格式)](./widecontrol-element-format.md)|定義視圖的寬 (單一值) 清單格式。|

## <a name="remarks"></a>備註

寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。 如需有關寬視圖元件的詳細資訊，請參閱[寬視圖元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示 `WideEntries` 定義單一專案的元素 `WideEntry` 。 `WideEntry`元素包含單一 `WideItem` 元素，可定義要在視圖中顯示的屬性或腳本值。

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

如需寬視圖的完整範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideControl 元素 (格式)](./widecontrol-element-format.md)

[WideEntry 元素 (格式) ](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
