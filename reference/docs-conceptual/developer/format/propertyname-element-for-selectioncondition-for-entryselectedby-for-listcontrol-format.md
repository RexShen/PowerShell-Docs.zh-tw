---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
description: ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: 1e318e3a29f07b157b9ae7343ba08759db8efbb5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665816"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>ListControl 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時，就 `true` 會符合條件，並且會使用清單專案。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) ListEntry 專案的 SelectionCondition (格式) 之 entryselectedby for ListEntry 的 SelectionCondition 格式之 entryselectedby 元素

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
|[適用于之 entryselectedby 的 ListEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|定義必須存在才能使用此清單專案的條件。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須至少指定一個屬性名稱或腳本區塊，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義使用視圖專案或專案的條件](./defining-conditions-for-displaying-data.md)。

如需清單視圖之其他元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。

## <a name="see-also"></a>另請參閱

[建立清單檢視](./creating-a-list-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[ListEntry 元素 (格式) ](./listentry-element-for-listcontrol-format.md)

[適用于 ListEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
