---
title: SelectionCondition for 之 entryselectedby for WideControl (Format 的 ScriptBlock 元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8f2223d4a1217786a930eb82390c24b81d2f72e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787609"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>WideControl 之 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，會符合條件，並使用寬專案定義。

Configuration 元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 專案 (格式) WideEntry 專案 (格式) 之 entryselectedby 元素（WideEntry 的 SelectionCondition (格式) 之 entryselectedby 元素，WideEntry 適用于 SelectionCondition (格式) 

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、子專案和元素的父元素 `ScriptBlock` 。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|定義必須存在才能使用此定義的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

如需有關寬視圖之其他元件的詳細資訊，請參閱[Wide view](./creating-a-wide-view.md)。

## <a name="see-also"></a>另請參閱

[建立寬型檢視](./creating-a-wide-view.md)

[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)

[WideEntry 之 EntrySelectedBy 的 SelectionCondition 的 PropertyName 元素 (格式)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[WideEntry (格式的之 entryselectedby 的 SelectionCondition 元素) ](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
