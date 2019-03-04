---
title: FirstLineIndent 組態 （格式） 的控制項的畫面格的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856344"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>設定之控制項的框架的 FirstLineIndent 元素 (格式)

指定資料的第一行向右移位的字元數。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomItem 控制項框架的組態 （格式） FirstLineIndent 項目的組態框架項目控制項的 CustomEntry 的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目組態 （格式） 的控制項

## <a name="syntax"></a>語法

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`FirstLineIndent`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomItem 組態 （格式） 的控制項的框架項目](./frame-element-for-customitem-for-controls-for-configuration-format.md)|定義資料的顯示方式，例如將資料轉移至左邊或右邊。|

## <a name="text-value"></a>文字值

指定您想要移動資料的第一行的字元數。

## <a name="remarks"></a>備註

如果未指定這個項目，您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)項目。

## <a name="see-also"></a>另請參閱

[FirstLineHanging 組態 （格式） 的控制項的畫面格的項目](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem 組態 （格式） 的控制項的框架項目](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
