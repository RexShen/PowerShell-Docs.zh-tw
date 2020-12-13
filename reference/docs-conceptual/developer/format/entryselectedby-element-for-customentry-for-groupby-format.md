---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652360"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>GroupBy 之 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用此控制項定義的 .NET 型別，或必須存在才能使用此定義的條件。 定義如何顯示新的物件群組時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) GroupBy (格式) CustomEntries 元素，用於 CustomEntry 的 groupby (格式) CustomControl 專案用於之 entryselectedby 的 groupby (格式) 的 CustomEntry 元素 (

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述專案的屬性、子項目和父元素 `EntrySelectedBy` 。 您必須為定義指定至少一個類型、選取集或選取條件。 您可以使用的子項目數目沒有最大限制。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用這個定義。|
|[GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|選擇性項目。<br /><br /> 指定一組使用此控制項定義的 .NET 類型。|
|[GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-groupby-format.md)|選擇性項目。<br /><br /> 指定使用此控制項定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[GroupBy 之 CustomControl 的 CustomEntry 元素 (格式)](./customentry-element-for-customcontrol-for-groupby-format.md)|提供控制項的定義。|

## <a name="remarks"></a>備註

選取條件是用來定義必須存在才能使用定義的條件，例如當物件有特定屬性，或當特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[GroupBy 之 EntrySelectedBy 的 SelectionCondition 元素 (格式)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[GroupBy 之 EntrySelectedBy 的 SelectionSetName 元素 (格式)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[GroupBy 之 EntrySelectedBy 的 TypeName 元素 (格式)](./typename-element-for-entryselectedby-for-groupby-format.md)

[檢視之控制項的 CustomEntries 的 CustomEntry 元素 (格式)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
