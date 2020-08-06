---
title: CustomControl for View (格式) 的 CustomEntry 的之 entryselectedby 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4d4900cefb0d499397fc9dff7e037ce0a541f72f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783682"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用此自訂專案的 .NET 類型，或必須存在才能使用此專案的條件。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 專案 (格式) CustomControl for view (CustomEntry 元素（CustomEntries for view) 之 entryselectedby 元素的 CustomEntry for view (格式) 

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
|[CustomEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|選擇性項目。<br /><br /> 定義必須存在才能使用此定義的條件。|
|[CustomEntry (格式的之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定一組使用此控制項視圖定義的 .NET 類型。|
|[之 entryselectedby for CustomEntry (格式的 TypeName 元素) ](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|選擇性項目。<br /><br /> 指定使用此控制項視圖定義的 .NET 類型。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[CustomEntries for View (格式的 CustomEntry 元素) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|定義特定 .NET 物件所使用的控制項。|

## <a name="remarks"></a>備註

您必須為專案指定至少一種類型、選擇集或選取條件。 您可以使用的子項目數目沒有上限。

選取條件是用來定義必須存在才能使用之專案的條件，例如當物件具有特定屬性時，或特定屬性值或腳本評估為時 `true` 。 如需選取條件的詳細資訊，請參閱[定義使用視圖專案或專案時的條件](./defining-conditions-for-displaying-data.md)。

如需自訂控制項視圖之元件的詳細資訊，請參閱[自訂控制項視圖](./creating-custom-controls.md)。

## <a name="see-also"></a>另請參閱

[CustomEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[CustomEntry (格式的之 entryselectedby 的 SelectionSetName 元素) ](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[之 entryselectedby for CustomEntry (格式的 TypeName 元素) ](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntries for View (格式的 CustomEntry 元素) ](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[自訂控制項視圖](./creating-custom-controls.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
