---
title: View (格式) 的 CustomControl 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 660e8fd6531862790a2af7ab27a82e073c230693
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786045"
---
# <a name="customcontrol-element-for-view-format"></a>檢視的 CustomControl 元素 (格式)

定義視圖的自訂控制項格式。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 元素 (格式) 

## <a name="syntax"></a>語法

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `CustomControl` 。 您必須指定一個子項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)|必要元素。<br /><br /> 提供自訂控制項視圖的定義。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[檢視元素 (格式)](./view-element-format.md)|定義用來顯示一個或多個 .NET 物件的視圖。|

## <a name="remarks"></a>備註

在大部分情況下，每個控制項視圖只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可以提供多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

## <a name="see-also"></a>另請參閱

[檢視之 CustomControl 的 CustomEntries 元素 (格式)](./customentries-element-for-customcontrol-for-view-format.md)

[檢視元素 (格式)](./view-element-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
