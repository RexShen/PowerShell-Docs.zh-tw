---
title: 設定之控制項的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363657"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>設定之控制項的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的 CustomItem 元素，用於 CustomEntry 的設定框架元素的控制項（格式）

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

下列各節說明屬性、子專案，以及 `Frame` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|必要元素|
|[設定之控制項的框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|選擇性元素。<br /><br /> 指定第一行資料向左移動的字元數。|
|[設定之控制項的框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性元素。<br /><br /> 指定第一行資料向右移動的字元數。|
|[設定之控制項的框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性元素。<br /><br /> 指定資料從左邊界下移的字元數。|
|[設定之控制項的框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|選擇性元素。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)元素。

## <a name="see-also"></a>另請參閱

[設定之控制項的框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[設定之控制項的 CustomEntry 的 CustomItem 元素](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
