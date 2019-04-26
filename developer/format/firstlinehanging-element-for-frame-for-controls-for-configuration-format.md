---
title: FirstLineHanging 組態 （格式） 的控制項的畫面格的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065881"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a>設定之控制項的框架的 FirstLineHanging 元素 (格式)

指定資料的第一行向左移動的字元數。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomItem 控制項框架的組態 （格式） FirstLineHanging 項目的組態框架項目控制項的 CustomEntry 的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目組態 （格式） 的控制項

## <a name="syntax"></a>語法

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`FirstLineHanging`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomItem 組態 （格式） 的控制項的框架項目](./frame-element-for-customitem-for-controls-for-configuration-format.md)|定義資料的顯示方式，例如將資料轉移至左邊或右邊。|

## <a name="text-value"></a>文字值

指定您想要移動資料的第一行的字元數。

## <a name="remarks"></a>備註

如果未指定這個項目，您不能指定`FirstLineIndent`項目。

## <a name="see-also"></a>另請參閱

[CustomItem 組態 （格式） 的控制項的框架項目](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
