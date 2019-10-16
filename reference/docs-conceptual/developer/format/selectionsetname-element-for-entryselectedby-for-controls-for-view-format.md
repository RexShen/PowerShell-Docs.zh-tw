---
title: View 之控制項的之 entryselectedby 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368347"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a>檢視之控制項的 EntrySelectedBy 的 SelectionSetName 元素 (格式)

指定一組使用此控制項定義的 .NET 類型。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素的 CustomEntries for view （format）之 entryselectedby 元素 for CustomEntry for view （format） SelectionSetName 元素 for controls 的控制項（格式）編排

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionSetName` 元素的父元素。

### <a name="attributes"></a>屬性

無

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定義使用此控制項定義的 .NET 類型，或必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定選取範圍的名稱。

## <a name="remarks"></a>備註

每個控制項定義都必須定義至少一個型別名稱、選擇集或選取條件。

當您想要定義多個視圖中使用的一組物件時，通常會使用選取範圍集。 如需定義選取集的詳細資訊，請參閱[定義選取範圍集合](./defining-selection-sets.md)。

## <a name="see-also"></a>另請參閱

[View 之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
