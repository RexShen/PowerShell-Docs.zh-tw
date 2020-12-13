---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)
description: 檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)
ms.openlocfilehash: 43187294a407d08f765f8c42aba25d13dba6d901
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652382"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 當定義可供視圖使用的控制項時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 專案 (格式) 控制項專案 (格式) 控制項專案 (格式) CustomEntries 元素，用於視圖 (格式的控制項 CustomControl 元素) 

## <a name="syntax"></a>語法

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `CustomEntries` 。 可指定的子專案數目沒有最大限制。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)|定義視圖所使用的控制項。|

## <a name="remarks"></a>備註

在大部分的情況下，控制項只會在單一元素中指定一個定義 `CustomEntry` 。 但是，如果您想要使用相同的控制項來顯示不同的 .NET 物件，就可以提供多個定義。 在這些情況下，您可以 `CustomEntry` 為每個物件或一組物件定義一個元素。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
