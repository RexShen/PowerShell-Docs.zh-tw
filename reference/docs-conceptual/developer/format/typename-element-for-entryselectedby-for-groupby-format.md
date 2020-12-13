---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 07cc92e9c501aa0eb2d219e416851be0fcd80f47
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645713"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此自訂控制項定義的 .NET 類型。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素適用于 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) 元素用於 CustomControl 的 groupby (格式)  (的之 entryselectedby 專案) 格式 (

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
|[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)|定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個控制項定義都必須定義至少一個類型名稱、選取集或選取條件。

如需自訂控制項視圖元件的詳細資訊，請參閱 [建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[建立自訂控制項](./creating-custom-controls.md)

[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
