---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)
description: 檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 72bb88bccc2bbd62f7ed160b820cf9169cb69341
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645743"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用自訂控制項視圖之定義的 .NET 類型。 可以針對定義指定的類型數目沒有任何限制。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (format) CustomControl 專案 (格式) CustomEntries 專案 (格式) 元素 (格式) CustomEntry 專案 (格式) CustomEntries 專案之 entryselectedby for view (格式) CustomEntry 元素

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 CustomEntry 的之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此自訂控制項視圖定義或必須存在的條件，以使用此定義的 .NET 類型。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個自訂控制項視圖定義都必須定義至少一個類型名稱、選取集或選取條件。

如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[建立自訂控制項](./creating-custom-controls.md)

[適用于 CustomEntry 的之 entryselectedby 元素 (格式) ](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
