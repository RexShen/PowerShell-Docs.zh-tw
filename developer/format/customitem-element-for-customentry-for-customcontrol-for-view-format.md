---
title: CustomControl 檢視 （格式） 的 CustomEntry CustomItem 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066406"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 CustomItem 元素 (格式)

定義自訂的控制項檢視所顯示的資料和顯示方式。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry 檢視 （格式）

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

下列各節說明屬性、 子項目和父項目`CustomItem`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 定義控制項所顯示的資料。|
|[CustomControl 檢視 （格式） 的 CustomItem 的框架項目](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 定義自訂的控制項檢視所顯示的資料和顯示方式。|
|[CustomItem 檢視 （格式） 的自訂控制項的新行項目](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 將控制項的顯示中的空白行。|
|[CustomItem CustomControl 檢視 （格式） 的文字項目](./text-element-for-customitem-for-customview-for-view-format.md)|選擇性的項目。<br /><br /> 指定要由控制項所顯示的資料的其他文字。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomControl 檢視 （格式） 的 CustomEntries CustomEntry 項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|提供自訂的控制項檢視的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[CustomEntry CustomEntries 檢視 （格式） 的項目](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding CustomItem 如 CustomControl 檢視 （格式） 的項目](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomControl 檢視 （格式） 的 CustomItem 的框架項目](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem CustomControl 檢視 （格式） 的新行項目](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[CustomItem CustomControl 檢視 （格式） 的文字項目](./text-element-for-customitem-for-customview-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
