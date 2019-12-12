---
title: CustomControl for View 的 CustomItem 的框架元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363637"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomItem for CustomControl for View 的 CustomEntry for CustomControlView （格式）框架元素（格式）

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

下列各節說明屬性、子專案，以及 `Frame` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|必要元素|
|[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行資料向左移動的字元數。|
|[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界下移的字元數。|
|[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry for View 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的 `Frame` 元素中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomEntry for View 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
