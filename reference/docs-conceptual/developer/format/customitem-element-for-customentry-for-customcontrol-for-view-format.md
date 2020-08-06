---
title: CustomControl for View (格式) 的 CustomEntry 的 CustomItem 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 25101c9c156ef91657f51db7044bf9a6653142a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785824"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)

定義自訂控制項視圖顯示的資料，以及顯示的方式。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素（CustomEntries for view) CustomItem 元素的 CustomEntry for view (格式) 

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
|[檢視之 CustomControl 的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 定義自訂控制項視圖顯示的資料，以及顯示的方式。|
|[ (格式之自訂控制項的 CustomItem 的分行符號元素) ](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 將空白行加入控制項的顯示中。|
|[CustomItem for CustomControl for View (Format 的 Text 元素) ](./text-element-for-customitem-for-customview-for-view-format.md)|選擇性項目。<br /><br /> 指定控制項所顯示之資料的其他文字。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|提供自訂控制項視圖的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomEntries for View (格式的 CustomEntry 元素) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomItem 的 ExpressionBinding 元素 (格式)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[檢視之 CustomControl 的 CustomItem 的 NewLine 元素 (格式)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem for CustomControl for View (Format 的 Text 元素) ](./text-element-for-customitem-for-customview-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
