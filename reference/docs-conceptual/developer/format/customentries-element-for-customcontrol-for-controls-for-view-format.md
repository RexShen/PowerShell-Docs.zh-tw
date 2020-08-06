---
title: View (Format) 的控制項之 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a52bd2368044c34a0b73da331785d55597e30260
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783699"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>檢視之控制項的 CustomControl 的 CustomEntries 元素 (格式)

提供控制項的定義。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 (CustomEntries 元素用於視圖) 格式的控制項 (的專案

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
|[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)|必要元素。<br /><br /> 提供控制項的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)|定義視圖所使用的控制項。|

## <a name="remarks"></a>備註

在大部分情況下，控制項只有一個定義，在單一元素中指定 `CustomEntry` 。 不過，如果您想要使用相同的控制項來顯示不同的 .NET 物件，就可以提供多個定義。 在這些情況下，您可以定義 `CustomEntry` 每個物件或一組物件的元素。

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[檢視之控制項的控制項 CustomControl 元素 (格式)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
