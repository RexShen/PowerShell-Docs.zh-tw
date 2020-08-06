---
title: 之 entryselectedby for EnumerableExpansion (格式的 TypeName 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670aeb0986b07c8b7834a9f4f9510f1757a62186
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785076"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定由這個定義擴充的 .NET 類型。 定義預設設定時，會使用這個元素。

Configuration 元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 專案 (格式) EnumerableExpansion 的之 entryselectedby (TypeName 元素 EnumerableExpansion) 格式 (

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
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
