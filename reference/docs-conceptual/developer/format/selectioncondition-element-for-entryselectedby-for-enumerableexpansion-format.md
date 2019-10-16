---
title: EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362007"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能展開這個定義的集合物件。

EnumerableExpansion 的 SelectionCondition （Format）之 entryselectedby 元素的 DefaultSettings 元素（格式） EnumerableExpansions 元素（格式） EnumerableExpansion 元素（格式）之 entryselectedby 元素EnumerableExpansion （格式）

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionCondition` 元素的父元素。 您必須指定單一 `PropertyName` 或 @no__t 1 元素。 @No__t-0 和 @no__t 1 元素是選擇性的。 您可以指定其中一個元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 指定觸發條件的腳本。|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[EnumerableExpansion 之之 entryselectedby 的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性元素。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-enumerableexpansion-format.md)|定義由這個定義擴充的 .NET 集合物件。|

## <a name="remarks"></a>備註

每個定義都必須定義至少一個型別名稱、選擇集或選取條件。

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義 Diplaying 資料的條件](./defining-conditions-for-displaying-data.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
