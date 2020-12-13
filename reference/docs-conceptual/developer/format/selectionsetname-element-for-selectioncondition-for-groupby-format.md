---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)
description: GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)
ms.openlocfilehash: a4f28c1caba3790718b99f63659cb0cbed8def16
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654998"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>GroupBy 之 SelectionCondition 的 SelectionSetName 元素 (格式)

指定一組觸發條件的 .NET 類型。 當這個集合中的任何型別存在時，就會符合條件，並使用此控制項來顯示該物件。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy 專案的視圖 (格式) CustomEntries 元素用於 GroupBy (格式) 元素用於 CustomEntry 的 groupby (格式) CustomControl 專案用於之 entryselectedby 的 groupby (格式) CustomEntry 專案的 SelectionCondition 的 groupby (格式) 之 entryselectedby 元素

## <a name="syntax"></a>語法

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionSetName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|定義必須存在才能使用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定選項群組的名稱。

## <a name="remarks"></a>備註

選項群組是一組通用的 .NET 物件，可供格式化檔案所定義的任何視圖使用。 如需有關建立和參考選取集的詳細資訊，請參閱 [定義選取集](./defining-selection-sets.md)。

當指定這個專案時，您無法指定 [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) 元素。 如需定義選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[GroupBy 之 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-groupby-format.md)

[GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[定義選取範圍集合](./defining-selection-sets.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
