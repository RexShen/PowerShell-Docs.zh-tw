---
title: 適用于 CustomControl for View (格式) 的 CustomItem 的框架元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781438"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素，CustomEntries for CustomItem 的 CustomEntry 專案) 格式 (CustomControlView 專案) 格式 (CustomItem for CustomControl for View)  (格式的 CustomEntries 元素

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
|`CustomItem Element`|必要元素|
|[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行資料向左移動的字元數。|
|[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界下移的字元數。|
|[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CustomEntry for View (格式的 CustomItem 元素) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[FirstLineHanging 元素](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 元素](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent 元素](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 元素](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomEntry for View (格式的 CustomItem 元素) ](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
