---
title: 適用于 CustomEntry 之 GroupBy (格式的 CustomItem 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e8086c5330b6644f83316ad4ae33c33ba40d9eee
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783716"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)

定義自訂控制項視圖顯示的資料，以及顯示的方式。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（groupby (格式）) CustomEntries 元素（適用于 groupby (格式的 CustomItem) CustomEntry 元素） (

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
|[GroupBy 之 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-groupby-format.md)|選擇性項目。<br /><br /> 定義自訂控制項視圖顯示的資料，以及顯示的方式。|
|[GroupBy 之 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-groupby-format.md)|選擇性項目。<br /><br /> 將空白行加入控制項的顯示中。|
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
