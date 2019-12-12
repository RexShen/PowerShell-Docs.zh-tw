---
title: ItemSelectionCondition for CustomControl for View 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362437"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>檢視之 CustomControl 的 ItemSelectionCondition 的 PropertyName 元素 (格式)

指定觸發條件的 .NET 屬性。 當這個屬性存在或評估為 `true`時，就會符合條件，並使用控制項。 定義自訂控制項視圖時，會使用這個元素。

Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（format） CustomEntries 元素，用於 CustomEntry for View （Format） CustomEntries 元素的 CustomControl for view （format） CustomItem 元素CustomEntry for view （Format） ExpressionBinding 元素 for CustomControl for view （format） ItemSelectionCondition 元素 for CustomControl for View （Format） PropertyName 元素CustomControl for View （格式

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
|[CustomControl for View 的運算式系結的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定觸發條件之 .NET 屬性的名稱。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[ItemSelectionCondition for CustomControl for View 的 ScriptBlock 元素（格式）](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[CustomControl for View 的運算式系結的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
