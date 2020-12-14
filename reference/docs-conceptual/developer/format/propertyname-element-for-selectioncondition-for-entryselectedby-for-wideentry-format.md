---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
description: WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)
ms.openlocfilehash: bda34b0c1e97fb85536132bedcec3986072801b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665697"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為時， `true` 就會符合條件，並使用定義。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 專案 (格式) 之 entryselectedby 專案 (格式) 專案 (格式) WideEntry 專案的 SelectionCondition (格式) 之 entryselectedby for WideEntry 的 SelectionCondition 格式之 entryselectedby 元素

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

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
|[適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|定義必須存在的條件，才能使用這個定義。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或要評估的腳本，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需廣泛視圖的其他元件的詳細資訊，請參閱 [Wide view](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)

[適用于 WideEntry (格式之之 entryselectedby 的 SelectionCondition 的 ScriptBlock 元素) ](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[適用于之 entryselectedby 的 WideEntry (格式的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
