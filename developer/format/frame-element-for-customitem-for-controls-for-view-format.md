---
title: 針對 CustomItem 框架項目控制項的檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859814"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry 如 CustomItem 用於檢視 （格式） 的控制項的檢視 （格式） 框架項目控制項的檢視 （格式） CustomItem 元素的控制項的檢視 （格式） CustomEntry 元素

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
|[控制項的檢視 （格式） 的框架 FirstLineHanging 項目](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定的第一行向左移動的字元數。|
|[控制項的檢視 （格式） 的框架 FirstLineIndent 項目](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定的第一行向右移位的字元數。|
|[控制項的檢視 （格式） 的框架 LeftIndent 項目](./leftindent-element-for-frame-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離左邊界的字元數。|
|[控制項的檢視 （格式） 的框架 RightIndent 項目](./rightindent-element-for-frame-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離右邊界的字元數。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)在相同的項目`Frame`項目。

## <a name="see-also"></a>另請參閱

[控制項的檢視 （格式） 的框架 FirstLineHanging 項目](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[控制項的檢視 （格式） 的框架 FirstLineIndent 項目](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[控制項的檢視 （格式） 的框架 LeftIndent 項目](./leftindent-element-for-frame-for-controls-for-view-format.md)

[控制項的檢視 （格式） 的框架 RightIndent 項目](./rightindent-element-for-frame-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
