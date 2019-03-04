---
title: 針對 CustomItem 框架項目控制項的組態 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862974"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） 的組態 （CustomControl 的 CustomEntries 項目控制項的組態 （格式） CustomControl 項目控制項的控制項項目的組態項目 （格式） 的控制項項目CustomControl CustomEntry 組態框架項目 CustomItem 組態 （格式） 的控制項的控制項的組態 （格式） CustomItem 元素的控制項的格式） CustomEntry 項目

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

下列各節說明屬性、 子項目和父項目`Frame`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|必要項目|
|[FirstLineHanging 組態 （格式） 的控制項的畫面格的項目](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定資料的第一行向左移動的字元數。|
|[FirstLineIndent 組態 （格式） 的控制項的畫面格的項目](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定資料的第一行向右移位的字元數。|
|[LeftIndent 組態 （格式） 的控制項的畫面格的項目](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離左邊界的字元數。|
|[RightIndent 組態 （格式） 的控制項的畫面格的項目](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離右邊界的字元數。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[組態控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義控制項所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)在相同的項目`Frame`項目。

## <a name="see-also"></a>另請參閱

[FirstLineHanging 組態 （格式） 的控制項的畫面格的項目](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent 組態 （格式） 的控制項的畫面格的項目](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent 組態 （格式） 的控制項的畫面格的項目](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent 組態 （格式） 的控制項的畫面格的項目](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[組態控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
