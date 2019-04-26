---
title: SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064007"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>設定之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用這個控制項顯示物件。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） CustomControl 項目控制項的 CustomControl 的組態 （格式） CustomEntries 項目控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目控制項的 EntrySelectedBy 的組態 （格式） SelectionCondition 項目控制項的 CustomEntry 的組態 （格式） EntrySelectedBy 項目控制項的 CustomControl 的組態 （格式） CustomEntry 項目SelectionCondition 控制項組態 （格式） 的組態 （格式） SelectionSetName 項目

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
|[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|定義必須存在，要使用的控制項定義的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。 如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。

選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍](./defining-selection-sets.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
