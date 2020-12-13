---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)
ms.openlocfilehash: 7c1195717ae0963ace3e02f0ae2ae7c34f69078a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654816"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定由這個定義擴充的 .NET 型別。 定義預設設定時，會使用這個元素。

設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案 (格式) EnumerableExpansion 的之 entryselectedby (的 TypeName 元素) 格式

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
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|定義使用此定義的 .NET 類型或必須存在的條件，才能使用這個定義。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo` 。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
