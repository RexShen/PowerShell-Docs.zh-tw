---
title: CustomControl 檢視 （格式） 的 CustomEntries CustomEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861814"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntries 的 CustomEntry 元素 (格式)

提供自訂的控制項檢視的定義。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl CustomEntries 檢視 （格式） 的檢視 （格式） CustomEntry 元素

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`CustomEntry`項目。 您必須指定定義所顯示的項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|選擇性的項目。<br /><br /> 定義使用自訂的控制項檢視或必須存在於要使用此定義條件的定義的.NET 類型。|
|[CustomItem CustomEntry 檢視 （格式） 的項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|定義自訂控制項定義的控制項。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomEntries CustomControl 檢視 （格式） 的項目](./customentries-element-for-customcontrol-for-view-format.md)|提供自訂的控制項檢視的定義。 自訂控制項的檢視必須指定一個或多個定義。|

## <a name="remarks"></a>備註

在大部分情況下，只有一個定義需要為每個自訂的控制項檢視中，但可以有多個定義，如果您想要使用相同的檢視來顯示不同的.NET 物件。 在這些情況下，您可以針對每個物件或一組物件提供不同的定義。

## <a name="see-also"></a>另請參閱

[CustomControl 檢視 （格式） 的項目](./customcontrol-element-for-view-format.md)

[CustomItem CustomEntry 檢視 （格式） 的項目](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
