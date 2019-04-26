---
title: FirstLineHanging CustomControl 檢視 （格式） 的畫面格的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6ac3d86-0529-4b93-9bc7-ee94fcef9618
caps.latest.revision: 8
ms.openlocfilehash: ea43e025f5f653ff000e1d7591b535e73da5c9e5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065966"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的框架的 FirstLineHanging 元素 (格式)

指定資料的第一行向左移動的字元數。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CustomControl CustomControl 檢視 （格式） 的畫面格的檢視 （格式） FirstLineHanging 項目的的 CustomItem CustomControlView （格式） 框架元素

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
|[CustomControl 檢視 （格式） 的 CustomItem 的框架項目](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|定義資料的顯示方式，例如將資料轉移至左邊或右邊。|

## <a name="text-value"></a>文字值

指定您想要移動資料的第一行的字元數。

## <a name="remarks"></a>備註

如果未指定這個項目，您無法指定[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)項目。

## <a name="see-also"></a>另請參閱

[FirstLineIndent CustomControl 檢視 （格式） 的畫面格的項目](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomControl 檢視 （格式） 的 CustomItem 的框架項目](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
