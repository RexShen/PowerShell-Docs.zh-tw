---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
description: EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647919"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在才能展開這個定義之集合物件的條件。

設定元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 專案 (格式) EnumerableExpansion 元素 (格式) 之 entryselectedby 專案的 EnumerableExpansion (格式) SelectionCondition 專案之 entryselectedby 的 EnumerableExpansion (格式) 

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `SelectionCondition` 。 您必須指定單一 `PropertyName` 或 `ScriptBlock` 元素。 `SelectionSetName`和 `TypeName` 元素是選擇性的。 您可以指定其中一個元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 指定一組觸發條件的 .NET 類型。|
|[EnumerableExpansion 之 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 (格式)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 型別。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion 的 EntrySelectedBy 元素 (格式)](./entryselectedby-element-for-enumerableexpansion-format.md)|定義由這個定義擴充的 .NET 集合物件。|

## <a name="remarks"></a>備註

每個定義都必須定義至少一個型別名稱、選取集或選取條件。

當您定義選取條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選取集，但不能同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱 [定義 Diplaying 資料的條件](./defining-conditions-for-displaying-data.md)。

如需廣泛視圖的其他元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
