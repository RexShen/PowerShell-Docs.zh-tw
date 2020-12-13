---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)
description: 檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666734"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)

定義自訂控制項視圖所顯示的資料，以及其顯示方式。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案格式 CustomItem 元素

## <a name="syntax"></a>語法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomItem` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 定義控制項所顯示的資料。|
|[檢視之 CustomControl 的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 定義自訂控制項視圖所顯示的資料，以及其顯示方式。|
|[適用于 View (格式之自訂控制項的 CustomItem 的分行符號元素) ](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 在控制項的顯示中加入空白行。|
|[CustomItem for CustomControl for View (Format 的 Text 元素) ](./text-element-for-customitem-for-customview-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項所顯示之資料的其他文字。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|提供自訂控制項視圖的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[適用于 CustomEntries 的 CustomEntry 元素 (格式) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem for CustomControl for View (Format 的 Text 元素) ](./text-element-for-customitem-for-customview-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
