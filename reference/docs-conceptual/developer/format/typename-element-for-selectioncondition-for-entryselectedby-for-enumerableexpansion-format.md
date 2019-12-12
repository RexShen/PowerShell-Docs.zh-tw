---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9100ab7-fbdc-4c0d-bb56-57669ef42b95
caps.latest.revision: 9
ms.openlocfilehash: 316e54d11647aedc1552a0bb74b943de7e4e3588
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361577"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)

指定觸發條件的 .NET 類型。

Configuration 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansions 專案（格式）之 entryselectedby 元素（用於 EnumerableExpansion 的 SelectionCondition 專案）之 entryselectedby 元素EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 EnumerableExpansion （格式） TypeName 元素（格式）

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
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|定義必須存在的條件，才能展開這個定義的集合物件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
