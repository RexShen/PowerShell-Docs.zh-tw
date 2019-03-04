---
title: GroupBy （格式） 的畫面格 FirstLineHanging 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855614"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>GroupBy 之框架的 FirstLineHanging 元素 (格式)

指定資料的第一行向左移動的字元數。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 框架 GroupBy （格式） 的 GroupBy （格式） FirstLineHanging 元素的 GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素

## <a name="syntax"></a>語法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`FirstLineHanging`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomItem 的框架項目](./frame-element-for-customitem-for-groupby-format.md)|定義資料的顯示方式，例如將資料轉移至左邊或右邊。|

## <a name="text-value"></a>文字值

指定您想要移動資料的第一行的字元數。

## <a name="remarks"></a>備註

如果未指定這個項目，您無法指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)項目。

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的畫面格 FirstLineIndent 項目](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的 CustomItem 的框架項目](./frame-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
