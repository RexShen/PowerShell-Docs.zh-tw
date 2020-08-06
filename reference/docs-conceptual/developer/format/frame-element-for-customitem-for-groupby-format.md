---
title: GroupBy (格式) 的 CustomItem 框架元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1568236ff7b6142f7e41be70a3ae5e28307cf790
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785756"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>GroupBy 之 CustomItem 的框架元素 (格式)

定義資料的顯示方式，例如將資料向左或向右移位。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式)  (CustomControl 元素，CustomItem 的 groupby) 格式 (CustomEntry 元素) 的專案。

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
|[GroupBy 之框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-groupby-format.md)|選擇性項目。<br /><br /> 指定第一行資料向左移動的字元數。|
|[GroupBy 之框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-groupby-format.md)|選擇性項目。<br /><br /> 指定第一行資料向右移動的字元數。|
|[GroupBy 之框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-groupby-format.md)|選擇性項目。<br /><br /> 指定資料從左邊界下移的字元數。|
|[GroupBy (格式之框架的 RightIndent 元素) ](./rightindent-element-for-frame-for-groupby-format.md)RightIndent 元素|選擇性項目。<br /><br /> 指定資料從右邊界向外移動的字元數。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)|定義控制項所顯示的資料及其顯示方式。|

## <a name="remarks"></a>備註

您不能在相同的專案中指定[FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md)和[FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md)元素 `Frame` 。

## <a name="see-also"></a>另請參閱

[GroupBy 之框架的 FirstLineHanging 元素 (格式)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 FirstLineIndent 元素 (格式)](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 LeftIndent 元素 (格式)](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy 之框架的 RightIndent 元素 (格式)](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素 (格式)](./customitem-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
