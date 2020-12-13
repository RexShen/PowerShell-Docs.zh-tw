---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的框架的 FirstLineIndent 元素 (格式)
description: 設定之控制項的框架的 FirstLineIndent 元素 (格式)
ms.openlocfilehash: 59a41410160879c2414819de4d367ecdedd8e182
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660169"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>設定之控制項的框架的 FirstLineIndent 元素 (格式)

指定第一行資料向右移動的字元數。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) CustomEntry 元素針對設定 (格式的控制項的 CustomControl 格式) CustomItem 元素，用於 CustomEntry 的設定框架專案控制項的設定 (格式 (設定的控制項框架) FirstLineIndent 元素) 

## <a name="syntax"></a>語法

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `FirstLineIndent` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|定義顯示資料的方式，例如將資料向左或向右移動。|

## <a name="text-value"></a>文字值

指定您想要將資料行移到第一行的字元數。

## <a name="remarks"></a>備註

如果指定了此元素，您就無法指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 元素。

## <a name="see-also"></a>另請參閱

[設定之控制項的框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
