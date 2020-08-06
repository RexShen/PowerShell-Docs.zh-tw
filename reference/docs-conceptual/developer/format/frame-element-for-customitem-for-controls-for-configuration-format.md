---
title: " (格式) 設定之控制項的 CustomItem 的框架元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: fa435b8d6b868d2d7c94b7926321d94edc2ec290
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781472"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 專案 (格式) 控制設定的控制項元素 (格式設定 (格式的控制項) 控制元素) 設定 (格式的 CustomControl 的 CustomEntries 元素) 設定 (格式) CustomControl 元素適用于設定 (格式之控制項的 CustomItem 的設定) CustomEntry (格式的控制專案的 CustomEntry 的控制項

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
|`CustomItem Element`|必要元素|
|[設定之控制項的框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定第一行資料向左移動的字元數。|
|[設定之控制項的框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[設定之控制項的框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界下移的字元數。|
|[設定之控制項的框架的 RightIndent 元素 (格式)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[設定之控制項的框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 RightIndent 元素 (格式)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
