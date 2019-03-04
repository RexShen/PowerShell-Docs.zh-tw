---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition SelectionSetName 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863274"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>TableControl 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)

指定的觸發條件的.NET 型別集。 當有任何在這組型別時，符合條件，並使用此定義的資料表檢視中顯示物件。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） TableControl 項目 （格式） TableRowEntries 項目 （格式） TableRowEntry 項目 （格式） EntrySelectedBy 項目 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） SelectionSetName 元素的項目

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
|[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定義要用於此 [資料表] 檢視的定義必須存在的條件。|

## <a name="text-value"></a>文字值

指定選取項目集的名稱。

## <a name="remarks"></a>備註

選取條件可以指定的選取項目集或.NET 類型，但不能同時指定。 如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

選取項目集是常見的.NET 物件，可供任何檢視中定義的格式化檔案群組。 如需有關建立及參考選取項目集的詳細資訊，請參閱 <<c0> [ 定義設定的物件](./defining-selection-sets.md)。

寬型檢視的其他元件的相關資訊，請參閱[建立資料表檢視](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立資料表檢視](./creating-a-table-view.md)

[定義何時顯示資料的條件](./defining-conditions-for-displaying-data.md)

[針對 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 項目](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
