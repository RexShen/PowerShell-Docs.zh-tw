---
title: View 之控制項的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363647"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>檢視之控制項的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） Frame 元素 for view （格式）之控制項的 CustomEntry

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
|[View 控制項框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 指定第一行向左移動的字元數。|
|[View 控制項框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 指定第一行向右移動的字元數。|
|[View 控制項框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 指定資料從左邊界下移的字元數。|
|[View 控制項框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-view-format.md)|選擇性元素。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[View 控制項框架的 FirstLineHanging 元素（格式）](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[View 控制項框架的 FirstLineIndent 元素（格式）](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[View 控制項框架的 LeftIndent 元素（格式）](./leftindent-element-for-frame-for-controls-for-view-format.md)

[View 控制項框架的 RightIndent 元素（格式）](./rightindent-element-for-frame-for-controls-for-view-format.md)

[View 之控制項的 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
