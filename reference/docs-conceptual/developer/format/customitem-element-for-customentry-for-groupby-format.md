---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)
description: GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645975"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)

定義自訂控制項視圖所顯示的資料，以及其顯示方式。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy (格式) CustomEntries 元素適用于 groupby (格式) CustomItem 專案用於 CustomEntry 的 GroupBy (格式) 

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
|[GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-groupby-format.md)|選擇性項目。<br /><br /> 定義控制項所顯示的資料。|
|[GroupBy 之 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-groupby-format.md)|選擇性項目。<br /><br /> 定義自訂控制項視圖所顯示的資料，以及其顯示方式。|
|[GroupBy 之 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-groupby-format.md)|選擇性項目。<br /><br /> 在控制項的顯示中加入空白行。|
|[GroupBy 之 CustomItem 的文字元素 (格式)](./text-element-for-customitem-for-groupby-format.md)|選擇性項目。<br /><br /> 指定控制項所顯示之資料的其他文字。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-groupby-format.md)|提供自訂控制項視圖的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-groupby-format.md)

[GroupBy 之 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[GroupBy 之 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-groupby-format.md)

[GroupBy 之 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-groupby-format.md)

[GroupBy 之 CustomItem 的文字元素 (格式)](./text-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
