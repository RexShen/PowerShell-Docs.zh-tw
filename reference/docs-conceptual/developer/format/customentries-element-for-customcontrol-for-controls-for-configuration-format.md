---
title: CustomControl 之控制項的 CustomEntries 元素，用於設定 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b1f494cf1a254d71362830ba9eb0f4905a2a484d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785977"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供通用控制項的定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl CustomEntries 元素) 

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomEntries` 。 您必須指定一或多個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CustomControl 元素，用於控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|定義通用控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項只有一個定義，定義在單一 `CustomEntry` 元素中。 不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以定義 `CustomEntry` 每個物件或一組物件的元素。

## <a name="see-also"></a>另請參閱

[CustomControl 元素，用於控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
