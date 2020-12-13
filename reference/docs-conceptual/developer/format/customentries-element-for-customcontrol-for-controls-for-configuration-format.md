---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)
description: 設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)
ms.openlocfilehash: 86c2b517d0d7075a355a3190a14e25d9dd4fe374
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655396"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>設定之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供通用控制項的定義。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定元素 (格式) 控制項的設定元素 (格式) 控制項的設定 (格式) CustomControl 元素，用於 CustomControl 的設定 (格式) 

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomEntries` 。 您必須指定一個或多個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CustomControl 元素，可控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|定義通用控制項。|

## <a name="remarks"></a>備註

在大部分的情況下，控制項只有一個定義，定義在單一專案中 `CustomEntry` 。 但是，如果您想要使用相同的控制項來顯示不同的 .NET 物件，則可以有多個定義。 在這些情況下，您可以 `CustomEntry` 為每個物件或一組物件定義一個元素。

## <a name="see-also"></a>另請參閱

[CustomControl 元素，可控制設定 (格式) ](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[設定之控制項的控制項 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
