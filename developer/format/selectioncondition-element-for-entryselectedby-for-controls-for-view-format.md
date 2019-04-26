---
title: 用於檢視 （格式） 的控制項 EntrySelectedBy SelectionCondition 項目 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064222"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>檢視之控制項的 EntrySelectedBy 的 SelectionCondition 元素 (格式)

定義必須存在，要使用的控制項定義的條件。 定義可供檢視的控制項時，會使用這個項目。

組態項目 （格式） ViewDefinitions 項目 （格式） 檢視項目 （格式） 項目 （格式） 控制項的 Controls 項目控制項的檢視 （格式） CustomEntries 項目控制項的控制項的檢視 （格式） CustomControl 項目CustomControl CustomEntries CustomEntry EntrySelectedBy 的檢視 （控制項的檢視 （格式） SelectionCondition 元素的控制項的檢視 （格式） EntrySelectedBy 元素的控制項的檢視 （格式） CustomEntry 元素的控制項格式）

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
|[PropertyName SelectionCondition 用於檢視 （格式） 的控制項的項目](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 屬性。|
|[用於檢視 （格式） 的控制項 SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定的指令碼，就會觸發條件。|
|[用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別集。|
|[用於檢視 （格式） 的控制項 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|選擇性的項目。<br /><br /> 指定觸發條件的.NET 型別。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|定義使用此控制項定義或必須存在於要使用此定義條件的.NET 類型。|

## <a name="remarks"></a>備註

在您定義的選取範圍條件時，適用下列需求：

- 選取條件必須指定至少一個屬性名稱或指令碼區塊，但不能同時指定。

- 選取條件可以指定任意數目的.NET 型別，或選取項目集，但不能同時指定。

如需如何使用選擇條件的詳細資訊，請參閱[定義條件的資料會顯示當](./defining-conditions-for-displaying-data.md)。

## <a name="see-also"></a>另請參閱

[PropertyName SelectionCondition 用於檢視 （格式） 的控制項的項目](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 SelectionCondition 的指令碼區塊項目](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 SelectionCondition SelectionSetName 項目](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 SelectionCondition TypeName 項目](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[用於檢視 （格式） 的控制項 CustomEntry EntrySelectedBy 項目](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
