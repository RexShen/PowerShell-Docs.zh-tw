---
title: 針對 ListEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075506"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a>ListEntry 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用此定義清單檢視中顯示物件。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） ListControl 項目 （格式） ListEntries 項目 （格式） ListEntry 項目 （格式） EntrySelectedBy 項目用於 ListEntry （格式） SelectionCondition 元素EntrySelectedBy ListEntry （格式） 的 EntrySelectedBy 的 SelectionCondition ListEntry （格式） SelectionSetName 元素

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`SelectionSetName`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義要使用此清單檢視的定義必須存在的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。 如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。

清單檢視的其他元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[ListEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
