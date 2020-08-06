---
title: WideControl (格式的 AutoSize 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 64e62142738916978b37eb1cd3a73536b0447099
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783869"
---
# <a name="autosize-element-for-widecontrol-format"></a>WideControl 的 AutoSize 元素 (格式)

指定是否根據資料大小來調整資料行大小和資料行數目。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) WideControl 元素 (format) Autosize 元素 for WideControl (Format) 

## <a name="syntax"></a>語法

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `AutoSize` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideControl 元素 (格式)](./widecontrol-element-format.md)|定義視圖的寬 (單一值) 清單格式。|

## <a name="remarks"></a>備註

定義寬視圖時，您可以加入 `AutoSize` 元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)專案，但無法同時新增這兩個專案。

如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

如需寬視圖的範例，請參閱[寬視圖 (基本) ](./wide-view-basic.md)。

## <a name="see-also"></a>另請參閱

[WideControl 的 ColumnNumber 元素 (格式)](./columnnumber-element-for-widecontrol-format.md)

[建立寬型檢視](./creating-a-wide-view.md)

[WideControl 元素 (格式)](./widecontrol-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
