---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomItem 的框架元素 (格式)
description: 設定之控制項的 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 85d095b9b0c25b68b2353bce56b85333aff91b98
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652239"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的框架元素 (格式)

定義顯示資料的方式，例如將資料向左或向右移動。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定專案 (格式) 控制項的設定專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的設定 (格式) 的設定 (格式) CustomControl 的控制項設定 (格式) 格式的控制項的 CustomItem 專案

## <a name="syntax"></a>語法

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `Frame` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|Required 元素|
|[設定之控制項的框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定將第一行資料向左移動的字元數。|
|[設定之控制項的框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[設定之控制項的框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界向外移動的字元數。|
|[設定之控制項的框架的 RightIndent 元素 (格式)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于設定之控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義控制項顯示的資料以及其顯示方式。|

## <a name="remarks"></a>備註

您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) 元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[設定之控制項的框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 RightIndent 元素 (格式)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[適用于設定之控制項的 CustomEntry CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
