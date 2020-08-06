---
title: GroupBy (格式的之 entryselectedby 的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e62762cf142bd2d20b21ad8f4249285bd3679280
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780259"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a>GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用自訂控制項定義的 .NET 類型。 此元素是在定義新物件群組的顯示方式時使用。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 元素（GroupBy (格式）) CustomEntries 專案（適用于 CustomEntry 的 groupby (格式) CustomControl 專案 (格式) 之 entryselectedby 元素用於 groupby (格式的 CustomEntry) TypeName 元素 (

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
|[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。

如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[建立自訂控制項](./creating-custom-controls.md)

[GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
