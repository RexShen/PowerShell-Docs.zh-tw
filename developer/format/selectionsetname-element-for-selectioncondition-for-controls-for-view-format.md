---
title: 用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063882"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>檢視之控制項的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定的觸發條件的.NET 型別集。 當有任何在這組型別時，即符合此條件，並使用這個控制項來顯示物件。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry EntrySelectedBy 的檢視 （控制項的檢視 （格式） SelectionCondition 元素的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項用於檢視 （格式） 的控制項 SelectionCondition 的格式） SelectionSetName 項目

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
|[用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|定義必須存在，要使用的控制項定義的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。 如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義的選取項目設定](./defining-selection-sets.md)。

選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義的條件，顯示資料](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍](./defining-selection-sets.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
