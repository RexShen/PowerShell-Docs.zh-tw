---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomItem 的框架元素 (格式)
description: 檢視之控制項的 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 6f26e19a6894ac213b924108a56cb80f9ffd1143
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652207"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的框架元素 (格式)

定義顯示資料的方式，例如將資料向左或向右移動。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 專案的視圖控制項的控制項 (格式若為 CustomControl for View (格式) CustomEntry 元素，用於 CustomEntries 的控制項 (格式) CustomEntry for 控制項的 CustomItem 專案 (格式)  () 格式控制項的控制項的框架元素

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
|[View (格式之控制項框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行向左移動的字元數。|
|[View (格式之控制項框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行向右移動的字元數。|
|[View (格式之控制項框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界向外移動的字元數。|
|[View (格式之控制項框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-controls-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項顯示的資料以及其顯示方式。|

## <a name="remarks"></a>備註

您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[View (格式之控制項框架的 FirstLineHanging 元素) ](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[View (格式之控制項框架的 FirstLineIndent 元素) ](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[View (格式之控制項框架的 LeftIndent 元素) ](./leftindent-element-for-frame-for-controls-for-view-format.md)

[View (格式之控制項框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-controls-for-view-format.md)

[檢視之控制項的 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
