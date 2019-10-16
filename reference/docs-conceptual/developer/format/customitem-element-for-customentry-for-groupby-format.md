---
title: GroupBy 之 CustomEntry 的 CustomItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363877"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)

定義自訂控制項視圖顯示的資料，以及顯示的方式。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomItem 元素GroupBy 的 CustomEntry （格式）

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
|[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)|選擇性元素。<br /><br /> 定義控制項所顯示的資料。|
|[GroupBy 之 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)|選擇性元素。<br /><br /> 定義自訂控制項視圖顯示的資料，以及顯示的方式。|
|[GroupBy 的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-groupby-format.md)|選擇性元素。<br /><br /> 將空白行加入控制項的顯示中。|
|[GroupBy 的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-groupby-format.md)|選擇性元素。<br /><br /> 指定控制項所顯示之資料的其他文字。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)|提供自訂控制項視圖的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-groupby-format.md)

[GroupBy 之 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-groupby-format.md)

[GroupBy 之 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)

[GroupBy 的 CustomItem 的分行符號元素（格式）](./newline-element-for-customitem-for-groupby-format.md)

[GroupBy 的 CustomItem 的文字元素（格式）](./text-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
