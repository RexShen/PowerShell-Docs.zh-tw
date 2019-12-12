---
title: 設定之控制項的 CustomEntry 的之 entryselectedby 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368767"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>設定之控制項的 CustomEntry 的 EntrySelectedBy 元素 (格式)

定義使用通用控制項定義的 .NET 類型，或必須存在才能使用此控制項的條件。 此元素是在定義可供格式檔案中的所有視圖使用的通用控制項時使用。

Configuration 元素（格式）控制設定（format） CustomControl 元素的設定（格式）控制項專案的設定專案（格式） CustomControl 設定的 CustomEntries 元素（格式）Format） CustomEntry 元素，用於 CustomControl 控制項的設定（格式）之 entryselectedby 元素（用於設定的控制項）（格式）

## <a name="syntax"></a>語法

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>屬性與元素

下列各節說明屬性、子專案，以及 `EntrySelectedBy` 專案的父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 定義必須存在的條件，才能使用通用控制項定義。|
|[設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定一組使用此通用控制項定義的 .NET 類型。|
|[設定之控制項的之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|選擇性項目。<br /><br /> 指定使用此通用控制項定義的 .NET 類型。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[設定之控制項的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|提供通用控制項的定義。|

## <a name="remarks"></a>備註

每個定義至少必須指定一個 .NET 類型、選取範圍或選取條件。 您可以指定的類型、選擇集或選取條件的數目沒有上限。

## <a name="see-also"></a>另請參閱

[設定之控制項的之 entryselectedby 的 SelectionCondition 元素（格式）](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[設定之控制項的之 entryselectedby 的 SelectionSetName 元素（格式）](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[設定之控制項的 CustomControl 的 CustomEntry 元素（格式）](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[設定之控制項的之 entryselectedby 的 TypeName 元素（格式）](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[撰寫 PowerShell 格式化檔案](./writing-a-powershell-formatting-file.md)
