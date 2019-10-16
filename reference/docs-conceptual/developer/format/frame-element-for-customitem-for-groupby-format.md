---
title: GroupBy 之 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362947"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 的 groupby （format） CustomItem 元素的 CustomControl，適用于 groupby 的 CustomItem （格式）

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

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `Frame` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|必要元素|
|[GroupBy 之框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-groupby-format.md)|選擇性元素。<br /><br /> 指定第一行資料向左移動的字元數。|
|[GroupBy 之框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)|選擇性元素。<br /><br /> 指定第一行資料向右移動的字元數。|
|[GroupBy 之框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-groupby-format.md)|選擇性元素。<br /><br /> 指定資料從左邊界下移的字元數。|
|[GroupBy 之框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素|選擇性元素。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。

## <a name="see-also"></a>另請參閱

[GroupBy 之框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
