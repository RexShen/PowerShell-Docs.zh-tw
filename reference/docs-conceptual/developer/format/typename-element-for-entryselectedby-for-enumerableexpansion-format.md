---
title: EnumerableExpansion 之之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0506928-db92-4ec4-855f-6f3592a383ae
caps.latest.revision: 6
ms.openlocfilehash: 5ead806d956ebbef95eeffc42bb39ef784208017
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361747"
---
# <a name="typename-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 TypeName 元素 (格式)

指定由這個定義擴充的 .NET 類型。 定義預設設定時，會使用這個元素。

Configuration 元素（格式） DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素，用於 EnumerableExpansion 的之 entryselectedby （格式） TypeName 元素EnumerableExpansion （格式）

## <a name="syntax"></a>語法

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `TypeName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)|定義使用此定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[EnumerableExpansion 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
