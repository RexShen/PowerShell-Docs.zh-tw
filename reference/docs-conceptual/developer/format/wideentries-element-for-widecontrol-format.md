---
title: WideControl 的 WideEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361427"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl 的 WideEntries 元素 (格式)

提供寬視圖的定義。 寬視圖必須指定一或多個定義。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式）

## <a name="syntax"></a>語法

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `WideEntries` 專案的屬性、子專案和父項目。 至少必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)|提供寬視圖的定義。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|定義視圖的寬（單一值）清單格式。|

## <a name="remarks"></a>備註

寬型視圖是一種清單格式，可顯示每個物件的單一屬性值或腳本值。 如需有關寬視圖元件的詳細資訊，請參閱[寬視圖元件](./creating-a-wide-view.md)。

## <a name="example"></a>範例

下列範例顯示定義單一 `WideEntry` 元素的 `WideEntries` 專案。 `WideEntry` 元素包含單一 `WideItem` 元素，可定義要在視圖中顯示的屬性或腳本值。

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

如需寬視圖的完整範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[建立寬型視圖](./creating-a-wide-view.md)

[WideControl 元素（格式）](./widecontrol-element-format.md)

[WideEntry 元素（格式）](./wideentry-element-for-widecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
