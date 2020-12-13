---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl 的 ColumnNumber 元素 (格式)
description: WideControl 的 ColumnNumber 元素 (格式)
ms.openlocfilehash: 1ddbbfbd5b53065afcc6c1326d6abf1fadedc67b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648395"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>WideControl 的 ColumnNumber 元素 (格式)

指定以寬視圖顯示的資料行數目。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) WideControl 元素 (格式) WideControl (格式的 ColumnNumber 元素) 

## <a name="syntax"></a>語法

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ColumnNumber` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideControl 元素 (格式)](./widecontrol-element-format.md)|為視圖定義寬 (單一值) 清單格式。|

## <a name="text-value"></a>文字值

指定正整數值。

## <a name="remarks"></a>備註

定義廣泛的視圖時，您可以加入專案 `AutoSize` 或 `ColumnNumber` 元素，但無法同時加入兩者。

如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。

如需寬視圖的範例，請參閱 [wide (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl (格式的 Autosize 元素) ](./autosize-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[寬型檢視 (基本)](./wide-view-basic.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
