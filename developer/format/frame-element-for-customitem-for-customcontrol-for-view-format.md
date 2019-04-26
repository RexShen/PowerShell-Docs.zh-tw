---
title: 畫面格元素 CustomItem CustomControl 的檢視 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065575"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義自訂控制項的檢視時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 用於檢視 （格式） CustomItem 元素的檢視 （格式） CustomEntry 元素CustomEntry CustomControl 檢視 （格式） 的 CustomItem CustomControlView （格式） 框架元素

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

下列各節說明屬性、 子項目和父項目`Frame`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|必要項目|
|[FirstLineHanging 項目](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定資料的第一行向左移動的字元數。|
|[FirstLineIndent 項目](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定資料的第一行向右移位的字元數。|
|[LeftIndent 項目](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離左邊界的字元數。|
|[RightIndent 項目](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離右邊界的字元數。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[CustomItem CustomEntry 檢視 （格式） 的項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義控制項所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)在相同的項目`Frame`項目。

## <a name="see-also"></a>另請參閱

[FirstLineHanging 項目](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 項目](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent 項目](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 項目](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem CustomEntry 檢視 （格式） 的項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
