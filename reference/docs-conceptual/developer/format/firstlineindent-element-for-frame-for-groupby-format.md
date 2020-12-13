---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之框架的 FirstLineIndent 元素 (格式)
description: GroupBy 之框架的 FirstLineIndent 元素 (格式)
ms.openlocfilehash: 391a6f338e264fd9fdd1948ded74bf022cb114d1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645788"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>GroupBy 之框架的 FirstLineIndent 元素 (格式)

指定第一行資料向右移動的字元數。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) GroupBy 專案的視圖 (格式) 適用于 groupby (格式) CustomEntries 專案 (格式) 專案的專案 (格式)  (格式)  (格式的) CustomEntry 專案 (格式) 的格式

## <a name="syntax"></a>語法

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `FirstLineIndent` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-groupby-format.md)|定義顯示資料的方式，例如將資料向左或向右移動。|

## <a name="text-value"></a>文字值

指定您想要將資料行移到第一行的字元數。

## <a name="remarks"></a>備註

如果指定了此元素，您就無法指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 元素。

## <a name="see-also"></a>另請參閱

[GroupBy 之框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy 之 CustomItem 的框架元素 (格式)](./frame-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
