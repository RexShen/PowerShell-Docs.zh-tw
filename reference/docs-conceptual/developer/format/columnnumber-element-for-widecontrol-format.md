---
title: WideControl 的 ColumnNumber 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364217"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>WideControl 的 ColumnNumber 元素 (格式)

指定在寬視圖中顯示的資料行數目。

WideControl （格式）的設定元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） ColumnNumber 元素

## <a name="syntax"></a>語法

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ColumnNumber` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|項目|說明|
|-------------|-----------------|
|[WideControl 元素（格式）](./widecontrol-element-format.md)|定義視圖的寬（單一值）清單格式。|

## <a name="text-value"></a>文字值

請指定正整數值。

## <a name="remarks"></a>備註

定義寬視圖時，您可以加入 `AutoSize` 元素或 `ColumnNumber` 專案，但無法同時新增兩者。

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

如需寬視圖的範例，請參閱[寬視圖（基本）](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 的 Autosize 元素（格式）](./autosize-element-for-widecontrol-format.md)

[建立寬型視圖](./creating-a-wide-view.md)

[寬視圖（基本）](./wide-view-basic.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
