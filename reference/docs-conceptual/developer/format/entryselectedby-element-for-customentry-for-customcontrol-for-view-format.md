---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)
description: 檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)
ms.openlocfilehash: 4821f22560f35034f90d018e5a109004f331441f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655350"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用此自訂專案的 .NET 型別，或必須存在才能使用此專案的條件。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomEntries 專案 (格式) 專案 (格式) CustomEntry 專案 (格式) CustomEntries 專案格式之 entryselectedby 元素

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `EntrySelectedBy` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[適用于之 entryselectedby 的 CustomEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用這個定義。|
|[適用于之 entryselectedby 的 CustomEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定一組使用此控制項的定義的 .NET 類型。|
|[適用于 CustomEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定使用此控制項視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于 CustomEntries 的 CustomEntry 元素 (格式) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|定義特定 .NET 物件所使用的控制項。|

## <a name="remarks"></a>備註

您必須為專案指定至少一個類型、選取集或選取條件。 您可以使用的子項目數目沒有最大限制。

選取條件是用來定義必須存在的條件，才能使用專案，例如當物件有特定屬性，或當特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

如需自訂控制項視圖元件的詳細資訊，請參閱 [自訂控制項視圖](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[適用于之 entryselectedby 的 CustomEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[適用于之 entryselectedby 的 CustomEntry (格式的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[適用于 CustomEntry 的之 entryselectedby 的 TypeName 元素 (格式) ](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[適用于 CustomEntries 的 CustomEntry 元素 (格式) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[自訂控制項視圖](./creating-custom-controls.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
