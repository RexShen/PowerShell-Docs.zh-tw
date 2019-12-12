---
title: CustomEntry for View 的之 entryselectedby 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368067"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>檢視之 CustomEntry 的 EntrySelectedBy 的 TypeName 元素 (格式)

指定使用自訂控制項視圖之定義的 .NET 類型。 可以針對定義指定的類型數目沒有限制。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，適用于 CustomEntry for View 的 CustomControl for View （format） CustomEntries 元素（格式）之 entryselectedbyCustomEntry for View （Format） TypeName 元素的元素，用於 CustomEntry for View 的之 entryselectedby （格式）

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
|[CustomEntry for View 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義使用此自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定 .NET 類型的完整名稱，例如 `System.IO.DirectoryInfo`。

## <a name="remarks"></a>備註

每個自訂控制項視圖定義都必須定義至少一個型別名稱、選擇集或選取條件。

如需自訂控制項視圖之元件的詳細資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[建立自訂控制項](./creating-custom-controls.md)

[CustomEntry for View 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
