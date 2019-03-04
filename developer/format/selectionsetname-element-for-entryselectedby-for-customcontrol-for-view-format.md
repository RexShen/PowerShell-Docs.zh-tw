---
title: CustomControl 檢視 （格式） 的 EntrySelectedBy SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855024"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組.NET 物件清單項目。 可供指定的項目選取項目集的數目沒有限制。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） CustomControl 項目 （格式） CustomEntries 項目 CustomControl 檢視 （格式） 的檢視 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry EntrySelectedBy CustomEntry （格式） 的檢視 （格式） SelectionSetName 元素的項目

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|定義.NET 型別，使用此自訂的項目或要使用此項目必須存在的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

每個自訂控制項項目必須至少一個型別名稱、 選取項目集或選擇條件的定義。

您想要在多個檢視中定義一組所使用的物件時，會通常會使用選取項目集。 例如，您可能要建立的資料表檢視和相同的物件集的清單檢視。 如需定義選取項目集的詳細資訊，請參閱[定義的選取項目設定](./defining-selection-sets.md)。

如需詳細的自訂控制項的檢視元件的相關資訊，請參閱[建立自訂控制項](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[EntrySelectedBy CustomEntry 檢視 （格式） 的項目](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[自訂的控制項檢視](./creating-custom-controls.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
