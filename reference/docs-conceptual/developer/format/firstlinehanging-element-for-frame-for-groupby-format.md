---
title: GroupBy 之框架的 FirstLineHanging 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363817"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>GroupBy 之框架的 FirstLineHanging 元素 (格式)

指定第一行資料向左移動的字元數。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素適用于 CustomEntry 之 groupby （格式） CustomItem 元素的 groupby （format） CustomControl 專案（適用于 GroupBy 的框架的 groupby （格式） FirstLineHanging 元素）

## <a name="syntax"></a>語法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `FirstLineHanging` 元素的屬性、子專案和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)|定義資料的顯示方式，例如將資料向左或向右移位。|

## <a name="text-value"></a>文字值

指定您想要將資料行移到第一行的字元數。

## <a name="remarks"></a>備註

如果指定這個元素，您就不能指定[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素。

## <a name="see-also"></a>另請參閱

[GroupBy 之框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy 之 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
