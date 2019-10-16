---
title: CustomControl for View 的 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363947"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)

定義自訂控制項視圖顯示的資料，以及顯示的方式。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for View （格式）

## <a name="syntax"></a>語法

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomItem` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 定義控制項所顯示的資料。|
|[適用于 CustomControl for View 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 定義自訂控制項視圖顯示的資料，以及顯示的方式。|
|[View 的自訂控制項的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 將空白行加入控制項的顯示中。|
|[CustomItem for CustomControl for View 的 Text 元素（格式）](./text-element-for-customitem-for-customview-for-view-format.md)|選擇性元素。<br /><br /> 指定控制項所顯示之資料的其他文字。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的 CustomEntries 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|提供自訂控制項視圖的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomEntries for View 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[CustomControl for View 的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[適用于 CustomControl for View 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomControl for View 的 CustomItem 的換行元素（格式）](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem for CustomControl for View 的 Text 元素（格式）](./text-element-for-customitem-for-customview-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
