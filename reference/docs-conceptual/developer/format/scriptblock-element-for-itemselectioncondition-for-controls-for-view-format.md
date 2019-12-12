---
title: View 之控制項的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364917"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>檢視之控制項的 ItemSelectionCondition 的 ScriptBlock 元素 (格式)

指定觸發條件的腳本。 當此腳本評估為 `true`時，就會符合條件，並使用控制項。 定義可供視圖使用的控制項時，會使用這個元素。

設定專案（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 專案（格式）控制項的控制項專案（格式） CustomControl 元素，用於控制項的 View （Format） CustomEntries 元素CustomControl for View （format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for view （format） CustomEntry 元素 for view （format） ExpressionBinding 的控制項ExpressionBinding 的 ItemSelectionCondition 元素，適用于 view （Format） ScriptBlock 元素，用於 ItemSelectionCondition 的控制項（格式）

## <a name="syntax"></a>語法

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `ScriptBlock` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|定義必須存在才能使用此控制項的條件。|

## <a name="text-value"></a>文字值

指定要評估的腳本。

## <a name="remarks"></a>備註

如果使用這個元素，則在定義選取條件時，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)元素。

## <a name="see-also"></a>另請參閱

[View 之控制項的 ItemSelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[View 之控制項的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
