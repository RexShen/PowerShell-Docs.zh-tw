---
ms.date: 09/13/2016
ms.topic: reference
title: 檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)
description: 檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)
ms.openlocfilehash: 78b977548243b6f3a658f15a0249d8cad12e2f1b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664919"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為時 `true` ，就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

設定元素 (格式) ViewDefinitions 元素 (格式) View 元素 (Format) CustomEntries 元素 for View (Format) 元素 for CustomControl for View (format) 元素 for CustomEntry for CustomEntries for CustomControl for view (format) CustomItem 專案 for CustomEntry for CustomControl for view (format) SelectionCondition for 之 entryselectedby for CustomControl 的 SelectionCondition 專案 (格式) 

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
|[適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在才能使用控制項定義的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

選取條件必須指定至少一個要評估的腳本或屬性名稱，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱 [定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[適用于 CustomControl 的之 entryselectedby SelectionCondition 元素 (格式) ](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[撰寫 PowerShell 格式設定檔案](./writing-a-powershell-formatting-file.md)
