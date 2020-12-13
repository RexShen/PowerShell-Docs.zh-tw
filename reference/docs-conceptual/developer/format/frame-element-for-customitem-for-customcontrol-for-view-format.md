---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomItem 的框架元素 (格式)
description: 檢視之 CustomControl 的 CustomItem 的框架元素 (格式)
ms.openlocfilehash: 1ffe071bb6c4f590e4c79803a3faff2108c7b636
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652187"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的框架元素 (格式)

定義顯示資料的方式，例如將資料向左或向右移動。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 元素 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案 CustomItem for CustomEntry 的 CustomControlView 專案 (格式) CustomItem for CustomControl 的專案格式

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

下列各節說明屬性、子專案和元素的父元素 `Frame` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`CustomItem Element`|Required 元素|
|[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定將第一行資料向左移動的字元數。|
|[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界向外移動的字元數。|
|[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 CustomEntry 的 CustomItem 元素 (格式) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義控制項顯示的資料以及其顯示方式。|

## <a name="remarks"></a>備註

您無法在相同的元素中指定 [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 和 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[適用于 CustomEntry 的 CustomItem 元素 (格式) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
