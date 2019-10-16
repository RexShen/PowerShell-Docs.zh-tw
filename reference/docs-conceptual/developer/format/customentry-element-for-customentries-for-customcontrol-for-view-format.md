---
title: CustomControl for View 的 CustomEntries 的 CustomEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364017"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)

提供自訂控制項視圖的定義。

CustomEntry for view 的 CustomControl for View （Format） CustomEntries 元素的設定元素（格式） ViewDefinitions 元素（格式） CustomEntries 元素（格式）

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomEntry` 元素的父元素。 您必須指定定義所顯示的專案。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry for View 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|選擇性元素。<br /><br /> 定義使用自訂控制項視圖定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[CustomEntry for View 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義自訂控制項定義的控制項。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-view-format.md)|提供自訂控制項視圖的定義。 自訂控制項視圖必須指定一或多個定義。|

## <a name="remarks"></a>備註

在大部分的情況下，每個自訂控制項視圖都只需要一個定義，但是如果您想要使用相同的視圖來顯示不同的 .NET 物件，則可能會有多個定義。 在這些情況下，您可以為每個物件或一組物件提供個別的定義。

## <a name="see-also"></a>另請參閱

[View 的 CustomControl 元素（格式）](./customcontrol-element-for-view-format.md)

[CustomEntry for View 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[CustomEntry for View 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
