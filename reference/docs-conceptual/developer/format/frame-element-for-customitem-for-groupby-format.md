---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomItem 的框架元素 (格式)
description: GroupBy 之 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652167"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的框架元素 (格式)

定義顯示資料的方式，例如將資料向左或向右移動。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式)  (格式的 CustomControl 專案) 格式 (的 CustomItem 專案) 格式 (

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
|[GroupBy 之框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-groupby-format.md)|選擇性項目。<br /><br /> 指定將第一行資料向左移動的字元數。|
|[GroupBy 之框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-groupby-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[GroupBy 之框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-groupby-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界向外移動的字元數。|
|[GroupBy (格式之框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)|定義控制項顯示的資料以及其顯示方式。|

## <a name="remarks"></a>備註

您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[GroupBy 之框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 RightIndent 元素 (格式)](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
