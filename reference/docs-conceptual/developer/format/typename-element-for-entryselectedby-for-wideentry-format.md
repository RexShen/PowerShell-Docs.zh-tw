---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 2e0facd6ff7c6fec96dabf488449a8502429bcff
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654785"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>WideEntry 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定定義的 .NET 類型。 只要顯示這個物件，就會使用定義。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式)  (格式) 格式的 WideEntry 元素

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節說明屬性、子專案和元素的父元素 `TypeName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)|定義使用此寬專案的 .NET 型別，或必須存在才能使用此專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

每個寬專案都必須指定一或多個 .NET 類型、選取集或必須存在的選取條件，才能使用定義。

如需更多有關廣泛視圖的元件的詳細資訊，請參閱 [建立廣泛的觀點](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[WideEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-wideentry-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
