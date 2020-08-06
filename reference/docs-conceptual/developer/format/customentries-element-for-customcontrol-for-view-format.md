---
title: CustomControl for View (格式) 的 CustomEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c89eb25f6922a92e2c18298d0128c4c2ca93df3d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785960"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntries 元素 (格式)

提供自訂控制項視圖的定義。 自訂控制項視圖必須指定一或多個定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomControl 元素 (format) CustomEntries 元素 for View (Format) 

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomControlEntries` 。 您必須指定一或多個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntries for View (格式的 CustomEntry 元素) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|必要元素。<br /><br /> 提供自訂控制項視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視的 CustomControl 元素 (格式)](./customcontrol-element-for-view-format.md)|必要元素。<br /><br /> 定義視圖的自訂控制項格式。|

## <a name="remarks"></a>備註

在大部分情況下，控制項只有一個定義，定義在單一 `CustomEntry` 元素中。 不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以定義 `CustomEntry` 每個物件或一組物件的元素。

## <a name="see-also"></a>另請參閱

[檢視的 CustomControl 元素 (格式)](./customcontrol-element-for-view-format.md)

[CustomEntries for View (格式的 CustomEntry 元素) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
