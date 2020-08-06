---
title: 適用于 CustomControl 之 GroupBy (格式的 CustomEntries 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785943"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a>GroupBy 之 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 GroupBy (格式的 CustomControl）) 

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述元素的屬性、子專案和父項目 `CustomEntries` 。 可以指定的子項目數目沒有上限。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-groupby-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 的 CustomControl 元素 (格式)](./customcontrol-element-for-groupby-format.md)|定義顯示新群組的自訂控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項只有一個定義，在單一元素中指定 `CustomEntry` 。 不過，如果您想要使用相同的控制項來顯示不同的群組，也可以提供多個定義。 在這些情況下，您可以定義 `CustomEntry` 群組的元素。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[GroupBy 的 CustomControl 元素 (格式)](./customcontrol-element-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
