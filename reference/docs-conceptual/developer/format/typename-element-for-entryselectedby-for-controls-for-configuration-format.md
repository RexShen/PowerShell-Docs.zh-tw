---
title: 設定 (格式) 之控制項的之 entryselectedby 的 TypeName 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 994cd368872392abe47b4e9422c661cd8c03e05c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783342"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用此控制項定義的 .NET 類型。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 專案 (格式) Controls 設定的控制項元素 (格式設定的控制項) 控制項專案 (格式) 設定 (格式的 CustomControl 的 CustomControl 元素 CustomControl 的設定)  (格式) 之 entryselectedby 元素 ()  ()  (格式設定的控制項的 CustomEntry 專案的之 entryselectedby for configuration) 的 TypeName 元素

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
|[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
