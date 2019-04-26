---
title: 框架 CustomItem GroupBy （格式） 的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065592"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料轉移至左邊或右邊。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry CustomItem 的 GroupBy （格式） 的 GroupBy （格式） 框架元素的 GroupBy （格式） CustomItem 元素

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
|[GroupBy （格式） 的畫面格 FirstLineHanging 項目](./firstlinehanging-element-for-frame-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定資料的第一行向左移動的字元數。|
|[GroupBy （格式） 的畫面格 FirstLineIndent 項目](./firstlineindent-element-for-frame-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定資料的第一行向右移位的字元數。|
|[GroupBy （格式） 的畫面格 LeftIndent 項目](./leftindent-element-for-frame-for-groupby-format.md)|選擇性的項目。<br /><br /> 指定的資料會移離左邊界的字元數。|
|[GroupBy （格式） 的畫面格 RightIndent 元素](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 項目|選擇性的項目。<br /><br /> 指定的資料會移離右邊界的字元數。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-groupby-format.md)|定義控制項所顯示的資料和顯示方式。|

## <a name="remarks"></a>備註

您無法指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)並[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)在相同的項目`Frame`項目。

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的畫面格 FirstLineHanging 項目](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的畫面格 FirstLineIndent 項目](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的畫面格 LeftIndent 項目](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的畫面格 RightIndent 項目](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
