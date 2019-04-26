---
title: SelectionCondition EntrySelectedBy 組態 （格式） 的控制項的項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075761"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>設定之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在，要使用的通用控制項定義的條件。 定義可供的格式化檔案中的所有檢視通用控制項時，會都使用這個項目。

組態 （格式） 的組態 （格式） CustomControl 項目控制項的 CustomControl 的組態 （格式） CustomEntries 項目控制項的控制項的控制項項目的組態項目 （格式） 的控制項項目針對 CustomEntry 的 EntrySelectedBy 的組態 （格式） SelectionCondition 項目控制項的 CustomEntry 的組態 （格式） EntrySelectedBy 項目控制項的 CustomControl 的組態 （格式） CustomEntry 項目組態 （格式）

## <a name="syntax"></a>語法

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節說明屬性、 子項目和父項目`SelectionCondition`項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[PropertyName SelectionCondition 組態 （格式） 的控制項的項目](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|
|[SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別集。|
|[TypeName SelectionCondition 組態 （格式） 的控制項的項目](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|定義.NET 型別，使用通用控制項定義的這個項目。|

## <a name="remarks"></a>備註

定義選取範圍條件時，必須遵循下列指導方針：

- 選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[PropertyName SelectionCondition 組態 （格式） 的控制項的項目](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock SelectionCondition 組態 （格式） 的控制項的項目](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName SelectionCondition 組態 （格式） 的控制項的項目](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName SelectionCondition 組態 （格式） 的控制項的項目](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy CustomEntry 組態 （格式） 的控制項的項目](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
