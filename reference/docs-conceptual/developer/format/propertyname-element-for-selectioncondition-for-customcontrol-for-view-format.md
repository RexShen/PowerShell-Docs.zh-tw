---
title: SelectionCondition for CustomControl for View 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362347"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 SelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用定義。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for view （format） CustomEntries 元素 for CustomEntry for view （format） CustomEntries 元素Format） CustomItem 元素，用於 CustomControl for view （format） CustomEntry for CustomControl for view （format） SelectionCondition 元素之 entryselectedby for view （格式） PropertyNameCustomControl for View 的 SelectionCondition 元素（格式）

## <a name="syntax"></a>語法

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `PropertyName` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|定義必須存在的條件，才能使用控制項定義。|

## <a name="text-value"></a>文字值

指定 .NET 屬性名稱。

## <a name="remarks"></a>備註

選取條件必須指定至少一個屬性名稱或腳本，但不能同時指定兩者。 如需如何使用選取條件的詳細資訊，請參閱[定義顯示資料的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[CustomControl for View 的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
