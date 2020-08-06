---
title: View (Format) 的控制項之 CustomItem 的框架元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5ade36c183a026cb9001a2abbe91d31638a87108
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773448"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 (格式) CustomEntries 專案的控制項的控制項 (的 CustomControl 元素針對 CustomControl for View (格式) 的 CustomEntries for 控制項的 CustomEntry 專案， (格式]) CustomItem 元素用於 view (format) Frame 元素 for view 的控制項 (格式) 

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
|[ (格式之 View 控制項框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行向左移動的字元數。|
|[ (格式之 View 控制項框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行向右移動的字元數。|
|[ (格式之 View 控制項框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界下移的字元數。|
|[ (格式之 View 控制項框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[ (格式之 View 控制項框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[ (格式之 View 控制項框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[ (格式之 View 控制項框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-controls-for-view-format.md)

[ (格式之 View 控制項框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-controls-for-view-format.md)

[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
