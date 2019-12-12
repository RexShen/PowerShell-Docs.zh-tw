---
title: CustomControl for View 的 CustomEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368777"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，適用于 CustomEntry for View 的 CustomControl for View （format） CustomEntries 元素（格式）之 entryselectedbyView 的 CustomEntry 元素（格式）

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `EntrySelectedBy` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此定義的條件。|
|[CustomEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定一組使用此控制項視圖定義的 .NET 類型。|
|[CustomEntry 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定使用此控制項視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomEntries for View 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|定義特定 .NET 物件所使用的控制項。|

## <a name="remarks"></a>備註

您必須為專案指定至少一種類型、選擇集或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義必須存在才能使用之專案的條件，例如當物件具有特定屬性時，或特定屬性值或腳本評估為 `true`時。 如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。

如需自訂控制項視圖之元件的詳細資訊，請參閱[自訂控制項視圖](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[CustomEntry 之之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry 之之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[CustomEntry 之之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntries for View 的 CustomEntry 元素（格式）](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[自訂控制項視圖](./creating-custom-controls.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
