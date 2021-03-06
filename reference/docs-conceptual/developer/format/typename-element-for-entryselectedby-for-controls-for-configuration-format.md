---
ms.date: 09/13/2016
ms.topic: reference
title: 設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)
description: 設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: ce74c23ca35597902c6b94fdccd44324ba8e0233
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667737"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此控制項定義的 .NET 類型。 當定義可供格式化檔案中所有視圖使用的通用控制項時，會使用這個元素。

設定專案 (格式) 控制項設定的控制項專案 (格式設定的控制項) 控制項專案 (格式) CustomEntries 專案的 CustomControl 設定 (格式) 的格式 (格式) 的格式 (格式)  (格式控制項的控制項) 格式 (的控制項的 CustomControl 的控制項) 格式

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
|[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
