---
title: 設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368447"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在的條件，才能使用通用控制項定義。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制項的設定（格式）控制項元素的元素，用於控制項的設定（format） CustomControl 元素，用於控制項的 CustomControl 的設定（格式） CustomEntries 元素設定（格式） CustomEntry 元素，用於 CustomControl 的設定（格式）之 entryselectedby 元素（適用于 SelectionCondition for 之 entryselectedby 的設定（Format） CustomEntry 元素）之控制項的 CustomEntry設定（格式）

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `SelectionCondition` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 屬性。|
|[設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的腳本。|
|[設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型集合。|
|[設定之控制項的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定觸發條件的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義使用此通用控制項定義之專案的 .NET 類型。|

## <a name="remarks"></a>備註

定義選取條件時，必須遵循下列指導方針：

- 選取條件必須指定至少一個屬性名稱或腳本區塊，但不能同時指定兩者。

- 選取條件可以指定任意數目的 .NET 類型或選擇集，但無法同時指定兩者。

如需如何使用選取條件的詳細資訊，請參閱[定義資料顯示時的條件](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[設定之控制項的 SelectionCondition 的 PropertyName 元素（格式）](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 SelectionCondition 的 ScriptBlock 元素（格式）](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 SelectionCondition 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 SelectionCondition 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式）](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
