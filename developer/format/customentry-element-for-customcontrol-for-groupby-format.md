---
title: GroupBy （格式） 的 CustomControl CustomEntry 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860364"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)

提供控制項的定義。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素GroupBy （格式） 的 CustomControl

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目，以及的父項目`CustomEntry`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-groupby-format.md)|選擇性的項目。<br /><br /> 定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。|
|[GroupBy （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-groupby-format.md)|必要項目。<br /><br /> 定義控制項顯示資料的方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy （格式） 的 CustomControl CustomEntries 項目](./customentries-element-for-customcontrol-for-groupby-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy （格式） 的 CustomEntry CustomItem 項目](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy （格式） 的 CustomControl CustomEntries 項目](./customentries-element-for-customcontrol-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
