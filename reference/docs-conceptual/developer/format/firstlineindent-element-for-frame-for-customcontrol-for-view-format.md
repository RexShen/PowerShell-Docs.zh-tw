---
title: CustomControl for View 的 Frame 的 FirstLineIndent 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363057"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的框架的 FirstLineIndent 元素 (格式)

指定第一行資料向右移動的字元數。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomItem for CustomControl for View （Format） FirstLineIndent 元素的 CustomEntry for CustomControlView （Format） Frame 元素

## <a name="syntax"></a>語法

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節描述 `FirstLineIndent` 元素的屬性、子專案和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[適用于 CustomControl for View 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|定義資料的顯示方式，例如將資料向左或向右移位。|

## <a name="text-value"></a>文字值

指定您想要將資料行移到第一行的字元數。

## <a name="remarks"></a>備註

如果指定這個元素，您就不能指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[CustomControl for View 的 Frame 的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[適用于 CustomControl for View 的 CustomItem 的框架元素（格式）](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
