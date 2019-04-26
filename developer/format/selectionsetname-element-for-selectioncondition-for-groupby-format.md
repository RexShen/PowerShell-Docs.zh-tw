---
title: GroupBy （格式） 的 SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063756"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)

指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用這個控制項顯示物件。 定義新的群組物件的顯示方式時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） GroupBy 項目檢視 （格式） CustomControl 項目，用於 GroupBy （格式） CustomEntry 元素 CustomControl 的 GroupBy （格式） CustomEntries 元素CustomControl CustomEntry EntrySelectedBy SelectionCondition 的 GroupBy （格式） 的 GroupBy （格式） SelectionSetName 元素的 GroupBy （格式） SelectionCondition 元素的 GroupBy （格式） EntrySelectedBy 元素

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
|[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|定義必須存在，要使用的控制項定義的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。 如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義的選取項目設定](./defining-selection-sets.md)。

當指定這個項目時，您無法指定[TypeName](./typename-element-for-selectioncondition-for-groupby-format.md)項目。 如需定義選擇條件的詳細資訊，請參閱 <<c0> [ 定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[GroupBy （格式） 的 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍](./defining-selection-sets.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
