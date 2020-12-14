---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
description: TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: dcb59fc438ae217870566f09204fb16b8f031614
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665782"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a>TableRowEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用資料表專案。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) TableRowEntry 專案的 SelectionCondition (格式) 之 entryselectedby for TableRowEntry 的 SelectionCondition 格式之 entryselectedby 元素

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `PropertyName` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|定義必須存在才能使用此資料表專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須至少指定一個屬性名稱或腳本區塊，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

如需有關資料表視圖元件的詳細資訊，請參閱 [建立資料表視圖](./creating-a-table-view.md)。

## <a name="see-also"></a>另請參閱

[建立表格檢視](./creating-a-table-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[適用于 TableRowEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[適用于之 entryselectedby 的 TableRowEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
