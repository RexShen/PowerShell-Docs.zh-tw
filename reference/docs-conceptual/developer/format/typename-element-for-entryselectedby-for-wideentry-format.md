---
title: 之 entryselectedby for WideEntry (格式的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9af443067467f590df824b28636f57b807a4fc94
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780180"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定定義的 .NET 類型。 每當顯示此物件時，就會使用此定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 專案 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素用於 WideEntry (格式的) TypeName 元素 (

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
|[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)|定義使用此寬專案的 .NET 類型，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個寬型別都必須指定一個或多個 .NET 類型、一個選取集，或必須存在才能使用定義的選取條件。

如需有關寬視圖之其他元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
