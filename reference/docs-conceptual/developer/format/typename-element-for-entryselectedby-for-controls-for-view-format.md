---
title: 控制項的之 entryselectedby 的 TypeName 元素，用於 View (Format) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6eaa4f80a18c91ca351657fd40a8cac6f688c22f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783325"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a>檢視之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此控制項定義的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

Configuration 專案 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) 控制項專案 (格式控制項的) 控制項專案 CustomControl 格式 CustomEntries 的控制項 (格式控制項) CustomControl 元素 CustomEntry 的控制項視圖 (格式) CustomEntries 元素之 entryselectedby 的控制項 (格式) 的專案的專案

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
|[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[檢視之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
