---
title: GroupBy 之 CustomControl 的 CustomEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364057"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)

提供控制項的定義。 此元素是在定義新物件群組的顯示方式時使用。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） GroupBy 元素（format） CustomEntries 專案的 groupby （format） CustomControl 元素，適用于的 CustomControl for GroupBy （format） CustomEntry 元素GroupBy 的 CustomControl （格式）

## <a name="syntax"></a>語法

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `CustomEntry` 元素的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-groupby-format.md)|選擇性元素。<br /><br /> 定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|
|[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)|必要元素。<br /><br /> 定義控制項顯示資料的方式。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[GroupBy 之 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy 之 CustomEntry 的 CustomItem 元素（格式）](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy 之 CustomControl 的 CustomEntries 元素（格式）](./customentries-element-for-customcontrol-for-groupby-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
