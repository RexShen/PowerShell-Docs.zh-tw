---
title: WideControl (格式的 ColumnNumber 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5f151bb0e629efcebe6295cdcae6cebcbbb1b39b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783852"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>WideControl 的 ColumnNumber 元素 (格式)

指定在寬視圖中顯示的資料行數目。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideControl (格式的 ColumnNumber 元素) 

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
|[WideControl 元素 (格式)](./widecontrol-element-format.md)|定義視圖的寬 (單一值) 清單格式。|

## <a name="text-value"></a>文字值

請指定正整數值。

## <a name="remarks"></a>備註

定義寬視圖時，您可以加入 `AutoSize` 元素或專案 `ColumnNumber` ，但無法同時新增這兩個專案。

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

如需寬視圖的範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl (格式的 Autosize 元素) ](./autosize-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[寬型檢視 (基本)](./wide-view-basic.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
